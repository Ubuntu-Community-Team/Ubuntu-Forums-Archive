---
title: "out of space - can't boot"
date: 2009-01-17
forum: Desktop Environments
---

### Post by bonfire89 on 2009-01-17
I ran out of disk space and now can no longer boot into gnome. After typing in my password I get a bunch of error messages a lot about have not being able to save settings, one about the power manger etc.... None of the panels load up, not wallpaper, no ability to right click the desktop and interestingly, a bit of my awn dock loads up, no icons, just some background.


so. via the terminal I removed about 2 gigs worth of data.

I ran the utilities in the recovery mode.

but I am still getting the same error messages after logging into gnome.

If I could get some help on fixing gnome that would help a lot. 

I'm not completely opposed to re installing gnome if need be, but, I would need some help on that.

---

### Post by adamlau on 2009-01-17
What do the error messages say and what utilities did you use in recovery mode? To be safe, I would run e2fsck (depends on your filesystem) from live media against your partitions.

---

### Post by RJARRRPCGP on 2009-01-17
This problem may be caused by being unable to access the swap.

---

### Post by taurus on 2009-01-17
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by bonfire89 on 2009-01-17
"An error occured while loading or saving configuration information for 
update-notifier. Some of your configuration settings may not work 
properly"

Details: "failed to contact configuration server; some possible causes 
is that you need to enable TCP/IP for ORBIT or you have stale NFS locks 
due to system crash. See [http://www.gnome.org/projects/gconf](http://www.gnome.org/projects/gconf) for 
information. (Details - 1: could not send message to gconf daemon: 
message did not recieve reply (timeout by message bus))"  and this 
repeats a couple times.

"An error occured while loading or saving configuration information for 
evolution-alarm-notify. Some of your configuration settings may not work 
properly"

Details: same as above


I had not read that as thourough as I should have in the first place. 
I'm going to look up some stuff on NFS locks, but still going to post 
this because I don't want to lose what I have typed. That took a bit of 
time switching between the screens.

There is a third message about the power manager that disapears pretty 
quickly. I'll figure out getting that if this can't be resolved.



Part of the tools that I ran from the recovery mode was one that checked 
the disk. Another was to clean and another to fix broken packages. I 
believe those were all three.

The fact that the swap was mentioned is interesting. Because, as result 
of this I also found out that my vista install in busted (next on the 
agenda)

My harddrive partions go like this (sizes not completely to scale)

|---vista---|-swap-|------------ubuntu-------------|

but who knows when the vista died. I haven't gone into that for some 
time.

---

### Post by bonfire89 on 2009-01-17
I found a tip that says

in .profile instert line

export GCONF_LOCAL_LOCKS=1


but warns not to be in gnome while doing that. I shall give that a shot 
if I can find .profile

---

### Post by bonfire89 on 2009-01-17
unfortunately the tip that I came accross did not work.


But, I got the 3rd error message

"The configuration defaults for GNOME Power Manager have not been 
installed correctly. Please contact your comptuer administrator"

---

### Post by bonfire89 on 2009-01-18
I believe I cam accross something that sugested renaming the home folder 
then copying it back. Since I don't have enough space on my hard disk 
I'm copying it to another drive then back. It's going to take quite some 
time. Though, while copying back I'm going to leave off the videos for 
the time being to save some time as they account for 30 gigs or so.


If that doesn't work. It seems like it is just my user profile that is 
currupt. I will just delete it and make it again.

---

### Post by bonfire89 on 2009-01-18
that didn't work.

I deleted my account and made a new one.

so essentially


after booting into recovery mode from the grub menu then dropping into the root shell


```

mv /home/userName /home/userName.bck
userdel userName
useradd -d /home/userName -m userName
passwd userName

```


just incase someone else needs to do this.

This is not idea. You will lose your configurations and such but not your data since you can recover it from the backup you made with "mv /home/userName /home/userName.bck"

Though on that note... there will be a bunch of hidden folders that are in your home directory that will have certain settings in. I'm not sure how to recover that stuff. but going to give it a look see.

Anyways. Been up all night, sun going to come up quite soon. making this thread solved... though.. it isn't really. But, any solutions wont have any worth to me.

---

