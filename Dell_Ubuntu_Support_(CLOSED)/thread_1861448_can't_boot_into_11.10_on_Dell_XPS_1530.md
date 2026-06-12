---
title: "can't boot into 11.10 on Dell XPS 1530"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Richard85 on 2011-10-15
The installation completed without any errors and I went to reboot and nothing.

Last three messages

Starting Userspace bootsplash [ok]
Stopping anac(h)ronistic cron [ok]
Stopping Userspace bootsplash [ok]

Any ideas? I believe the same thing happened when I installed 11.04 with marginal success i.e installation completed but couldn't boot in.

---

### Post by Richard85 on 2011-10-15
Went into grub and deleted the line 'quiet splash vt.handoff=7'
Now it just boots me right into a command prompt with

Foundation login:_

I logged in, updated, upgraded, then typed the command 'unity' and got the following:

WARNING: no DISPLAY variable set, setting to to :0
unity-panel-service: no process found
compiz (core) -Fatal: Couldn't open display :0

---

### Post by Richard85 on 2011-10-16
I'm sure there are plenty of other posts similar to this one. This one is marked solved bc I solved the problem by installing linux mint 11.
I'll wait til the next Ubuntu LTS comes around when I'll have a new computer.

---

### Post by primalinea on 2011-10-17
> **Richard85 said:**
> The installation completed without any errors and I went to reboot and nothing.

Last three messages

Starting Userspace bootsplash [ok]
Stopping anac(h)ronistic cron [ok]
Stopping Userspace bootsplash [ok]

Any ideas? I believe the same thing happened when I installed 11.04 with marginal success i.e installation completed but couldn't boot in.

I've the same problem: the XPS 1530 hangs at boot-time.

---

### Post by kriegoamigo on 2011-10-18
Hi friends...
Even my friend had the same problem on his XPS laptop. Later I tried installing from Wubi. And guess what...It worked....

I don't know exactly how it worked and why booting directly was a mess but still this is a very unusual solution to your problem....

Try it...
I hope this works :)

---

### Post by Richard85 on 2011-10-18
I'm not running windows so I don't understand how wubi will help me...Thanks for the suggestion though. Hopefully it will help another user!

---

