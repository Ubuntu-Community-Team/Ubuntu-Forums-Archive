---
title: "GNOME login manager issues"
date: 2006-01-28
forum: Desktop Environments
---

### Post by avicado on 2006-01-28
Hello!  This is my first post, so I hope I have the right forum and I hope I'm doing this correctly.  Having said that...

...I'm having problems with the resolution of my initial login screen.  I'd like it to be set to 1400 x 1050 @ 60 Hz, like it is when I'm logged in, but I'm pretty sure it's set to something different (when I move the cursor off the edge of the screen, the screen moves).

Here's what I've tried:

1) When the GNOME Login Manager window appears, there's some kind of "Configure" or "Settings" option I can choose from the menu.  Unfortunately, it asks me for the administrator password (which threw me for a 127.0.0.1, as I thought one of the nifty things about Ubuntu was that it didn't use things like root passwords), and as I don't know it, that was a dead end.

2) I edited /etc/X11/xorg.conf so in Section "Screen", SubSection "Display" for the DefaultDepth of 24, the very first Mode was now "1400x1050".  That _did_ fix it slightly -- the resolution was still wrong, but now at least the GNOME Login Manager window was centered on the screen.

I don't know if this'll help any, but I'm running Ubuntu 5.10 on an hp pavilion zt1000c laptop (with a 15-in SXGA+ (1400x1050) TFT LCD display and an S3 Savage4 AGP4X 3D graphics chipset).

Any suggestions or help would be greatly appreciated.  Thanks!  :D

Avi

P.S.  Is there a way to change the background image on the login screen as well?

---

### Post by chris_andrew on 2006-01-28
If you are entitled to use root, type the following:

sudo passwd root

This will ask you to type in your passwd, then set a password for root.

Once you have successfully done this, you can enter the root password when prompted, or type:

su -
passwd

to gain root access.

Hope this helps.

Chris.

---

### Post by avicado on 2006-01-30
Thanks!  I was able to use your tip to gain root access... unfortunately, it didn't give me any option to change the screen resolution.  Ouel.  Any other suggestions?

---

