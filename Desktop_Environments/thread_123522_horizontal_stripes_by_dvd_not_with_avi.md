---
title: "horizontal stripes by dvd not with avi"
date: 2006-01-30
forum: Desktop Environments
---

### Post by maxdevis on 2006-01-30
when i play a dvd, it seems like it is build with horizontal stripes.
You can see it the most when there's a lot of movement.
It's really irritating.

But when i play an avi, it's not.
What can i do?

I play them with VLC
I have a PIV 1,8 and an ati 9550

---

### Post by eriqk on 2006-01-30
What do these lines look like? Are they very fine, approximately 1 pixel, or very thick?
If they're very fine, you may be looking at interlacing. This is how most video frames are built up, and they're very noticable during horizontal motion on a non-interlaced screen.
VLC doesn't de-interlace, I believe, so that may be your problem. You could try a mediaplayer that hat a post-processing option.

Groet, Erik

---

### Post by maxdevis on 2006-01-30
yes very fine.
do you know such player?

---

### Post by mcduck on 2006-01-30
Yes, that's definitely caused by interlacing used in everything that's ment to be displayed in TV. They display only half of the picture per every frame, first odd lines and then even. (or the other way round) Nasty thing, and it was never ever supposed to be permanent feature of either NTSC or PAL system. It justv stuck around.

I think that VLC _does_ have deinterlace filter, you'd just have to turn it on. But you could also try Xine (or Totem-Xine) too. I use Xine for all DVD-movies, I think it does very good job with filtering.

---

### Post by maxdevis on 2006-01-30
how do i install xine?

---

### Post by mcduck on 2006-01-30
Like almost any software: 'sudo apt-get install gxine' (or xine-ui if you want. gxine fits better in Gnome desktop) You can find bot with Synaptic too, search for 'xine'.

---

### Post by maxdevis on 2006-01-30
can you give me the settings of your xine?
now the view shocks and my dma is on

---

### Post by mcduck on 2006-01-30
try setting video driver to 'xv' or something else.

---

### Post by maxdevis on 2006-01-30
i did this an everything works fine

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

---

