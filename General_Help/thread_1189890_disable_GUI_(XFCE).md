---
title: "disable GUI (XFCE)"
date: 2009-06-17
forum: General Help
---

### Post by cazz on 2009-06-17
Hi I have read alot of thread here and other places but I still have problem to disable the XFCE desktop.

everytime I have found something I get

```
kinit: name_to_dev_t(/dev/disk/by-uuid/4ba402b2-7102-4bfe-ab33-6f367841f758) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/4ba402b2-7102-4bfe-ab33-6f367841f758
kinit: No resume image, doing normal boot...
```
And after that nothing happend, nothing at all.


I just like to disable the XFCE so if I need to have it on I can enable but when I dont want to have it going to be disable.

---

### Post by ezramorris on 2009-06-17
> **cazz said:**
> I just like to disable the XFCE so if I need to have it on I can enable but when I dont want to have it going to be disable.

When you boot normally, does it get in to XFCE successfully?

You can disable XFCE at bootup by opening a terminal and running:
```
sudo update-rc.d -f gdm remove
```

Then when you boot it will boot into a terminal, and then you can type:
```
sudo /etc/init.d/gdm start
```
to start XFCE, and
```
sudo /etc/init.d/gdm stop
```
to stop it.

If you ever wanted to make it start at boot as before, just run:
```
sudo update-rc.d gdm defaults 30 01
```

The problem showing the messages you got is a slightly different one, but let me know whether it boots to XFCE successfully normally, or if this solution works first.

---

### Post by cazz on 2009-06-17
Hi
> When you boot normally, does it get in to XFCE successfully
Yes I get successfully in to XFCE in normally boot

> sudo update-rc.d -f gdm remove

Yes I did try that but then I get same problem as before.

But I have no found the problem.

I have add a address to a script that I like to autorun when the computer start (I have the address in rc.local)
When I remove it, it work

The funny is that work great in recovery mode :)


So I have to now move the address to my script from rc.local to somewhere else that can run in sudo mode and right after the computer have start.

---

### Post by ezramorris on 2009-06-17
What exactly did you add to rc.local?

It may be the script itself which is causing the problem.

---

### Post by cazz on 2009-06-17
> **ezramorris said:**
> What exactly did you add to rc.local?

It may be the script itself which is causing the problem.

I just add

```
/home/clone/backup.sh
```

and inside that I have a string to partimage


it is nothing wrong with the file, if I run it manuall it work as I want it to.

---

### Post by ukee1593 on 2009-10-02
hey folks, I am having the exact same issue with the xubuntu machine I attempted to disable the GUI on.  I didn't change any files but I just typed 
```
sudo update-rc.d -f gdm remove 			 		
```
and I did also install mingetty to auto login still!
heck I might just install ubuntu server edition fresh!

---

### Post by nirf on 2009-12-22
any luck, anyone?

---

### Post by nirf on 2009-12-27
should we use the upstart mechanism instead of the older mechanisms?

---

### Post by nirf on 2009-12-27
Found a way here:

[http://ubuntuforums.org/showthread.php?t=1351501]("http://ubuntuforums.org/showthread.php?t=1351501")

in short, this is the trick:

sudo mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec

---

### Post by nirf on 2010-01-01
ok, this is (i hope) my final post for this topic.

here is a discussion:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1305659](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1305659)


so edit the file /etc/init/gdm.conf, and use [post #8]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8196273&postcount=8") recommendation

---

