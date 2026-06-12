---
title: "no text in forefox or any web browser"
date: 2009-06-24
forum: General Help
---

### Post by sdlynx on 2009-06-24
I recently installed Ubuntu onto my laptop and it ran fine the first time I booted it up.  However, I restarted and proceeded to open Firefox for the internet and found that no text was showing up.  For links, I could see the underline, but nothing for just text.  The only web site I found that I could read was wikipedia.  Everything else is fine, just the internet and web browsers are having this problem. I can highlight the text but it still reads nothing.  I can copy the text and it is readable in gedit.  Fixes for this?

Example: [http://ubuntuforums.org/attachment.php?attachmentid=96086&d=1229048087](http://ubuntuforums.org/attachment.php?attachmentid=96086&d=1229048087)

---

### Post by utnubuuser on 2009-06-24
An xorg issue maybe?

Used to be > sudo dpkg-reconfigure xserver-xorgfixed those kinds of issues.

---

### Post by lovinglinux on 2009-06-24
[http://ubuntuforums.org/showthread.php?t=1008752](http://ubuntuforums.org/showthread.php?t=1008752)
[http://ubuntuforums.org/showthread.php?t=911375](http://ubuntuforums.org/showthread.php?t=911375)

EDIT: oops, I just saw that the imaged attached on your post is the same on the first link I provided, so I guess yo already been there. My bad.

Did you tried the second link?

---

### Post by sdlynx on 2009-06-24
I tried making Firefox only use its default fonts and that seems to have worked.  It must have something to do with my fonts.  I'd rather it be that I am able to see the fonts chosen by web pages if I have them though...

Unfortunately the first thread doesn't have a solution actually written (as I saw last time), but the second one was rather useful.

EDIT: I tried sudo dpkg-reconfigure xserver-xorg but that didn't seem to fix anything.
RE-EDIT: I removed all the fonts I had installed on the computer and now I can use the 'use fonts specified by web pages' option so that must have been it.  The exact same fonts work fine on my other ubuntu 9.04 machine...

---

