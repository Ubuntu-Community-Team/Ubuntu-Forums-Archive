---
title: "Multisync - unable to connect to Sony Ericsson phone"
date: 2007-06-05
forum: Desktop Environments
---

### Post by supernicko on 2007-06-05
Hi everyone,

I have a Sony Ericsson K610i phone which I can connect to using gammu/wammu and the usb connection. However using the same device name in multisync I get 'connection failed'.

I've searched high and low and I'm no closer to an answer. Has anyone had a similar experience and been able to overcome it? Alternatively has anyone found a different solution for syncing their Sony Ericsson phone with Evolution?

It's a shame that wammu isn't designed for that.

Thanks very much,
Nick

---

### Post by EvanStz on 2007-11-12
I also have the same problem and I'm looking for answers but haven't found one. If I get a solution I let you know.
BTW... I also have the K610.

Cheers.

---

### Post by bizna on 2007-11-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/multisync/+bug/123303](https://bugs.launchpad.net/ubuntu/+source/multisync/+bug/123303) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Nick, Evan,

There seems to be a problem with multisync on Ubuntu.

Try to run the command multisync from the command line, and look at the output. I have found the following troubling lines:
```
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/user/.multisync/1/remotesettings
[evo2-sync] WARNING: File /home/user/.multisync/1/remotesettings does not exist
[evo2-sync] DEBUG: end: sync_connect

```
I have artificially created the file, and instead of saying that it wasn't there, it said that it could not open the file.

Whether it has to do with the connection or not, this is something that still needs to be examined. But the fact that this basic file is having trouble, is troubling by itself.

I have also added this to a bug on launchpad.

Let's hope for the best.

Dotan

---

