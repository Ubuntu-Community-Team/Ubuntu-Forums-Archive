---
title: "GRUB won't load - Error 17"
date: 2009-06-04
forum: General Help
---

### Post by mcimo88 on 2009-06-04
I recently built a new PC, with Windows 7 RC, and two hard drives. I decided the other day that I wasn't using the second hd for much anyways, so I installed Ubuntu 9.04 on it. 

Now here's the problem: when I turn on my PC, I see the normal BIOS and all that, and it says "GRUB loading, please wait..." and just stays like that, and nothing happens. Every once in a while GRUB **will** load, and everything works perfectly, Ubuntu and Windows.

But the majority of the time: nothing. I have to restart the computer and hope that it will work. Obviously not very practical. Additionally, I received an Error 17 message once.

Reinstalled Ubuntu, but still have same problem. Can anyone help? Below are my PC's specs:

Gigabyte GA-EP45-UD3P Motherboard
Intel Core 2 Quad 2.4 gHz Processor
NVIDIA GeForce 9800GT Video Card
Cooler Master CM690 Case
Rosewill RP500-2 500 Watt Power Supply
[B]650 GB Hard-drive - Windows 7 RC
150 GB Hard-drive - Ubuntu 9.04[/B]
Dual DVD-Burners
4 GB Corsair Gaming Memory
 
5 Internal Fans
12 USB Ports
5 Firewire Ports
3 eSata Ports
7.1 Channel Sound Card
SPDIF Optical Audio Out
Digital Coax Out
TV Tuner
Dual DVI Video Out
S-video In and Out
Composite Video In

EDIT: Almost forgot, I have three partitions on the Linux HD: 1-/ 2-/boot 3-swap hope that helps :)

---

### Post by t4ggs on 2009-06-04
check in the bios what HD is set as first boot device, the Windows or the Ubuntu...

---

### Post by mcimo88 on 2009-06-04
I believe right now the Windows HD is set to load first. I'll try having the Ubuntu HD load first, give me just a few minutes

---

### Post by coffeecat on 2009-06-04
> **mcimo88 said:**
> Now here's the problem: when I turn on my PC, I see the normal BIOS and all that, and it says "GRUB loading, please wait..." and just stays like that, and nothing happens. Every once in a while GRUB **will** load, and everything works perfectly, Ubuntu and Windows.

But the majority of the time: nothing. I have to restart the computer and hope that it will work. Obviously not very practical. Additionally, I received an Error 17 message once.


Grub stages 1 and 1.5 are on the first hard disc. Grub stage 2 will be on your second hard disc, specifically in the /boot/grub folder of your Ubuntu / partition. 

So sometimes grub works fine and sometimes not, and once you got an error 17. From [The grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors"):

> 
17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.By the way, although that's listed as a stage 2 error, stage 1.5 gives the same errors. Which makes me think your second hard drive is dying. Sometimes it works; sometimes it doesn't. And soon it may not work at all.

The only other thing I can think of is a BIOS problem, but I've never heard of internittent BIOS problems. My money's on a faulty HD.

---

### Post by mcimo88 on 2009-06-04
Just checked, and I do have the Ubuntu (2nd) hard drive set to load first.

coffeecat - Right now I'm logged in to Ubuntu. It seems like it's almost 1 out of every 3 times that I'm able to log in. Was using this hard drive as a secondary hd for windows before, and haven't had any problems with it, although I did get it out of my old Dell. But once grub loads, everything works perfectly.

---

### Post by coffeecat on 2009-06-04
> **mcimo88 said:**
> But once grub loads, everything works perfectly.

Good point, although dying hard drives can be infuriatingly unpredictable, sometimes working fine for long stretches.

Another thing to check would be the cables connecting the second drive, making sure they are seated securely - both ends.

---

### Post by mcimo88 on 2009-06-04
> **coffeecat said:**
> Good point, although dying hard drives can be infuriatingly unpredictable, sometimes working fine for long stretches.

Another thing to check would be the cables connecting the second drive, making sure they are seated securely - both ends.

I'm one step ahead of you, I already reconnected all the cables for both drives, so they're not going anywhere.

Now, did you say that GRUB is loaded on the second HD or the first? Because the first one shouldn't be dying, as it is brand new. The second one is older, so it is possible.

---

### Post by t4ggs on 2009-06-04
i think u should set your ubuntu disk as first disk in BIOS and the reinstall grub, being sure that it is in that disk (the same as ubuntu)

---

### Post by mcimo88 on 2009-06-04
> **t4ggs said:**
> i think u should set your ubuntu disk as first disk in BIOS and the reinstall grub, being sure that it is in that disk (the same as ubuntu)

The ubuntu disk is set to load first in bios. How do I reinstall grub? When I installed Ubuntu, I did not see an option to choose where grub is installed... I did set up a partition on the ubuntu hd for booting: /boot

---

### Post by t4ggs on 2009-06-04
chek this out
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I believe that as coffeecat said maybe there is a problem with your windows disk, i just want to be sure that the first stage of grub is in the ubuntu disk, since this one is the newer, right??

---

### Post by mcimo88 on 2009-06-04
> **t4ggs said:**
> chek this out
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I believe that as coffeecat said maybe there is a problem with your windows disk, i just want to be sure that the first stage of grub is in the ubuntu disk, since this one is the newer, right??

First HD is Newer - 640 GB - Windows 7 RC

Second HD is Older (from a dell) - 150 GB - Ubuntu 9.04

In bios, Second HD is set to load first.

Thanks for the link, I'll see if I can reinstall Grub. Can I install Grub to the first (newest) HD, but leave Ubuntu on the second (older) HD?

---

### Post by coffeecat on 2009-06-04
> **mcimo88 said:**
> Now, did you say that GRUB is loaded on the second HD or the first? Because the first one shouldn't be dying, as it is brand new. The second one is older, so it is possible.

> **t4ggs said:**
> I believe that as coffeecat said maybe there is a problem with your windows disk, i just want to be sure that the first stage of grub is in the ubuntu disk, since this one is the newer, right??

Let me just clarify what I meant. Grub stage 2 is in /boot/grub of your (older) Ubuntu disc. This is the one I thought might be dying - not the Windows one. Grub stages 1 and 1.5 will be on whichever disc you have set the BIOS to boot from. I assumed it was your Windows disc, as you said this is the first, but since then you've said (if I'm following this correctly :) ) that the BIOS is set to boot from the second. And that would mean that all stages of grub are on the second disc.

But that is actually immaterial to my suggestion. A dying hard drive affecting grub stage 2 and its partition would probably be enough to cause the symptoms you're describing - if that indeed is the problem.

There's an app in the repos that you can use to check the integrity and functioning of a HD, but frustratingly I can't remember its name. Does anyone else?

---

### Post by mcimo88 on 2009-06-04
> **coffeecat said:**
> Let me just clarify what I meant. Grub stage 2 is in /boot/grub of your (older) Ubuntu disc. This is the one I thought might be dying - not the Windows one. Grub stages 1 and 1.5 will be on whichever disc you have set the BIOS to boot from. I assumed it was your Windows disc, as you said this is the first, but since then you've said (if I'm following this correctly :) ) that the BIOS is set to boot from the second. And that would mean that all stages of grub are on the second disc.

But that is actually immaterial to my suggestion. A dying hard drive affecting grub stage 2 and its partition would probably be enough to cause the symptoms you're describing - if that indeed is the problem.

There's an app in the repos that you can use to check the integrity and functioning of a HD, but frustratingly I can't remember its name. Does anyone else?

Let me first say thank you for all the help. This is truly why I love Linux, not just because of the OS, but all the wonderful support on these forums as well.

Now, from what I understand of how you are explaining it, grub stage 2 is the actual menu where you can choose what to load, and 1 and 1.5 are the stages preceding the menu part of it? This seems to make sense as I do see a message about Grub stage 1.5, and then it says Grub is loading. Am I following correctly?

---

### Post by t4ggs on 2009-06-04
> **mcimo88 said:**
> Can I install Grub to the first (newest) HD, but leave Ubuntu on the second (older) HD?

yes u can

---

### Post by mcimo88 on 2009-06-04
> **t4ggs said:**
> yes u can

So if I do that, will this (potentially) fix my problem, if the HD grub is loaded on now is dying? I'll give it a try if it will.

EDIT: Also, since I am in Ubuntu right now, do I need to log out and use the live cd to install grub, or can I just do it straight from Ubuntu?

2nd EDIT: Sorry for all the questions, but I love learning things. What does MBR stand for?

---

### Post by t4ggs on 2009-06-04
ok, im not sure on whats going on, so i will propose a little experiment, disconnect yout ubuntu diks and let windows boot alone in order to determine wich is the "faulty" disk... mbr stands for master boot record

---

### Post by mcimo88 on 2009-06-04
> **t4ggs said:**
> ok, im not sure on whats going on, so i will propose a little experiment, disconnect yout ubuntu diks and let windows boot alone in order to determine wich is the "faulty" disk... mbr stands for master boot record

Great idea! I'll give it a go, and report back here with the results.

---

### Post by t4ggs on 2009-06-04
i forgot to tell u, in the case windows wont boot, insert the windows disk and use the windows startup repair, i dont know if its still the same in windows 7..
it will reinstall the windows boot sequence and uninstall grub, but dont worry, u can reinstall grub later with the ubuntu live cd

---

### Post by mcimo88 on 2009-06-04
> **t4ggs said:**
> i forgot to tell u, in the case windows wont boot, insert the windows disk and use the windows startup repair, i dont know if its still the same in windows 7..
it will reinstall the windows boot sequence and uninstall grub, but dont worry, u can reinstall grub later with the ubuntu live cd

Thanks. First, I realized I actually had the boot order backwards of what I originally said, so I was loading the Windows HD first, the the Linux HD. Ok, here are the results from my test.

1: First I unplugged the windows hd, and after bios, nothing happened.

2: I then unplugged the linux hd, and after bios it said that grub was loading, then I got an **error 22** message.

3: I plugged both back in and set the linux hd to boot first, and got the same **error 22** message.

4: I set the windows hd to boot first, and grub loaded perfectly for some reason.

5: I loaded the live cd, and got to the grub promt, and typed "find /boot/grub/stage1" and received the message "Error 15: File not found"

So now I am really confused... any suggestions?

EDIT: I just tried restarting it four times, and Grub loaded 3 of the 4 times normally.... but 1 of the times it did what it was doing before...

---

### Post by t4ggs on 2009-06-04
well, now im even more confused... try doing it only with the linux hd

---

### Post by coffeecat on 2009-06-04
> **mcimo88 said:**
> Now, from what I understand of how you are explaining it, grub stage 2 is the actual menu where you can choose what to load, and 1 and 1.5 are the stages preceding the menu part of it? This seems to make sense as I do see a message about Grub stage 1.5, and then it says Grub is loading. Am I following correctly?

A quick heads-up on grub and its stages. :) Stage 1, together with the partition table, occupies the first 512 bytes, (this is the master boot record, mbr), of whichever disc the BIOS is set to boot from - usually the first, but I'm now confused as to which disc you've set yours to boot from. :p Stage 1 replaces the Windows mbr. The Windows mbr calls the Windows NTLDR in the Windows C: partition. Grub stage 1 calls grub stage 1.5 which occupies the 30 kilobytes immediately after the mbr - i.e. on the same disk as stage 1. This 30 kb is an otherwise unused area of the disc.

Stage 1.5 calls stage 2 which is in your Linux root partition.

Which leads on to...

> **mcimo88 said:**
> Thanks. First, I realized I actually had the boot order backwards of what I originally said, so I was loading the Windows HD first, the the Linux HD. Ok, here are the results from my test.

1: First I unplugged the windows hd, and after bios, nothing happened.

2: I then unplugged the linux hd, and after bios it said that grub was loading, then I got an **error 22** message.

3: I plugged both back in and set the linux hd to boot first, and got the same **error 22** message.

4: I set the windows hd to boot first, and grub loaded perfectly for some reason.

5: I loaded the live cd, and got to the grub promt, and typed "find /boot/grub/stage1" and received the message "Error 15: File not found"

If it is the Windows disc that the BIOS is configured to boot from, I'm not surprised by #1. No Windows disc = no stage 1 = no boot process. With #2, if you are booting from disc 1, that is stage 1 + 1.5 present, but no stage 2, but you get:

> 
22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.Pass. :?

#3 - If you're booting from the Linux HD, then you must have grub stages 1 and 1.5 installed on that disc as well. Perhaps the error 22 is another symptom of disc 2 failing. Maybe; maybe not.

#4 Which is what it should do, I guess.

#5  :confused: 

> **mcimo88 said:**
> So now I am really confused

You're not the only one! :lol:

> **mcimo88 said:**
>  EDIT: I just tried restarting it four times, and Grub loaded 3 of the 4 times normally.... but 1 of the times it did what it was doing before...

I still reckon it's a dodgy HD - the Linux one.

---

### Post by mcimo88 on 2009-06-04
> **coffeecat said:**
> A quick heads-up on grub and its stages. :) Stage 1, together with the partition table, occupies the first 512 bytes, (this is the master boot record, mbr), of whichever disc the BIOS is set to boot from - usually the first, but I'm now confused as to which disc you've set yours to boot from. :p Stage 1 replaces the Windows mbr. The Windows mbr calls the Windows NTLDR in the Windows C: partition. Grub stage 1 calls grub stage 1.5 which occupies the 30 kilobytes immediately after the mbr - i.e. on the same disk as stage 1. This 30 kb is an otherwise unused area of the disc.

Stage 1.5 calls stage 2 which is in your Linux root partition.

Which leads on to...



If it is the Windows disc that the BIOS is configured to boot from, I'm not surprised by #1. No Windows disc = no stage 1 = no boot process. With #2, if you are booting from disc 1, that is stage 1 + 1.5 present, but no stage 2, but you get:

Pass. :?

#3 - If you're booting from the Linux HD, then you must have grub stages 1 and 1.5 installed on that disc as well. Perhaps the error 22 is another symptom of disc 2 failing. Maybe; maybe not.

#4 Which is what it should do, I guess.

#5  :confused: 



You're not the only one! :lol:



I still reckon it's a dodgy HD - the Linux one.

Wow, you really humble me with your vastly superior knowledge of linux.:KS

Anywho, I'm gonna have to do a bit more playing around with it, and if I find anything, I'll be sure to post back here. Thank you very much for your help so far, I'm sure we'll be able to figure this out eventually... :)

---

### Post by t4ggs on 2009-06-04
lol so just do one of the following options

1)use only the windows hd and with the windows cd reinstall windows mbr
or
2)use only the linux hd and reinstall grub with the live cd

this way u can detect if theres is a faulty disk
good luck

---

