---
title: "colorful commands"
date: 2008-12-18
forum: General Help
---

### Post by amini on 2008-12-18
Hi everybody,

As you know, many of linux commands like LS,FIND,etc generate a lot of results and usually finding the start point of the results is not easy..especially for those who have weak eyes, like me!
My question is that, how can I have different colors for the "commands (prompt)" and the "results" in command line ubuntu to recognize the results start point easier??

Thanks
Amin.

---

### Post by pastalavista on 2008-12-18
you might like this one ```
sudo apt-get install terminal.app
```. It will show up in the Applications/System Tools menu as 'Terminal'.

---

### Post by hivelocitydd on 2008-12-18
Try This Code


#!/bin/sh
#
# This script will be executed *after* all the other init scripts.
# You can put your own initialization stuff in here if you don't
# want to do the full Sys V style init stuff.

touch /var/lock/subsys/local
echo -en \\033[32m\\033[8] >/dev/console

---

### Post by Koselara on 2008-12-19
> **amini said:**
> how can I have different colors for the "commands (prompt)" and the "results" in command line ubuntu to recognize the results start point easier?

Hi Amin --

I was wondering the same thing a few months ago, and found this really useful old forum post after a lot of searching: 
[HowTo: Customizing bash prompt]("http://ubuntuforums.org/showthread.php?t=614743")

I could be wrong, but I seem to recall that going through those steps also turned on colors in response to my commands, like in that person's screenshots. If you use GNOME Terminal, you can change the colors it uses for that as part of editing the profiles.

---

