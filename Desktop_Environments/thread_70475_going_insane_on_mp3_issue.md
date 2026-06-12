---
title: "going insane on mp3 issue"
date: 2005-09-30
forum: Desktop Environments
---

### Post by unixsphere on 2005-09-30
I dont understand why doesnt ubuntu just support mp3? are you guys another redhat? What possible "legal" issues can arise? I mean its a format of music. No ONE will ever drag anyone to court for supporting mp3 music.

I cannot play mp3 with rhythymbox? I did a search but nothing is helping. I am absolutely new to ubuntu and am coming from slackware linux

---

### Post by xmastree on 2005-09-30
[http://www.ubuntuforums.org/showthread.php?t=51444](http://www.ubuntuforums.org/showthread.php?t=51444)

You need to download the codecs.

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by Knome_fan on 2005-09-30
[QUOTE=unixsphere]I dont understand why doesnt ubuntu just support mp3? are you guys another redhat? What possible "legal" issues can arise? I mean its a format of music. No ONE will ever drag anyone to court for supporting mp3 music.
[/quote]
That's not true, people already have been draged to court.

[QUOTE=unixsphere]
I cannot play mp3 with rhythymbox? I did a search but nothing is helping. I am absolutely new to ubuntu and am coming from slackware linux[/QUOTE]

It's actually very simple. Mp3 support for gstreamer (the engine rhythmbox uses) is in the multiverse repository.
Just add ```
deb http://archive.ubuntu.com/ubuntu hoary multiverse 
``` into your /etc/apt/sources.list, then do an apt-get update and install gstreamer0.8-mad.

Have fun!

P.S.:
You might also want to take a look at the ubuntuguide for more information about issues like this:
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by wmcbrine on 2005-09-30
It's a patent problem. I assure you, it's real, and you can take the quotes off of "legal". Yes, it's widely ignored; Ubuntu is being more conscientious about it than some. And others have in fact paid for licenses; you just don't hear about it.

There's a whole site devoted to the issue, put up by the patent holders:

[http://www.mp3licensing.com/](http://www.mp3licensing.com/)

The patents are not valid in all countries.

Note again that this has nothing at all to do with whether the content (music) is pirated or not. It's purely about patents on algorithms used in MP3 decoders and encoders. There were similar issues with GIF images, until the patents expired recently. These and other patents were a prime motivation behind the creation of alternative formats like gzip (vs. old Unix's compress), PNG (vs. GIF) and Ogg Vorbis (vs. MP3). The fact that the unencumbered formats are also better-performing is a plus. :)

---

### Post by az on 2005-09-30
[QUOTE=unixsphere]? are you guys another redhat? .[/QUOTE]

If by that you mean another linux distribution that promotes free and open software, yes.  

I would love to be able to buy music online in ogg format.  It it completely free aqnd open source, there are no royalty fees on the part of the seller or buyer and it works great.

For this to happen, somebody has to make a stand somewhere.

[QUOTE=unixsphere]What possible "legal" issues can arise? I mean its a format of music. No ONE will ever drag anyone to court for supporting mp3 music.
I cannot play mp3 with rhythymbox? I did a search but nothing is helping.[/QUOTE]

The problem you are experienceing is with the documentation.  I am pretty sure that this is much better in Breezy.  The codec cannot be shipped, but you can be informed better.

---

