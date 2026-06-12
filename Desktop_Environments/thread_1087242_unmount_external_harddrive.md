---
title: "unmount external harddrive"
date: 2009-03-04
forum: Desktop Environments
---

### Post by M@rco on 2009-03-04
To be able to toggle between Linux(ubuntu 8.10) and Windows XP on my system  I have to 'remove safely' (unmount) my external hard drive in Windows XP to be able to boot again in Linux. If not, Linux won't boot. So far my internetsearch hasn't come up with anything usefull. 

Any suggestions?

Thanks in advance!

---

### Post by hexanol on 2009-03-04
And when you say that you have to "remove safely' (unmount) my external hard drive in Windows XP to be able to boot again in Linux.", you are not unplugging it after, is this right ?

And when you say Ubuntu won't boot, what kind of error are you getting ? Is the error happening just after you select an entry in the grub boot menu ?

---

### Post by InspiredIndividual on 2009-03-04
I checked on my Windows XP install, and I can easily unmount external media by right-clicking the media in Windows Explorer and choosing 'Unmount' or 'Eject' or 'Safely remove disk'  or something like that. You don't have such an option? If not, were there any pre-installed utilities on your external harddisk? My USB-stick, for example, has a pre-installed utility that sits in my taskbar and enables me to unmount. If neither is the case for you, is there any documentation provided about your harddisk?

By the way, I did a quick web search and this seems to be a common Windows problem. Shutting down all virus programs seems to help for some users... Anyway, if my suggestions do not help you, you may be well advised to ask your question on a Windows forum, as the problem seems to be related to Windows and not Ubuntu.

---

### Post by M@rco on 2009-03-04
yes, i just unmount and not fysically remove my external usb drive in windows. If i do not, the ubuntu booting process will stall, giving me error warning 'Buffer I/O error on device sdb2'.

I know i could just unmount leaving windows, but it is just plain unpractical to have to do it everytime. Besides: a good friend of mine claims he never has to unmount his external drive before leaving windows... Isn't that an indication that it's not just a windows-related problem?

---

### Post by M@rco on 2009-03-04
.

---

### Post by InspiredIndividual on 2009-03-05
> **M@rco said:**
> yes, i just unmount and not fysically remove my external usb drive in windows. If i do not, the ubuntu booting process will stall, giving me error warning


Am I understanding you correctly here? You say you do not physically remove the external usb drive, and this causes stalling of the ubuntu boot process. What about physically removing the drive after unmounting, could that solve your problem?

> 
Besides: a good friend of mine claims he never has to unmount his external drive before leaving windows... Isn't that an indication that it's not just a windows-related problem?

Not necessarily... I'm not saying it's a Windows problem for sure, but the fact another Windows user doesn't have the problem doesn't necessarily mean it's not a Windows problem. In order to try and provide you with useful information, I searched the web a bit. Several Windows blogs and fora that related to this particular problem mentioned it is quite common in Windows. That's what I based my observation that it seems to be a quite common Windows problem upon. 

I'll specify what I meant to transcribe in my previous post. The problem is unlikely to be Ubuntu related. I do not know whether Windows or the external drive is causing the problem. In either case you might be better off asking your question on a Windows forum as well, because the problem seems to be much more regular in Windows than in Ubuntu. As this is an Ubuntu forum, it's less likely people will know the solution to what seems to be a Windows based problem (regardless of whether Windows or the drive is the cause of the trouble).

---

