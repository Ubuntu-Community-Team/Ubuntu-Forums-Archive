---
title: "Terraria lags and stutters on Ubuntu 24.04 LTS"
date: 2024-06-06
forum: Gaming &amp; Leisure
---

### Post by vhagg on 2024-06-06
Sup everyone. I switched to Ubuntu 24.04 LTS a month ago and yesterday I decided to play Terraria again. I've finished Terraria a few times on Windows 10, on the same pc, I've also passed the Calamity mod - all without issues, stable 60+ FPS. But on Ubuntu I'm getting lags and stutters that make the game unplayable... Mangohud shows constant 59-60 fps but the game doesnt feel smooth at all, especially in the caves. I posted this issue on the Terraria forums too but they couldn&#8217;t find the exact cause, some moderators said that the issue is not in the game. They recommended me to post the issue here too. 
**My specs are:**

**GPU** - Nvidia Geforce 940MX, driver version 535.171.04
**CPU** - Intel i5 7200u
**RAM** - 8GB DDR4
**Monitor** - 60 Hz

**What I tried to do:**
-Running the game with Gamemode: It made no difference
-Running the game with Vulkan: It made the game a little smoother on idle but it caused heavy visual bugs and the game still lagged heavily in caves (still with 60 FPS showing)
-Running the game with proton: Almost no difference, still laggy
-Changing the process priority to high: No difference
-Changing the Frameskip settings: It does lag less with Frameskip off, but the game is still very laggy sometimes and not smooth

By the way, Im a huge Linux noob and I dont know a lot of stuff yet.
If you need more information let me know (and please also tell me where to get it)

**Here are also a few screenshots:**
[https://imgur.com/a/terraria-laggy-screenshots-s9cf8Pz](https://imgur.com/a/terraria-laggy-screenshots-s9cf8Pz)

**Thanks in advance**

---

### Post by currentshaft on 2024-06-07
You haven't mentioned how the game was installed - Steam? Lutris? Do other games or applications lag on Ubuntu?

I would strongly consider upping your RAM, 8 GB in 2024 just doesn't quite cut it, and it's dirt cheap to upgrade.

---

### Post by vhagg on 2024-06-07
Terraria is installed in Steam, other native games seem to be running fine. I dont think that the RAM is the problem here because, again, I&#8217;ve played Terraria on this same pc on Windows multiple times with no issues. 8 GB of RAM is also supposed to be more than enough for Terraria according to the game&#8217;s requirements and resource usages. But yeah, 8 gigs is overall not a lot nowadays, but instead of upgrading it im planning to buy a new pc soon.

---

### Post by currentshaft on 2024-06-07
How did you install Steam, from a deb or Flatpak? Can you run "htop" while running Terraria and see what system resource usage is like?

---

### Post by vhagg on 2024-06-08
I installed steam with "sudo apt install steam". Here's the htop output when running Terraria - [IMG]https://imgur.com/a/FCnQzOv[/IMG]https://imgur.com/a/FCnQzOv

---

### Post by vhagg on 2024-06-11
I made and error, edited &#8220;Aptitude&#8221; with &#8220;sudo apt install steam&#8221;

---

### Post by currentshaft on 2024-06-12
My only suggestion would be to try installing Steam as a flatpak, it seems to handle drivers and dependencies a little better. Odd that it only happens to Terraria. I own a copy on Steam and will give it a try tonight.

---

### Post by vhagg on 2024-06-13
Now that I try again, other games like gothic 2 (with proton) and a few other games seem to be laggy as well&#8230; Can it be caused because of the gpu driver settings? I cant help but suspect it

---

### Post by Tadaen_Sylvermane on 2024-06-13
What gpu driver? I know in my case, granted a gt730 is old as dirt but MInecraft is unplayable with Nouveau. With proprietary it runs flawlessly. Something to consider.

---

### Post by vhagg on 2024-06-14
No, I already use the proprietary 535 driver

---

### Post by currentshaft on 2024-06-17
One way to rule out the graphics driver is to try playing a 4K video in YouTube or whatever and see if it stutters.

---

### Post by vhagg on 2024-06-18
I&#8217;ll try that

---

### Post by vhagg on 2024-06-22
I've tried a few 4K videos on YouTube and they all lagged and stuttered horribly. They would stop and buffer every 2 seconds even tho the video was loaded quite a lot...

---

### Post by currentshaft on 2024-06-23
> **vhagg said:**
> I've tried a few 4K videos on YouTube and they all lagged and stuttered horribly. They would stop and buffer every 2 seconds even tho the video was loaded quite a lot...

This sounds a lot like a driver issue. I know you said you have the latest from Nvidia, but perhaps reinstalling it would help?

---

### Post by vhagg on 2024-06-28
I have already tried that using this method - [https://askubuntu.com/questions/1344434/how-to-clean-up-reinstall-nvidia-drivers-on-ubuntu-20-04](https://askubuntu.com/questions/1344434/how-to-clean-up-reinstall-nvidia-drivers-on-ubuntu-20-04)

It didnt fix anything it seemed

---

### Post by vhagg on 2024-06-29
Oh also the version 535 driver that I have is not the latest driver for this GPU. There’s the 550 driver that you can download from nvidia’s page. Its just that 535 is in the software and updates app and its labeled as “proprietary and tested”, people said that its better to use this driver than the new one (even nvidia says that on their page as far as I remember) so I kept that one

Update: I installed the 550 version but it made it way worse sadly…

---

### Post by currentshaft on 2024-07-01
Can you boot to a live Ubuntu 24 image and try the YouTube test, without installing proprietary drivers?

---

### Post by vhagg on 2024-07-02
How do I do that? Sorry I couldnt find anything on the internet because idk much about os images and such. Do I just reinstall ubuntu or something? Or do I just install ubuntu on a flash drive and boot it from there?

---

### Post by currentshaft on 2024-07-02
Correct, just create a USB installer for Ubuntu and boot to it - you'll have the option to "Try" Ubuntu before installing.

---

### Post by vhagg on 2024-07-03
Oh alright, I’ll do that as soon as I access my laptop again

---

### Post by mimimillerms on 2024-07-10
Thank you for what you have shared.

---

### Post by vhagg on 2024-07-13
I just tried it out; I ran the “try version” of ubuntu 24.04 from a usb flash and did the youtube 4k test. It was pretty smooth, there were still small lags but, again, it was nowhere close to what I had in my installed version. Btw, I didnt install any updates or anything, I opened Firefox right after closing the ubuntu installer.

---

### Post by soonerthanlatte on 2024-07-20
I'm having the same issues running games through steam. I have the correct driver for my 1070 but both games I've tried (gmod and 7DTD) both run horribly. Tried the 4k yt video test and it plays beautifully so I'm pretty confused.

edit
HOLD THE PHONE! I sorted it out, i reinstalled steam from the official website instead of the "app center" and everything works.

---

### Post by vhagg on 2024-07-21
Yeah the snap version of steam is janky, I installed it using the repo

---

### Post by slovenskekasina on 2024-08-06
Install Steam as a flatpak

---

