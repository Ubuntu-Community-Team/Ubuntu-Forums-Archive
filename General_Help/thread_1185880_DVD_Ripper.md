---
title: "DVD Ripper"
date: 2009-06-12
forum: General Help
---

### Post by Shibblet on 2009-06-12
Anyone know a DVD ripper for Ubuntu that ONLY rips the VOB files to the Hard Drive?  

I don't want to convert.

As I am previously a Windows user.  I really liked DVD Shrink, and DVD Decrypter.  Know anything like that?

---

### Post by japher on 2009-06-12
Depends what you want from the app I suppose.

This link has a good discussion of a few apps:
[http://linux.com/archive/feature/128105](http://linux.com/archive/feature/128105)

I'd recommend HandBrake ([http://handbrake.fr](http://handbrake.fr)). Make sure you download the GUI version though :)

---

### Post by Shibblet on 2009-06-12
> **japher said:**
> Depends what you want from the app I suppose.

This link has a good discussion of a few apps:
[http://linux.com/archive/feature/128105](http://linux.com/archive/feature/128105)

I'd recommend HandBrake ([http://handbrake.fr](http://handbrake.fr)). Make sure you download the GUI version though :)

I'd like to find a program that rips the DVD into VOB format, then I can do my conversion with another program.

DVD Shrink for Windows allows me to keep just the audio and video streams that I choose.

Anything like that?

---

### Post by rhodry on 2009-06-12
I am sure I have seen dvdshrink for Linux somewhere? Have you checked a Google search?

Also in the repos you have 'vobcopy' & 'ogmrip' both of which I am pretty sure can just copy the vob files from the dvd.

Cheers,
Rhodry.

---

### Post by khelben1979 on 2009-06-13
According to [this page]("http://www.mrbass.org/linux/ubuntu/dvdshrink/") they say that DVDShrink is working with the [wine]("http://en.wikipedia.org/wiki/Winehq") program.

---

### Post by Shibblet on 2009-06-14
I guess I was hoping for a Linux alternative to DVD Shrink.  But this program is definitely the best.  Fortunately for me it runs under Wine wonderfully.  

What I am looking for is a program that will RIP the VOB file off of the DVD, remove all of the copy protections and such into either a VOB or MPG (MPEG-2) file on the HDD.

DVD Shrink does exactly that, and allows me to choose only the main movie, along with 1 soundtrack.  

After I get it to the HDD, then I want to convert it to an Xvid (Not sure which container yet) file format.

So, I will further along this discussion...

Does anyone know a good encoder for Ubuntu?  Something that will convert from MPEG-2 to MPEG-4 (XviD) and allow for cropping of the black bars and such?

---

### Post by TrakerJon on 2009-06-14
Will MPEG, MPEG-2 or MPEG-4 be ok?

K9copy is a free open source DVD backup, copying, compression and authoring utility (requires libdvdcss).
**sudo apt-get install k9copy**

---

### Post by Shibblet on 2009-06-14
> **TrakerJon said:**
> Will MPEG, MPEG-2 or MPEG-4 be ok?

K9copy is a free open source DVD backup, copying, compression and authoring utility (requires libdvdcss).
**sudo apt-get install k9copy**

I've tried K9Copy and I can't get to recognize my DVD-Rom.  It calls it cdrom0.

I like your tagline.  Bloom County?

---

### Post by TrakerJon on 2009-06-14
You can browse to the files on your drive...and yes it calls my DVD player cdrom0 as well. Yep, Bloom County...poor Opus is no longer with us once again.

---

