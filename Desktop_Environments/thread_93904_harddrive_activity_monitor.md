---
title: "harddrive activity monitor"
date: 2005-11-23
forum: Desktop Environments
---

### Post by art on 2005-11-23
Hi 
Anyone knows any app which shows which files are currently being accessed on HDD, and by which process, I just see some activity on harddrive (constant, periodic), can't figure out which process is using it. I am attaching a screenshot of gkrellm to show what I mean.
Thanks a lot!

---

### Post by aysiu on 2005-11-23
I don't know if this really answers your question, but I believe there are a lot of gdesklets that do that.

You can also open up a terminal and type ```
top
``` in.

---

### Post by megamania on 2005-11-23
[QUOTE=art]Hi 
Anyone knows any app which shows which files are currently being accessed on HDD, and by which process, I just see some activity on harddrive (constant, periodic), can't figure out which process is using it[/QUOTE]

I'm not answering your question either, but whenever I see some "unexpected" disk activity on my computer it is caused by the slocate cronjob.

You probably know that already, but trying "top" from the terminal can be a good place to start.

---

### Post by art on 2005-11-23
Maybe my picture was not good, so I am attaching another one. As you can see, the HDD activity is really periodic, so I thought mayvbe it's beagle, so I uninstalled beagle, but it's still there... The thing is in **top** I don't see, or at least I don't know how to see which process is accessing hdd, I can see CPU etc. As for gdesklets, I'll start searching for one.

---

### Post by aanderson on 2005-12-13
I have noticed the same thing, namely a small bit of disk activity every second or so. It is hard to nail down which process is causing it, but I am working on it.

The activity persists even if gdm is stopped, so I think it is unrelated to the desktop.

One shouldn't expect top to show what this is since it probably uses very little resources. I have been sampling /proc fd files looking for clues, but I'm not sure how to catch such transient behaviour... but I'll keep trying.

I assume it's one of the many daemons ubuntu sprouts, but so far I'm not sure which.

---

### Post by art on 2005-12-13
It'd be great to know what it is. My work computer is RedHat EL(Gnome), and I see the same behaviour, so I think it's not "Ubuntu" specific...

---

### Post by SweVoyager on 2006-01-03
Hello,

First of all, I'm a real Linux newbie so please use this advice with care. :)

If I'm not mistaken you can log your hd activity by doing this:

sudo bash
echo 1 > /proc/sys/vm/block_dump

And you'll also want to stop the log after a while with:

echo 0 > /proc/sys/vm/block_dump

in the same root bash.

It would probably be a good idea to stop syslogd beforehand.

I had the same problem you have, and did this. It seemed to be kjournald which was the offending service, since it kept accessing the hd every 5 seconds (or so). I guess, by reading som other stuff regarding kjournald, that it's working as intended. :( It keeps irritating me, and if anyone has any ideas how to get rid of this I would be most pleased.

---

### Post by pelle.k on 2006-01-15
[http://www.ubuntuforums.org/showthread.php?p=660011](http://www.ubuntuforums.org/showthread.php?p=660011)

:)

---

