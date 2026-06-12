---
title: "Terrible Lag When Copying Files"
date: 2005-08-13
forum: Desktop Environments
---

### Post by duminas on 2005-08-13
Alrighty.
Coming off Windows, I had to back up about 50 GB of media; music, images, movies, and more. Copying from my DVD media (/media/cdrom0) to the custom mount I have set up for a sixty GB partition (ext3) works fine, but it is quite laggish.

That is, one of my DVDs has about 1400 files on it, and the thing has 4.3 GB of data in total. When I copy the enterity of this DVD, the copy dialogue comes up fine, but it feels much slower than it did on Windows, and while the copy process is underway, all actions on my system lag.

BMP's scrolling title lags (it skips, like frameskipping), ALT+TABbing between applications takes a couple seconds to actually *switch* the window, and typing is not instant. When I hit a key, it takes about a half-second for it to show up on my monitor.

Any ideas as to why this is happening?
Under Windows, copying was perfectly fast and there was no lag at all.
Under Linux, copying 4.3 GB takes me about fifteen minutes; it took me about eight under Windows.

Thank you for your time.

---

### Post by Lord Illidan on 2005-08-13
I think you need to enable DMA... try searching the forum, using the search facility at the top, there should be a howto...

---

### Post by duminas on 2005-08-13
Well, that seems to have gotten rid of the lagging, at least.

Though, kinda bugs me that I get an error about */dev/hdc* not existing during bootup (edited /etc/hdparm.conf to enable dma), but **hdparm -d /dev/hdc** does now report DMA as being enabled.

By the way, is it OK to ask another question about something unrelated in the same thread? I've seen lots of different ideas about this, so I figured I should make sure of one way or another first. ^^

Thank you, Illidan.

---

### Post by Lord Illidan on 2005-08-13
> By the way, is it OK to ask another question about something unrelated in the same thread? I've seen lots of different ideas about this, so I figured I should make sure of one way or another first. ^^

You've just asked it... lol..

No, it is better to open another thread otherwise everything will go off topic..

Glad to help!

---

