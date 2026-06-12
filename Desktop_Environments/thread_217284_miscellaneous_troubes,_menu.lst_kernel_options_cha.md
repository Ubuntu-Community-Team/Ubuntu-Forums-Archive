---
title: "miscellaneous troubes, menu.lst kernel options change, dma gets turned off"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mwolfe on 2006-07-16
I have been having two minor problems/annoyances in ubuntu lately.

First of all, in order for me to see the splash screen on bootup, with the boot text, i need to enable vga=795 in my kernel options in the menu.lst file. However it seems like this is constantly being overwritten, even when i havent updated the kernel. Any idea why does my menu.lst file get overwritten all the time, the only thing thats been updated that i can remember that last couple days is compiz (via apt-get) and yet my menu.lst file was updated..

Secondly, my dvd and dvdrw drives are constantly not booting with dma on even though i've put 

```
/dev/dvdrw {
        dma = on
}

/dev/dvd {
        dma = on
}
```

in my hdparm.conf file (which used to work fine but as of recently they are booting without dma being on)

now the only way to get dma turned on is to manually run
sudo hdparm -d 1 /dev/dvd and 
sudo hdparm -d 1 /dev/dvdrw and they will work with dma on.

any idea as to either of these problems.

---

### Post by wargames on 2006-07-16
Hi. I'm having the same problem with my dvdrw drive as well. I can't get dapper to boot with dma turned on for this drive. I've tried editing hdparm.conf as well, then rebooting but it refuses to boot with dma turned on for my dvdrw drive. I can manually turn it on just like you did. But after a reboot that setting is lost.

I even tried: sudo hdparm -d1 -k1 /dev/hdc and still dapper will not remember the dma setting after a reboot.

I'm currently still searching for an answer. Any ideas anyone? :confused:

---

### Post by wargames on 2006-07-17
DMA issue FIXED! :-D 

Here's what I did to fix my dma being turned off on my dvdrw drive after reboot.

I have an amd cpu (AMD64 Athlon). So I inserted the modules "amd74xx" and "ide-cd" into my /etc/modules file.

Then I added to my /etc/hdparm.conf file this:
/dev/hdc {
dma = on
}

Then rebooted, and now I have dma on my dvdrw drive and dvd's now play fine without any choppy video.

Here is what my original /etc/modules file looked like before I modified it:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod




And after I inserted the correct module lines:




# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
amd74xx
ide-cd
sr_mod

Through testing I discovered that I had to place the "amd74xx" and "ide-cd" between "sdp2" and "sr-mod" for it to work correctly.

I believe from the information that I read on the Ubuntu wiki related to DMA that:

for an Intel cpu you would use
piix
ide-core
ide-cd

and for a VIA Chipset you would use
via82cxxx
ide-cd

but someone with these cpu's would have to confirm this information.

Hope this helps someone.

---

### Post by wargames on 2006-07-18
I guess NOT fixed! :evil: 

Went to play a dvd today and dma is now off on my dvdrw drive. It worked fine for a day and now it's back off! ](*,) 

Why does dapper keep resetting the dma to off and ignoring my settings in hdparm.conf file? This same drive worked just fine in Breezy, and under Dapper my hard drive has dma on but dapper refuses to leave dma on for my dvdrw drive.

Any suggestions?

---

### Post by wargames on 2006-07-19
Well I'm back again.

Ok, I think I might have fixed the dma issue on my dvdrw drive.

Ignore what I said above about changing /etc/modules file.

Ok, after doing alot of reboots trying different settings, here is what I've come up with.

Basically, my dvdrw drive would lose it's dma setting when I would insert a dvd movie and even after using "sudo hdparm -d1 /dev/hdc" it would report that dma is on, but when I would play a dvd, it would get reset back to dma being off. But if I did the hdparm command a few times it would eventually keep the setting, until I rebooted or ejected the DVD and then the dma would be turned off again. Basically Dapper seemed to be having a problem remembering the dma setting just for the dvdrw drive even through I had edited my hdparm.conf file with the usual:

/dev/hdc {
dma = on
}

it would just reset the dma to off anytime I would insert a disk, so instead of inserting the /dev/hdc lines into hdparm.conf I did the following...

So here is how I fixed it:

gedit your hdparm.conf file and put this at the end:

command_line {
	hdparm -d1 -K1 /dev/hdc
}

And then reboot, and now it seems to remember the dma setting for my dvdrw drive. Or at least I hope so. [-o< 

So maybe now I can put this problem to rest, and I hope this helps anyone having problems keeping dma enabled on their dvdrw drive. :D

---

### Post by wargames on 2006-07-20
Busted again! ](*,) 

Well, I just booted up and tried a dvd movie again, only to find out that Dapper has reset the dma on my dvdrw drive back to off, even though I'm using a hdparm command in hdparm.conf. This is weird! One minute it works, then the next it doesn't. It seems to make no sense, and has a mind of it's own. Also, I noticed a few times lately, and just when I tried to boot-up Dapper that it's starting to produce some sort of error messages related to Xorg and fglrx graphics driver. I have the latest from ATI. But just like the dma issue, it doesn't have the error messages on every boot. Maybe they are related?

If anyone has any clue on how to fix this please post. I'm almost out of ideas, and patience. :( 

This same hardware worked great under Breezy, but now seems to be a bust under Dapper.

---

### Post by mwolfe on 2006-07-20
yeah its annoying, mine luckily works fine after issuing the hdparm command, even after i've played or burned a dvd (at least i think it does?).

i have no clue whats causing this and i can't believe i'm not hearing anything else about it.. i read somehwere they mention other steps like creating some symoblic link.. i'll have to read up on it more because that may be what we need.. it seems the settings are coming from somewhere else now.

---

### Post by wargames on 2006-07-22
No solutions yet? :( 

Well, after trying everything I can think of, and doing many hours of searching and trying many different options. Nothing works! DMA is busted on just my dvdrw drive no matter what I do. This same computer worked great under Breezy but under Dapper it's busted. DMA seems to be enabled for just the hard drive but that's it. I've tried kernel options in grub, editing hdparm.conf, editing /etc/modules file trying amd74xx, trying different BIOS settings, making sure all drives are configured for master/slave instead of cable select, but nothing works. :( 

After using Ubuntu since last year, I've decided that since this distribution is now broken and will no longer work on my system, I'm going to look for another Linux distribution or simply reinstall Windows so I can use this PC again.

Thanks, for the help.

---

### Post by mwolfe on 2006-07-22
so you can't enable dma period?? or its just not enabled when you boot?

Mine was enabling fine when i ran the command manually, it just wasnt saving the settings.. However as of yesterday, now dma is being enabled on boot.. at least the last 3 boot up's its been on already after booting.. all thats been updated lately for me is compiz and compiz-gnome on my system.. i wonder if by some odd reason compiz was effecting dma.. i have no clue why.. 

Anyways, if you can't get dma to work at all then i can see your frustration but if you just can't get it to work automatically on boot, you might wait this one out as it could just be some random problem that goes away.. 
Good luck!

---

### Post by wargames on 2006-07-22
> **mwolfe said:**
> so you can't enable dma period?? or its just not enabled when you boot?

Mine was enabling fine when i ran the command manually, it just wasnt saving the settings.. However as of yesterday, now dma is being enabled on boot.. at least the last 3 boot up's its been on already after booting.. all thats been updated lately for me is compiz and compiz-gnome on my system.. i wonder if by some odd reason compiz was effecting dma.. i have no clue why.. 

Anyways, if you can't get dma to work at all then i can see your frustration but if you just can't get it to work automatically on boot, you might wait this one out as it could just be some random problem that goes away.. 
Good luck!

Yes, my frustration hit a max last night with my last post. To recap my story:...I almost had my new Dapper install complete, with everything just how I liked it, when I tried to play a dvd and noticed choppey dvd playback. Well, from my experience with Linux (I'm still learning) I knew that it must be the dma setting on my dvdrw drive. So I did the usual hdparm /dev/hdc and it said it was off. So I did the "sudo hdparm -d1 /dev/hdc" and it then reported that dma was on. No error messages. I then hit the play button on VLC and got choppey dvd playback again. So I then checked the dvdrw drive dma settings with hdparm /dev/hdc and dma was back to off. And in my kernel log, is an error message about "atapi being reset", and dma being disabled. Weird since this drive just worked fine and had dma in Breezy. So I tried it again with "sudo hdparm -d1 -k1 /dev/hdc" to try to set the drive settings. And again it said dma was on with no error messages. Again, I hit the play button, and again choppey playback, and again another check of hdparm /dev/hdc shows dma turned off again and the same error message in the kernel log.

Even more weirdness...If I do the "sudo hdparm -d1 /dev/hdc", then hit the play button, get choppy playback, hit stop, and issue "sudo hdparm -d1 /dev/hdc"...if I do this dance four times in a row, dma will then be set to on and stay on and I get smooth playback, but it will only do that for the disc that's in the drive. As soon as I eject and reinsert the dvd movie and vlc or totem autoplay (same happens to both) the dma gets turned off again, and now I have to do the 4-times dance to get dma on for just that disc.

Also, when I first boot-up, if I go directly to terminal and hdparm /dev/hdc the dvdrw drive, it reports dma being on. But as soon as I insert a dvd movie, dma gets turned off and as I stated above I have to do the 4-times dance to get it to stay on. Freakn' weird and driving me nuts! ](*,) 

So with this strange dma problem on my dvdrw drive, I don't want to burn coasters, especially with dual layer disks, and since I have to do this stupid 4-times dance routine to make dma stick, I can't rely on this dvdrw drive's performance, which makes this install suck.

I tried the usual hdparm settings for hdparm.conf, I tried adding a script to /etc/init.d to issue a hdparm command, tried different BIOS settings, opened the case and checked master/slave settings, blah, blah, blah. I've been working on this for almost two weeks now, and nothing yet has worked, which is why my frustrations got the better of me last night. I really like the Ubuntu distribution alot! But this dma issue is really starting to get at me, especially since I just want to finish the configuration of my install and get on with my life. :) 

Anyway, I'll try to cool off a bit, take a deep breath, chill out, and think about this somemore. And if anyone, anywhere, has any info. or advice, I'm all ears. If by some chance I do figure this out, I'll be sure to post my fix so it might help someone else.

Now I'm off to go research this somemore....[-o<

---

### Post by wargames on 2006-07-23
I think I might have finally fixed this dma thing. I know, I know, I've said that before, but really, I'm serious. ;) 

Ok, I found someone else in the forum that had a similar problem as mine.
[http://www.ubuntuforums.org/showthread.php?t=117772&highlight=autoplay+dma](http://www.ubuntuforums.org/showthread.php?t=117772&highlight=autoplay+dma)

When they had autoplay on, dma would be off. And when they had dma on, autoplay would be off. They wanted both. They also had almost the same problems as I did. Since they wanted both autoplay and dma, they seemed to have changed their dvdrw drive setting to slave and moved it to their primary IDE channel. But I didn't want to put my dvdrw drive and hard drive on the same channel, since I heard this can affect performance. I believe they said they had a SATA hard drive so they should be ok. Anyway, both of my drives are IDE so here is my solution for my system...


This got me to thinking  :-k   that I have autoplay on as well and dma goes off when I autoplay a disc. So I then decided to turn autoplay off, and set the dma back to on for my dvdrw drive. And then...yes, you guessed it, the dvd played smooth and dma stayed on. Why does autoplay turn off dma is beyond me. :roll:  Maybe some kind of bug. Anyway, autoplay is not a big deal for me anyway. So now I just tried playing a dvd, burning a data dvd+rw and listening to a audio cd and everything worked smooth and dma stayed on. =D> 

Here's the steps I did:

Go to Configuration Editor->desktop->gnome->volume manager and you'll find all the autoplay options for your applications. I just unchecked the autoplay option on the audio cd's, dvd's and vcd's. Then I closed the Configuration Editor.

Then I edited /etc/hdparm.conf file and put a command line at the bottom:
command_line {
hdparm -d1 -k1 -K1 /dev/hdc
}

Saved and rebooted. It appears to be working just fine. After inserting your disc, just start whatever application you want to use for it. It also appears, that autobrowse and autoburn do not affect the dma setting either.

Hope this helps someone else, if you're having problems give this a shot.

---

### Post by krazykirk on 2006-07-24
I know this has nothing to do with your problem, but I finally figured out how to turn autoplay! It's been bugging me for ages!

Thanks!

---

