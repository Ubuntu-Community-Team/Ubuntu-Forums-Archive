---
title: "Nautilus is slow"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Abild on 2005-04-23
Hi guys

I've been using Ubuntu for the last 4 months now and so far i've been happy with it. 

However, for about a week ago i started expiriencing wierd problems with Nautilus. It suddenly became extremely slow. Opening my Home folder now takes 1 minute! Opening a smaller folders with fewer files takes about 30 sec.

Is there anyone who got an idea of what the problem could be?
Any help would be highly apriciated  :)

---

### Post by nad on 2005-04-23
Please open a terminal window and run the top application ' top '. This is a display of all the current processes showing some of their resources updated every three seconds by default.

Is there an application at or near the top of the list that stays there and is consuming considerable (>~15% and possibly >90%) cpu time?

Dan M

---

### Post by Abild on 2005-04-23
The 3 most resource consuming applications right now:
XFree86 using 3-8% of my cpu,
Firefox using 3-6% of my cpu and
gnome-system-mo using 1-4% of my cpu.

So there dont seem to be any problems there.

---

### Post by nad on 2005-04-23
Hmmmm....Is the problem intermittent or ongoing?

I have seen nautilus hang and sometimes time out when opening folders. I hate to continue to blame things on hald (the hardware abstraction layer daemon) but this system and its' subsystems; pmount, lvm and hotplug and the udev filesystem are still a little buggy. Probably a powered down issue with your hard drive and having to spin it up to access it. The processes, mentioned above, that handle this are not quite tuned. To be fair, I've seen the same problems with that other operating system and their $50B in resources.

Dan M

---

### Post by Abild on 2005-04-23
The problem is ongoing.

I doubt its an issue with my hd since i have no problems browsing folders with other programs than nautilus.

What is $50B?

---

### Post by nad on 2005-04-23
Nautilus is tightly integrated with the gnome desktop environment which in turn uses these subsystems to perform actions transparently, such as automatically mounting devices, controlling power management, etc. This is one thought. I use filerunner myself and have seen it occassionally hang. But an ongoing problem sounds like something else is wrong. Out of curiosity, how much free space do you have on your hard drive?

The $50B remark was a slight of Microsoft Corp and the enormous resources at their disposal yet the poor quality of their operating systems.

Dan M

---

### Post by Abild on 2005-04-24
I've got 74gb free space...

I think i'm going to reinstall my system with hoary later today.
But thanks for your help anyway!

---

### Post by Karlos on 2005-04-24
try apt-getting rox-filer

i like it

it's very fast...supersonic in fact\\:D/

---

### Post by jazzer on 2005-04-24
Abild, you haven't disabled any system services during this time have you or changed anything you can think of?  One thing I would check is in your /etc/hosts file to see if you have an entry looking like this:

127.0.0.1  localhost.localdomain  localhost  hostname

replace hostname with whatever you entered during installation.  Is this effecting any other apps?  You can at least try this, though personally, I don't expect this is the problem if it's only affecting 'nautilus' - but it's worth a shot I had a similar problem when I was in Fedora.

---

### Post by Abild on 2005-04-24
I think i've solved the problem now :):)

I tried running nautilus from a console window and i saw that nautlius was printing the following text over and over again to the console windows while it tried to open a folder:

```
failed to find gam_server
failed to exec (null)
Failed to connect to socket /tmp/fam-root-
```

I searced for gam_server on this forum and i found out that it was installed by a package called gamin. So i searched for gamin in Synaptic and installed the package. 
And then, the problem was solved and nautilus is running fast again.

I have no idea of how gamin was uninstalled though  :-? 

Thanks for the help everyone :)

---

