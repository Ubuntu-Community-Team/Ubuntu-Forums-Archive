---
title: "Various Segmentation Faults"
date: 2005-04-25
forum: Desktop Environments
---

### Post by gingermark on 2005-04-25
Hi,

Am using 5.04, and have recently found several of my programs simply won't work. I tried running them from the terminal, and for each I received a segmentation error. The programs are xmms, frozen-bubble (the game), vlc & mplayer.

With the exception of mplayer, which I just installed via apt-get, the programs have all worked previously. I thought the problem might be related to upgrading from 4.10, but I can't remember exactly when the first program stopped working.

Any help or ideas would be appreciated.

Many thanks,
gingermark.

---

### Post by gingermark on 2005-04-29
Sorry to "bump" this, but I could really do with these programs working!  :) 

I was thinking about it, and I should probably add that as a complete newbie (as opposed to just a normal newbie as I am now) I installed a few debian packages when other programs said they depended on the latest versions.

I can't remember what packages they were, and I've since read this is kinda a bad idea, but nothing broke at the time, so I figured I'd gotten away with it.

I've also tried reinstalling the programs, but that hasn't helped. Basically, despite looking for simple explanations, I have no idea what a Segmentation error is, or how to approach fixing it.

As before, any help or advice, or even places to look for more info, would be gladly received.

Best regards,
gingermark.

---

### Post by Professor X on 2005-04-29
Did you remember to do the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
```?

---

### Post by gingermark on 2005-05-01
Yeah, did that, but still have a problem. I also went and installed the Hoary versions of the Debian libraries that I installed (I think I got all of them).

I think there are a few dependencies that are still a little off, whether they are causing the Segmentation faults or not, I don't know.

---

