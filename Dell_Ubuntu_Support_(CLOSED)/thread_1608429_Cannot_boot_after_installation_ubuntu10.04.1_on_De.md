---
title: "Cannot boot after installation ubuntu10.04.1 on Dell optiplex 980"
date: 2010-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by herbertd on 2010-10-29
Hi everyone!

I installed ubuntu 10.04.1 on Dell optiplex 980 and everything goes fine along installation, but when I reboot after livecd ejected, I select the ubuntu in grub(Another os is windowsXP), the screen is black and shows nothing, When I enter in "recovery mode", the screen shows something like 'generic usb.xxxxx quiet keyboard.xxxxx' and then black again. 

I checked the net to know there're maybe the problem about BIOS, Need I upgrade it ? I cann't download it from DELL Official website. 

Anyone know how to solve it ? Thanks a lot!:popcorn:

---

### Post by wilee-nilee on 2010-10-29
In my signature is a link to a boot script run it as described and post the text in code tags. You can generate code tags by click on the (#) in the reply window.

Also were you able to run the live cd before hand by just booting it. I just wonder if you need a graphics driver maybe.

---

### Post by herbertd on 2010-10-29
Yes, I can login with livecd, and it prompts a Problem:

No proprietary drivers are in use on this system.

and NVIDIA accelerated graphics driver(version 173) and (version current) are NOT ACTIVATED!

Is is the problem? I am trying it out.

Thanks.

---

### Post by wilee-nilee on 2010-10-29
I have been lucky with my computers all have cards that run right off the bat. Try hitting e at the grub menu and put nomodeset in the kernel line where you see no splash. This will only get you in in a low graphics mode basically to install drivers. You can remove the nosplash if you want to see the text after you hit ctrl-x after the edit to boot.

---

### Post by herbertd on 2010-10-29
[wilee-nilee]("http://ubuntuforums.org/member.php?u=906928"), you are my hero! Thanks!

[SIZE=4][COLOR=Black]nomodeset[/COLOR][/SIZE] works, and now I'm writing in the new ubuntu, that's fabulous. 

It's obviously Video card driver problem. System->Monitor shows a UNKOWN monitor, I'd better find the driver out. :guitar:

My monitor is Dell 23'', and I don't know about the video card.

---

### Post by wilee-nilee on 2010-10-29
Look in system-admin-additional drivers and see if there is anything there to activate. If I read this correctly it sounds like you don't have the drivers installed you can run this command in the terminal and it will tell you the graphic card if you need to. The nomodeset is a single session as you are using so if you reboot without drivers setup you willhave to do the same again.
```
lspci | grep VGA
```

---

### Post by herbertd on 2010-10-29
I tap 'Hard driver' and a small window splash and then nothing comes out. The window shows:

[HTML]Downloading and updating package indexes..[/HTML]

lspci shows:

```
 01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1)
```

That's the driver I want.  :KS

---

### Post by herbertd on 2010-10-29
I'm sorry to leave this thread for some hours(Off work). See you later! Thanks again.:)

---

### Post by wilee-nilee on 2010-10-29
> **herbertd said:**
> I'm sorry to leave this thread for some hours(Off work). See you later! Thanks again.:)

Have a rip roaring time I say. I'm not familiar with loading graphic drivers, but many others are so we have them identified it will probably get resolved with somebody noticing the thread.

---

### Post by herbertd on 2010-11-01
Hey I'm roaring back. 

The problem fixed partly:

Download Nvidia Linux-x86 260.19.12 Driver and install it in RECOVERY mode with 'nomodeset' in grub.

Then reboot to Recovery mode with 'nomodeset' and a 1080Ped huge screen is working for me now.

---

