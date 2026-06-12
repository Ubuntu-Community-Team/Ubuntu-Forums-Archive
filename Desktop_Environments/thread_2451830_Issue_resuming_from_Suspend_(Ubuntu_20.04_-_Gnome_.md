---
title: "Issue resuming from Suspend (Ubuntu 20.04 - Gnome 3.36.3)"
date: 2020-10-11
forum: Desktop Environments
---

### Post by oobi2 on 2020-10-11
Good Day to you all!

Loving 20.04! Unfortunately with my Lenovo ThinkPad T470S, i've been having issues resuming my session after the laptop suspends from the lid closing, or from timeout. I think it has to do with my desktop environment, as the operating system still functions normally in tty mode during all of this.

When attempting to login after resuming from suspend, as soon as authentication succeeds, my screen freezes on the purple login background with my user picture and password entry. Switching to tty when it's frozen here is possible, but the GUI is unusable until the system is rebooted, losing unsaved work.
I've tried switching to tty, logging in, and restarting the display manager; once doing so I'm greeted with a functional login screen again, but once I try logging into my account, i'm successfully authenticated but immediately directed back to the login screen. The only way to make the GUI usable again is to reboot the system, losing unsaved work.


These symptoms repeat no matter what applications or processes are running when the system enters suspend. This just started happening recently, and I think it has to do with a kernel update that came out.

What's a good place to start diagnosing this issue? What logs should I look at to see what's happening?

---

