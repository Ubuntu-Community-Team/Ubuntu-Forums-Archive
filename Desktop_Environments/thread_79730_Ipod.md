---
title: "Ipod"
date: 2005-10-20
forum: Desktop Environments
---

### Post by shanghaipi on 2005-10-20
So I broke down and bought the new Ipod Video...

Mounts alright in Ubuntu, but it doesn't unmount....also...it does not work well with GTKpod, Amarok or Banshee.  Is anyone else having problems with their ipods on Breezy?

I've read the How-tos on Hoary, but they don't seem to work....I've also read the How-To for GTKpod, but it doesn't seem to recognize my ipod at all...got the ipod's name right and everything.

---

### Post by lassel on 2005-10-20
I have trouble with my ipod shuffle.

I think that when you update the firmware the database format gets incompatable with what the open source project has reverse engineered.

Anyways.. I was able to use "restore" from windows and then fill it up using banshee (but not gtkpod og gnupod). However, the next day when I attempted to put more songs on it from banshee it said that it didn't support my database version (14 i think).

So, for what it is worth, you are not alone.

---

### Post by seethru on 2005-10-20
hmm, my 3rd gen ipod works great, but it's possible they've made some major changes to the way the database works in these ones. I think I remember reading something about the nano and incompatibility, so whatever people did to get the nano working will probably get your ipod video working.

---

### Post by snooo on 2005-10-20
I have EXACTLY THE SAME PROBLEM. I am using 4G iPod and I cant unmount it under breezy. It mounts fine, but unmounting it under gnome produces an error and makes the ipod reboot if you remove the cable. which sucks.

If anyone cares, the error produced is: "Invalid Argument"

Dave

---

### Post by ThirdWorld on 2005-10-20
I dont understand why apple dont support our plataform, 15% of desktop users worldwide have linux installed in thei computers and numbers are growing fast. It will be so simple to provide a linux version of itunes since apple and linux both use the same language: Unix

---

### Post by wellery on 2005-10-20
[quote=ThirdWorld]I dont understand why apple dont support our plataform, 15% of desktop users worldwide have linux installed in thei computers and numbers are growing fast. It will be so simple to provide a linux version of itunes since apple and linux both use the same language: Unix[/quote]

I somehow doubt that 15% of desktop uses use linux. I thought it was more like 90%+ use windows. There is only a small percentage that use linux. Probably less that those that use mac. From that you can understand why they don't support linux.

---

### Post by majikstreet on 2005-10-20
I have an ipod 4g 20gb ipod black and white screen. Works great in breezy.

---

### Post by gpw797 on 2005-10-20
I manage music in amarok and use YamiPod up sync changes to ipod .. works great. YamiPod is at: [http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by ThirdWorld on 2005-10-20
[QUOTE=wellery]I somehow doubt that 15% of desktop uses use linux. I thought it was more like 90%+ use windows. There is only a small percentage that use linux. Probably less that those that use mac. From that you can understand why they don't support linux.[/QUOTE]

15% + of desktop users use linux worldwide, you are probably not aware that the majority of these people use linux and windows in the same machine. ;)

---

### Post by shanghaipi on 2005-10-20
Well, Yamipod is the only one I haven't tried....I switched over to my other hard drive which has Kde breezy 5.10....the ipod wouldn't even mount.

I can read the songs on Rhythmbox and Amarok just fine, but I can't add anything to it....ughhh

could you type exactly what you did to install Yamipod right after extracting the tar file?

---

### Post by dave9191 on 2005-10-20
[QUOTE=ThirdWorld]15% + of desktop users use linux worldwide, you are probably not aware that the majority of these people use linux and windows in the same machine. ;)[/QUOTE]

From the last stats that bounced of me, it was something like windows 90%, mac 5% and linux 3-4% and some others. Thats for laptops and desktops. Either way, last time i did a survey for Apple about my pod they asked which OS i was using Mac or Windows. So I had no choice but to pick windows and then a sub category of windows was Linux... 

And my 2nd Gen ipod mini works like a charm with gtkpod. 

Dave

---

### Post by shanghaipi on 2005-10-21
i guess there are not many ipod users in the ubuntu forums...I heard that 1.3.3 is supposed to solve some ipod bugs, is this true?

---

### Post by Seth on 2005-10-21
Yes, that is correct. Namely the one that makes AmaroK crash when transferring files.

---

### Post by adis on 2005-10-22
[QUOTE=snooo]I have EXACTLY THE SAME PROBLEM. I am using 4G iPod and I cant unmount it under breezy. It mounts fine, but unmounting it under gnome produces an error and makes the ipod reboot if you remove the cable. which sucks.

If anyone cares, the error produced is: "Invalid Argument"

Dave[/QUOTE]

This is a known bug, look at 
[http://bugzilla.ubuntu.com/show_bug.cgi?id=5049](http://bugzilla.ubuntu.com/show_bug.cgi?id=5049)

Try "sudo eject */ipod/mount/point*". The error doesn't go away but the iPod should be correctly unmounted.

Cheers.

---

### Post by graabein on 2005-10-26
Anyone know how to transfer an album, some songs, from the library in Banshee to my iPod? Banshee recognices it and I can play songs from it but I have not tried transferring some songs from the library yet. I don't want to mess up my iPod.

---

### Post by lasermike026 on 2005-10-26
I have an ipod nano.  When I was running Hoary it automounted fine.  I rebuilt my system to Breezy and its not automounting.  I get this log entry in my messages file:

Oct 26 21:54:20 comp kernel: [4295302.001000] usb 1-1.4: new full speed USB device using uhci_hcd and address 15

This message repeats for a while but the scsi dev is not generated.  lsusb is sluggish too.  Any idea's.  I'm dieing over here.

It feels like a usb problem.

---

### Post by Hairy_Palms on 2005-10-26
eww i hate ipods, overpriced, ugly, unreliable pieces of poo.  get an iriver and have more fun with life :D

---

### Post by dave9191 on 2005-10-28
[QUOTE=Hairy_Palms]eww i hate ipods, overpriced, ugly, unreliable pieces of poo.  get an iriver and have more fun with life :D[/QUOTE]

Come on, Ipods aren't bad. They are pretty, highly reliable, high quality, have a fantastic interface and good batt life. Irivers dont look anywhere as good and Ive never seen one in real life, they aren't on display in shops and Ive never met anyone who bought one. 

Dave

---

### Post by snooo on 2005-10-30
For the record, I found that my iPod Linux install was the probably cause of the rebooting. It seems that breezy opens up both the main and linux partition, which the ipod responds badly to. 

However, there are still probs with ejecting the device. GTKpod works wonderfully and there dont seem to be any probs with actually transferring songs, but the eject thing is a pain in the rear. You can rip out the cord and it doesnt seem to cause any probs, especially after its been dismounted, but its not a very tidy way of doing things. Hope this gets fixed.

---

### Post by bradroger on 2005-11-01
How can I transfer songs from my ipod to my computer while MAINTAINING all my ratings and playcounts?  I've tried gtkpod and yamipod and both say they transfer ratings but I haven't been able to see them in any programs.  I'd hate to lose all the data for my smart playlists and everything.  Also, is there any programs that will update the ratings and playcounts as I play the songs so I can sync them with the ipod?
It seems like there are a few happy iPod users in ubuntu....how are you guys set up?  Can you use smart playlists?

---

### Post by abou on 2005-11-01
[quote=dave9191]Come on, Ipods aren't bad. They are pretty, highly reliable, high quality, have a fantastic interface and good batt life. Irivers dont look anywhere as good and Ive never seen one in real life, they aren't on display in shops and Ive never met anyone who bought one. 

Dave[/quote]To be honest, I have only seen and experienced the opposite for iPods.  I find them to be horrid players with little functionality.  The best digital audio player you can get is the Cowon iAudio X5L.  It has ~35 hours battery life, can play FLACs, MP3s, OGGs, has a built in mic, FM radio, and video/picture/text capability - all for roughly the same price of an iPod.  Firmware is updated regularly and recently got IDv3 support.  It is what I own and I enjoy it greatly.

I really cannot stress it enough - best player on the market.

---

### Post by angkor on 2005-11-01
[QUOTE=snooo]However, there are still probs with ejecting the device. GTKpod works wonderfully and there dont seem to be any probs with actually transferring songs, but the eject thing is a pain in the rear. You can rip out the cord and it doesnt seem to cause any probs, especially after its been dismounted, but its not a very tidy way of doing things. Hope this gets fixed.[/QUOTE]

sudo eject /path/to/ipod/mountpoint doesnt work for you?

---

### Post by dave9191 on 2005-11-01
[QUOTE=abou]To be honest, I have only seen and experienced the opposite for iPods.  I find them to be horrid players with little functionality.  The best digital audio player you can get is the Cowon iAudio X5L.  It has ~35 hours battery life, can play FLACs, MP3s, OGGs, has a built in mic, FM radio, and video/picture/text capability - all for roughly the same price of an iPod.  Firmware is updated regularly and recently got IDv3 support.  It is what I own and I enjoy it greatly.

I really cannot stress it enough - best player on the market.[/QUOTE]

Well it looks pretty good, not something I have heard of before. Hijacking the thread a bit, how do you scroll through tracks quickly like the ipod wheel or the zen touch bar? if you have to press a next button to scroll the tracks it has a fatal flaw in my opinon. Choice of music players is a personal thing in the end :)

Dave

---

### Post by abou on 2005-11-03
The joystick can simply be held down and it will scroll through your list.  That joystick is much more functional than it seems.

---

### Post by graabein on 2005-11-07
OK can anyone give me a step-by-step run down on how to transfer some songs from the Banshee library to the iPod?

I want to search for an album in my library and check the tags before I copy the songs. I do not want to do that sync thingie that replaces everything. I am a bit of a wuss when it comes to this because I have already screwed up a friend of mine's iPod... :(


That Cowon iAudio X5L looks real good by the way. I would seriously consider it if was to buy a music player now...

---

### Post by Vierge on 2005-11-07
I hope there are happy ipod linux users out there, because I would like to become one.  So far, I am foiled.  I am absolute newbie, so I'm just trying to solve one problem at a time.

My ipod is brand new (my last one stopped charging before I switched over to ubuntu and I had to replace it) so I'm assuming it's unformatted and that could be causing problems.  Any way to format it on an ubuntu box?

---

### Post by Leif on 2005-11-07
[QUOTE=graabein]OK can anyone give me a step-by-step run down on how to transfer some songs from the Banshee library to the iPod?

I want to search for an album in my library and check the tags before I copy the songs. I do not want to do that sync thingie that replaces everything. I am a bit of a wuss when it comes to this because I have already screwed up a friend of mine's iPod... :(
[/QUOTE]

start up banshee, add some songs to your local library. plug in your ipod, it should pop up in banshee too. drag and drop the files you want to transfer to your ipod. click sync, choose "manual changes" (or smt like that, I can't remember). that way you can copy only what you want.

I should point out that while I had some luck with my ipod (photo) using banshee, after I'd moved a couple of hundred tracks it became unresponsive, and would simply crash when trying to display what was on the ipod. I'm sorry to admit that after playing around with gtkpod, amarok and banshee, I've had to reboot to XP for the first time in ages. after all that hassle, itunes is pure bliss.

---

### Post by ltmon on 2005-11-07
[QUOTE=Vierge]I hope there are happy ipod linux users out there, because I would like to become one.  So far, I am foiled.  I am absolute newbie, so I'm just trying to solve one problem at a time.

My ipod is brand new (my last one stopped charging before I switched over to ubuntu and I had to replace it) so I'm assuming it's unformatted and that could be causing problems.  Any way to format it on an ubuntu box?[/QUOTE]

I think there is using such things a gnupod, but I failed at this miserably.  In the end I just formatted on a family members windows box, and haven't looked back since.

L.

---

### Post by earobinson on 2005-11-07
anyone know why i cant mount or even detect my ipod, when i plug it in this is what happens

earobinson@null:~$ dmesg | tail
[4450639.149000] hw tcp v4 csum failed
[4450716.081000] hw tcp v4 csum failed
[4451224.952000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[4451224.952000] usb 2-1: USB disconnect, address 45
[4451225.050000] usb 2-1: new low speed USB device using uhci_hcd and address 46[4451225.123000] usb 2-1: device descriptor read/64, error -71
[4451225.340000] usb 2-1: device descriptor read/64, error -71
[4451225.509000] usb 2-1: new low speed USB device using uhci_hcd and address 47[4451225.720000] input: USB HID v1.00 Mouse [HP HP USB WHEEL MOUSE] on usb-0000:00:1d.1-1
[4451260.048000] hw tcp v4 csum failed

---

### Post by snooo on 2005-11-10
[QUOTE=angkor]sudo eject /path/to/ipod/mountpoint doesnt work for you?[/QUOTE]

It does, but i'd like to eject it without having to go to sudo all the time. Any ideas?

---

### Post by stimulator on 2005-11-18
Yup, been having problems unmounting and it makes rhythmbox crash. For what it's worth, I was able to use it with Yami pod and was able to copy videos and music to my Linux box (Ipod is authorized for my Mac) [http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

If you find anything out I'd like to know too.

FInally, I've begun encoding my films for the new ipod - [http://submediatv.com](http://submediatv.com)

cheers//frank

---

### Post by stimulator on 2005-11-18
Found this while searching around and it works well and I don't have to 'sudo' all he time.

sudo chmod +s /usr/bin/eject

cheers//frank
[http://submediatv.com](http://submediatv.com)

---

### Post by linuxted on 2005-11-20
I can't transfer playlists on my ipod to the computer and  reload  them using gtkpod.  Can anyone explain how to do this?


Thank you

---

### Post by doclivingston on 2005-11-20
[QUOTE=stimulator]Yup, been having problems unmounting and it makes rhythmbox crash.[/QUOTE]

Can you file a bug about this? If bug-buddy comes up when Rhythmbox crashes, it will generate a *backtrace* which will be handy to determine the cause.

---

### Post by aysiu on 2005-11-20
[QUOTE=linuxted]I can't transfer playlists on my ipod to the computer and  reload  them using gtkpod.  Can anyone explain how to do this?[/QUOTE] Are you saying you know how Gtkpod is *supposed* to work but that it's not working? Or are you saying you *don't* know how it's supposed to work at all?

---

### Post by linuxted on 2005-11-20
[QUOTE=aysiu]Are you saying you know how Gtkpod is *supposed* to work but that it's not working? Or are you saying you *don't* know how it's supposed to work at all?[/QUOTE]

I would say it is the latter.  Can gtkpod save the playlist to the computer or is it only residing on the ipod?

Thanks

---

### Post by laiyf on 2005-12-02
I have some problem on recharging Ipod Shuffle. Somehow it never get charged, orange light blinking all the while. Anyone has any idea? I am using Ubuntu 5.10 with USB 2.0 ports.

---

### Post by shanghaipi on 2005-12-06
The only reason why I'm using Windows XP right now, is the god damn ipod.  I wish apple would just port iTunes over to linux.  Although I like Amorak, I agree with a guy who posted earlier, iTunes is a breath of fresh air.

nevermind...tried 'sudo eject dev/sda1' and it worked!  I don't need to use windows anymore.  Now I made a launcher on my desktop that has a red apple as an icon.  How would i go about finding that ipod icon that Breezy uses?

---

### Post by linuxted on 2005-12-18
[QUOTE=linuxted]I can't transfer playlists on my ipod to the computer and  reload  them using gtkpod.  Can anyone explain how to do this?


Thank you[/QUOTE]

In the interest of sharing knowledge, here is how I got it to work:

To use gtkpod, select "gtkpod" under playlist, Add Dirs and then Sync.
To save a playlist made on the ipod, select the playlist, go to File->
Create Playlist File -> Selected Playlist.  Type in a name for the
file, use "MSU" and "Prefer Local"

While you can add individual songs to your iPod playlists through
gtkpod, it's a lot easier to just add a playlist. I have found that
the playlist needs to be in the .m3u format. There may be some other
formats it supports, but .m3u is a pretty universal format, and it
works well with gtkpod. To add a .m3u playlist, simply click on the
Playlist button, and choose the playlist from your file system.  Make
sure you hit sync after loading in the new playlist.

To write a playlist from gtkpod, use the defaults "M3U" and "Prefer
Local".  Make sure to title the file *.m3u.  Note that the "*" in the
filename will be used by gtkpod for the name of the playlist in when
it is read back into gtkpod.

When making a new playlist, use the "New PL" button on Gtkpod Song
order can be manipulated on Gtkpod or manually on the text file on the
computer.  When loading in new playlists, "click shift" will allow you
to do an antire directory of playlist.  Note that reading in a
directory using the "+directory" button on gtkpod does not work.

---

### Post by nrwilk on 2006-02-18
I found that I couldn't eject my ipod until I quit Amarok.  It told me the the ipod was still in use.

Maybe this'll help some people?

(I really wish I could get it to mount with firewire, but it'll only mount with it's usb cable.  Anyone know anything about this?)

---

### Post by ddonky on 2006-02-24
[QUOTE=laiyf]I have some problem on recharging Ipod Shuffle. Somehow it never get charged, orange light blinking all the while. Anyone has any idea? I am using Ubuntu 5.10 with USB 2.0 ports.[/QUOTE]

The orange light normally blinks when it is mounted and being used as a disk.

---

