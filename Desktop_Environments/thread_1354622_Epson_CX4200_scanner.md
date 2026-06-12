---
title: "Epson CX4200 scanner"
date: 2009-12-14
forum: Desktop Environments
---

### Post by Sabir V on 2009-12-14
I connected my Epson Stylus CX4200 all in one (printer/scanner/copier) and maneged to get the driver for the printer but the scanner won't work. When I start XSane it says no device. I installed all libsane packages but still no device. Can any one help?:(

---

### Post by Sabir V on 2009-12-15
I found a reply on archives by user ***fubarbundy*** dated January 19th, 2006 as this:
 
[COLOR="SeaGreen"]Re: scanning on epson cx4200
Woohoo! I know the answer for this one

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
libusbscanner 0x0003 0x04b8 0x0820 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000

7. Save and close.
8. Unplug and replug your printer/scanner.
9. Run XSane (Applications/Graphics).
10. ???
11. Profit!

NOTE FOR OTHER EPSON STYLUS CX/DX SERIES (UNTESTED):

0x820 is the Product ID for the DX4200. If you are using another multifunction (e.g. DX3800, DX3850, DX4250, DX4800, DX4850), you need to replace this in the two files above with your multifunction's product ID. To find this, run the device manager from System/Administration. In the devices list on the left, click the line that says "USB Vendor Specific Interface". Then click the "Advanced" tab on the right, and scroll down to usb.product_id. You want the number in parentheses (brackets).

E.g.

usb.product_id int 2080 (0x820)

would be 0x820

Good luck!

p.s. if anyone has a solution to xsane out of memory errors at high resolutions, let me know [/COLOR]

But I got stuck on point 5, the file libsane.usermap is not found and thus can not be edited! ANY HELP?:(

---

### Post by Sabir V on 2009-12-23
I got busy for while and hadn't enough time to carry on the problem. Lately I searched Epson website for support and got re-directed to:

[COLOR="DarkGreen"]http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do
[/COLOR]
where I selected all what implies to model, version, etc..., then I downloaded the file:

[COLOR="DarkGreen"]iscan-plugin-cx4400_2.1.0-1_i386.deb[/COLOR]

which works with Hardy, installed, ran Xsane, and everything fine.:P, UBUNTU ROCKS:guitar:

---

