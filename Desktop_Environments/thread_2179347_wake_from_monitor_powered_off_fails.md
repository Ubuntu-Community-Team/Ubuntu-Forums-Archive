---
title: "wake from monitor powered off fails"
date: 2013-10-07
forum: Desktop Environments
---

### Post by timjunk on 2013-10-07
i'm using intel haswell chip for my gpu.  i can wake out of the  screensaver and the lock screen shows nicely.  when i wake after the  monitor has been powered off, i get either blank or garbled or offset  screen.  i'm using gnome-screensaver.  i can still type my password and  enter, and it will come back properly.  it just doesn't display the lock  screen.  sometimes when i wake it, it looks like it is usable.  the  mouse moves, but nothing responds.  i type my password and it works.  

i've  tried xscreensaver and it's worse.  i have to power down to get out of  it (there may be another way, i just don't know it).  

currently i'm trying some different settings in system->brightness and lock.  any ideas?

---

### Post by theDaveTheRave on 2013-10-08
My first thought would be for you to restard the desktop, you say you are using gnome so something along the lines of 
```

 /etc/rc.d/gdm restart

```

should do the trick.

The real question is if you can bind this to a keybinding to restart. and if you can execute this keypress when the system is in 'lock' ??

other options are...

When you boot into your system it normally defaults to tty7 (tty = teletype)

You can change teletypes using the key combo of < ctrl Alt F# > where F# is one of the function keys.

F1 will send you to ttyp1
F2 will send you to ttyp2
... etc...

[See here for info on tty]("http://ubuntuforums.org/showthread.php?t=1836985")

I guess that by quickly switching from  back and forth your screen may come back to life?

you'll have to try it out.

David

---

### Post by timjunk on 2013-10-13
thanks! switching tty's worked.  would be nice if there was a way to do this on wake or fix the issue.

---

### Post by theDaveTheRave on 2013-10-14
to be honest I'm surprised it worked ! pleased though.

I suspect that when you switch between tty's the screen if forced to do a refresh, i'm not sure.

I suspect that the problem is that the system isn't capturing the activity on the keyboard correctly, but by switching tty's you force it to 'wake up'.

So lets think about this.....

do you have a laptop or desktop ?

I know that on my dekstop / laptop if I attach a second screen it takes a few seconds for it to be recognised, and come to life.

you could try unplugging / re plugging in your screen (this is just a test, not a suggested solution). 

However if this works you know that the process of searching for newly attached devices is working, you just need to find a way to force it to happen.

I would propose that you look at the output of dmesg, and possibly the syslog, to see when (if) the screen is getting recognised. Moving between tty's should show up quite nicely.

Otherwise I thing you need to be looking at your graphics card and seeing if there are any bugs in the driver.

There is this thread [on askubuntu]("http://askubuntu.com/questions/341811/intel-haswell-strange-graphics-and-boot-issue"), which may have some bearing on resolving your issue.

David

---

