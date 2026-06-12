---
title: "Nautilus Timeout?"
date: 2010-10-29
forum: Desktop Environments
---

### Post by TLangas on 2010-10-29
I am experiencing strange behavior with nautilus.

I've been working away all day and noticed nautilus has stopped working. I shrugged it off and finished what I was working on. I've had nautilus lock up on me before but it was always easy to recover from.

Normally I just restart gdm (or reboot).

In this case I get the following when trying to start nautilus:
> Unique-DBus-WARNING **: Error while sending message: Did not  receive a reply. Possible causes include: the remote application did not  send a reply, the message bus security policy blocked the reply, the  reply timeout expired, or the network connection was broken.

I've tried purging nautilus and nautilus-data. Followed by a install and restarting the computer.

Now I am using nautilus-dropbox. I've never had a problem with it so far and I really don't think it is causing trouble.

I'm at a lost. Anyone have an idea on how to get nautilus working again?

---

### Post by TLangas on 2010-11-02
I figured out what was wrong. Apparently viewing an Inkscape .svg file with nautilus would cause it to freeze/crash. It took me a while to figure this out, since I had a few svg files sitting on my desktop, causing nautilus to crash right away.

For now, I've moved the svg files into a folder and use the terminal or another file manager (gnome-commander) to enter that folder. It's not ideal, but at least I have nautilus working again.

There are already several bug reports involving nautilus and svg files. I'll add my two cents when I get around to it.
[https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/305546](https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/305546)

---

