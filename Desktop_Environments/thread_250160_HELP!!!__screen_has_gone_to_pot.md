---
title: "HELP!!!  screen has gone to pot"
date: 2006-09-03
forum: Desktop Environments
---

### Post by elpuerco on 2006-09-03
I have been using Kubuntu all weekend and everything has been tip top.

The only thing was that the screen resolution was set at 1440 wide or there abouts which meant lots of space on screen but writing very small.

I changed display settings to 1024*768 and all was well.  I then rebooted and it has defauled to 640 * 480?

I set to 1024 * 768 which is now the max and it all goes ga ga?

I have an ATI Mobility 9700.

In Windows XP allows resolution up 2048 * 1536 

Can anyone help me please?

---

### Post by ispmarin on 2006-09-03
Maybe the xorg configurations are wrong. You can try to 
sudo dpkg-reconfigure xserver-xorg
and then set the resolution that you want. Also, you can try to edit the
/etc/X11/xorg.conf
to change the modes. Are you using the right driver for your card?

---

### Post by elpuerco on 2006-09-03
Hi,

OK thanks for this...

I will give it a go to see what happens....

In the Display settings in Ku it just says ATI

---

### Post by elpuerco on 2006-09-03
Ok I ran the sudo dpkg-reconfigure xserver-xorg command and I now have it back to as it was.

In the display settings it is set to 1400 * 1050 which makes everything very small!

The driver is set to ATI (fglrx)

In the list there is no entry for ATI Mobility Radeaon 9700 :(

---

### Post by ispmarin on 2006-09-03
Not problem with your board it is not in the list, if you are using the flgrx driver everything is fine. You can try to enlarge the font size on the System -> fonts panel.

---

### Post by elpuerco on 2006-09-03
Hi,

OK I have played about with font settings etc and the window title, menus and toolbars are much better and readable.  However the actual window content remains tiny.

As I type now although it is nice to see so much on the screen it is very very small text!!

---

