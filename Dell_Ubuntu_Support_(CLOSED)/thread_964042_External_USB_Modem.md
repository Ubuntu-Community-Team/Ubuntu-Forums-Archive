---
title: "External USB Modem"
date: 2008-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by woodfern on 2008-10-30
[FONT="Comic Sans MS"][SIZE="2"]So far I am on #4 (below). I highlight the debian folder (which has a lic. and a 1386 file in it) and click copy but then the paste is not active.  Plus I have no idea where I'm pasting it?  Could someone please give me some help?  Thank you....

This is the modem I got.

 Dial-Up External USB Modems
 Model 3095 V.92 USB Mini External
Miniature 56K modem works with Windows, Mac, and Linux computers

The low-cost Model 3095 modem plugs into the USB port of any notebook or desktop computer. It's miniature design makes it ideal for travel or use in your office.

The Model 3095 is approximately the size of a disposable lighter. The modem’s short, integrated cable plugs directly into a computer USB port, and the other end of the modem connects to a phone jack through a standard phone cord. The standard phone cord is easy to replace if it’s lost or forgotten, a considerable advantage over the proprietary phone cords used with most PC Card modems.

The modem’s power is provided by the computer’s USB port, eliminating the need for a power adapter when traveling, and reducing power adapter clutter in the home or office.

These are the instructions I am trying to follow.

Installing the Modem on a Linux PC

1  Plug the modem into any USB port on your computer.
2  Connect one end of the supplied telephone cable to the phone jack on the modem, and the other end of the cable to a wall telephone jack.
3  Insert the modem CD into your CD-ROM drive, double-click the CD icon, and open the Linux folder.
    You will see three folders containing Linux drivers: rpm, debian, and tar.
4  Select the appropriate folder for your version of Linux, and copy the folder to your computer.
5  From the command prompt, access the folder containing the driver.

•	To install the driver in. rpm or. deb format:
a	Type su (for rpm) or sudo (for debian) and press Enter.
b	At the prompt, enter your super user password.
C	Next, for.rpm, enter
   rpm -i dgcmodem.i386.rpm For deb, enter
   dpkg -i dgcmodem i386.debd	At the prompt, enter the Linux source build directory that matches your running kernel.
e	If necessary, run dgcconfig to complete the installation.
To install the driver in . tar format:
a	Extract the driver with
tar -xzf dgcmodem-1.Ol.tar.gz
b	Change to the driver directory with cd dgcmodem-1.01
C Enter
su make install or
sudo make install
d	At the prompt, enter your super user password.
[/SIZE][/FONT]

---

### Post by woodfern on 2008-10-31
I forgot to say this is on the Mini 9.
Is this the wrong forum for this question?
Thanks....

---

