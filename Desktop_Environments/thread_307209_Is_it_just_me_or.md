---
title: "Is it just me or?"
date: 2006-11-26
forum: Desktop Environments
---

### Post by Foxen on 2006-11-26
...Does KDM seem to crash way more often in Edgy than in Dapper? I've just reinstalled Edgy on my laptop and thought that it would fix a bunch of small problems I had, one of them being that when using KDM as the display manager for KDE it would always hang when I chose "log out", and sometimes when I picked "reboot" or "shutdown", with GDM that never happens... So, is the newest version in the repos of KDM f***ed up or am I stupid or something?

Besides all this I would really like to have Beryl running in the native X server(not XGL on top), since I have an ATI X1600 Mobility I am stuck with "composite" "disable" and thus has to run XGL, but I found some kind of guide that showed how to use the XGL server as the native one, this guide was for KDM, but KDM obviously doesn't like me or my computer, so, any other options except ditching this laptop and getting one with a nVidia chipset and GFX instead?

---

### Post by Lord Illidan on 2006-11-26
Use gdm instead.

---

### Post by wieman01 on 2006-11-26
KDM has never crashed in my case... But I am using Dapper which is stable as a rock.
[U][B]
EDIT:[/B][/U]
What guide have you been using?

---

### Post by Foxen on 2006-11-26
I can't remember which specific guide netted which result, the only one who've worked is one that specifically told you to make a separate XGL login session but even that one borks up after a few hours and then KDE complains when you log out and crashes ;)

I've already installed the package Ubuntu-desktop onto my Kubuntu installation and specified that gdm should be used, but if I choose to log into gnome nothing really happens, after a while a part of the red-brown background switches to a white rectangle in the upper left corner and then nothing happens at all, to get out of it I did ctrl-alt-backspace to kill the xserver and re-login to KDE...

---

