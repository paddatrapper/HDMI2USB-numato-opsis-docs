---
layout: page
title: "USB IDs"
category: getting-started
---

Due to the configurable nature of the [Cypress FX2] the board can appear under
a number of different [USB IDs]. This page tries to collect all the common 
[USB IDs] that the Opsis board can enumerate as.

More information about the USB IDs can be found at the following places;

 * [FIXME: Put a link to the USB spec here](http://FIXME/)
 * [USB in a NutShell: USB Descriptors](http://www.beyondlogic.org/usbnutshell/usb5.shtml#DeviceDescriptors)

## Summary

|                 Mode                  | Vendor ID | Product ID | Device ID | Serial No                             |
| -------------------------------------:|:---------:|:----------:|:---------:|:------------------------------------- |
|                              Failsafe | 0x04b4    | 0x8631     |   0x0     | None |
|                          Unconfigured | 0x2A19    | 0x5440     | [See Device ID table](did) | None |
|                 USB-JTAG and USB-UART | 0x2A19    | 0x5441     | [See Device ID table](did) | Device MAC |
|                         [HDMI2USB.tv] | 0x2A19    | 0x5442     | [See Device ID table](did) | Device MAC |
| *Reserved for Customer Designs (FX2)* | 0x2A19    | 0x5443     | [User defined](reserved-fx2-did) | [User defined](reserved-fx2-sno) |
| *Reserved for Customer Designs (OTG)* | 0x2A19    | 0x5444     | [User defined](reserved-otg-did) | [User defined](reserved-otg-sno) |
|                  Older [ixo-usb-jtag] | 0x16C0    | 0x06AD     |   0x4     | `hw_opsis` |
|           [fx2lib] CDC-Serial Example | 0x04B4    | 0x1004     |   0x0     | Device MAC |
|    Low Speed I/O TOFE Expansion board | 0x2A19    | 0x5445     |   0x0     | Set by FPGA firmware, should be Device MAC |

---

| Vendor ID | Vendor Name                       | Description |
| --------- | --------------------------------- | ------------------------- |
|  0x04b4   | Cypress Semiconductor Corp.       | Makers of the [Cypress FX2](Cypress FX2) chip used on the Opsis board. |
|  0x2A19   | Numato Lab                        | Manufacturers of the Opsis board. |
|  0x16C0   | Van Ooijen Technische Informatica | Original developers of [ixo-usb-jtag](ixo-usb-jtag). |
|  0x1D50   | OpenMoko, Inc.                    | Originally made phones but now have [donated their ID to open source projects](http://wiki.openmoko.org/wiki/USB_Product_IDs). |

## Device ID

| Device ID | Board Type                                         |
| --------- | -------------------------------------------------- |
|     0x0   | Unknown / unspecified.                             |
|     0x1   | First board ever created.                          |
|     0x2   | Preproduction batch, loaded with non-populated items. |
|     0x3   | Preproduction batch, sent out as part of [Champion program](https://www.crowdsupply.com/numato-lab/opsis/updates/1823). |
|     0x4   | First production board.                            |
|     0x5   | Production board.                                  |

### Serial Number

No serial number is provided in *[Failsafe Mode]* or *[Unconfigured Mode]*.

In other modes, the serial number should be the MAC Address embedded in the EEPROM.

## Failsafe Mode

If the [Cypress FX2] is unable to read from any EEPROM on boot it will boot
into [Failsafe Booting].

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x04b4 |
|  Product ID | 0x8631 |
|   Device ID | 0x0    |
|   Serial No | None   |
| Chip & Port | [USB Peripheral](/features/usb-peripheral.html), USB-B port on front. |

## Unconfigured Mode

If the FPGA is unable to provide the [Cypress FX2] with firmware, the FX2 will
boot in [unconfigured mode].

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x2A19 |
|  Product ID | 0x5440 |
|   Device ID | [See Device ID table](did) |
|   Serial No | None   |
| Chip & Port | [USB Peripheral](/features/usb-peripheral.html), USB-B port on front. |


## USB-JTAG and USB-UART

In this mode you can program the FPGA using the 
[USB-JTAG](/getting-started/jtag.html)
and talk to it using a 
[USB-UART](/getting-started/uarts.html).

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x2A19 |
|  Product ID | 0x5441 |
|   Device ID | See below |
|   Serial No | MAC Address |
| Chip & Port | [USB Peripheral](/features/usb-peripheral.html), USB-B port on front. |

The Device ID number is used to determine the mode the board is operating in.

| Device ID | Board Type                                         |
| --------- | -------------------------------------------------- |
|     0x0   | Unknown mode                                       |
|     0x1   | [ixo-usb-jtag]() mode                              |
|     0x2   | EEPROM mode                                        |
|     0x3   | CDC Serial UART mode                               |


## HDMI2USB.tv Firmware

In this mode the device appears as a USB webcam and USB serial port.

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x2A19 |
|  Product ID | 0x5442 |
| Chip & Port | [USB Peripheral](/features/usb-peripheral.html), USB-B port on front. |

## Reserved for Customer Designs (FX2)

This USB ID is reserved for customer designs running on the 
[USB Peripheral](/features/usb-peripheral.html) (Cypress FX2) connected to the
USB-B on the front of the board.

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x2A19 |
|  Product ID | 0x5443 |
| Chip & Port | [USB Peripheral](/features/usb-peripheral.html), USB-B port on front. |

## Reserved for Customer Designs (OTG)

This USB ID is reserved for customer designs running on the 
[USB OTG](/features/usb-otg.html) which is connected to the Micro-USB on back
of board.

|             |        |
| -----------:| ------ |
|   Vendor ID | 0x2A19 |
|  Product ID | 0x5444 |
| Chip & Port | [USB OTG](/features/usb-otg.html), Micro-USB on back of board. |


 [did]: #device-id
 [reserved-fx2-did]: #reserved-for-customer-designs-(fx2)
 [reserved-fx2-sno]: #reserved-for-customer-designs-(fx2)
 [reserved-otg-did]: #reserved-for-customer-designs-(otg)
 [reserved-otg-sno]: #reserved-for-customer-designs-(otg)
