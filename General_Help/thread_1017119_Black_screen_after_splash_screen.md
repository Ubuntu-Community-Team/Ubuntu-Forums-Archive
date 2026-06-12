---
title: "Black screen after splash screen"
date: 2008-12-20
forum: General Help
---

### Post by HenkR on 2008-12-20
Hi,

I wanted to try the Wubu install for Ubuntu 8.10 but it didn't go well.

-After the install in windows it needed to reboot
-After rebooting I choose Ubuntu
-The splash screen came up
-After that the screen went black
-I waited and pushed also some buttons
-After a while the pc's rebooted
-Again I choose Ubuntu
-Again it went black after the splash screen (I do hear some sound)

What can I do to make it work? I really want to try Ubuntu using the Wubi install.

My computer:
Win Vista 32bit
2GB RAM
Nvidia GForce 8800 GTS

---

### Post by HenkR on 2008-12-25
Nobody? :(

---

### Post by ginderhulk on 2009-01-04
i have the same problem

---

### Post by rben13 on 2009-01-08
I am having a similar problem, except I do get prompted with a non-graphics login. I can login and run in console mode, there is no graphical interface. I've checked the other virtual consoles using Alt-F1 to Alt-F8 and they all show logins except F7 which is a blank screen and F8 which apparently has a single log entry.

I don't know if it's relevant, but I have a nVidia 9800 GT graphics card, 4G of memory, and I asked WUBI to set up as Kubuntu.

Thanks.

---

### Post by Orlsend on 2009-01-08
Have you guys tried login in recovery mode?

---

### Post by Yashiro on 2009-01-09
Try version 8.04 instead.

---

### Post by stuv306 on 2009-01-09
When I wake up in the morning,You are all I see;When I think about you,And how happy you make me.You're everything I wanted;You're everything I need;I look at you and know;That you are all to me. More WoW news in our [world of warcraft gold](http://www.inwowgold.com/) site. By the way,We have done a great number of orders for [wow gold](http://www.inwowgold.com/) and have hundreds of orders for [wow power leveling](http://www.inwowgold.com/power-leveling/) currently. [Buy wow gold](http://www.inwowgold.com/) from our cheap wow gold and [world of warcraft power leveling](http://www.inwowgold.com/power-leveling/) shop here.

---

### Post by HenkR on 2009-02-01
I found a solution that worked for me.

I reinstalled Ubuntu using the Wubi-install. When the install in Windows is ready and it needs to reboot, I then choose Ubuntu from the bootloader. After that I hit escape and choose the safe color mode (or something similar, I don't know the exact name). I can then see the installation (no black screen). When Ubuntu starts up the first time it does an automatic update and downloads the latest drivers for my graphics card. 

I can now see all the nice effects.

Really nice.

;)

---

### Post by vipinkmar on 2009-02-09
I did the same, pressed esc after booting ubuntu, but couldn't find safe mode or similar option.

---

### Post by HenkR on 2009-02-09
Normally it should be there, but you have to press escape immidiately after you choose ubuntu (within 1 sec.)

Try reinstalling it, after the installation screen in windows, it reboots, choose ubuntu and hit escape.

You have several options there, one should be "safe graphic mode" it think.

---

### Post by Mithral on 2009-02-09
I have exactly tha same problem but when I choose recovery mode the only choice I have is to write in shell mode....
What can I do?Is there any command with which I can download the drivers?

---

### Post by thomasboleyn on 2009-02-09
Try adding the boot option 'acpi=off', this works for a lot of people who can't get past the splash screen for distros newer than 7.04.

---

### Post by Mithral on 2009-02-09
Where do we add it?

---

### Post by thomasboleyn on 2009-02-10
> **Mithral said:**
> Where do we add it?

[http://ubuntuforums.org/showthread.php?p=5278082#post5278082](http://ubuntuforums.org/showthread.php?p=5278082#post5278082)

Scroll down to Victormd's post (3rd one). This should definitely help.:KS

---

### Post by Mithral on 2009-02-10
The problem is that we don't have grub because of Wubi,so I can't press e..Nothing happens...I tried to alter the boot loader to grub but couldn't do it...so?
Btw,thanks for ur help...

---

### Post by Mithral on 2009-02-10
I've searched it around all day and found out that it's because of the ATI drivers that we can't get past the splash screen..I can't even boot from the live-cd as it is...
> **thomasboleyn**

[http://ubuntuforums.org/showthread.p...82#post5278082](http://ubuntuforums.org/showthread.p...82#post5278082)

Scroll down to Victormd's post (3rd one). This should definitely help.
After I typed sudo gedit/boot/grub/menu.lst and then noapic and noapci it booted just fine from the live cd...
But what about Wubi? I guess it's not possible...So,the only solution may be to boot it as it is and not in Windows....
And I'm saying this because I also have openSuse 11 on the Pc and when grub loads it only recognizes itself and Windows,no Kubuntu...If I choose Windows then I get the screen where I can choose between Windows and Kubuntu (that don't work)..

---

