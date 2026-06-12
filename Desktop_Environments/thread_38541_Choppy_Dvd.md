---
title: "Choppy Dvd"
date: 2005-05-31
forum: Desktop Environments
---

### Post by HoyesHappiness on 2005-05-31
I have read through all of the forums on DVD's on this site and I still cant get rid of my choppy DVD play. 

I did everything they suggest here:
[http://ubuntuguide.org/#DVDplayback](http://ubuntuguide.org/#DVDplayback) 

I update the codecs.  Im really not sure what else to try.  I have tried using xine and Totem Movie player.  

Can anyone make some suggestions to what i could try.

Thanks

---

### Post by codejunkie on 2005-05-31
have you tried enabling dma on your dvd drive? that helped my dvd preformance alot.

---

### Post by HoyesHappiness on 2005-05-31
Yeah. tried that.

---

### Post by logan2004 on 2005-06-01
please post your hardware specs

---

### Post by SNo0py on 2005-06-01
Same problem here - and DMA is enabled and everything worked fine with Gentoo... but Ogle just stops playing and mplayer refuses to play AVI files and all that stuff...

That's the only thing I don't like in Ubuntu - that the DVD and video playback does not really work...

---

### Post by logan2004 on 2005-06-01
did you try vlc to play videos?

gnome-vlc

you may also need the vlc audo plugin

---

### Post by chz on 2005-06-20
i am getting the same thing. i have hoary on my pc and i noticed the choppy playback  but thought it was my hardware, then i upgraded my laptop from warty (where dvd playback was smooth) to hoary and now i am experiencing the same thing on my laptop, so it must me some issue somewhere in hoary.

---

### Post by YaAqoB on 2005-06-21
I had the exact problem.
I installed Xine and that almost fixed it. Then I enabled DMA and had to edit something in the DMA editing file from CDRom to DVDRom or someting. I'm sorry this is vague, I just followed a howto from this forum some where but I can't find it.
After the above Xine runs my Divx's and DVD's mint as.
I'll try to find the howto I followed.

---

### Post by irusun on 2005-06-21
Maybe [this thread](http://www.ubuntuforums.org/showthread.php?t=22026) would be of some help...

---

### Post by YaAqoB on 2005-06-21
I did what they said in this thread and changed it to /dev/dvd and that worked for me.

[http://www.ubuntuforums.org/showthread.php?t=35584&highlight=dma](http://www.ubuntuforums.org/showthread.php?t=35584&highlight=dma)

---

### Post by irusun on 2005-06-21
I just did a little test playing a VOB file ripped straight from a DVD...

Totem plays full screen kind of slow/choppy, though the sound is at normal speed.  It would appear to be an issue with Totem, because...

Xine plays full screen perfectly.

Mplayer just crashes... which is unfortunate because it's been my favorite.  I know that Mplayer *should* be able to play it perfectly because it plays perfectly when using gentoo on this same computer.

Edit: I should add, that looking more closely at Totem, it's unfortunate that it's not working so well either... it has a really elegant interface...

---

### Post by ritger on 2005-06-21
So, try installing totem-xine. It's totem, except for the fact that it uses xinelib instead of gstreamer.

---

### Post by TristanMike on 2005-06-21
I'm having the same issue with Totem, did installing Totem-xine work??  How do you check to see if DMA is enabled?

TristanMike

---

### Post by irusun on 2005-06-21
[QUOTE=ritger]So, try installing totem-xine. It's totem, except for the fact that it uses xinelib instead of gstreamer.[/QUOTE]
tome-xine works nice.  Thanks!

[QUOTE=TristanMike]How do you check to see if DMA is enabled?[/QUOTE]
See links posted on previous page... HTH.

---

### Post by TristanMike on 2005-06-21
I'm sorry, I still don't really get the hang of commands yet and the links were confusing......only a week fresh.  How do I tell which hd"?" is my DVD, or just my CDrom or my actual hard drive?  I'm still very stupid.
TristanMike
Edit: I just checked, I'm already using Totem-xine, but still choppy...also, haven't really "configured" my computer yet, that is to say update video card drivers and such, so it might be a reason but I really don't know, I'm sorry I'm such a noob.

---

### Post by YaAqoB on 2005-06-21
TristanMike. Have a read here.
[http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

I assume if you already have DMA enabled then it will already say:

/dev/cdrom {
	dma = on
}

I could be wrong though, but this seems logical to me.  :roll:

---

### Post by TristanMike on 2005-06-21
Nice thread, I actually didn't see that one, thanks  :)  I have two roms, hdc, and hdd, how do I know which is my DVD and which is just my regular cdrom?

TristanMike

---

### Post by irusun on 2005-06-21
[QUOTE=TristanMike]I'm sorry I'm such a noob.[/QUOTE]
Didn't mean to blow you off - being new to linux doesn't = stupid.  Make sure to do a forum search first (the DMA question is a common one) and if you find the previous threads confusing, be specific about what you're not understanding so that someone doesn't just give you an answer that's still going to be confusing.

Configuring the hardware can be a key part of getting "multimedia" software to work right (audio and video drivers) - so it's a good idea to dive into that once the dma is set.

---

### Post by TristanMike on 2005-06-21
That's more than ok, I didn't think you thought that I thought that you thought  :confused: ....anyway.....I am pretty stupid, or ignorant, but that's ok, I wanna learn and it's Micro$hafts fault anyway.... :razz:  But I also don't want you to think that I post without research, I have like 6 windows open now on dma, but none of them, as far as I can see, tell me how I'm to recognise which is my DVD drive.  I haven't even gotten to edit anything cause I have two drives, the other one is a regular cdrom and when I read this.... [Quote=Firetech]Be a bit careful with enabling DMA on older CD-players, they can (and probably will) break, or just not work right.
Enabling DMA on my CD recorder (I would guess it's about 5 years old), seem to have been the reason that my computer got totally stuck twice... Last time it got stuck in BIOS while "Auto-detecting Secondary Master" (Which is the CD). This, AND some strange messages in the syslog about "ATAPI timeout" and "disabling DMA", makes me think DMA was a bad idea...
Think twice about the age of your CD player (I guess DVD playes aren't affected by this...) before enabling this.
There is a reason why there is an option in the kernel for not enabling DMA on CD-ROMs, and why the stock ubuntu kernel has this enabled.[/Quote] It made me just want to be 100% sure that I was enabling my DVD and not CD, you understand?  Is it "common sense" tho?  If my DVD is the last on the IDE cable then it's hdd and not hdc(which would be my CD rom cause it's first/slave?)?
TristanMike

EDIT:  Ok, I found which was my dvd, I went to System-Administration-Device Manager and went down to where my CD and DVD roms were and looked under the advanced tab, and there they were, in all their spectacular glory.  Enabled DMA as instructed on one of the links  :wink: and everything is running smooth now.  Thanks for all your help everyone.

---

### Post by irusun on 2005-06-21
[QUOTE=TristanMike]I have two roms, hdc, and hdd, how do I know which is my DVD and which is just my regular cdrom?[/QUOTE]
Well, I'm sure there's a command line for that, but I don't know it off hand.  

Try System Menu>Administration>Device Manager.  Look under your ATA Controller.  The second Controller will list the devices by name.  The Master is hdc and the slave is hdd.  Does that help?

(you should also be able to figure it out from the BIOS - hdc is the second controller-master and hdd is the second controller-slave).

Edit: I'm not keeping up with you!  BTW, you should be fine enabling DMA for both the cdrom and the dvd.

---

### Post by YaAqoB on 2005-06-21
You could turn your PC off and unplug the power cable to your CD Rom and then bootup and see what device is left.
Although I'm sure there will be a better way of finding out :)

---

### Post by TristanMike on 2005-06-22
[QUOTE=irusun]Well, I'm sure there's a command line for that, but I don't know it off hand.  

System>Administration>Device Manager.  Look under your ATA Controller.  The second Controller will list the devices by name.  The Master is hdc and the slave is hdd.  Does that help?

(you should also be able to figure it out from the BIOS - hdc is the second controller-master and hdd is the second controller-slave).

Edit: I'm not keeping up with you!  BTW, you can enable DMA for the cdrom and the dvd.[/QUOTE]
I musta been reading your mind cause that's just what I did, great minds think alike eh? lol

TristanMike

---

### Post by irusun on 2005-06-22
[QUOTE=TristanMike]I musta been reading your mind cause that's just what I did, great minds think alike eh? lol

TristanMike[/QUOTE]

Glad you got it figured out.

---

