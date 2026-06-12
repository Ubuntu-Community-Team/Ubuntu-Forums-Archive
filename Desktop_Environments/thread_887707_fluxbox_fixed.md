---
title: "fluxbox fixed?"
date: 2008-08-12
forum: Desktop Environments
---

### Post by legit on 2008-08-12
hey all,

originally I was going to follow this guide ([http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)) to install fluxbox because it said that:
> FLuxbox is in the ubuntu repositories but they are two versions behind and are missing a lot of handy features like fluxbox-generate_menu. Also, the package in the repositories loads really slow wich should not be the case for a window manager that's supposed to be really fast.

However, after looking in the repositories it looks like version 1.0 is available which is what the fluxbox site has for download as well.  so I was wondering if the version in the repositories fixes the problems stated above?

thanks,
- legit

---

### Post by snowpine on 2008-08-12
> **legit said:**
> hey all,

originally I was going to follow this guide ([http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)) to install fluxbox because it said that:


However, after looking in the repositories it looks like version 1.0 is available which is what the fluxbox site has for download as well.  so I was wondering if the version in the repositories fixes the problems stated above?

thanks,
- legit

Hi Legit, if you read all the way through to page 23 (!!!!) of that thread, you'll learn that the version in the Hardy repos is up to date. :) The original guide is from 2006.

(edit) ps I use fluxbox hardy every day and have never had problems with menus not updating like they used to. It also fixes an annoying fluxbuntu bug where there were separate menus for Apps and Applications. :)

---

### Post by legit on 2008-08-12
sweet thanks! :)

---

### Post by Lutherian on 2008-08-15
Hey legit, I've got the answer to your fluxbuntu woes.
Unfortunately, fluxbutu seems to be an abandoned child, and it makes me sad, because I am a big fan of Ubuntu. I found the answer in Linux Mint Fluxbox edition, after an experience with the non-functioning fluxbuntu ISO.

Linux Mint Fluxbox works outof the box and it even has almost all common codecs pre-installed and fluxbox-generate_menu is in there as well. It's built on top of xfce so it uses thunar for file managment and similar issues. Using xfce is a good idea as it's also light on resources.

Also, linux mist uses the ubuntu repos - so you haven't abandoned ubuntu. I hate to say this, but Linux Minut Fluxbox, is what Fluxbuntu should have been.

Unfortunately, they have a small development community and are trying to get a version based on Hard Heron off the ground and I'm going to give them my full support in anyway I can. (Anyone want to join me?) .. what's the alternative ...wait another year for fluxbuntu 8.04 to arrive, and then will the ISO file even work, like the last one did?

---

### Post by snowpine on 2008-08-15
> **Lutherian said:**
> Hey legit, I've got the answer to your fluxbuntu woes...

Hi Lutherian, sweet, thanks for the tip! I will definitely check out Linux Mint Fluxbox. 

However, Legit's question had nothing to do with Fluxbuntu... I think you are confusing Fluxbuntu (the distro) with Fluxbox (the windows manager). :)

ps If you're having trouble installing Fluxbuntu, why don't you start a thread and I'll try my best to help--I have installed successfully on 2 different computers and several virtual machines.

---

### Post by snowpine on 2008-08-15
Lutherian, thank you so much for turning me on to Linux Mint Fluxbox! There are some good ideas in there that I will definitely borrow for my own Fluxbox install.

Overall, however, I was extremely unimpressed by this distro. I tried it on a virtual machine with 64mb of ram (the minimum for Fluxbuntu) and it wouldn't even boot. I upped the ram to 96mb, still nothing. I increased it to 128mb. It finally loaded to the desktop, but then immediately crashed when I tried to run Firefox. Frustrated, I doubled the ram to 256mb, and finally was able to boot up, where I saw the menu had some neat features I might borrow for my own menu file. There is some good stuff there, but I fail to see how a distro that requires 400% of the system resources is "what Fluxbuntu should have been."

Most troubling, I learned ([http://www.linuxmint.com/blog/?p=235](http://www.linuxmint.com/blog/?p=235)) that by visiting their page and downloading Linux Mint, my computer may be infected by a Trojan virus!!! This is completely unacceptable and I could never in good faith recommend Mint to anyone. :(

Well I just realized this is extremely off-topic, so my apologies for the rant. :)

---

### Post by Lutherian on 2008-08-16
Hi snowpine. Yup, I saw the info about the trojan, but it's win32 based ... and yes, I've heard some issues about memory usage - which is a concern for me. On the topic of fluxbox, if you have any examples of fluxbox + ubuntu configurations that use minimal resources, could you tell me about them?
Your system's build sounds pretty interesting .. was it standard ubuntu with the fluxbox ontop?

---

### Post by snowpine on 2008-08-16
> **Lutherian said:**
> Hi snowpine. Yup, I saw the info about the trojan, but it's win32 based ... and yes, I've heard some issues about memory usage - which is a concern for me. On the topic of fluxbox, if you have any examples of fluxbox + ubuntu configurations that use minimal resources, could you tell me about them?
Your system's build sounds pretty interesting .. was it standard ubuntu with the fluxbox ontop?

Hi Lutherian, the system I am using was really easy to put together:

0. If you already have a satisfactory working OS on your computer (Ubuntu. Mint, Debian, etc), skip to step 2. 
1. Install Crunchbang using the Live CD (or, if you are low on ram,  install Cruchbang using [the alternate method]("http://http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation"), which I've tested down to 64mb of ram; follow the link to see my notes.). I chose Crunchbang for the base because its default applications cover 99% of my needs.  
2. apt-get install fluxbox
3. (optional) Insert a Fluxbuntu install CD. Find and install the fluxbuntu-artwork package (it's in a folder called 'pool').
4. Switch to Fluxbox by logging out and choosing it in Sessions. 
5. Customize your Fluxbox (menus, startup, keys, etc); the link in Legit's OP is a good guide.

It was really simple to set up, and I really enjoy having my pick of Openbox (Crunchbang's default) and Fluxbox sessions. It's not *quite* as light and fast as Fluxbuntu (which I have a lot of experience with), but it is up-to-date with 8.04.1 and uses "full-featured" applications, which I prefer to the "lightweight" ones in Fluxbuntu. 

ps So sorry, Legit, for hijacking your thread!!!

---

### Post by Lutherian on 2008-08-18
I've never heard of Crunchbang, will check it out.
Thanks, snowpine for the info, and thanks to legit for starting the thread in the 1st place.
What we've learned:
1) Fluxbox + Hardy is working
2) Don't confuse fluxbutu with Ubuntu + fluxbox
3) LinuxMint Fluxbox has some good ideas, worth checking out
4) It's possible to run a fluxbox system in 64 MB RAM (wow!)
5) Crunchbang is something for fluxheads to checkout

not bad for a sinlge thread.

---

### Post by billgoldberg on 2008-08-18
If you are new to fluxbox (you didn't mention) you should find my guide in my signature to be a great help.

It's written under the assumption you installed fluxbox from the hardy repo's, but should work on most other distro's also.

---

