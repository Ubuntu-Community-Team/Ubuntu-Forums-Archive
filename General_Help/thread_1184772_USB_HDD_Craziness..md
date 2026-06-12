---
title: "USB HDD Craziness."
date: 2009-06-11
forum: General Help
---

### Post by BurnGates on 2009-06-11
First Up - I'm a total n00b and incompetent at most computer stuff so it'd be easiet if you talk to me like i'm an infant ;)
 
The problem's my Maxtor Basics 500gb USB HDD, which I was hoping to use as an intermediary between windows and Ubuntu (The HDD with Ubuntu on it is relative small - only 15gb).
 
Ubuntu seems to recognize the device no problem, but when i try to play mp3s off it (Exaile), the songs play for a while and then Maxtor seems to get disconnected - Exaile says the songs don't exist+drive icon disappears from the desktop, led is off on device. my usb wireless card (with which there have been no other problems) also seems to disonnect.
 
after shut down i get this:
 
[4608.232177] hub1-0:1.0 unable to enumerate usb device on port 2 - I get the same message for port 3 (one being hdd, other being wireless card). At this point i get a command line - but don't know how to use this to shut down or anything. 
 
Is this a problem with my USB hub?
 
sorry this is so verbose.

---

### Post by Frenziefrenz on 2009-06-11
I don't know about your USB issues, but you can use "sudo shutdown" on a command line to shut your computer down. It might need an extra argument like "-h now" or something, I'm not too sure about that.

---

### Post by synapsys on 2009-06-11
did you format the drive before copying files to it? If you want it to be read by both ubuntu and winblows then ntfs is your best option. If you did format it, it sounds like a problem with your wireless usb adapter. Have you tried the same thing in winblows?

---

### Post by BurnGates on 2009-06-11
No I didn't reformat  - just used it straight out of the box. what is ntfs? 

Is that something to do with file structure? How can I find out what it is currently?. 

the drive works fine in XP. 


Don't think the wireless adapter is the problem - my Internet works even better in Jaunty than in XP. 


BTW - thanks guys:)__[]("http://ubuntuforums.org/member.php?u=850688")

---

### Post by BurnGates on 2009-06-12
Anyhoo, consider this solved -

I'm gonna use the ultra techy option of just copying the media I want from Maxtor to Ubuntu hdd and play it from there, unmount maxtor and leave well enough alone. 

Peace out

---

