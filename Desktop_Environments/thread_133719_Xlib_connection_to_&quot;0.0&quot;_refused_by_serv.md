---
title: "Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2006-02-20
forum: Desktop Environments
---

### Post by turtletime on 2006-02-20
How can I fix this error?  If I run my desktop continuously for a couple of days and then try to start any program it just won't load.  If I manage to get the console window to load and try and execute a program manually I get :

```

Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
: cannot connect to X server :0.0

```

The only way I can get rid of it is to reload the Xwindows.  

Anybody know what is going on?

Thanks :)

---

### Post by turtletime on 2006-02-20
I think this may have something to do with firefox.  I usually have a lot of browser windows open(yah yah tabs).  But, even if I close them the problem still persits until I restart X.

C'mon anyone?

---

### Post by turtletime on 2006-02-20
This is my last try.  I can't believe nobody has an answer for this.  I have a fairly decent system.  1 gig of RAM, AMD 2600, ATI 9800 Pro etc.

I can't figure this out.

Anyone..Please?

---

### Post by wezzul on 2006-11-02
Same issue here, when I find the fix, I'll post back.

WEZ

---

### Post by wezzul on 2006-11-02
Try the following commands to see how many x clients and x windows are in use:

> xlsclients | wc -l

xwininfo -root -children | wc -l


For xlsclients, I had a totally manageable number, like 24 or something (max is 128 from what I know).

For xwininfo, however, I had like 340+.  I killed firefox, it dropped it by about 30.  Nothing else dropped it nearly that much.  After that, I was able to open stuff again.  Will continue to research this in hopes of finding something definitive out...

WEZ

---

### Post by EDevil on 2006-11-08
I also have this problem. It's the first time I've seen it and it never happened with Dapper or Breezy.

---

### Post by EDevil on 2006-11-08
I also think the problem lies in firefox. I closed it and xwininfo reported a 250 drop. I then opened it, it loaded the previous tabs and that number only increased 20...

---

### Post by izm81 on 2006-11-20
```

$ totem
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached

(gnome_segv2:18793): Gtk-WARNING **: cannot open display:

$ xlsclients | wc -l
32

$ xwininfo -root -children | wc -l
1205

$ uname -a
Linux semper 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux


```

(I'm using Dapper)

Significant programs running: Eclipse, Firefox (2 tabs), Thunderbird, a few gnome-terminals, gnome-text-editor w/5 tabs, a couple nautilus (file browser) widnows, and a japanese dictionary program.

---

### Post by giruzz on 2006-11-21
Same problem here.

laptop:~$ xlsclients | wc -l
4
laptop:~$ xwininfo -root -children | wc -l
283


let's see if is still happening without firefox

g.

---

### Post by giruzz on 2006-11-21
Oh yes. It is firefox!

Without firefox I didn't get the error...

laptop:~$ xwininfo -root -children | wc -l
214
laptop:~$ xlsclients | wc -l
3

---

### Post by Xhosa on 2006-11-21
Just to add that I've also seen this issue - killing firefox resolved it.  Am now waiting to see if it reappears once firefox has been running again for a while...

---

### Post by arun_maurya on 2006-11-21
Run this command before running your programs
#/usr/libexec/at-spi-registryd &
I think this is a bug.

---

### Post by qhuys on 2006-11-25
Hey guys

Yes, same issue here. Happens again and again after my system's been up and running for a while. Killing firefox doesn't help -- only thing I've found to help is to start a new gdm session. 

arun_maurya: Thanks for the thip, but I can't find the at-spy-registry command -- are you sure it's in /usr/libexec ?  

I'm running dapper, which otherwise runs super-smoothly, and didn't have this issue on Breezy.... Good luck.

---

### Post by lnostdal on 2006-11-29
same thing here .. 
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/70872](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/70872)

---

### Post by kristerfl on 2007-11-22
Are any of you by any chance running amd64 and 64 bit installation? Or anything related to 64 bit?

---

### Post by Douglas Royds on 2008-02-20
> **turtletime said:**
> How can I fix this error?  If I run my desktop continuously for a couple of days and then try to start any program it just won't load.  If I manage to get the console window to load and try and execute a program manually I get :

```

Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
: cannot connect to X server :0.0

```

The only way I can get rid of it is to reload the Xwindows.  

Anybody know what is going on?

Thanks :)
This is also symptomatic of a deleted ~/.Xauthority file

---

### Post by kristerfl on 2008-02-21
its because one or more processes are eating up the connections to the server (as indicated in the error message)
i know there are two shell commands to list information about those connections, but any utility that you use to investigate will do.

---

