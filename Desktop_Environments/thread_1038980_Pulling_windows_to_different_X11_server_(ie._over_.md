---
title: "Pulling windows to different X11 server (ie. over ssh)"
date: 2009-01-14
forum: Desktop Environments
---

### Post by Nepthar on 2009-01-14
Alright, so I've scoured google and I cant find any info on this.  I recall someone wanting to do something like it, but that was over a year ago and I can't find the article anymore.  Here's what I want to do:

Say I have pidgin running on my desktop, which runs ubuntu.  Now say I SSH into my desktop from my mac laptop, running x11.  I want to pull pidgin from the X11 server on my desktop to the x11 server on my laptop, keeping all of the windows intact.  I know I can simply run another copy of pidgin using standard x11 forwarding, but I'd really like to have my active session carried over from one computer to the other.

As I said, I believe someone made a program to do this already, but google turns up nothing.  As I recall, his program did something like this

1- make new display with Xnest.
2- put any windows you think you will want to pull through in that Xnest display
3- somehow pull the xnest display from the desktop to the laptop over ssh.

any ideas?

---

