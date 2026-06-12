---
title: "[SOLVED] I hate GRUB."
date: 2008-12-15
forum: General Help
---

### Post by Cadeyrn on 2008-12-15
Well, for no reason, Ubuntu suddenly stopped starting up. I'm posting from my Mac side to say that every time I try, after the GRUB initialization and the Ubuntu loading bar finishes and it's all done with that, suddenly I get a bunch of lines about the system doing things with "port 7", and then all the text is wiped and I get a black screen, plus that typing blinking line thing, and the only thing my computer can do from there is shut down when I hold the power button.

Help would be appreciated.

---

### Post by jpkotta on 2008-12-15
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Try the "Backup, Repairing and Reinstalling GRUB" "Commandline" method.  The GUI method looks rather dubious or outdated.

---

### Post by Cadeyrn on 2008-12-15
Uhh... I used someone else's CD and don't have it with me. Is there a different way to do this or do I have to deal with a broken computer until late afternoon tomorrow?

---

### Post by frankleeee on 2008-12-15
If you get the problem fixed you can install startup manager from add remove which has a auto update default boot option.

---

### Post by Cadeyrn on 2008-12-15
Are you saying I can switch to Super Grub? Because if that's what you mean, I feel like running around in circles shouting happy sounds for a few hours. XD

---

### Post by frankleeee on 2008-12-15
I don't think you were addressing me but after looking at what super grub does it (sounds good) but I have never used it and would just be careful.;)

---

### Post by Cadeyrn on 2008-12-15
Yeah, I should probably backup all of stuff first.

Well, I guess if I get my hands on the Ubuntu 8.10b disc before someone gives me another suggestion, I'll carry on with jp's idea. But I would like to have my system fixed sooner.

---

### Post by falcon61102 on 2008-12-15
The Super Grub Disk works great or if you really wanted to, you could download and burn your own version of the Ubuntu LiveCD.

If you're going to be using Ubuntu, I recommend keeping a current version of the LiveCD handy just because you never know when you'll need it.  And the Super Grub Disk is not a bad thing to keep handy either.

---

### Post by Cadeyrn on 2008-12-15
XD, my internet is so slow, whether I download it or re-borrow it from my friend I won't get a chance to use it till late afternoon tomorrow. But thanks for reminding me that. Now I know I should copy the disks contents onto my own CD when I get it.

Wow, the Super Grub Disk download is only 500 KB? I can totally download it and fix my problem right now!

---

### Post by falcon61102 on 2008-12-15
Understandable with a slow connection.  

I don't know if you got the chance to take a look at the Super Grub Disk, but it's only around a 4mb download so that shouldn't be too painful.  At least it will get you up and running before late afternoon tomorrow.

---

### Post by Cadeyrn on 2008-12-15
Well, I just looked at the guide I was linked to and whether I use Super Grub or not, I'm gonna need the Ubuntu CD. But at least with my new .iso I can update Grub to Super Grub after I fix Ubuntu. That'll be SO awesome.

By the way, while we're on this subject, can someone tell me how to use the disk image to install Super Grub? Googling it does nothing more than links to download the .iso or guides to use it to restore Linux.

---

### Post by falcon61102 on 2008-12-15
If you use the Super Grub Disk you shouldn't need the Ubuntu Live CD.  Just download the Super Grub Disk .iso and burn it to a cd and reboot with it in your tray.  If you have to, press the appropriate F (function) key to be able to select your boot device and the Super Grub Disk will load and do the rest.

---

### Post by cariboo on 2008-12-15
Grub is not your problem, if you can boot up to a  black screen with just a flashing cursor, you have a problem with your video driver.

I would suggest restarting in recovery mode and once at the menu select xfix (Assuming you're running intrepid) after xfix is done select continue. You should get back to your desktop.

Jim

---

### Post by falcon61102 on 2008-12-15
Wow, thanks Jim.  I completely missed where he mentioned the Ubuntu loading bar on my first read.  

Cadeyrn,
Yeah, you're problem certainly isn't the GRUB then.  Sorry I didn't catch that.

---

### Post by Cadeyrn on 2008-12-15
Hmm, well now that I think about it the problem did arise right after I installed the Restricted ATI Radeon driver. But why didn't it take effect until my other problem regarding resolution was fixed?

EDIT: And I still wanna install Super Grub XD :D
Grub just plain sucks.

---

### Post by falcon61102 on 2008-12-15
So you installed the restricted drivers and then what happened?  What's the resolution problem?

Also did you try the xfix option?

---

### Post by Cadeyrn on 2008-12-15
Oh, the res problem was totally my fault. I accidentally set the res to 320xsomething and had to use TTY1 or whatever Ctrl+Alt+F1 takes you to to reset it. Has nothing to do with the graphics driver XD

OK, I'm about to try the xfix option now.

---

### Post by RJARRRPCGP on 2008-12-15
At least at first, it didn't even sound like it was video driver related. 

Sounded like corrupted boot data. (real early in the boot process)

(a blinking cursor may be a failing HDD)

Before the logo sounds like corrupted boot data. After the logo sounds like X crashing.

---

### Post by Cadeyrn on 2008-12-15
That was strange... When I ran xfix, although it fixed the problem, its log didn't say anything about video drivers, which I still have. It was talking about a changed xorg.conf, which of course was because of my res meddling. I think what I did to the file messed it up somehow, and so xfix restored the file, which sent my resolution from 320xsomething or maybe from the 1024x768 I had told xorg.conf to set it to to my default 1440x900. So it was the weirdest problem ever, but it's all good XD

I'm marking this thread as solved, but let's continue talking about how I'd go about installing Super Grub as my regular Linux starter.

EDIT: Aw, crap. It turns out the problem WAS that Restricted driver. I remember Compiz makes you need it to run the desktop animations, but that driver messes up Ubuntu for most people who use it. So I'm uninstalling Compiz.

Hmm... I think I'll just make a new thread for help on installing Super Grub.

---

### Post by falcon61102 on 2008-12-16
Glad you got it fixed.

---

### Post by tfy on 2008-12-16
At least it will get you up and running before late afternoon tomorrow.

---

