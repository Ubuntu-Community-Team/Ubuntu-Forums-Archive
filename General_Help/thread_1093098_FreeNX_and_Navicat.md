---
title: "FreeNX and Navicat"
date: 2009-03-11
forum: General Help
---

### Post by niels_r on 2009-03-11
Hi,

I am using Ubuntu 8.10 Desktop edition on a machine that is mainly used as a file and development server. For running some Linux-only applications, I use FreeNX to connect from my Mac to the Ubuntu machine. This works fine.

Recently I have purchased Navicat Linux edition (actually the Windows version that runs through Wine...). This program runs fine when I start it directly on the Ubuntu machine. When I connect to the Ubuntu machine using FreeNX, it does start but no display output is passed through to my Mac.

In the 'start_navicat' script, I found a line that says:
export DISPLAY=":0.0"

Thus, the display output is explicitly sent to the current machine which is the Ubuntu machine. When commenting out this line, Navicat works fine when starting it locally on the Ubuntu machine and it does give some output using FreeNX, but most of its windows are black (only icons are displayed). Since I don't work directly on the Ubuntu machine (there is no display attached ;)), this is a problem for me.

Is there a way to use Navicat via FreeNX on my Mac? Any help would be appreciated!

Regards, Niels

---

