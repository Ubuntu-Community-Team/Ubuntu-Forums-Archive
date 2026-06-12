---
title: "Problems with system speed - Hitachi HTS54106 Slows down - Dell Inspiron 600m -"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by jspangler on 2007-08-29
Hi,

I've been using Ubuntu Feisty Fawn for about 4 months now, and I love it. I have only one problem. Sometimes my computer (often when using firefox, but not necessarily) slows down significantly. At first it seemed random, but I seem to have figured out when it happens:

- Using flashin Firefox, especially YouTube. This often slows down my system so much I have to restart. I thought this was the problem, but:
- Downloading files, from other computers or from the Internet. This also occurs when using my USB HHD (NTFS unfortunately, I can't resize and reformat till I get another drive). It also occurs over the network. What happens is all transfers go great for a few minutes (even up to 10, 15 minutes), then everything becomes so slow, to the point that the computer becomes almost unusable and nothing more is really transferring. This even happens when reading information (such as music files) from the drive.

As stated in the title, I have a Dell Inspiron 600m, with a Hitachi HTS54106 SATI Drive. Any help anybody could offer would be really appreciated.

Thanks!

---

### Post by K.Mandla on 2007-08-29
Hi. My mother uses 6.06 on a 600m, and as far as I know, she's never had a problem like you describe.

[LIST=1]
[*]Are you using a wireless connection to access the Internet? What kind of router are you using?

[*]What video card is in your machine? Have you installed proprietary drivers for it? How did you install those?

[*]Are you using Gnome (regular Ubuntu)? Have you tried any other desktop environments?

[*]Can you check the system monitor to see if one program or another is monopolizing your resources?

[*]Does a different network (like a library wireless network or a coffee shop network) behave the same?

[*]Is the Hitachi drive in the USB drive? or is that your internal drive?
[/LIST]
I'm sure there's something in this mix that we can pin down. ;)

---

### Post by jspangler on 2007-08-29
Hi,

To answer your questions:

1. I do sometimes use a wireless connection to access the Internet. I am using a Belkin F5D6230-3 router. However, when transferring over the network I am almost always wired in. Whats interesting is that I get the same problem whether transferring files from my girlfriend's computer (setup as an NFS server) or from my usb drive.

2. I have an ATI Mobility Radeon 9000. I made some changes to my xorg.conf file a while back to get beryl to work. However, I recall having some sort of similar problems earlier. Not sure though. I don't use beryl anymore so I'm happy to reconfigure xorg.

3. I am using gnome. I have tried xfce, and the same problems arose at the same times.

4. Right now, I have been using my computer for several hours with no slow-downs, and  nothing is taking more than 2% of cpu (except for system monitor!! :-)) However, when the slowdown occurs, something is clearly taking a lot of cpu. When the problem comes from watching youtube, it shows firefox dominating resources (and sometimes it shows xorg up to 10% cpu). Right now I'm transferring files (trying to reproduce the problem) and it shows nautilus and mount.ntfs-3g around 10% (but no slowdowns yet). I will reproduce the problem and let you know.

5. Good idea. As soon as I get a chance I will check another network. However, much of my problem is with hard drive. 

6. The Hitachi drive is internal.

---

### Post by jspangler on 2007-08-29
By the way, I got a little more info for you. I didn't install any other drivers for ATI. It is set up using the FireGL driver. I also was able to reproduce the problem. I started by transferring files from my usb hard drive, which worked just fine, although if I had transferred more it would have eventually slowed everything down (of course!!). Then I opened Banshee music player and decided to reload my entire library. That did the trick. Within minutes my computer was crawling. I noticed then that Firefox was jumping up to 60% cpu, xorg was jumping between 9% and 30%, and most of the rest was taken by system monitor (this is after I forced-quit banshee, which before was taking up most of the resources). In my experience, quitting firefox completely (making sure the process actually closes) at this point does not help me regain normal system speed.

Hope that helps.

ADDITION:

Before reproducing this problem, I was using my computer very smoothly for hours. But i know when I'm gonna try to watch youtube or transfer files that it's gonna slow down. I've heard that some internal SATI hard drives have "driver issues" with ubuntu.

---

### Post by jspangler on 2007-08-29
One more thing. I do not get slowdowns while downloading even extremely large files directly from the internet. I DO get slowdowns after a few hours of downloading through bittorrent.

---

### Post by K.Mandla on 2007-08-29
Curiouser and curiouser. Well, a couple of things come to mind. 

[LIST=1]
[*]First, I don't think the SATA driver issue is doing it; if I remember right, that driver issue made installation a bear or interfered with access completely. So while I'm no expert, I'm guessing that if you had a SATA problem it would have cropped up long before now, and with much more drastic effects.

[*]I know that my mom still uses the open-source "ati" driver that comes in a default Ubuntu installation, and I know that she's also using a 9000. You could, just as an experiment, switch back the driver, and see if that has any effect. I don't think it's involved either, but you never know. ATI is shifty.

[*]Firefox is the biggest suspect from my perspective, but that would just be an educated guess. The fact that it gobbles up resources when playing movies is a problem; you could try an alternative browser and see how that behaves. By the way, are you using Flash 9, or an earlier version?

[*]Look for a BIOS update, just in case the USB subsystem had a bug or something that got ironed out later. I haven't followed my mother's computer at that level in about two years, so it's possible that there haven't even been any updates, but you never know.

[*]Find another network to try. Your router could be suspect; double-check the settings on that. I'm not sure if routers can be programmed to throttle bandwidth, but it might be that you have a stray setting in there. It's a long shot, and it wouldn't account for the system load, but it's worth checking.

[*]Find a lightweight live CD that you can load completely into memory, and then see if you can trigger another slowdown. Try the newest version of [SLAX]("http://www.slax.org") or something like that -- something very stable but very full-featured, and see if you can get it to do the same thing. Mount your internal drive into the live environment, plug in the USB drive and transfer some files. Then run Firefox past YouTube and see if it does the same thing too. The idea here is to see if the issue is solely within Ubuntu, or if it's something at the core Linux level.

[*]Finally, try an Ubuntu live CD, especially if the previous live CD works fine. It might be that something in your installation is interfering, or that there's a weird setting out in left field that's causing issues. It could also be that a recent kernel update or something is causing you problems; I've seen it happen where something silly and fundamental -- like a PS/2 mouse -- is suddenly a huge system drag because of something that changed between kernels.[/LIST]
I think that's all I can think of for now. Remember that your system logs are (most likely) inside /var/log, and you can dig through those and watch for error messages at the lowest level. It might tell you if there's a hardware-level problem that's causing the slowdown.

Good luck! :)

---

### Post by jspangler on 2007-08-30
Thanks for your suggestions! I'll get right on them today and tomorrow and see how they go.

On another note, I installed the dell sensor program, and noticed that it's running pretty hot sometimes. Could that be an issue?

And, do you recomment another browser to use?

---

### Post by mirceade on 2007-08-30
Check this [http://ubuntuforums.org/showthread.php?t=536357](http://ubuntuforums.org/showthread.php?t=536357) (regarding your temperature question).

---

### Post by K.Mandla on 2007-08-30
> **jspangler said:**
> On another note, I installed the dell sensor program, and noticed that it's running pretty hot sometimes. Could that be an issue?
I'm not sure which sensor program that is -- is it the i8k tools package?

> **jspangler said:**
> And, do you recomment another browser to use?
Hmm. Try Opera or Epiphany or maybe even Konqueror, if you don't mind adding a little KDE to your machine. You could try Kazehakase, but the point here is to overload it, not underload it, and Kazehakase might be too light.

Post back if you get any good results. Or bad results, of course. ;)

---

### Post by jspangler on 2007-08-30
Hi,

I am using the i8k tools. I managed to reproduce the problem while using opera (downloading the slax torrent). I will try that next, when I have a bit of time.

However, I noticed that along with the slowdown, my cpu temps got up to 80 degrees Celsius!  That's way too hot. I read a little more and I think my fans might be clogged, so when I get some free time and some static bags (I love my laptop too much to not do it right) I'm gonna dissasemble the thing and see if my fans are clogged.

Thanks for all your help so far.

---

