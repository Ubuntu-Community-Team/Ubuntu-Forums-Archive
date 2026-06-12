---
title: "Remote+Local X Session"
date: 2010-01-09
forum: Desktop Environments
---

### Post by HyperHacker on 2010-01-09
I know this is possible, but I don't really know how to do it, and I haven't managed to get it working at all.

I have two machines, Mercury (running Xubuntu 9.04 because I haven't got around to upgrading it) and Shugo (running a fresh install of 9.10).

Mercury is my main desktop, using two monitors on an nVidia AGP card. The motherboard doesn't seem to be capable of running multiple video cards, so I've gone this route.

Shugo is another machine which *is* capable of running multiple video cards, but is a bit older, and (due to desperately needing RAM/HDD upgrades) horrendously slow, so I don't use it as a desktop much.

I have five monitors (isn't technology just crazy these days? :p) but since Mercury can only run two, I want Shugo to run the other three. However since it's basically too slow to do much of anything, and I'm not big on using two machines at once, I decided instead, I should use multiple X sessions.

The idea is one session runs and displays on Mercury as normal, and the second runs on Mercury but displays on Shugo. (Then add Synergy into the mix and it's like having all five monitors on one machine. :D) The two are connected via LAN.

The problem is I don't know how to go about setting up remote X login. On Mercury I've enabled XDMCP, style set to "Same as Local", TCP allowed. There's a nice "Include Hostname Chooser" option here but on Shugo the dialog is completely different and has no such option. So I don't know how to go about actually starting the remote X session and logging in. Every guide I find has completely different steps (which often include editing a config file, but they fail to mention *what* file). So far the most reliable source said to stop gdm and run "X -broadcast", which gets me 3 blank screens.

---

