---
title: "lucid fonts (firefox)"
date: 2010-07-14
forum: Desktop Environments
---

### Post by metalfan_ on 2010-07-14
Hi,

ive installed 10.04 from the amd_x64 cd, the fonts in firefox look like this:

[IMG]http://i25.tinypic.com/30ji3hv.png[/IMG]

the problem is mostly with firefox, the rest of the desktop only has a few "errors"

any ideas?

---

### Post by darkmaxa on 2010-07-14
I'm struggling with the same problem ([click]("http://ubuntuforums.org/showthread.php?t=1530224")), but what frustrating me even more is that no one of "ubuntu lovers" do not see or do not want to see that their lovely OS don't have some basic funcionality such as proper font rendering.

---

### Post by QIII on 2010-07-14
... or, others are simply not having the same issues as you.  That doesn't make your issues insignificant.  They need to be resolved.

Also to be considered is the user's personal sense of aesthetics.  Some like their steaks rare, others well done.

If I get a chance, I'll look through launchpad.  (Lunch break is about over, so I can't promise anything.)

In the meantime, check this out.  lovinglinux may have something useful with regard to Firefox.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

---

### Post by Haylz on 2010-07-14
Try installing Windows fonts and changing Firefox's fonts (in preferences) to a Windows one...

Look for "Ubuntu restricted extras" in the software centre.

Or type "sudo apt-get install ubuntu-restricted-extras" in a terminal.

> Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

---

### Post by darkmaxa on 2010-07-14
> **QIII said:**
> ... or, others are simply not having the same issues as you.

I've made bootable USB flash, and I've tried Ubuntu on two desktops and one laptop. Font rendering is identical (and bad) on all of that three computers.

> **QIII said:**
> 
Also to be considered is the user's personal sense of aesthetics.  Some like their steaks rare, others well done.

I do not expect Ubuntu to be Windows clone. For example, I do not prefer Win XP rendering, but I can't say it's bad, just I don't like it. On the other hand, Ubuntu & Firefox font rendering is simply **bad**, I can't say "it is just different".

---

### Post by QIII on 2010-07-14
Remember that I said the issue is not insignificant and needs to be  resolved.
 
 What metalfan gave us is definitely bad.  No doubt about that. 
  
  I've not had that sort of a problem.  But it is certainly possible that  because I have been carrying my /home (and a lot of extra stuff that I  like to keep) forward on fresh installs for years, I have forgotten  something I did a long time ago.
  
  I've been in several threads about fonts where someone has complained  about fonts/rendering based on more aesthetic grounds.
  
  "I like my fonts crisp, like this...", accompanied by an image of a font  that looks pixellated  -- like an old "green on black" monochrome terminal -- to me.
  
  To get more Microsoft-like fonts, you have to install them.  And, if I  am not mistaken, you can only get a subset of the true-type fonts at  that.

metalfan's clearly sub-standard rendering aside, what you may consider  "proper font rendering" may be at odds with someone else's view of  proper font rendering. 

In the thread you linked to, you did say "for my taste".

---

### Post by darkmaxa on 2010-07-14
I've installed MS fonts, but then font rendering on web pages looks even worst. It seems to me that rendering engine better handle native fonts than MS fonts.

Can you post some screenshot?

What do you think about this screenshot?
[IMG]http://i25.tinypic.com/2hx1s3t.png[/IMG]

I'm testing Kubuntu now, font rendering in FF looks better (vs Ubuntu), but [COLOR=#000000]I'm not impressed. :|
[/COLOR]

---

### Post by darkmaxa on 2010-07-14
Here is one pretty nice example from [another thread]("http://ubuntuforums.org/showthread.php?t=1064418"):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103633&d=1234888022[/IMG]

---

### Post by lovinglinux on 2010-07-14
> **QIII said:**
> In the meantime, check this out.  lovinglinux may have something useful with regard to Firefox.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

Yes, I guess I have :). That's a common problem. See the last item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by darkmaxa on 2010-07-14
> **lovinglinux said:**
> Yes, I guess I have :). That's a common problem. See the last item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

I've tried it already, no big difference, still bad.

And why hintmedium and hintfull do not make **any** difference?

---

### Post by lovinglinux on 2010-07-14
> **darkmaxa said:**
> I've tried it already, no big difference, still bad.

And why hintmedium and hintfull do not make **any** difference?

Not sure.

---

### Post by UberStudent on 2010-07-15
Yep, I experienced the very same thing, system-wide. Dealing with .fonts.conf did not fix.

I'm thus pretty confident it's an X bug. I installed and enabled NVIDIA proprietary driver and it ceased.

---

### Post by lovinglinux on 2010-07-15
> **UberStudent said:**
> I'm thus pretty confident it's an X bug. I installed and enabled NVIDIA proprietary driver and it ceased.

Good to know. Thanks for the info.

---

