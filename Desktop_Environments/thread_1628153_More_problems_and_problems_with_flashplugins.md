---
title: "More problems and problems with flashplugins"
date: 2010-11-22
forum: Desktop Environments
---

### Post by HotForLinux on 2010-11-22
I can't watch the videos in this page:

[http://www.rtve.es/alacarta](http://www.rtve.es/alacarta)

with these three browsers in Hardy Heron: firefox, epiphany and konqueror .  But I can see the videos in youtube.


I have upgraded the the nonfree plugin and the adobe plugin, but nothing helps.

I booted with Lucid Lynx Live-cd and, after installing adobe's flashplayer,  I could see them using firefox. But later, I installed also Arora web browser and, again, I can watch youtube vids but not those in the above link..


BTW: I think detected a bug  in the Live Lucid Lynx CD, but I don't know  if it is already fixed nor how to report it.

---

### Post by tom4everitt on 2010-11-23
I can view the videos from my Ubuntu 10.04/Google Chrome without problem. 

Google Chrome comes bundled with its own flash player, so maybe it will bypass the problem. Could be worth a try:

[http://www.google.com/chrome](http://www.google.com/chrome)

(I'm not sure whether Chromium has flash bundled or not.)

---

### Post by TBABill on 2010-11-23
Have you tried using Lovinglinux's Firefox extension called Flash-Aid? You can go to extensions in Firefox, then click "view more extensions" and when the website comes up, just search for flash aid or lovinglinux. Once you add it the extension will make sure your current flash is appropriate for your OS (meaning...if you use a 64 bit Ubuntu, it will remove the 32 bit that comes from the repo and replace it with the most current 64 bit from Adobe automatically). It will also verify the version you are using each time you open Firefox is the latest from Adobe and prompt you to update via one click to the latest if yours is not the latest. It's super simple to use and works great. I don't know if it will help any, but worth a shot and only takes about 1 minute to install and try it out and just as easy to remove if you don't like it.

---

### Post by HotForLinux on 2010-12-13
> **tom4everitt said:**
> I can view the videos from my Ubuntu 10.04/Google Chrome without problem. 

Google Chrome comes bundled with its own flash player, so maybe it will bypass the problem. Could be worth a try:

[http://www.google.com/chrome](http://www.google.com/chrome)

(I'm not sure whether Chromium has flash bundled or not.)

Thanks, I installed it time ago and remove it later. I can't remember what I disliked. Maybe it is better now. I didn't know it came with its own flashplugin bundled in it. But ,.. does it or doesn't it?

---

### Post by HotForLinux on 2010-12-13
> **TBABill said:**
> Have you tried using Lovinglinux's Firefox extension called Flash-Aid? You can go to extensions in Firefox, then click "view more extensions" and when the website comes up, just search for flash aid or lovinglinux. Once you add it the extension will make sure your current flash is appropriate for your OS (meaning...if you use a 64 bit Ubuntu, it will remove the 32 bit that comes from the repo and replace it with the most current 64 bit from Adobe automatically). It will also verify the version you are using each time you open Firefox is the latest from Adobe and prompt you to update via one click to the latest if yours is not the latest. It's super simple to use and works great. I don't know if it will help any, but worth a shot and only takes about 1 minute to install and try it out and just as easy to remove if you don't like it.

Thank you. I'll give it a try, though I solved the problem.
Browsing the web I found a place with a solution for the same case (same ubuntu version) that worked ok.

The solution was to download the .deb package, with the flashplayer plugin, from Adobe, save it and installed it later with ***dpkg -i***. The problem was trying to install it directly without saving to disk.
Cray! 
But I also tried installing from the repository and it didn't work

---

### Post by tom4everitt on 2010-12-14
> **HotForLinux said:**
> Thanks, I installed it time ago and remove it later. I can't remember what I disliked. Maybe it is better now. I didn't know it came with its own flashplugin bundled in it. But ,.. does it or doesn't it?

Oh, sorry for the confusion. Chrome does come with flash-plugin. Whether Chromium, which is the open source browser that Chrome is built upon, comes with flash I'm not sure. Flash is not very open source :P, but, on the other hand, Chrome is extremely similar to Chromium. The easiest way to find out is probably to try Chromium...

---

### Post by HotForLinux on 2010-12-19
> **tom4everitt said:**
> Oh, sorry for the confusion. Chrome does come with flash-plugin. Whether Chromium, which is the open source browser that Chrome is built upon, comes with flash I'm not sure. Flash is not very open source :P, but, on the other hand, Chrome is extremely similar to Chromium. The easiest way to find out is probably to try Chromium...

Ok, thank you, Yes, I should try it and remove epiphany that crashes every 5 minutes. I have to do all sorts of strange actions to avoid crashes, and it helps, but still crashes.
I was wrong before, what I removed because was problematic was Opera. I tried the chrome browser a little bit in a Lubuntu install and it worked nice. I think that chromium is the name of the project, while Chrome broswer and Chrome OS the software products. Isn't it like that?

---

### Post by Bleak888 on 2010-12-19
> **TBABill said:**
> Have you tried using Lovinglinux's Firefox extension called Flash-Aid? You can go to extensions in Firefox, then click "view more extensions" and when the website comes up, just search for flash aid or lovinglinux. Once you add it the extension will make sure your current flash is appropriate for your OS (meaning...if you use a 64 bit Ubuntu, it will remove the 32 bit that comes from the repo and replace it with the most current 64 bit from Adobe automatically). It will also verify the version you are using each time you open Firefox is the latest from Adobe and prompt you to update via one click to the latest if yours is not the latest. It's super simple to use and works great. I don't know if it will help any, but worth a shot and only takes about 1 minute to install and try it out and just as easy to remove if you don't like it.
Wow. I could not view some of my sites that required flash but others seemed to work. I thought I couldnt use Firefox. I tried chrome but it was extremely buggy. I tried the flash-aid and it fixed my issues with firefox. I know this was for someone else but I really appreciate that fix as Firefox has so many cool plug-ins (Flash-Aid is one) . That is great. Thanks!

---

