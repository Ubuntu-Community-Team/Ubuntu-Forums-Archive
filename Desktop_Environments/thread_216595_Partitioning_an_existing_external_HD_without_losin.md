---
title: "Partitioning an existing external HD without losing data"
date: 2006-07-15
forum: Desktop Environments
---

### Post by carlos1 on 2006-07-15
I'm trying to partition an external HD (130GB) which already has about 25GB of data on it.  I want to create a separate partition on the end, of about 40GB, without losing any of the existing data.

Can anyone point me to a good app or a how-to for this? I'm trying to avoid having to transfer all the data i already have, wipe the drive and re-partition from scratch.

---

### Post by Jagot on 2006-07-15
GParted:

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by carlos1 on 2006-07-15
Thanks. 
I'm using KDE so I installed qtparted. 
I read through the MAN pages of parted, and it does give the commands, but I'm trying to ensure that when I shrink the partition I don't lose the data already on it. 
Is there possibly a howto on this?

---

### Post by carlos1 on 2006-07-16
When I try doing this with gparted, it doesn't let me re-size the partition. 
When I try it with qtparted, I get an error message:
```
An error happen during ped_file_open call
```

Can anyone tell me if there is an easier way, or does this just mean I have broken packages?

---

### Post by stanz on 2006-07-16
broken package?...hummm....gparted always worked well for me.
if your dealing with ms stuff, did ya do all the defrag stuff?
I got gparted seperate, and put it on a disk- to start it all- at boot.
with no os loaded, i think it works best ~ or has for me... and i'm no techie!
I've never lost data, or borked it up myself...so ~ I likes gparted :mrgreen:

My search ~ with "ask.com"....
> There is also a [Live CD]("http://www.answers.com/topic/live-cd"), based on [Slackware]("http://www.answers.com/topic/slackware") and built on latest 2.6 [Linux kernel]("http://www.answers.com/topic/linux-kernel"). [Live CD]("http://www.answers.com/topic/live-cd") is updated with each new GParted release. Send you error messege or search their forums @ [qtparted.sourceforge]("http://qtparted.sourceforge.net/")
I don't know the diff between the two, but using one or the other at boot, by disk, seems a way to go ~ or try. ;)

[Homepage & Download qtparted]("http://qtparted.sourceforge.net/")
[Homepage & Download qparted]("http://gparted.sourceforge.net/")

`well, I hope its a help to ya...maybe there are other partitioners to google for,,, that may help?

---

### Post by carlos1 on 2006-07-16
THanks for the advice. 

I gave up in the end with the GUI stuff and did it from the command line, just using parted, and it worked fine, so problem solved.

---

