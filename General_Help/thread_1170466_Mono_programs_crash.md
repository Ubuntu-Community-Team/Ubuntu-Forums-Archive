---
title: "Mono programs crash"
date: 2009-05-26
forum: General Help
---

### Post by lfaraone on 2009-05-26
Hi,

I'm currently not able to run the two mono programs I have installed on my Ubuntu desktop: tomboy and gnome-do.

Both crash when started with a shell session something like this:
```
lfaraone@stone:~$ gnome-do

** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault
lfaraone@stone:~$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault

```

---

### Post by directhex on 2009-05-26
> **lfaraone said:**
> Hi,

I'm currently not able to run the two mono programs I have installed on my Ubuntu desktop: tomboy and gnome-do.

Both crash when started with a shell session something like this:
```
lfaraone@stone:~$ gnome-do

** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/gnome-do/Do.exe:27141): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault
lfaraone@stone:~$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/tomboy/Tomboy.exe:27152): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault

```

This is using a standard Jaunty Mono install? No funny PPAs?

---

### Post by lfaraone on 2009-05-26
Correct.

---

### Post by directhex on 2009-05-26
Odd. Does adding --debug to the command names change the output?

---

### Post by lfaraone on 2009-05-26
No. last-exit also crashes in the same fasion.

---

### Post by directhex on 2009-05-26
> **lfaraone said:**
> No. last-exit also crashes in the same fasion.

What does "mono --debug /usr/lib/mono/2.0/gacutil.exe" say?

---

### Post by lfaraone on 2009-05-26
> **directhex said:**
> What does "mono --debug /usr/lib/mono/2.0/gacutil.exe" say?
```
lfaraone@stone:~$ mono --debug /usr/lib/mono/2.0/gacutil.exe

** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault

```

---

### Post by directhex on 2009-05-26
> **lfaraone said:**
> ```
lfaraone@stone:~$ mono --debug /usr/lib/mono/2.0/gacutil.exe

** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/mono/2.0/gacutil.exe:9858): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

Segmentation fault

```

I'm not sure what to suggest, I can't find any obvious references to this anyplace.

If you wait a little, I'm preparing a test PPA for 2.4 packages which may change the behaviour

---

### Post by lfaraone on 2009-05-26
Odd, it seeemed to go away after I reinstalled all the mono packages via synaptic and restarted my session.

---

