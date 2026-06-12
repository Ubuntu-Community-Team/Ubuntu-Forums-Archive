---
title: "MP3 support in Ubuntu and its Patent Issue"
date: 2005-07-24
forum: Desktop Environments
---

### Post by jery_wang2002 on 2005-07-24
Hi,

I can't seem to have mp3 support (codec) in my grip.

Is it because Ubuntu have some issues with patented mp3? Where can I download mp3 codec for grip?

If mp3 is supported, does this mean Ubuntu (Canonical) pays royalties to MP3 licensor? So that we (end-user) can use it without paying royalties. If Ubuntu did not pay any royalty, does Ubuntu in anyway infringe MP3 patent?

I know fedora core (up to fc4) never distribute mp3 codec. But I can always get it from freshrpm. Does this mean that I am infringing patented MP3 by downloading MP3 codec from freshrpm. And likewise, whoever runs freshrpm also infringes the MP3 patent?

Can someone help me understand all this before I download and use it or install it in my friends' computer?

Thanks.
Jerry

---

### Post by ubuntp on 2005-07-24
You can get lame when you add the following to your repositories in /etc/apt/sources.list

deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

and simply *sudo apt-get update && sudo apt-get install lame*. Notice that grip needs the full path to the encoder, like /usr/bin/lame.

About the license:

> A license is needed for commercial (i.e., revenue-generating) use of mp3/mp3PRO in broadcast systems (terrestrial, satellite, cable and/or other distribution channels), streaming applications (via Internet, intranets and/or other networks), other content distribution systems (pay-audio or audio-on-demand applications and the like) or for use of mp3/mp3PRO on physical media (compact discs, digital versatile discs, semiconductor chips, hard drives, memory cards and the like).

However, no license is needed for private, non-commercial activities (e.g., home-entertainment, receiving broadcasts and creating a personal music library), not generating revenue or other consideration of any kind or for entities with an annual gross revenue less than US$ 100 000.00. 

---

### Post by danns on 2005-07-24
I'm not sure about the legality issues behind mp3, but from what I hear it is a commercial codec and if used for commercial purposes there is a license to be paid somewhere down the line.

Lame is released under the lgpl, is a pretty easy compile and can be found here:  [http://lame.sourceforge.net/](http://lame.sourceforge.net/) 

This should work with grip as it is listed under the preferences.

---

### Post by jery_wang2002 on 2005-07-24
Thanks.

Which site did you get the link about the license?

Jerry
[QUOTE=ubuntp]You can get lame when you add the following to your repositories in /etc/apt/sources.list

deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

and simply *sudo apt-get update && sudo apt-get install lame*. Notice that grip needs the full path to the encoder, like /usr/bin/lame.

About the license:[/QUOTE]

---

### Post by ubuntp on 2005-07-24
[http://www.mp3licensing.com](http://www.mp3licensing.com)

---

### Post by jery_wang2002 on 2005-07-24
[QUOTE=ubuntp]You can get lame when you add the following to your repositories in /etc/apt/sources.list

deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

and simply *sudo apt-get update && sudo apt-get install lame*. Notice that grip needs the full path to the encoder, like /usr/bin/lame.

About the license:[/QUOTE]

How about MPEG4, I'd like to rip my DVD collection into mp4 files. Is the licensing is the same?

What front-end tool in Ubuntu for me to rip my DVD into MPEG4 files?

I always find Ubuntu forum is very responsive and supportive.

Thanks
Jerry

---

### Post by angkor on 2005-07-24
[QUOTE=ubuntp]Y
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
[/QUOTE]

Isn't 'lame' available from the universe repos?


```
apt-cache search lame | grep MP3
lame - LAME Ain't an MP3 Encoder
lame-extras - LAME Ain't an MP3 Encoder
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
```

---

### Post by MetalMusicAddict on 2005-07-24
[QUOTE=jery_wang2002]How about MPEG4, I'd like to rip my DVD collection into mp4 files. Is the licensing is the same?

What front-end tool in Ubuntu for me to rip my DVD into MPEG4 files?

I always find Ubuntu forum is very responsive and supportive.

Thanks
Jerry[/QUOTE]
Man Ive been trying to fine out the same thing for 6 months. I think theres nothing as good as GordianKnot. I use it on windows to go to XviD/OGG.

---

