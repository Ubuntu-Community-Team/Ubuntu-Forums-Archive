---
title: "Legal way to have restricted formats without owning Windows?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by misha680 on 2006-08-06
Hi,

I just recently realized that, from what I understand, using  the restricted format codecs (like MP3) using the w32codecs package is illegal if you live in the United States and do not own a copy of Windows. Although a lot of people do own Windows, as it probably came pre-installed on their computer, it seems that having to own Windows to be able to legally use MP3s on Ubuntu is not good. Is there anyone aware of a solution to this problem, such as mailing say $5 to some address somewhere (to the patent-holders) or something like that? Just wondering, because to me one of the advantages of Ubuntu (over say Windows) is that you can legally have a complete OS with Office capabilities, etc. for free, and I would just like to be able to tell people this and that they will be able to use MP3, MPG, etc. files legally as well.

Thanks a lot for any comments,
Misha

---

### Post by someguyouknow on 2006-08-06
i dunno..... buy a copy of windows 95 off of ebay for a couple of bucks? ;) 
lol.....

---

### Post by Sethro on 2006-08-06
Or a licence from Microsoft for like what... 80 bucks or something
lol

---

### Post by ardchoille on 2006-08-06
Or, do what everyone else does - just go ahead and use them.. no one's gonna care. Jails/prisons are over populated, the government is going broke.. I doubt they would go through the time, expense and trouble to track down all the people who are using restricted stuff. There aren't enough jails on the planet to hold all of us anyway.

---

### Post by az on 2006-08-06
Since the w32codecs are not licenced for redistribution, I doubt anyone is legaly entitled to download and install that package (even if you own a version of windows).  I think that if you read the fine print for every codec in that package, you are not specifically allowed to use them on another OS.

Now Gstreamer is legal in the licencing sense.  The codecs may be under patent, so that is another legal avenue...

---

### Post by Delkster on 2006-08-06
> **misha680 said:**
> I just recently realized that, from what I understand, using  the restricted format codecs (like MP3) using the w32codecs package is illegal if you live in the United States and do not own a copy of Windows. Although a lot of people do own Windows, as it probably came pre-installed on their computer, it seems that having to own Windows to be able to legally use MP3s on Ubuntu is not good.

You don't need Windows codecs for MP3 playback (nor for MP3 encoding). MP3 playback for applications using gstreamer is in the gstreamer0.10-plugins-ugly package which is in universe and doesn't depend on a Windows license in any way.

> Is there anyone aware of a solution to this problem, such as mailing say $5 to some address somewhere (to the patent-holders) or something like that?

The patent holders don't seem to go after decoders distributed and used non-commercially (right now I can't find a reference saying whether they officially announce that non-commercial decoding isn't a problem, though). The problem is mostly with commercial distribution and use of decoders, and with all encoders, commercial or not.

I'm not sure if the w32codecs package contains any Windows codecs for MP3 anyway so I don't know if having it and the corresponding licenses for the Windows software would help with that.

---

### Post by VirtuAlex on 2006-08-06
As long as I own legal copy of media I do not care about means I use to play it and nobody could possibly stop me.

---

