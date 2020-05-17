# Tally

Simple tally light implementation, almost entirely unchanged from the `usb-simple` example
in [tomu-samples](https://github.com/im-tomu/tomu-samples/tree/master/usb_simple)

When connected, the device will appear as:

```
Manufacturer: "Tomu"
Product Name: "Tally Light"
Serial Number: "e018bf6d-0e3b-4f20-bf9f-c25ee5e0f769"
```

## Building

To generate a simle build:

`make`

To generate a build with a different serial number, generate one (e.g. with `uuidgen`), then:

`make TALLY_FLAGS="-D TALLY_SERIAL=YOUR_NEW_SERIAL_HERE" 

## Control

The `usbtest.py` script in this directory may be used to control the LED.

One may send a USB Control Transfers of a Vendor request type (0x40) in order to change the LED state:

 * 0: Off
 * 1: Green
 * 2: Red
 * 3: Green and Red

## Flashing to a device with autorun

To build and flash `tally` with autorun enabled, so you don't need to flash on power-on:

```
make TALLY_FLAGS="-D TALLY_SERIAL=YOUR_NEW_SERIAL_HERE -DTOBOOT_FORCE_AUTORUN"
```

If you want to be able to reflash this, you need to [short the two outer pads on power-on](https://github.com/im-tomu/tomu-bootloader#entering-toboot).
