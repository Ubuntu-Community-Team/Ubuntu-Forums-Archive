---
title: "Creative Zen Microphoto - software support"
date: 2006-04-16
forum: Desktop Environments
---

### Post by stengah on 2006-04-16
Hope this is the right forum for this post.

My girlfriend recently purchased a Creative Zen Microphoto device. Problem is that Creative apparently doesn't support Linux platforms and we've chosen to abandon MS for good on all my/our computers.

I've tried Gnomad2 and Neutrino. No luck- and as far as I can tell this is due to the fact that this particular  player is relatively new. 

I've tried wine- installing the windowssupported software, but it doesn't allow any install (wine has restricted support for MS apps, I know...)

To turn a long story into a (relatively) short question:

Have anybody succesfully managed to get this particular player up and running - and if so, by all means; please enlighten me as to HOW!](*,) 

Research has show me that there's possibly a couple of options left; one being nomadsync and another the KDE app. Creative Nomad Jukebox KIO::Slave. As I'm running Gnome I wonder if anybody has any experience with these in conj. with this player?!? E.g. a kubuntu user... or anybody running KDE.

Otherwise, my last option seems to be emulating any given windows platform with vmware player - really annoying just for one silly MS driver/app. (ofcourse my gal thinks it's far from silly);-)

Any help will be much appreciated.:)

---

### Post by Super King on 2006-04-16
Sorry, but I think you might be out of luck. The Zen Micro Photo is one of those MTP MP3 players which are meant to work exclusively on Windows XP.

The KDE app you might be talking about is [KZenExplorer ](http://kzenexplorer.sourceforge.net/parser/parser.php?file=/index.ctn), which uses the libnjb library, which does not support any of the MTP players.

> Working Devices:
Creative NOMAD Jukebox 1 (aka D.A.P.)
Creative NOMAD Jukebox 2
Creative NOMAD Jukebox 3
Creative NOMAD Jukebox Zen
Creative NOMAD Jukebox Zen USB 2.0
Creative NOMAD Jukebox Zen NX
Creative NOMAD Jukebox Zen Xtra
Creative Zen Touch
Creative Zen Micro
Creative Zen Sleek
Creative Zen
Dell Digital Jukebox ("Dell DJ")
Second Generation Dell DJ
Dell Pocket DJ

NOT SUPPORTED:
Creative Zen Portable Media Center
Creative Zen MicroPhoto
Any other MTP device 

---

### Post by dengar on 2006-04-16
Good place to go for nomad player support is nomadness.net, its a fan driven site with specific creative player forums. They sight said, and the gnomad2 site confirmed, that an experimental release that supports MTP players has been released, deb files are available, and the site suggests it supports the Zen Micro Photo, although only for music files. It's worth a shot at least, I'll try it tonight and update you on how I do (know that I have a Zen Xtra, but it also has the MTP firmware, so it'll probably function the same)

---

### Post by stengah on 2006-04-16
Super king: Thanks for the briefing. That has been my conclusion as well so far... sad that Creative doesn't look further than the scope of MS. Hopefully Dengar's research can bring up something of use;-)

Dengar: thanks a bunch for the info. Didn't know about that webside and the MTP issue, though I was more or less aware that it might be problematic - I don't want to get my hpes up too high but it does sound promising with the MTP player supported release;-)

Please keep me updated with your progress- thanks again for helping out!!:)

---

### Post by Frodogodo on 2006-05-01
Stengah,

   past week i've purchased this device and now I have It working (basic functionality only, just transfer tracks) with  of gnomad2 2.8.3 (thanks Linus Walleij ! ). 
BTW: I have to build it from sources so I have to download libmtp, I've not be able to build gnomad2 with 0.0.3 version of libtmp, I've to use 0.0.2 version instead. Also remember that in this version of gnomad you must execute it as root in order to connect to the device ...

---

### Post by zad on 2006-05-01
Your lucky i cant get my creative media player to work at all in linux :S
might look at vmware and sticking xp or somat on there so i dont have to reboot to winblows when i wanna add some music etc..

zad

---

### Post by stengah on 2006-05-01
Thanks Frodo... like zad I've sort of given up hope as to get native support for this version, at least for now. I don't (and my gal most certainly doesn't) see a point unless the picture part of the Zenplayer supported.

If I had the vaguest idea that this piece of junk was solemnly developed for MS I'd made sure to get her an Ipod... now I have to go vmware.

---

### Post by Reliant on 2007-05-31
Stengah  if you have Feisty Fawn and also have Amarok, Amarok will support MTP devices such as the Creative Zen.  I have the Microphoto 8gb version and it works fine with Amarok.  You can easily drag and drop your MP3 files into the player.  As for the photos, I do not know since I do not use that function.

---

### Post by strabes on 2007-06-25
Can anyone else confirm what reliant said above? I'm thinking about getting an 8gb zen microphoto from creative because they're on sale for $100 right now.

---

### Post by hmsf on 2007-07-30
Maybe it's too late (I hope the sale is not over), but I confirm that I have my Zen MicroPhoto working with Amarok in Feisty.
About the photos, I'm still trying to make it work... Btw, anybody know how I can upload my photos to my ZMP?
Thanks!

---

### Post by hvymtlsteve on 2007-08-16
I've had one of these Microphoto players for about a year and a half now, and I've been running Ubuntu on my new desktop ever since I got it back in February or March or so. My WinXP laptop is now officially dead. I mean officially. 
I was using that anytime I wanted to transfer music up until now, and didn't bother trying to look at the device in Ubuntu until now. Looks like they've got it all taken care of, all I had to do in Feisty was:
> sudo apt-get install gnomad2

I fired up the program really quickly to test it out, it got the list of songs off my player, so I assume I can also now transfer songs. 

I think that's one more thing I can cross off the list of things I would like to do on my Ubuntu box that I previously needed Windows for. 
I think I really only have two items left to take care of!
:guitar:

---

### Post by arun_gopalan on 2007-08-16
Hi There -

I have created a new project which has java based User interface for MTP device.

[http://jmtpsynchronizer.googlecode.com/](http://jmtpsynchronizer.googlecode.com/)

It is still in its very early stages (just uploaded the code today :P)

It will be great if some of you guys could install and use it, and give me feedback.

Regards
Arun

---

### Post by samb0057 on 2007-11-12
Here's a compatibility review: [www.ubuntuhcl.org/pub/reviews.php?product_id=303](www.ubuntuhcl.org/pub/reviews.php?product_id=303)

---

