---
title: "How to Beryl AIGLX Feisty Upgrade, esp: Toshiba Satellites."
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by chocolatemintmocha on 2007-04-25
If you get a blank screen when running beryl, or get really slow 3d effects, then the new feisty xorg.conf file might be the problem.
It is not the most elegant solution, but it's a solution none the less. Requirements: A floppy, usb key, internet with email, etc... An ubuntu 6.10 live cd.

1. Run the live cd.
2. While running the live cd copy /etc/X11/xorg.conf into your storage device. Or open xorg.conf in a text editor and e-mail the contents to yourself.
3. Restart the computer without the live cd, and run the installed ubuntu 7.04.
4. type sudo chmod o+w /etc/X11/xorg.conf
5. Then type sudo chmod o+w /etc/X11
6. Rename xorg.conf to something like .feistyxorg.conf
7. Paste the ubuntu 6.10 xorg.conf into /etc/X11/xorg.conf
8. type sudo chmod o-w /etc/X11/xorg.conf
9. type sudo chmod o-w /etc/X11
10. Reboot.
11. Load Beryl and see what happens.
__________________

---

