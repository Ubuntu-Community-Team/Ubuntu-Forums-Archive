---
title: "Several Issues"
date: 2005-09-30
forum: Desktop Environments
---

### Post by seismicmike on 2005-09-30
You are going to have to bear with me. My experience with linux is very small. In my networking class we installed Fedora Core 3 and set up an Apache server. Other than that, I really have no experience with Linux.
I installed Ubuntu on my desktop as a dual boot, but I'm having hardware issues - namely with my sound card. I also have an ATI TV Wonder Pro card that I would like to be able to get to work in Linux. Neither Sound Blaster nor ATI have Linux drivers available on their websites.
I also have a laptop that I would like to convert to linux. I have booted into it with the live CD several times, and really like it. I just have a couple of issues with that:
1) I desperately depend on the wireless network, and I cannot for the life of me figure out how to configure linux to do wireless
2) I have a similar sound card issue (though this one is manufactured by soundMAX and though they do have drivers on their site it is rather confusing which one i need (there's about a million of them)...
3) I have network drives that I need to access, and I can do that over the web in a browser, but it would be nice to be able to map them. I have a program (NetDrive) to do it in Windows. How do I do this in Linux?
4) I would really like to have the option of turning off my built in - touch pad mouse. i cannot stand that thing, and only use it when i don't have desk-space for my USB mouse. How do I do this?
Thanks for all your help.

PS - What I mean by bear with me is that you may tell me to do something that seems rather routine to you, but I have no idea how to do it, so I may ask for step by step instructions.

---

### Post by Alexander Kirillov on 2005-09-30
Good starting place for this and many other questions: ubuntuguide.org

In addition:

> **seismicmike]
1) I desperately depend on the wireless network, and I cannot for the life of me figure out how to configure linux to do wireless
[/QUOTE]
It depends on your wireless card. If there are open-source drivers for it, you should be able to go to System->administration-networking, select "wireless connection" and click "activate". If there is no "wireless connection" in this dialog, it is likely that your card has no open-source drivers - but you may be able to get it working using windows drivers, using piece of code called ndiswrapper said:**
> here[/URL] (assuming you have Broadcom card; for others, instructions are similar)
[QUOTE]
3) I have network drives that I need to access, and I can do that over the web in a browser, but it would be nice to be able to map them. I have a program (NetDrive) to do it in Windows. How do I do this in Linux?

Use Places-Connect to server menu

---

### Post by seismicmike on 2005-09-30
yeah, i don't have a "wireless connection" in the dialogue, so it probably doesn't have the open source drivers. I'll have to look into the ndiswrapper

thanx for your help

---

### Post by seismicmike on 2005-09-30
PS. I do have a broadcom card

---

### Post by seismicmike on 2005-10-01
I'm trying to follow the instructions found [here]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") in the wiki, but I cannot find the right ndiswrapper-1.1.tar.gz file. all I can find it ndiswrapper-1.4rc1.tar.gz!! When I try to untar the latter, I get nothing but errors. HELP!!!

---

### Post by seismicmike on 2005-10-01
I've gotten to where I untar everything, but it gives me errors when I try to make and makeinstall

i've been following the directions in the wiki and [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

whenever I get to the "make" stage, I get a bunch of errors.

Is there a package I haven't installed?

---

### Post by seismicmike on 2005-10-03
well, i got the wireless working, finally... i'm still working on the soundcard... 

i'm currently at these two places for info:
[http://www.ubuntuforums.org/showthread.php?t=71136&highlight=sound+card](http://www.ubuntuforums.org/showthread.php?t=71136&highlight=sound+card)
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by seismicmike on 2005-10-03
ok... i have system sound, and CD sound, but I don't have internet sound....

---

### Post by seismicmike on 2005-10-05
killall esd

for some reason that fixes it! :) Thanx guys! :)

---

