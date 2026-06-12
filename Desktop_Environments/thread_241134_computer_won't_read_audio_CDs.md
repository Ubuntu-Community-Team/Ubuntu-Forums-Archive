---
title: "computer won't read audio CDs"
date: 2006-08-21
forum: Desktop Environments
---

### Post by maniacmusician on 2006-08-21
before i get flamed, i already did a search and went through the first few pages. there were problems like this, but with different error messages, and none of the solutions applied. 

that being said, the problem is that when I pop an audio CD into the computer, it doesn't mount the drive. it whirs and spins for a little while then quiets down again. when I check Mount Devices (its a taskbar plugin for XFCE, shows you which devices are mounted, lets you mount and unmount), it says that /dev/hdc is not mounted. 

When I check the disk manager (I believe the program is "disks-admin"), it recognizes there that there is an audio CD in the drive. It even tells me that there's 12 tracks that last 62:41. There's a play CD button, but when I do that, nothing happens. my cpu usage goes up like 3% then falls back, and there's no output in terminal either. 

so, then I tried to mount it manually with sudo mount /dev/hdc. it says:
```
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

i checked dmesg, and there were quite a few lines that had to with hdc, so i've posted them all:

```
[17181590.436000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181590.436000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17181590.436000] ide: failed opcode was: unknown
[17181590.436000] end_request: I/O error, dev hdc, sector 64
[17181590.436000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17181851.604000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17181851.604000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17181851.604000] ide: failed opcode was: unknown
[17181851.604000] end_request: I/O error, dev hdc, sector 64
[17181851.608000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17189856.308000] cdrom: This disc doesn't have any tracks I recognize!
[17190197.284000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17190197.284000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17190197.284000] ide: failed opcode was: unknown
[17190197.284000] end_request: I/O error, dev hdc, sector 64
[17190197.284000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17190492.620000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17190492.620000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17190492.620000] ide: failed opcode was: unknown
[17190492.620000] end_request: I/O error, dev hdc, sector 64
[17190492.620000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17190506.920000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17190506.920000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17190506.920000] ide: failed opcode was: unknown
[17190506.920000] end_request: I/O error, dev hdc, sector 64
[17190506.924000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17190517.988000] cdrom: This disc doesn't have any tracks I recognize!
[17190547.084000] cdrom: This disc doesn't have any tracks I recognize!
[17190551.864000] cdrom: This disc doesn't have any tracks I recognize!
[17190555.212000] cdrom: This disc doesn't have any tracks I recognize!
[17190597.544000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17190597.544000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17190597.544000] ide: failed opcode was: unknown
[17190597.544000] end_request: I/O error, dev hdc, sector 64
[17190597.548000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
```

Other CDs still work (I tried the Xubuntu live install cd), and the audio CDs i tried to play work fine on my stereo. I dont really know what to do at this point, any suggestions would be helpful

thanks.

---

### Post by b_martinez on 2006-08-21
Do you have am-utils installed. I am not sure it is necessary in Ubuntu or deriatives, but I have installed it in FC5 and OpenSUSE 10.0 and everything 'just worked as far as mounting the CD's. I always have to opt to either 'do nothing' or 'open' ,since I will not allow any removable media to auto play.
This program may help you out.
Bill

---

### Post by maniacmusician on 2006-08-21
i just installed it. I tried running amd, but there was no .conf file created. it was supposed to automatically create it (its in the list of "Installed Files" in synaptic), but the command amd returns "Amd configuration file (/etc/amd.conf): No such file or directory". i'm not really sure how to proceed from here. any other suggestions?

edit: i just figured out that synaptic installed amd.conf in /etc/am-utils. i ran amd again, and it ran fine (no errors, at least). I took out my cd and put it back in, but nothing happened.

---

### Post by b_martinez on 2006-08-21
I just did "whereis amd.conf" andit returned "/usr/sbin/amd". Looking in my /usr/sbin I show amd and amd-fsinfo. I'll check the second with an editor and get back to you
Bill

edit: forget it, they are both binary files. Dummy me, I should have known, as they are in /usr/sbin
B

---

### Post by maniacmusician on 2006-08-21
^see my edit

---

### Post by b_martinez on 2006-08-21
Will look thru my cd files/piles for a commercial music cd. I put them on a removable hdd so long ago, I lost track of the originals. Give me a few minutes.
Bill

---

### Post by maniacmusician on 2006-08-21
sure thing. i'm not sure this will fix the problem. i understand problems with automounting, but it should have at least been able to do it with "sudo mount". and normal CDs still work. but i'm up to trying anything though, I just want to get these CDs onto my mp3 player.

---

### Post by b_martinez on 2006-08-21
My Bob Seeger just popped up in Sound Juicer. Do you have amd active in SYSTEM>ADMINISTRATION>SERVICES ?
It may have been autoed, but check anyway.
Bill

---

### Post by maniacmusician on 2006-08-21
i dont have adminstration > services (Xubuntu), but i used the boot up manager from Automatix instead. it doesnt have amd listed, but it does have am-utils. Under "Running", there is a question mark. nothing i seem to do (such as Start, Stop, Start again) seems to have any effect on the status of the question mark.

sudo /etc/init.d/am-utils tells me that amd is already running. Audio CDs still dont work.

---

### Post by b_martinez on 2006-08-22
I switched to XFCE desktop, was in Gnome. Do you have the header 'Applications' at the top left hand corner of your screen? If yes, n go to "System" --> "Services" and see if you have Volumes mounter checked. If 'no' then we have to figure a way to get it on your screen.
Bill

---

### Post by maniacmusician on 2006-08-22
haha wow, didnt even see that. But yeah, Volumes mounter is checked. like i said, the am-utils service is already running, but nothing pops up on the screen when I insert a cd. I'm expecting a notice kind of like XP had when a CD was inserted...maybe i'm missing something, but I don't think I am.

---

### Post by b_martinez on 2006-08-22
Which music player are you going to use, if I have it installed , we may still have a chance. And does it have a dialog to select the source? Say , 'load files from cd/dvd/streamin media/et&c ' Or do you have Grip installed, or Sound juicer? My SJ is opening every time I try to load an audio cd. That may be the way to go, just remember to install the codecs you'll want .

Bill

---

### Post by maniacmusician on 2006-08-22
well the problem is not so much what player i'm going to use (havnt decided yet) but that I cant see the CD at all. wont show up in thunar, can't even get it to mount. 

goin to bed now, hope someone comes up with something

thanks.

---

### Post by b_martinez on 2006-08-22
When you get up , try Sound Juicer or Grip. I gotta go to bed myself. Been up since 4:30 yesterday afternoon. Will check in around noon MST (GMT-6:00) [ I think]
Bill

---

### Post by Super King on 2006-08-22
Just wanted to say I'm in the exact same boat as maniacmusician: every data CD I've tried loads/mounts fine in Xubuntu, but every audio CD does not show up in Thunar. Are some audio codecs necessary (I've installed them all through Automatix anyway)? Oddly enough, in Systems -> Services I don't even have a Volume mounter.

This is my etc/fstab FWIW:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by compwiz18 on 2006-08-22
I am having the same problem mounting a CD in Gnome...but the CD works fine if I use a KDE CD player/ripper...

I guess what I'm saying: try a KDE cd player and tell me the results - this is an annoying bug.

---

### Post by Super King on 2006-08-22
Just tried with Amarok, the audio CD is still not recognized.

---

### Post by maniacmusician on 2006-08-22
@Super King: The reason you don't have Volume Mounter is because it is a service called am-utils that I installed on a suggestion from bill (didnt work). that service shouldn't really be necessary to be able to read an audio CD. there are hundreds of Xubuntu users, I'm sure most of them had it working out of the box.

I also tried Soundjuicer, and it still didnt work. Grip doesn't work either. It's clearly not a problem of what player is used. the fact of the matter is that the system refuses to even mount an audio CD so that it can be read. I posted relevant error information in my first post, and i believe that's where the solution lies.

---

### Post by Super King on 2006-08-22
Whoops, missed that part.

---

### Post by maniacmusician on 2006-08-26
anyone?

---

### Post by JairunCaloth on 2006-08-30
I'm currently having this exact same problem, same error message and everything. I'm in Xubuntu as well. ](*,)

---

### Post by mssever on 2006-08-31
Not sure if this will help, but...

First, you don't mount audio CDs. You play them unmounted, if I recall correctly.

Do you dual-boot? If so, can you play CDs from the other OS?

---

### Post by maniacmusician on 2006-08-31
I don't dual boot, so i can't test it. I didn't realize that audio CDs were played unmounted....how am i supposed to play the cd if it doesn't automatically load it?

thanks for the response.

ps: did you take a look at the error messages in the first post?

---

### Post by mssever on 2006-08-31
Yes, I looked at the errors. I also dug up an audio CD just now to try on my system. And it plays just fine.
```
~:$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``` So that confirms that you can't mount audio CDs.

Your dmesg output makes me think that you have a bad CD drive. Playing audio CDs uses a different mode--and even a different cable--so it's possible for the drive to work for data CDs and to not work for audio CDs, or vice versa. This is why I asked about dual booting.

EDIT: I just looked at my dmesg and I had similar errors in it, apparantly from trying to mount the CD. So, we might be back to square one, since I have no problems with audio CDs. You seem to have unusual issues...

---

### Post by maniacmusician on 2006-08-31
oO so what do you suggest i do

---

### Post by mssever on 2006-08-31
Hard to say. If you have another computer and can swap out CD drives, it would be a useful test. I'd suggest trying a live CD based on another distro, but when you're using a live CD, you can't eject it to test an audio CD.

Another thought...If you have Gnome installed, you could try from there. On my system (Gnome), when I put a CD in, Sound Juicer opens up and an icon for the CD appears on the desktop. Or, you could try to open up something like Sound Juicer directly and see if it can play a CD.

But I really think that you should try swapping CD drives. Borrow one from someone if you must.

---

### Post by maniacmusician on 2006-08-31
eh thats a little tough. I have extra CD drives but this one is a CD burner so i dont want to let it go. and my other drive is a DVD drive, and i dont have space for any more on wire ribbon thing. this kinda blows lol. i'll try to figure it out later, i'm really pooped for now. 'twas a long day. thanks for replying.

for extra info, Grip can't detect the cd when i put it in either, and that cant be good. as i said, i'll look more into it tomorrow, and post back.

---

### Post by mssever on 2006-08-31
My thought when it comes to swapping drives is just to do it temporarily. If everything works, then we know you have a bad drive. If not, then the problem is something else. You can also try putting that CD drive in another computer and testing it from there.

---

### Post by maniacmusician on 2006-09-01
ok this is weird. when i put it in my CD/CD-RW, it doesnt read it. But i just tried putting it in my DVD drive, and clicked "Open CD" with Exaile, and it worked! i find this kind of odd. the cd burner works for everything else, just not audio cds. so maybe you were right, maybe its just a bad drive. but its kind of odd that it was only for Audio cds...

---

### Post by mssever on 2006-09-02
OK...I didn't realize that you had two drives on your machine. My desktop has two CD drives, but I can only play CDs from one, as well. The reason--at least for me--is that CD drives play audio CDs in firmware. Some even have play controls and a headphone jack on the player itself. Back when I was using Windows 95, I remember starting an audio CD using Win's built-in player, and once I started the CD, I could close the program and the CD would continue to play. I could even shutdown, as long as I didn't power off.

On my machine, there's a separate cable that runs from the CD drive to the sound card. And since there's only space to plug one cable in, you can only play audio CDs on one drive unless you open up the case and switch cables around. Of course, if your CD drive has play controls and a headphone jack mounted on it, you could take that route, as well.

---

### Post by maniacmusician on 2006-09-03
oops double post

---

### Post by maniacmusician on 2006-09-03
there's no way to get both of my drives to play audio? that's kind of stupid...can DVD drives even read CDs reliably? because i want to rip audio, i dont want it to be glitchy. 

and are you sure theres no way around only one drive being able to play audio?

---

### Post by mssever on 2006-09-03
As far as I know, the only way to tell if you can use both drives is by opening up your computer. And having a hardware guru handy would make things easier, too.

EDIT: It should be trivial to switch the audio cable from the DVD drive to the CD drive, if that's what you want to do.

---

### Post by maniacmusician on 2006-09-03
will that affect me being able to play DVDs? ie, will i be able to play dvd's with sound or will i get just videos if i move the cable?

also, i thought that newer computers had eliminated the need for those cables...i guess not..

---

### Post by mssever on 2006-09-03
I don't know the answer to those questions. The only DVD drive I have is in my laptop--which is a different beast altogether. Also, my dasktop is circa 2002, so I don't know what might have changed since then. I'm really not much of a hardware expert.

---

### Post by maniacmusician on 2006-09-03
I see. thanks for the input anyways, at least we figured out what the problem was.

---

### Post by bloob99 on 2006-09-15
Try to use VLCplayer or XFmedia. From the menu you can select to play audiocd.

---

### Post by singedwings on 2006-09-15
> On my machine, there's a separate cable that runs from the CD drive to the sound card. And since there's only space to plug one cable in, you can only play audio CDs on one drive unless you open up the case and switch cables around. Of course, if your CD drive has play controls and a headphone jack mounted on it, you could take that route, as well.

Don't listen to this it is a red herring. The audio on a pc can be played through the ide cable or through the funny little analog cable. You should be able to play audio cds from both drives, without the analog cable.

I am suffering from this problem with xubuntu, but I have ubuntu installed on another machine. With ubuntu you just pop the cd in either drive and it auto mounts and plays with sound juicer. So this problem appears to be specific to xubuntu.](*,)

---

### Post by maniacmusician on 2006-09-15
I can confirm that this isn't the case...I have KDE as well, and it doesn't work there either.

I am actually thoroughly convinced that it's the drive. It's been screwing up on burning some CD's lately, and it f*cks up when trying to read audio CDs. I'll just have to buy a new CD-RW drive. Though I'll have to wait till thanksgiving when the big sales are hehe. 

i'll live.

---

### Post by singedwings on 2006-09-16
:D Ok I think I have worked it out. Try this out, unless your drive is really trashed it should work.

Put cd in drive,
Open Xfmedia player,
Expand the playlist window,
Left click the plus button and select add-other-cd.

The disc then gets read into the playlist (seems to take approx 5 mins with my setup).

Then select 1st track in playlist and press play (again seems to delay while track is read but music does play from cd).

I only have 256MB of ram in my sys so that may be why it delays, let me know how you get on.

P.S. I tried swapping my cd drive over, but it made no difference.

---

### Post by 3rdalbum on 2006-09-16
Have you tried installing Grip, and playing your CD with that?

On my iMac, Grip was the only program that could actually play CDs for me.

---

### Post by maniacmusician on 2006-09-16
> **singedwings said:**
> :D Ok I think I have worked it out. Try this out, unless your drive is really trashed it should work.

Put cd in drive,
Open Xfmedia player,
Expand the playlist window,
Left click the plus button and select add-other-cd.

The disc then gets read into the playlist (seems to take approx 5 mins with my setup).

Then select 1st track in playlist and press play (again seems to delay while track is read but music does play from cd).

I only have 256MB of ram in my sys so that may be why it delays, let me know how you get on.

P.S. I tried swapping my cd drive over, but it made no difference.

you're running linux, not windows. 256 should be more than enough to play a cd. and I tried that at first, but that doesnt work. it's a system-wide problem for me. besides, your solution is not really complete...i dont want to wait 5 minutes to listen to a CD. I just want to rip them to my computer.

> **3rdalbum said:**
> Have you tried installing Grip, and playing your CD with that?

On my iMac, Grip was the only program that could actually play CDs for me.

of course, that's what I use to rip my CDs. it only works on my dvd drive.

---

### Post by mgmiller on 2006-09-16
> can DVD drives even read CDs reliably? because i want to rip audio, i dont want it to be glitchy. 

Yes, DVD drives reliably read, write and rip CD's.  I haven't used a cd-rom or cd-rw in a couple of years.  I do everything from dvd-rom and dvd burners.  They rip & create audio cd's just fine.  I have a Samsung dvd burner, 2 layer, dual mode (- &+) that I picked up at a local microcenter warehouse for about $35.00  It works great.  

Also, as a previous poster said, you don't need the seperate little audio cables for audio any more.  Everything works through the ide ribbon cable.

Some older and off brand optical drives may have compatibility issues with linux, so stick with modern name brand stuff and you shouldn't have any problems.  DVD readers and writers are very inexpensive these days.

---

### Post by maniacmusician on 2006-09-16
yes that's true, they're not too expensive. i'm going to end up just buying another drive, probably.

---

### Post by crendon on 2006-11-30
I think you can listen CDs with any media player that supports CD format. I put my CD in my xubuntu machine but nothing happens... then I open VLC, gXine or Mplayer to listen the CD and it works (check if the path of the CD unit is properly configured). Meaby you were expecting to see an icon on your desktop like ubuntu (gnome). Thunar will not show your CD tracks, I hope for the next version it will. If it still doesnt work try to install gnome CD player -ripping tool:

sudo apt-get install sound-juicer

It works for me, I hope for you also. Greetings and good luck

C.Rendon
[www.titanjp.com](www.titanjp.com)

---

### Post by oswaldkelso on 2007-04-26
I was looking at this thread as I had the same problem. Albeit debian etch and xfce. the pc in question is rather old an amd k6 300mhz box. No mount commands worked or fiddling with fstab. Audacious could not see the audio cd either, nothing could..... except xfmedia.

opened it up clicked the plus box goto other,  cd and success all the tracks show up.

---

### Post by TheLoneIguana on 2007-05-14
What seemed to work best for me was to change the preferences in whatever program from **/dev/cdrom** to **/dev/scd0**

VLC was the only program I had installed that would recognize an audio CD, and it was using a different path to the CD. The path may be different on another system.

Doing a **dmesg | grep cdda** on my system came back with the drive as **/dev/sr0**, which itself is a link to **/dev/scd0**.

Made Amarok, xmms, and some others work like a charm.

---

