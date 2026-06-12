---
title: "many sites crashing firefox"
date: 2005-02-23
forum: Desktop Environments
---

### Post by machiner on 2005-02-23
I'm running Hoary - array-4 updated.  Since I have changed from Warty to Hoary  many sites are c rashing Firefox.

Anyone else noticing this...Deviant Art just crashed Firefox, it was the last one prior to posting this thread. To recreate - just click a link ( but I doubt we're running the same config).

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=machiner]I'm running Hoary - array-4 updated.  Since I have changed from Warty to Hoary  many sites are c rashing Firefox.

Anyone else noticing this...Deviant Art just crashed Firefox, it was the last one prior to posting this thread. To recreate - just click a link ( but I doubt we're running the same config).[/QUOTE]

Yep, I have noticed that Firefox has been crashing more as well........

Thank Gnod for the "force quit" applet.

---

### Post by machiner on 2005-02-23
yeah -- and I just wrote a thread in the Hoary forum bragging about how stable it was....sheesh.

I need a toothpick for the feathers!

---

### Post by machiner on 2005-03-01
*** loading the extensions datasource
NP_Initialize
New
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 31 error_code 172 request_code 149 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


****************

I tried the noapic noacpi on the kernel string, no dice, so I just uninstalled the flash plugins.

Whoopie -- I can do with out them until Hoary is ready-for-prime-time.

---

### Post by Jet2k5 on 2005-03-02
I don't know if I'm using hoary, but I have the default installation and pretty new to Ubuntu, so I'm guessing I'm using warty.  I too notice that firefox crashes and is very slow when loading up websites.  My website loads very slowly, and sometimes the default webpage never comes up, might be a bug.  I thought that warty downgraded firefox because the said that 1.0 was very buggy?  If so what happened?  Anyone noticing these problems in warty too?

---

### Post by buldir on 2005-03-02
Does "generic" Mozilla have these same problems?  Just curious.

---

### Post by Grey on 2005-04-16
I've been having this same problem... but I think I can pretty much put all the blame on the flash plugin.  I have no idea why it's happening, but it stops when I uninstall flash.

---

### Post by Jin on 2005-04-29
Yepp, tried galeon, epiphany, mozilla, mozilla-firefox.. All have the same problem because they all use Gecko which is :codename for Mozilla.org's highly standards-compliant, groundbreaking, layout/rendering engine. 

The problem is Gecko, some kind of bug in it. I'll post again if I find anything.

---

