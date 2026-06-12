---
title: "Yet Another &quot;Don't Have Permission to Open VIDEOCD&quot;"
date: 2012-05-16
forum: Desktop Environments
---

### Post by Acharn on 2012-05-16
Yesterday I finally got a new hard drive, and promptly installed Ubuntu. I upgraded from 10.10 to 11.10, and expect to go on to upgrade to 12.04 today. It seems I still cannot use my CD/DVD reader/burner. If I insert a DVD (which was burned in this device under Windows) it just sits there like a lox-- nothing happens at all. I haven't really started exploring possibilities there, but I did install the libdvd2 and libdver4read thingy. They should be irrelevant, because the DVD is not encrypted.

Anyway, when I insert a video cd (which was burned in this device under Windows) it is detected and I get an icon shouwing the mounted device and an error message that says: "An error occurred. Could not open location; you might not have permissions to open the file." So I used 'ls -l' to see what permissions are set on the files:

roger@roger-Aspire-M1610:~$ ls -l /media
total 2
dr-x------ 1 roger roger 2048 1978-07-14 07:00 VIDEOCD
roger@roger-Aspire-M1610:~$ ls -l /media/VIDEOCD
total 8
dr-x------ 1 roger roger 2048 1978-07-14 07:00 ext
dr-x------ 1 roger roger 2048 1978-07-14 07:00 mpegav
dr-x------ 1 roger roger 2048 1978-07-14 07:00 segment
dr-x------ 1 roger roger 2048 1978-07-14 07:00 vc

So the device and files are being opened with the execute and read permissions for the owner set. Is this significant? I've been really frustrated by this problem. I haven't yet tried installing SMPlayer (my choice, I really like it) or VLC Player, but I've installed all the codecs, including the ubuntu restricted. This is so frustrating, because it worked without problems under Windows and the VCD (and the DVD) are readable by the player attached to my TV. Oh, yeah, I can't burn cd's, either, which is why I've had to upgrade insteat of just burning the iso of Ubuntu 12.04 and installing it.

---

### Post by Acharn on 2012-05-17
OK, I installed SMPlayer and it works. Why nobody else ever simply said, "The Totem Movie Player does not play VCDs," I do not know. For anybody else having this problem, you'll find many threads advising you to install VLC Player or SMPlayer, and that is the solution, but they should also tell you that the reason you're getting the error message is because the default Movie Player cannot play VCDs. Now I need to find out where they moved the System Setting to for Removable Media in 12.04. And it still does not detect DVDs.

---

### Post by anka8 on 2012-05-31
If you cant play a VCD cd, then follow these.  Install VLC Player then open it. From the 'Media' options select the 'Open Disc' from there select the 'VCD'. There you go, it works.

---

### Post by Acharn on 2012-06-01
Well, as posted above I accomplished the same thing with SMPlayer, which I like better than VLC Player because it remembers where I interrupted the movie. The problem I still have, reported in another thread, is that the drive does not detect some DVDs at all. I mean I put the DVD in the drive and the drive spins and the light blinks -- without end. The drive never recognizes the DVD, whether it's one that I burned in this drive under Windows, or a blank DVD. That's the big problem now. It does not recognize a blank DVD so I can't use it to burn a DVD. To my immense frustration, it **does** recognize some DVDs. I have an incomplete set of The Sopranos, and not only does the drive recognize them, Movie Player plays them.

So the drive recognizes CDs, including blank CDs, it recognizes some DVDs that have already been recorded, and it does not recognize other DVDs that were burned on it and does not see/recognize blank DVDs. Oh, yeah, the DVDs that were burned in this drive are readable by the DVD player attached to my TV set (I "authored" them with a Windows program named DVD Flick).

Thanks for the suggestion, though.

---

### Post by anka8 on 2012-06-01
Well. What is your DVD's file extension? Does it work in other operating systems? For burning a blank CD or DVD, I suggest you the  K3B. It never leave me in midway. And it will warn you whether the inserted DVD/VCD blank or not.

---

### Post by Acharn on 2012-06-02
> **anka8 said:**
> Well. What is your DVD's file extension?
File extension? This is discs we're talking about, not files. For what it's worth, the discs are Princo, a low-price brand here in Thailand. I admit they're pretty old, but the CDs work OK.
> Does it work in other operating systems?
It used to work fine in Windows XP Pro. The DVDs were burned in this drive using ImgBurn under WinXP Pro. I had a hard drive failure last year and had to start using Ubuntu instead, and now I don't want to go back to Windows. The discs, both CD and DVD work fine in the DVD player attached to my TV set. I'm currently not able to try them in another computer using a different operating system.
> For burning a blank CD or DVD, I suggest you the  K3B. It never leave me in midway. And it will warn you whether the inserted DVD/VCD blank or not.
You don't seem to understand. The drive is not reading the DVDs I burned in it a couple of years ago, and is not recognizing blank DVDs. When I put them in the drive and shut the drawer, it starts spinning, the light starts blinking, and ten minutes or half an hour later it's still doing that. If I insert a blank CD, after a few seconds Ubuntu shows an icon on the desktop indicating there's a blank CD in the drive. So it sees CDs OK, it reads the commercial DVDs I have, but it doesn't detect a blank DVD, so I can't use ANY burning program. Movie Player, which can't seem to play the VCDs I burned on this drive a few years ago, plays the commercial DVDs without hesitation. But I can't burn a new DVD because the drive doesn't know what it is when I put it in there.

I'm glad you're trying to help me, but the problem is not what I originally posted about here -- that was solved already.

---

### Post by anka8 on 2012-06-02
Sorry, cant help more. Here a site giving some info regarding DVD file formats: [http://dvd-ripper-software-review.toptenreviews.com/so-many-video-formats-which-one-do-i-use-.html](http://dvd-ripper-software-review.toptenreviews.com/so-many-video-formats-which-one-do-i-use-.html), 

Good day.

---

