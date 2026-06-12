---
title: "Why there are some programs that are not looking good?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by zurih on 2006-09-23
Hi

I'm a new user of ubuntu, just installed is last night.

I'm wondering why some of the programs I install look "un-themed" ubuntu style?
I attached a screenshot of what I mean.

Thanks in advanced

---

### Post by ayoli on 2006-09-23
this is, in this particular case, only a vmware issue. there is a discuss [here]("http://www.vmware.com/community/thread.jspa?messageID=358931") about it

---

### Post by zurih on 2006-09-23
ok. but there are lots of other application with the same issue. for example XMMS options/skin windows (image attached).

Is there away to change this?

thank you very much

---

### Post by ayoli on 2006-09-23
xmms is a gtk-1.2 (old gtk) app so you have to find a theme for old gtk that fit your need.
btw you could also use a recent xmms like player such as beep-media-player. Search for it in synaptic package manager.

---

### Post by skymt on 2006-09-23
XMMS uses GTK1. The only way to make it look better is to install gtk-theme-switch and get some GTK 1.x themes at [GNOME-Look](http://www.gnome-look.org/). It still won't match your other applications, but it won't look as bad.

If you want something like XMMS that takes your theme, check out Beep Media Player (beep-media-player in Synaptic).

---

### Post by Omnios on 2006-09-23
This is a real good post on how to theme GTK-1 so it looks good. I can confirm it works.

[http://ubuntuforums.org/showthread.php?t=107135](http://ubuntuforums.org/showthread.php?t=107135)

---

### Post by zurih on 2006-09-23
> **skymt said:**
> XMMS uses GTK1. The only way to make it look better is to install gtk-theme-switch and get some GTK 1.x themes at [GNOME-Look](http://www.gnome-look.org/). It still won't match your other applications, but it won't look as bad.

If you want something like XMMS that takes your theme, check out Beep Media Player (beep-media-player in Synaptic).

cool :) installed and it works very well :)
the only thing is that it doesn't support flac files...
how can enable it?

thanks

---

### Post by ayoli on 2006-09-23
install xmms-flac package (works also for beep media player)

---

### Post by zurih on 2006-09-23
hmmm... strangly bmp exits itself just after I run it. with no notice and no errors.
this occured before I installed xmms-flac.

what can be wrong?

---

### Post by ayoli on 2006-09-23
run it from a terminal and copy/paste here if there any error ouput

---

### Post by Omnios on 2006-09-23
> **Omnios said:**
> This is a real good post on how to theme GTK-1 so it looks good. I can confirm it works.

[http://ubuntuforums.org/showthread.php?t=107135](http://ubuntuforums.org/showthread.php?t=107135)


 This mod takes all the GTK-1 ugly themes and makes all of them look rather well. Even fixes mplayer.

 Anyways welcome to the Ubuntu Forum comunity

---

### Post by zurih on 2006-09-23
> **ayoli said:**
> run it from a terminal and copy/paste here if there any error ouput

```

Received SIGSEGV

This could be a bug in BMP. If you don't know why this happened, send a mail to us at beepmp-devel@lists.sourceforge.net

```

---

### Post by zurih on 2006-09-23
> **Omnios said:**
> This mod takes all the GTK-1 ugly themes and makes all of them look rather well. Even fixes mplayer.

 Anyways welcome to the Ubuntu Forum comunity

thanks! glad to be here. great community :)

---

