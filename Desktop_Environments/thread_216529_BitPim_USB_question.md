---
title: "BitPim USB question"
date: 2006-07-15
forum: Desktop Environments
---

### Post by meyerto on 2006-07-15
I have successfully installed Bitpim, but my phone is not being detected. I read the 'Install BitPim' thread ([http://ubuntuforums.org/showthread.php?t=145946)](http://ubuntuforums.org/showthread.php?t=145946)), and I am looking for some further information.

First of all, on Bitpim's help page for 'Linux USB Setup', am I supposed to follow instructions for 'Direct USB access' or 'Direct USB access - udev' or both?

I have tried many permutations of the instructions to no avail. So my main question is, how do I debug this issue? I don't know how hotplug or udev is supposed to work.

Can anyone give a one-paragraph description of how the files in /etc/udev/* interact?

How does one go about debugging what is going on? What scripts can I put debug statements in to determine what is happening and what is failing?  What happens (ie what gets called) when I plug in the USB cable?

Any enlightenment would be greatly appreciated. Thanks!

-Tom

---

### Post by JerMe on 2006-07-19
I'm in the middle of changing the USB permissions for my phone and bitpim, but here's what I can help you with right now...

Use the 2nd udev guide.  To get your VID (vendor id) and PID (product id) of your phone, type **[FONT="Courier New"]sudo lsusb[/FONT]** at the terminal.  That will **l**i**s**t all **usb** at your computer.

Once you get the udev permissions straight, you *should* be able to run bitpim without root privs.  If not, use the command **[FONT="Courier New"]gksudo bitpim[/FONT]** to run bitpim as root.  I've heard bad stories about using **[FONT="Courier New"]sudo[/FONT]** with graphical applications, so be safe and use **[FONT="Courier New"]gksudo[/FONT]**.

That's where I am right now - running bitpim as root.  I'll have to restart udev or the computer to see if i can run bitpim as a regular user, but ATM at least I know bitpim is working.  Good luck!

---

