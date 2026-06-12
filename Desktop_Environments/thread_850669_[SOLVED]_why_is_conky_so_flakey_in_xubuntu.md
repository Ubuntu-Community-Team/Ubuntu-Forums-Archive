---
title: "[SOLVED] why is conky so flakey in xubuntu?"
date: 2008-07-05
forum: Desktop Environments
---

### Post by mdsmedia on 2008-07-05
I run conky in Ubuntu and have just installed (about 12 hours ago) xubuntu desktop.

I opened conky and it comes and goes from the desktop.

Is this something to do with it being a Gnome installation running in Xfce?

---

### Post by p_quarles on 2008-07-06
> **mdsmedia said:**
> I run conky in Ubuntu and have just installed (about 12 hours ago) xubuntu desktop.

I opened conky and it comes and goes from the desktop.
Post your configuration file, please. 

> Is this something to do with it being a Gnome installation running in Xfce?
No.

---

### Post by mdsmedia on 2008-07-06
I can't find my configuration file. I believe it's .conkyrc but I can't find it.

I installed conky without any configuration, so it's possible I haven't created a config file. I just installed conky and ran it from terminal.

I've looked in my /home folder including hidden files.

Thanks for your help.

---

### Post by mister_p_1998 on 2008-07-07
> **mdsmedia said:**
> I can't find my configuration file. I believe it's .conkyrc but I can't find it.

I installed conky without any configuration, so it's possible I haven't created a config file. I just installed conky and ran it from terminal.

I've looked in my /home folder including hidden files.

Thanks for your help.

yes, you need to create  a .conkyrc configuration file, to keep a permanant conky on screen, you need to enable double-buffering. Check someone elses config file, theres loads of the Ubuntu forum.
look here: [http://ubuntuforums.org/showthread.php?t=798139&highlight=conky](http://ubuntuforums.org/showthread.php?t=798139&highlight=conky)

---

### Post by mdsmedia on 2008-07-08
> **mister_p_1998 said:**
> yes, you need to create  a .conkyrc configuration file, to keep a permanant conky on screen, you need to enable double-buffering. Check someone elses config file, theres loads of the Ubuntu forum.
look here: [http://ubuntuforums.org/showthread.php?t=798139&highlight=conky](http://ubuntuforums.org/showthread.php?t=798139&highlight=conky)

I've been running conky (reasonably) successfully in Gnome for some time. It's only in Xfce that it seems "flakey" but I admit I had no .conkyrc. I had looked briefly for instructions on configuring conky but hadn't spent any time on it.

Then I tried xubuntu and it would flash on and off the desktop.

I checked this thread:

[http://ubuntuforums.org/showthread.php?t=353362&highlight=conky](http://ubuntuforums.org/showthread.php?t=353362&highlight=conky)

and used the first example .conkyrc file. Because it's based on a dual-core I tried commenting out all the references to additional CPUs. I still get an error when trying to run it.

Could someone show me where I could remove/comment out lines to let it work  on a single CPU.

I must admit that initial searches for configuring conky had brought up nothing of value, but when I simplified the search parameters it worked much better. I'll keep looking but if someone could look at that example....if not I can paste what I have, which is basically that example with some lines commented out.

---

### Post by bagy on 2009-10-06
Go to etc/conky/conky.conf and edit configuration...:)

---

### Post by FOSScula on 2012-05-31
ok really guys... no we have to keep the unititated running in circles?? when one installs conky it DOES NOT generate its own *.conky.rc* file in your home directory... with a lot of distros this is the case.. so... just copy the *conky.conf *located at /etc/conky/ and rename it to *.conky.rc* and paste in your home directory...

yes there is a "." before conkyrc, it should be a hidden file.. 

for future reference-- if you have a .conky.rc file in your home directory, conky will work from that.. if not it pulls from the /etc/conky/conky.conf file... 

You of course CAN just edit and use the /etc/conky/conky.conf file but you have to become root to make any changes EACH and EVERYTIME you want to edit it... ridiculous for day-to-day IMO..

```
cp /etc/conky/conky.conf /home/USERNAME/.conky.rc
```
above command will copy the default conky.conf and rename it properly and place in your home directory.. don't forget to change USERNAME to your own of course! :)

---

### Post by sffvba[e0rt on 2012-05-31
*Back to sleep **old** thread.*


404

---

