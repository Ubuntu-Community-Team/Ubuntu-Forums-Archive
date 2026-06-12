---
title: "Problem to install Desktop edition 7.10"
date: 2007-12-28
forum: Dell  Ubuntu Support
---

### Post by guruntu on 2007-12-28
Hi
I'm very new to Ubuntu and have problem to install desktop 7.1 on Vista 32-bits 
Dell DXP061 
Intel  Core2 Duo 6400 2.13GHz
2GB RAM
ATI Radeon 256MB
Dell 1907FP Screen
DVD

I downloaded and burned the Live CD using the .iso  image.
Once Ubuntu menu shows up, I can't select any option or select F1 -> F6. :confused:
Neither my keyboard or mouse is alive 
But after the install option is selected automatically after 30 secs.

Then it starts to do some checks... keyboard works...

After a while it says that something like "x-server restarted 6 times the last 2 min" or so...

I tried with-> sudo dpkg-reconfigure xserver-xorg but that didn't help

I never reach the "Desktop" view in order to install Ubuntu as described.

I have also tried with alternate CD but didn't helped that much. 
The question is what's wrong and how can I start to intstall Ubuntu?

Thanks!

---

### Post by empthollow on 2007-12-28
it sounds like you may need to start in safe graphics mode or some alternate startup option.  This is a problem for you because your bios is not seeing your keyboard and you cannot press any of those options.  ARRRGH.... but wait, if you use an olde school (i.e. ps/2 keyboard) you should  be able to utilize the boot options.  if you don't have one you can usually find them at a local thrift for around $3.  I say this under the asumption that you are using a USB keyboard because that is where i have run into problems like this.:guitar:

---

### Post by woodcarver on 2007-12-29
I'd agree with empthollow, partially. Sometimes the OS doesn't recognise the USB keyboard or mouse until it is fully installed. But if Vista will work with the keyboard, then the issue isn't in the BIOS. A computer will not boot without a keyboard installed.
My suggestion is the same, get a PS2 keyboard and try it.

---

### Post by Sef on 2007-12-29
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?  (It checks the download to make sure it is good.)

2) Did you burn the iso at 4x or less? (Faster can corrupt the download.)

3) Did you check the disk? (Instead of choosing start/install Ubuntu, go down the list to check disk (or something similar.)

---

### Post by guruntu on 2007-12-29
Yes, I use USB keyboard and mouse. 
Ok, I'll try to find PS2 keyboard and try again. But the keyboard works when I switch to textmode (Alt + F1) and try to type some commands. 

md5sum compared successfully.
alternate download behaves similar.

Btw, how do I "rollback" changes made by wubi-cdboot.exe file in case I would like to use my old default vista bootloader, e.i. without OS/partition selection option that was created by wubi.

---

