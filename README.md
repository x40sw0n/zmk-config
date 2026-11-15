# do52pro - ZMK shield for nRF52840 Pro Micro boards

Wireless split ZMK config for the do52pro PCB using two "ProMicro NRF52840 V1940"
(nice!nano v2 compatible) controllers. Pin map derived from ilfmoussa/do52pro (QMK, RP2040),
which is reverse engineered and unverified - test before trusting it.

## Install
1. Create a zmk-config repo from ZMK's template (https://zmk.dev/docs/user-setup).
2. Copy `config/boards/`, `config/do52pro.keymap`, `config/do52pro.conf` into its `config/` folder.
3. Replace/merge `build.yaml` (keep the board name your template uses).
4. Push; download the firmware artifact from GitHub Actions.

## Flash
Double-tap RST on the controller to get the UF2 drive. For a first flash on each half:
`settings_reset` -> then `do52pro_left` (left) / `do52pro_right` (right).

## Pin map (by physical Pro Micro position)
cols (left):  GP0 P0.06, GP1 P0.08, GP2 P0.17, GP4 P0.22, GP5 P0.24, GP6 P1.00
cols (right): same pins, reversed order
rows (both):  GP27 P0.02, GP8 P1.04, GP9 P1.06, GP29 P0.31, GP7 P0.11, GP28 P0.29 (DPAD)
GP3 (P0.20) was the wired-split serial line; unused with wireless.

## Testing
If a key types the wrong thing, the matrix map in do52pro.dtsi needs adjusting - note which
physical key produces which character. The DPAD columns are the most likely to need it.
No hardware has been built with these files yet.
