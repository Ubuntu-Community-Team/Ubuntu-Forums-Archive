---
title: "Firefox crashes on random sites"
date: 2006-04-25
forum: Desktop Environments
---

### Post by foureight84 on 2006-04-25
I have tried going to sites such as [www.woot.com](www.woot.com) and [www.myspace.com](www.myspace.com) and everytime, firefox would crash and close. THis is the error message given in the terminal:

```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I am currently running dapper 6.06 with aiglx and compiz installed. My firefox version is 1.5.0.1 (default installed).

Any one have any ideas as to what is causing this and how to fix it?

---

### Post by mips on 2006-04-25
I have also experienced crashes with FF1.5.0.1

---

### Post by aggiechemist on 2006-05-31
I had the same error, but I only got it after installing compiz.

I was able to fix it by taking compiz off the system (I disabled thefuture in the session startup and killed the /etc/gdm/gdm.conf-custom).

I don't  know what caused it, but it made me annoyed. For some reason, I never got the same error working with Mozilla, even though it is also a Gecko browser. Wierd.

Oh yes, and I also messed with my theme. I have seen some wierd Firefox crashes before, and changing my theme helped then so I did it this time as well.

---

### Post by rcarring on 2006-05-31
I am beginning to wonder about FF. So far:

FF has crashed a few times, but not often.
SeaMonkey crashed once
Mozilla has never crashed.

Maybe I am just lucky.

---

### Post by aurelieng on 2006-05-31
Could it be this one  [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942) ?

---

### Post by mips on 2006-05-31
You might find Swiftfox a refreshing alternative to Firefox.

---

### Post by nickle on 2006-05-31
I have been having random system freezes with FF. I need to resort to the reset button... I don't know whats causing it...

---

### Post by kufford on 2006-05-31
compiz package has an bug with the flash plugin for FF. I had the same troubles... As I use DD for my daily desktop, I'll wait for XGL/compiz until it's a bit more stable.

---

