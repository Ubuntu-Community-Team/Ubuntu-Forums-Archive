---
title: "Running seti@home or kboincspy with graphics"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Psimon on 2005-11-05
Has anyone managed to get the graphics working in  the boinc manager GUI? I've read some old posts on various forums that say there's no graphics support for the Linux Boinc client, but I wonder if there's anyway of getting it working.

I've seen some screenshots of the Windows version and a little more eyecandy like that would be nice.

There's some graphics options in the dropdown menus of Kboincspy, but they're all disabled, as are other entries to control the client. Has anyone managed to make these options available?

And then there's Ksetisaver which I can't get running.

Any advice would be much appreciated.

---

### Post by mac.ryan on 2008-02-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/72192](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/72192) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Ok, this is a rather old post, but given that the graphics still do not worked "out of the box" as of today (Gutsy Gibbon) I thought to write down how I managed to get the graphics anyhow here, for other users.

Basically the problem is with the permission set for *xhost*. Issuing the command:

```
sudo xhost +si:localuser:boinc
```

solved the problem for me. I added the matching bug report (from which I got the solution) to this thread.

---

### Post by charonn0 on 2008-04-22
Thanks, that worked for me as well!

---

