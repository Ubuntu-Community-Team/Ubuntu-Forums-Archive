---
title: "Numerous Errors on Shutdown"
date: 2008-05-21
forum: Desktop Environments
---

### Post by fballem on 2008-05-21
When I choose the shutdown on my computer, I get a large number of errors displayed on the screen after the ubuntu logo. I have a feeling that it's due to the order in which the shutdown commands are executed.

For example, I get the following two errors:

CIFS VFS: Server not responding
CIFS VFS: No response for cmd 50 mid 117.

This is reasonable, I think, since the ethernet adaptors have already been closed and the devices are network devices.

Is there a way to produce a log, and if there is, who do I send it to in order to determine if there are changes that will result in a more satisfactory shutdown experience?

Many thanks,

---

### Post by exploder on 2008-05-21
Here is the bug report on what is happening.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266)

We are all thinking that GDM is the problem.

---

### Post by fballem on 2008-05-21
I've subscribed to the bug, so hopefully this will get fixed. I don't know if it helps, but I've had the problem everytime I've installed ubuntu (several times over the past couple of weeks). If there is a log generated during shutdown, then I'll be happy to contribute a copy of mine.

I will need very specific instructions on how to do this - I'm a newbie to linux, although I've used Windows for many years. I also haven't figured out how to attach a file (short of cut and paste) in Launchpad, but if it can be done, then I'll be happy to do it.

Many thanks,

---

### Post by fballem on 2008-05-27
I have been reading the messages that have been displayed during the shutdown process (since we have the bug that allows at least some of them to be displayed).

It appears that the first thing the Network Manager does on Shutdown (or restart) is to close the ethernet adapters. The instant the adapters are closed, all network attached devices (including any externally mounted devices) are no longer accessible - thus resulting in a tonne of errors when there is an attempt made to unmount them.

Just a question - is it possible to change the shutdown order so that network connected devices and mount points are unmounted before the ethernet adapters are closed?

I also get bus errors on the cd drives, although I don't see the bus shutdown command. I suspect that the bus is being shutdown before the devices are unmounted.

Don't know if this helps, but sometimes fresh eyes see things that those who have been walking in the forest do not.

Many thanks,

---

