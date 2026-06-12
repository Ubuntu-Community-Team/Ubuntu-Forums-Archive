---
title: "scanning on epson cx4200"
date: 2005-11-23
forum: Desktop Environments
---

### Post by goneskiing on 2005-11-23
I have an all-in-one epson cx4200 - I installed as a printer with driver cx3200, works okay for printing.  But when I try to run the scanner app from the menu, it cannot detect a scanner device.  Do I somehow need to define the scanner driver and any ideas on how I can find the right scanner driver ?  thanks.

---

### Post by moon2js on 2006-01-11
Did you ever get the scanner functionality?

Anyone else have a Epson Stylus CX4200 (printer/scanner combo)?

Is there any disadvantage to simply using the CX3200 driver? How do I check to see if a CX4200 driver is available somewhere? I have a fresh installation of Breezy and the drivers only go up to CX3200 and then skip up to the CX5100s.

---

### Post by fubarbundy on 2006-01-19
Woohoo! I know the answer for this one :-)

By the way, isn't it DX4200?

1. Install sane
2. In a terminal or from Alt-F2:

sudo gedit /etc/sane.d/epson.conf

3. On a new line after "# usb 0x4b8 0x110", type:

usb 0x4b8 0x820

4. Save and close.
5. In a terminal or from Alt-F2:

sudo gedit /etc/hotplug/usb/libsane.usermap

6. After the 2 lines for the Epson CX5400, type:

# Epson Corp.|Stylus DX4200
libusbscanner             0x0003      0x04b8   0x0820    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000

7. Save and close.
8. Unplug and replug your printer/scanner.
9. Run XSane (Applications/Graphics).
10. ???
11. Profit!

NOTE FOR OTHER EPSON STYLUS CX/DX SERIES (UNTESTED):

0x820 is the Product ID for the DX4200. If you are using another multifunction (e.g. DX3800, DX3850, DX4250, DX4800, DX4850), you need to replace this in the two files above with your multifunction's product ID. To find this, run the device manager from System/Administration. In the devices list on the left, click the line that says "USB Vendor Specific Interface". Then click the "Advanced" tab on the right, and scroll down to usb.product_id. You want the number in parentheses (brackets). 

E.g.

usb.product_id       int       2080 (0x820)

would be 0x820

Good luck!

p.s. if anyone has a solution to xsane out of memory errors at high resolutions, let me know :-)

---

### Post by dougemd on 2006-02-20
I have the same issue when scanning 1200 dpi. It says out of memory.

---

### Post by beriiisek on 2008-05-17
You most in users and groups allow SCANNING...

---

