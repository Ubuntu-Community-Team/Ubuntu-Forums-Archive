---
title: "Fluxbox dragging window speed lag"
date: 2011-09-30
forum: Desktop Environments
---

### Post by kerryhall on 2011-09-30
Hello,

When using fluxbox, dragging windows lags about a second or two. The larger the window, the more lag. Any ideas?

Thanks!

---

### Post by kerryhall on 2011-10-02
Bump

---

### Post by Copper Bezel on 2011-10-02
Okay, a couple of quick questions, then, to narrow this down:

Is it an overall performance lag, or specifically when moving windows - i.e., does resizing the window also lag?

Do you get the same behavior under other window managers?

What's your video card?

---

### Post by kerryhall on 2011-10-03
Thanks for the help!

The drop in performance seems to be specifically related to dragging windows. Resizing windows has no lag in performance, but when I resize a window it just shows lines showing the size of the resized window, whereas when I drag a window it shows the whole contents of the window being dragged. 

I do not have this problem with metacity. 

My video card is (unfortunately) Embedded ATI ES1000.

---

### Post by kerryhall on 2011-10-05
Bump

---

### Post by Copper Bezel on 2011-10-05
Yeah, I don't know Fluxbox *or* this video card stuff, and I was hoping that someone might have had a similar problem to yours and have a solution. I imagine that if you've been poking around, you might have found [_this_]("http://lists.debian.org/debian-user/2008/10/msg01301.html"), which is the only similar problem I can find. The lag sounds similar and the suggestion was to try the open source driver instead, as the proprietary driver didn't play well with Fluxbox, but it's from *2008*. Are you using the proprietary driver, perchance?

---

### Post by kerryhall on 2011-10-10
I'm not sure. In my xorg.conf, it says Driver "ati" but that could mean anything I guess. I ran the restricted drivers manager and it says that no restricted drivers are in use. So I guess that is a no then.

BTW, is xorg.conf even used anymore? I have someone tell me that it was deprecated, but I dunno...

Thanks!!

---

### Post by kerryhall on 2011-10-12
Bump

---

### Post by Copper Bezel on 2011-10-12
Still no luck? Have you checked out the [_Fluxbox user group_]("http://groups.google.com/group/fluxbox?pli=1") or anywhere else?

---

