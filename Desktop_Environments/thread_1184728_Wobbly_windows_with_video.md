---
title: "Wobbly windows with video"
date: 2009-06-11
forum: Desktop Environments
---

### Post by frogbrains on 2009-06-11
Hello there!
On every other Ubuntu install I have used, (which include 8.04, 8.10, and 9.04) when the windows were manipulated, (wobbled about, set on fire etc.) it effected the video as well.  The video got curved, I mean.  I recently downgraded from 9.04 back to 8.04, because of the Intel graphics driver thing in 9.04, and I needed Blender.  Now, when wobbling the window about, if there is video in Totem or something, it goes all black and flickery until the window stops wobbling.  Also, the video isn't visible through the translucent volume meter thing that comes up.  I know this is something to do with compositing, but I don't know how to fix it.

Sorry if this has been posted before, but I wasn't sure what to search for to find it!
Adam

Edit: Also, I was just listening to some midis, and noticed how effing brilliant Timidity's softsynth is!  It's missing a couple of instruments, but those that are there sound really, really good!  Who agrees?

---

### Post by frogbrains on 2009-06-11
Hello there!
On every other Ubuntu install I have used, (which include 8.04, 8.10, and 9.04) when the windows were manipulated, (wobbled about, set on fire etc.) it effected the video as well. The video got curved, I mean. I recently downgraded from 9.04 back to 8.04, because of the Intel graphics driver thing in 9.04, and I needed Blender. Now, when wobbling the window about, if there is video in Totem or something, it goes all black and flickery until the window stops wobbling. Also, the video isn't visible through the translucent volume meter thing that comes up. I know this is something to do with compositing, but I don't know how to fix it.

Sorry if this has been posted before, but I wasn't sure what to search for to find it!
Adam

---

### Post by overdrank on 2009-06-11
Threads merged :)

---

### Post by Fzang on 2009-06-11
It must be a problem with your driver. My 9650M GT can do wobbly windows + videos without any problems or artifacts. I don't really have a solution for you, though...

I'm on 9.04 btw

---

### Post by frogbrains on 2009-06-12
> **Fzang said:**
> It must be a problem with your driver. My 9650M GT can do wobbly windows + videos without any problems or artifacts. I don't really have a solution for you, though...

I'm on 9.04 btw

Yeah.  As I think I said, it's worked fine for me in all other versions, including 9.04, just not 8.04

---

### Post by overdrank on 2009-06-12
> **frogbrains said:**
> Yeah.  As I think I said, it's worked fine for me in all other versions, including 9.04, just not 8.04

I am going off memory here but in Hardy with the intel graphics I believe you need to install the 915 resolution package and use the 810 driver for better performance.

---

### Post by frogbrains on 2009-06-12
> **overdrank said:**
> I am going off memory here but in Hardy with the intel graphics I believe you need to install the 915 resolution package and use the 810 driver for better performance.

And where would I get the 915 resolution package and the 810 driver?

---

### Post by overdrank on 2009-06-12
> **frogbrains said:**
> And where would I get the 915 resolution package and the 810 driver?

You may use synaptic manager for the 915 resolution, and you may use the command ```
gksu displayconfig-gtk
``` I believe to set up the i810 driver.

---

### Post by frogbrains on 2009-07-27
> **overdrank said:**
> You may use synaptic manager for the 915 resolution, and you may use the command ```
gksu displayconfig-gtk
``` I believe to set up the i810 driver.

Ok.  Is it possible that setting this up incorrectly could screw up my display?

---

