---
title: "seriously need help with dual boot, ubuntu/xp"
date: 2009-01-25
forum: General Help
---

### Post by holy_hawk_saw on 2009-01-25
Hey everyone, ubuntu newbie here. I've been trying to dual boot windows and ubuntu 8.10 for weeks now it seems, and I have had the same common issue regardless of how many different ways I try to go about it. I've checked the other threads, but I'm gonna need some one on one help from anyone who's up for the challenge (much appreciation in advance :). So, I have a frankenstein computer that I have built and upgraded over the past 6 years. My mobo supports IDE as well as SATA, and I still have the original IDE HD running strong alongside a 6 month old SATA HD. I successfully installed Ubuntu (on IDE HD) and its what I have been using for about 2 months. I wanted to install ubuntu on my IDE, and XP on my SATA and dual boot that way. The problem I keep having is when I boot from my SATA, I get "verifying DMI pooling data" and freeze. My SATA works because I took it to a friends and installed XP successfully hooked to their mobo, but when I brought it back and hooked it up, "Verifying DMI pooling Data." Ubuntu recognizes my SATA HD, and I use it for storage, but it will not boot into XP. I feel like this is a mobo issue, but I seriously don't know how to fix it through linux, which is the only option I have right now. Any help super appreciated, thanks!!!

---

### Post by fooman on 2009-01-25
hello,  welcome to the forums.  :)

if xp was installed onto this hard drive while connected to another mobo,  then just disconnected and hooked up to this mobo....

chances are really slim that its just going to work. :( 

unless the mobo it was installed on and the one its hooked up to now have the same chipset and other hardware installed....its just asking too much of xp to uninstall all the drivers its already installed and then set up everything for the present machine.  a "repair" install of xp *may* work,  but the proper way to set it up (really,  the *only* way to do it right)... is with a fresh install of windows* while hooked up to the mobo that it will be used on*.

the easist way to set up a dual-boot with windows xp is to install xp first,  *then* install ubuntu.  it can still be done now if your happy with your ubuntu install and don't want to reinstall it....but after xp installs,  you will at least have to reinstall grub.

---

### Post by holy_hawk_saw on 2009-01-25
well, I thought that installing XP from another computer to my HD was fishy, but I can't even boot from the HD on my comp because it freezes at "verifying DMI pooling data", so hooking it up to another computer and installing xp was more an act of desperation to see if it would even boot, once I hooked it back up to my mobo.

---

