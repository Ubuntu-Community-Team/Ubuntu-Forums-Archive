---
title: "Suspend Mode: High-pitch noise coming from bottom of laptop"
date: 2012-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aang_Aero on 2012-08-17
I have a Dell Inspiron Ultrabook 14z (5423) with Ubuntu 12.04 64-bit installed. I have a fresh install, nothing extra, and all the latest updates as of 8/16/2012.

Upon putting the laptop in suspend mode, either by closing the lid or explicitly entering suspend mode, the laptop then emanates a high-pitch noise similar to the hum that the old CRT Televisions make sometimes.

I have pointed out the location of the noise in the screenshot attached.

This only happens in suspend, and the noise is actually louder when entering suspend when on battery power only, and softer when on AC power.

I have ran hardware diagnostics and that all checks out ok.

Anyone have any suggestions for what the problem might be, or possible solutions?

---

### Post by 2F4U on 2012-08-17
What component is there? Maybe the CPU? This could be an indication that the laptop does not reach the intended power state and that there is still CPU activity. Are you sure that the laptop goes into suspend at all?

---

### Post by Aang_Aero on 2012-08-17
I believe that is where the RAM is located.  I did do a hardware diagnostic on the RAM, and it checked out ok.

I am sure is goes into suspend, as indicated by the power light flashing (typical to other suspends), and everything does seem to "suspend" (i.e. no noise from fans, and monitor goes black).

---

### Post by querolus on 2012-08-31
Hi,

I just bought a Dell Inspiron 14z Ultrabook recently. I'm installing the 12.04 64 bits version of Ubuntu in a partition i created with Windows through a USB stick. When the installation gets to the "Installation type" window it gets stuck. I've tried to do it in differet ways but no solution so far.
Have you had the same problem? I haven't done anything else with the computer as it is brand new and the first thing i tried was to install the Ubuntu...

I would much appreciate your help.

---

### Post by Aang_Aero on 2012-08-31
When I installed, I just installed Ubuntu over Windows.  I installed the the 500GB harddrive.

Could be something with the ISO you are using.  Do the md5 sums match?  If they do, try burning the ISO to another CD/DVD and try the install again.

When you get it installed, try suspending and let me know if you get the same high-pitched hum that I described above.  I would be interested to know if it is an issue, or just me :\

---

### Post by querolus on 2012-08-31
Ok

I'll try again this weekend. I wil let you know, if i'm able to install it, if i have the same noise...

---

### Post by querolus on 2012-09-08
Hi

I have been able to install Ubuntu succesfully. I've checked and i don't hear any special high pitch noise...

What i've realized is that the battery lasts no more than 1:30' , which is very dissappointing...

---

### Post by Aang_Aero on 2012-09-10
@querolus - Install this: [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276)

It absolutely makes a difference.

Thanks for your feedback on the topic as well :)

---

### Post by querolus on 2012-09-10
Well, i already installed Jupiter and did not find a significant difference... which is strange considering that you have the same computer...

---

### Post by Arcadeoddie on 2012-09-18
I also have the same issue with sound coming from the bottom while in suspend.

If I am using the laptop I also get a continues static sound that can be heard from under the keyboard.

This is a new XPS Dell 13" with their 'Sputnik' image.

I will tonight install the Ubuntu image instead.

---

### Post by DarioA on 2012-09-26
Hi!

I also have the same computer and a simillar problem.. but mine seems to come from the speakers and it only stops when i put the headphone. I´ve also tried to solve unsuccessfully with other distributions as Mint. 

Did u get any solution? THX

---

### Post by bcandrea on 2012-11-15
Hi,

I faced similar issues on a Dell Inspiron Ultrabook 14z (5423), trying both 32-bit and 64-bit versions of Ubuntu 12.04. The white noise seemed to come out of the speakers actually, and it was there since when I first booted the system (to be exact, even during the installation process). After some digging I found a (hacky-ish) workaround that solved the issue: it involves tweaking GPIOs at boot and when resuming the machine, and it is thoroughly documented in [this answer on askubuntu.com]("http://askubuntu.com/questions/192185/12-04-dell-14z-inspiron-5423-ultrabook-sound-noise/217672").

I hope you find it useful - and, if you do, please vote it :)

---

