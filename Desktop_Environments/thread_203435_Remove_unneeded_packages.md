---
title: "Remove unneeded packages?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by shawnrgr on 2006-06-25
I've noticed that when I install a package, for instance, i just installed the epiphany web browser extensions, it installed 2 more packages that were dependencies. But then I decided that I didn't want to use epiphany so I selected complete removal. However the 2 packages that i was forced to install as dependencies were not removed. Over time this can really build up. loosing space and slowing me down. Is there a way to remove unneeded packages that were installed as dependencies for programs that are no longer on the system?

----

Anyone?

---

### Post by shawnrgr on 2006-06-25
Someone must be able to help me out... anyone?

---

### Post by psylence on 2006-06-25
Install deborphan, it's in the repository.  It will show you (with reasonable accuracy) what's no longer needed.

---

### Post by lamego on 2006-06-25
Install the deborphan program.
Run it on a terminal, it will list the packages which can be safely removed (nothing dependes on them).

---

### Post by shawnrgr on 2006-06-25
thanks alot guys! that worked like a charm. cleared almost 100 megs! I feel lighter already ;)

one more question... What about when I boot up, I have like 4 different kernals avail. is it safe to remove some of the older kernals? and if so, how would I go about doing that?

---

### Post by kpkeerthi on 2006-06-25
Search for linux-image in synaptic and mark for complete removal if you want to get rid of them from you disk. If you prefer to keep them but do not want them listed in grub, edit your menu.lst and comment out the relevant lines.

---

### Post by dicecca112 on 2006-06-25
follow this.  has deborphan way and others [[howto] General 5.10 - HOWTO: Cleaning up all those unnecessary junk files... - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan")

---

### Post by aysiu on 2006-06-25
*deborphan* now has a graphical frontend called *gtkorphan*.

In the future, install with *aptitude* instead of *apt-get* or Synaptic, and you'll take the dependencies with you when you uninstall.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by amunimanghi on 2006-06-27
In gtkorphan, do you remove the "orphaned packages" or the "non-orphaned packages"?

---

### Post by aysiu on 2006-06-27
Orphaned.

---

### Post by shawnrgr on 2006-07-10
ok now i have a question, all that worked well for me however deborphan is telling me i can delete like all my gstreamer packages. What gives? i thought i needed them to play mp3's and such?

---

### Post by aysiu on 2006-07-10
> **shawnrgr said:**
> ok now i have a question, all that worked well for me however deborphan is telling me i can delete like all my gstreamer packages. What gives? i thought i needed them to play mp3's and such?
*You* as a person may need them.

But they're "orphaned" because no other packages **depend** on them.

For example, if you use Rhythmbox, you may say, "I **need** MP3 codecs to play my music," but the Rhythmbox package itself does not **depend** on those codecs. Rhythmbox can be installed without those codecs.

---

