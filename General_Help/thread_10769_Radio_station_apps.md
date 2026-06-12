---
title: "Radio station apps"
date: 2005-01-11
forum: General Help
---

### Post by nocturn on 2005-01-11
I'm looking for Free software to run a small, local radio station on Ubuntu.

What I'm looking for is software to assemble programs and include radio ads.

The Ubuntu server would be used to 
- broadcast via an antenna
- Possibly a streaming solution to provide radio over the Internet (not yet sure).
- compose the programs from a remote location.

This information is for a fiend of mine, I would like to keep him away from a windows based solution (with proprietary software), and I can help him admin the Ubuntu box.

Does anyone know if such software exists for Linux/Ubuntu and what it's capabilities are?

Thanks

---

### Post by jobezone on 2005-01-11
Have you looked at icecast? 
[http://www.icecast.org/](http://www.icecast.org/)
[http://www.gnuware.com/icecast/](http://www.gnuware.com/icecast/)

I've never used it, so I don't know if it has the features you need.

---

### Post by SFN on 2005-01-20
I'm doing exactly this. I use icecast and darkice and XMMS.

Although there are debs for both (through Universe if not through the Ubuntu repositories) I built them from source. To be honest I can't remember why although I don't usually build from source unless I can't find debs or the debs to don't work out.

At any rate, the point of darkice is it streams output from your sound card. That mens you can stream microphone input and music at the same time. Makes for a smoother flow.

You may also wish to look at MuSE. It's a streamer for icecast. It does all the stuff that darkice can do plus a few more things and it comes with a handy interface. You can find debs for that at the bottom of [ftp://ftp.dyne.org/muse/releases/](ftp://ftp.dyne.org/muse/releases/).

The only reason I don't use it is I like using XMMS for my player. It makes it easier to jump back and forth from using an automated playlist and managing your playlist live. 

Hope this helps.

SFN

---

