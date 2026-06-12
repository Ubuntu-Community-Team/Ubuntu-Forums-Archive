---
title: "[SOLVED] Wiimote with Cwiid in Gutsy"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by booljayj on 2007-10-26
Good news- the Cwiid packages are in the repository
Bad news- they don't work

Has anyone had luck with making Cwiid work in Gutsy? From what I can tell, bluetooth devices are failing immediately. Using 'hcitool scan' results in an immediate 'no device available' without even actually scanning. This may have something to do with the new bluetooth tools in Gutsy. The bluetooth preferences will not recognize any bluetooth devices at all. Have any ideas?

<Edit>
*******************SOLUTION
When installing Gutsy, the wireless functionality of some laptops defaults to off. To turn it back on, simply press the appropriate key on your keyboard.
Typing "sudo /etc/init.d/bluetooth start" may also work.

---

### Post by Jiz on 2007-10-27
Hey i'm runnig gutsy and i compiled hcitools version 3.19 and it works as it's supposed to. Have you got bluez installed? Cause that may cause your troubles...

greetz

---

### Post by booljayj on 2007-10-28
Okay, let me explain again, I have the bluetooth preferences dialog, which means that yes, I have the bluez packages installed. I have done EVERYTHING that must be done on Feisty for this to work, and yet it still does not.

I will not compile from source code, I hate doing it. It breaks things, changes things expectantly, and has caused me to reinstall Ubuntu on several occasions. Furthermore, it should not be necessary. In my opinion, if the user has to compile the source code from the website in order for the software to work correctly, Ubuntu hasn't been doing it's job maintaining the repositories. The reason we have repositories is so that we can easily access and install programs that run well with Ubuntu.

If that is the ONLY solution to this problem, then how do I put in a request to update a piece of software in the repositories?

---

### Post by superdexter on 2007-10-30
Wow, that sounded hostile.  I should say that I had the same problem and to get the hcitool scan to work I only had to "sudo /etc/init.d/bluetooth start" and then the hcitool worked.

I'm still having a problem to identify the package that will install the pin helper (like bluez-pin or bluepin).  If anyone can post which package supplies those apps it would be a huge help for me.

Cheers!

---

### Post by booljayj on 2007-10-30
I'm sorry that sounded hostile. Thank you both for your help.

I fixed the problem, and after so much fiddling it was actually an extremely simple fix. When I installed gutsy, my wireless functionality defaulted to off, so pressing the key on my laptop to activate it solved everything. I just didn't notice that the bluetooth light was off before. Once again, thank you both for your help.

---

