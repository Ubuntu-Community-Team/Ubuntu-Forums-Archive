---
title: "brief screen flashes and 100% cpu usage"
date: 2005-04-23
forum: Desktop Environments
---

### Post by El Rey de Todo on 2005-04-23
I've been having a problem for the past week or so that I can't seem to fix and I've run out of things to try myself.

When the problem started, I was playing around with getting Splashy working (and playing with framebuffers in general).  I have since uninstalled Splashy and all other stuff I installed at the time, but the problem didn't stop.

The problem is that when I have a terminal opened in gnome and i press tab to autocomplete or an arrow button in less or do anything really that requires a moment of though, the entire X screen momentarily flashes black and the CPU usage shoots up to 100% for a moment.  If I press tab multiple times it will flash the screen as many times as I pressed tab and there will be a brief pause between each of them.

I suspect the problem started because I installed some framebuffer-related package that changed a config file and didn't chage it back when it uninstalled.  Has anyone else had this problem or know how I can fix it? I can't even figure out what I changed to make it happen :(

Hardware info:
Centrino laptop with ATI Radeon 9200 graphics
I've tried this with the default ati driver, fglrx (ubutu version), and third-party fglrx drivers (which are currently installed).

Thanks!
Martin

---

