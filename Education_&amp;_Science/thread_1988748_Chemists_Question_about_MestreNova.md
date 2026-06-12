---
title: "Chemists: Question about MestreNova"
date: 2012-05-28
forum: Education &amp; Science
---

### Post by fennilein on 2012-05-28
hi!

I want to start using ubuntu on my new laptop, but beforehand I wanted to make sure that I can find alternatives for all the software I am using on windows currently. I am doing Chemistry and there are certain programs which I need every day...

One of them is MestreNova, an NMR-program. The thing is this... I got the files and the license from a friend on a USB and everythings works fine on Windows. Normally the license is extremely expensive and I couldn't afford it as a student. 

I am just wondering what happens if I want to install it on ubuntu? MestreNova offers the software for linux as well... so could I just download the trial version for linux and then just "copy" the license files from the windows package? 
Or would it work on with this "wine" thing? 

(sorry if all of that sounds really stupid... I am no computer genius and English is not my first language)

thank you a lot :))

---

### Post by PeterP24 on 2012-05-29
First, I am not a chemist. But I was wondering if MestreNova don't offer cheaper student versions as well. Pretty much every scientific software realise that it is in their best interest to offer student or educational versions of their software. 

As for your original question: I hope that when you say "the license from a friend on a USB" you are talking about an usb hardware key: which on MSWindows comes usually with specific driver and an associated license manager - good luck with those on wine.

---

### Post by jwpa17 on 2012-05-30
First, in spite of the glowing reviews, I've had a great deal of trouble getting anything to run correctly under Wine.  Even things that SEEM like they should be simple, let alone data acquisition software, etc.  
I've had MUCH more luck using a virtual machine with a copy of WXP installed, or even Win7.  In fact, right now in the lab, I have one chromatograph running with a virtual XP system doing data collection via a USB DAQ box and software secured by a USB "dongle."  A second system has a virtual Win-7 system running a spectroscopy program to communicate with a simple scanning UV-vis instrument.  I strongly recommend you go that route.
Good luck.

---

### Post by PeterP24 on 2012-05-30
> **jwpa17 said:**
> First, in spite of the glowing reviews, I've had a great deal of trouble getting anything to run correctly under Wine.  Even things that SEEM like they should be simple, let alone data acquisition software, etc.  
I've had MUCH more luck using a virtual machine with a copy of WXP installed, or even Win7.  In fact, right now in the lab, I have one chromatograph running with a virtual XP system doing data collection via a USB DAQ box and software secured by a USB "dongle."  A second system has a virtual Win-7 system running a spectroscopy program to communicate with a simple scanning UV-vis instrument.  I strongly recommend you go that route.
Good luck.

Yeah - I think the real denomination would be "USB DONGLE". I am really glad you worked out the issue by using a virtual machine. I am sad to mention that here, I, sometimes, cannot use the software for hours due to the license manager it comes with it. I setup it up a really low resource machine (celeron III, 512 MB RAM - WinXp due to the preference of our lab members) as a server that serves a maximum of four machines on our network due to the limitations imposed by our installed licensed manager (to be correct - by the type of licence we bought for that server licence type). It turns out that the license manager software is faulty - needing restarting the server computer several times a week because it can't find the associated clients on that network - thus stopping legitimate simulations. May I say that "remote desktop solutions" were never anticipated in this particular scientific field? I am mad (sort of a mad you gather by working 6 years in the same place and being stopped to do your work by commercial packages FEA software management)- I had to teach students for three years but I always had to deal with issue regarding the WinXp associated license manager - we had all the legal rights to run the program (like - Mr. Professor, I know my stuff, but right now, my client can't find the server you supposed to setup up)- but we were stopped by the license manager daemon - all the legitimate calls to the support never received the proper solution. It turns out that the software manufacturer and the protection provider (license manufacturer) are two different companies. Sorry for the rant - I suffered as a PhD Student for four years because of those -umm - professional software development companies companies in whatever field they do ...!

---

