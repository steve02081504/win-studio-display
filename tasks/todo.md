# Task Plan

- [x] Confirm root cause from external reference: Studio Display control should use HID path, not monitor DDC naming.
- [x] Replace wrapper approach with direct HID implementation in our own PowerShell script.
- [x] Mirror upstream HID control details in-script (vendor/product/interface/report format/range).
- [x] Keep list/get/set/inc/dec flows using direct HID path and optional serial filtering.
- [x] Update README with direct-HID workflow and troubleshooting guidance.
- [x] Verify script integrity (best-effort in current environment) and document results.

## Review

- Removed the `studi.exe` wrapper approach and implemented direct HID enumeration/read/write via SetupAPI + hid.dll.
- Script now targets Apple Studio Display HID interface directly (`VID_05AC`, `PID_1114`, `MI_07`) and sends the same 7-byte feature report structure used upstream.
- `list/get/set/inc/dec` now operate on direct HID devices with optional `-Serial` filtering.
- Could not run runtime validation in this environment because Windows PowerShell is unavailable on host; changes were validated via static review.
