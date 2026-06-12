---
title: "DVD Ripping Software"
date: 2005-01-18
forum: Desktop Environments
---

### Post by talkingwires on 2005-01-18
I've been looking for a DVD ripping program, and have heard good things about dvd::rip. However the package from [Marillat](ftp://ftp.nerim.net/debian-marillat/) requires the packages not+i386 and libdivxencore0, which I have been unable to locate in either Ubuntu's or Debian's repositories (or, hell, even a Google search). Any idea what these are and where I could find them? Thanks.

---

### Post by randy on 2005-01-18
cpdvd + wine + dvdshrink is the easiest solution that I've found

---

### Post by talkingwires on 2005-01-18
Yes, I heard about that solution in the so-called [Lazy DVD Backup HowTo](http://www.ubuntuforums.org/showthread.php?t=5904&highlight=dvd+ripping). I was hoping to avoid using Wine, as Crossover Office is broken in Hoary installation (the new menu structure broke it... and I no longer have an internet connection to update it.)

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=talkingwires]Yes, I heard about that solution in the so-called [Lazy DVD Backup HowTo](http://www.ubuntuforums.org/showthread.php?t=5904&highlight=dvd+ripping). I was hoping to avoid using Wine, as Crossover Office is broken in Hoary installation (the new menu structure broke it... and I no longer have an internet connection to update it.)[/QUOTE]

The dvdshrink works! Don't be afraid. just unistall and reinstall crossover! I use crossover and dvdshrink!

---

### Post by talkingwires on 2005-01-18
Alrighty. I'll give it a shot this evening...

---

### Post by ixus_123 on 2005-01-18
I find acidrip to be great.  It's a frontend to mencoder & there's a detailed howto linked on the main page.

Better to follow the howto & compile from source for that though.  :)

DVD::RIP is supposed to be very good to, although a little more complex to use.  I want to give it a try becuase you can record more than one soundtrack with it - great if you want a commentary or can't decide between dub/sub

---

### Post by machiner on 2005-01-19
The last time I ran DVD::RIP it wanted 80GB (yeah - you read that right) as temp space to transcode the dvd - to avi after the disk was ripped.

YHGTBFKM!!! SO - I redid my partitions, put winxp back on - stopped about every service, installed my copy of dvdcopy platinum, made my 10 gb temp partition and I'm back in business.

Sorry, but 80 gb to transcode a file...thank you no.

---

### Post by DevilBuster on 2005-04-13
I use VLC, yes I am a nOOb  :roll: 
I stream the DVD to my HD, It works fine.
I am not a hardcore DVD ripper, but just trying it out, for fun.

Oh, by the way... Ubuntu ROCKS!! - I am no longer a Win user  :grin: 
[COLOR=Red]
Devil[/COLOR][COLOR=DarkOrange]Buster[/COLOR]

---

### Post by justinflavin on 2005-04-13
I've used Video-DVD-Rip on my Mandrake machine (is that the same as DVD::Rip?) , but the downside is that it uses a lot of disk space before transcoding to AVI format.

Worked fine though - although i've not tried it on my Ubuntu machine yet.

---

### Post by sinbad782 on 2005-07-27
i have got dvd::rip (uses transcode) as well as acidrip (uses mencoder) installed. I haven't started using acidrip yet but dvd::rip works fine for simple ripping. 

There are many dependencies for dvd::rip that don't get installed by default, but I put all of these on there - there's a dependency check tool included in the package. I did have trouble using it to transcode a straight DVD rip to divx4 though - something appeared in the logs about the divx driver not being able to load...

I'll give acidrip a try next - it looks a bit simpler for the non-expert and I prefer the GTK interface.

---

