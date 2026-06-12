---
title: "one dvd won't play -- faulty or encrypted"
date: 2005-12-23
forum: General Help
---

### Post by jennhi on 2005-12-23
Hi guys! I've got a sweet DVD RAM which has played many dvds faithfully and still does. But there is this one DVD that simply won't play. It plays fine in my Playstation2, but Xine says that it's encrypted or faulty. So I think there's a special kind of encryption on this dvd that isn't on any others I have.

This DVD played fine before I upgraded to Breezy, too.

I do have libdvdcss2 and libdvdread. I couldn't compile xine-lib, though. Any recommendations? 

Thanks!
Jennifer

---

### Post by DevilsAdvocate on 2005-12-23
I don't mean to be insulting, but did you check for scratches or smudges on it?  Often, when I'm makeing a copy of a DVD (archival purposes of course) I'll find it's "encrypted."  I clean it off and suddenly it's not encrypted anymore.  Also, is it produced by Sony/BMG?

---

### Post by jennhi on 2005-12-23
not insulting. In fact, I did see something that looked like a bubble near the core. So even though this dvd played fine in another, less efficient player (the PS2), I bought a new DVD. I have the same problems with this one, and the same error message.

---

### Post by DevilsAdvocate on 2005-12-23
I would run Xine from the command line and see what error messages you get, then post them here.

---

### Post by DevilsAdvocate on 2005-12-23
Another suggestion, install VLC and see if that will play it.  Tends to play anything you throw at it.

---

### Post by jennhi on 2005-12-23
unfortunately, this is all I'm getting. Dunno if it's terribly helpful.

> libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

That prints itself twice.

Oh, and I can't find "Sony" anywhere on the packaging of the DVD or the DVD itself.

Any chance this is remedy-able?

---

### Post by jennhi on 2005-12-23
Ah, yes, someone else did suggest VLC. Unfortunately, I couldn't get it to cooperate either.

---

### Post by DevilsAdvocate on 2005-12-23
try running Xine as sudo; i.e., 

```
sudo xine
```

and see if it's a permissions problem for some reason.

---

### Post by DevilsAdvocate on 2005-12-23
Let me summarize:

1.  You definately can play other commercial DVDs w/ Xine on your box.

2.  This DVD won't play and you know it's not the DVDs fault.

3.  You're getting the above error.

Right?

---

### Post by jennhi on 2005-12-23
Regarding the 3 summaries, yes. 

Here is the output when I run Xine as sudo:

> $ sudo xine
Password:
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a1
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000001a1)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000001e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001d36f2
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d3740
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001d88d7
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001d88d7)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d8925
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001d8925)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 4

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1631 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1636 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1636 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1636 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1636 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***



This is much more substantial. Any hope?

---

### Post by rcerreto on 2005-12-23
looks like libdvdcss can't crack the DVD.
I see you're using version 1.2.5
you could have more luck using 1.2.9

adding
**deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main**
to /etc/apt/sources.list should allow you to get the new version via apt-get

---

### Post by DevilsAdvocate on 2005-12-23
Yep, looks like a cracking problem.  When you open Synaptic, what version of libdvdcss do you have?  Is there a 2 at the end?  Where did you get it?  I'm not at my box right now, so I can't check 'til I get home.  Here's the most Ubuntu friendly way to get libdvdcss.

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

At that line to your sources list and reload, then search for libdvdcss.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
Can you tell us WHAT DVD this is so those of us who care may avoid supporting the publisher in the future?

---

### Post by jennhi on 2005-12-24
The company that put the DVD out is called GoodTimes Entertainment LLC. They're probably not all that big, so they probably went through another company to create these DVDs. It doesn't say anything more than that on the packaging, though.

DevilsAdvocate, I did grab the latest version (1.2.9) via your instructions and it still doesn't crack the code. Is there no hope left?

Here's the newest error message:
> sudo xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a1
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000001a1)
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000001e0
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001d36f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d3740
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001d88d7
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d8925
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 5


Thanks for all your help and recommendations!

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
Goodtimes? EEEEEEEWWWWW it's GT Media - the people who run all those annoying infomercials for Charlton Heston Bible stories and Richard Simmons and Tae-Bo....

Well, I guess we know another reason to click the remote when these folks show up. Don't waste your money on TV SPAM, folks!

*Is there no hope left?*

I doubt it. DECSS depends on a known "hole" in the spec. More than a year ago the industry agreed upon a new spec that left out some critical (cracked) keys. The folks selling TV SPAM are not filmakers - they don't have "secondary markets" to help fill in the gaps: they're going to do whatever they can to keep all those "good christian people" from bootlegging Charlton Heston's Bible stories...

---

### Post by kosmic on 2005-12-24
Hum you could also use DVDdecrypter and make a backup of the movie :) there's a howto in the forums showing howto use DVDDecrypter with wine, you should have a look :) and post if you can see the movie after that :)

---

### Post by DevilsAdvocate on 2005-12-26
Yep, I agree w/ kosmic.  When all else fails, DVDDecryptor is your best bet (I've actually never had it not be able to crack something).  You can pick it up by searching the following site [www.afterdawn.com]("http://www.afterdawn.com") .  If it's a one time need, it may be simpler to install it in Windows.  Setting it up to work w/ wine isn't that difficult, but does require some effort.

---

### Post by JimS on 2005-12-26
...
DVD Decryptor has been dropped by AfterDawn.   :-({|= 
See story @ [http://www.afterdawn.com/news/archive/6501.cfm](http://www.afterdawn.com/news/archive/6501.cfm)

But all is not lost.  Using Google we find other sites which will
provide DVD Decryptor.   \\:D/ 

Try  [http://fileforum.betanews.com/detail/DVD_Decrypter/1011845169/1](http://fileforum.betanews.com/detail/DVD_Decrypter/1011845169/1)
I just downloaded it, so I know it is still available now.   =D> 

JimS
Prostate Cancer Aware
...

---

### Post by DevilsAdvocate on 2005-12-27
[QUOTE=JimS]...
DVD Decryptor has been dropped by AfterDawn.   :-({|= 
See story @ [http://www.afterdawn.com/news/archive/6501.cfm](http://www.afterdawn.com/news/archive/6501.cfm)

But all is not lost.  Using Google we find other sites which will
provide DVD Decryptor.   \\:D/ 

Try  [http://fileforum.betanews.com/detail/DVD_Decrypter/1011845169/1](http://fileforum.betanews.com/detail/DVD_Decrypter/1011845169/1)
I just downloaded it, so I know it is still available now.   =D> 

JimS
Prostate Cancer Aware
...[/QUOTE]


Bummer...

---

### Post by jennhi on 2006-01-21
Hi guys! Sorry about the long hiatus -- I was on vacation and not worrying about DVDs for a while. I've been getting several DVDs from a rental service called GreenCine, and they play just fine on the Playstation2; now none of them will play on Xine. One of them was the Dave Chappelle show, and I know that one should play! I'm starting to think Breezy is useless as a multimedia station if it can't play DVDs that Hoary played just fine.

So I did get DVD Decrypter and was trying to figure out how to use it. In the Linux instructions, it said to go under I/O in the options and check "SPTI" but it's grayed out on my screen. Is there anything I can do about this?

rcerretto, I added your line in my sources list successfully. DevilsAdvocate, when I added your line, I got a lot of errors on every update, so I had to comment it out. Any reason you know of for that?

Thanks, everyone!

---

### Post by hamil on 2006-02-05
Hello!

I have the same troubles as stated here..
I have libdvdcss2_1.2.9-1plf3 installed on my system.
Some DVD's plays just fine, but others wont even start.

When browsing my Computer, the DVD is listed correctly on cdrom0
Manually trying to start watching the DVD with, MPlayer, Totem, VLC or Ogle, makes no change. Nothing at all happens... In Totem i get the error message that it seems to be an encrypted disc, and that I dont have libdvdcss installed, which I offcourse have... In MPlayer it just states that it cant start playing the dvd.

If i browse into the discs Video.ts folder, and manually pick the vob files, it can start them one by one, but this is not the way to watch movies...

Is there any real solution to this problem?
I have been looking for a newer version of libdvdcss, but I can not find any newer than my installed one..

---

### Post by jennhi on 2006-03-09
Hi guys! I'm noticing a lot of unresolved threads with similar problems. Has there been any progress on this issue? Is there something in Breezy that refuses to break encryption? I've been putting in DVD after DVD I rented and none of them will play on this box now.

Thanks!

---

