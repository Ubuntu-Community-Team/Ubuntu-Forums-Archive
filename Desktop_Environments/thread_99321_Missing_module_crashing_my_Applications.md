---
title: "Missing module crashing my Applications"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Havoc on 2005-12-05
Hi,

I don't know how, but somehow, I seem to have "misplaced" a module, "libatk-bridge" in paticular.Here's what I get when I run, let's say, Rhythmbox:

> havoc@Nosgoth:~$ rhythmbox
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(rhythmbox:7537): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

I'd like to note that Rhythmbox starts all right, but after a while crashes, and generally misbehaves.This problem is found on all GTK+ apps that depend on libatk, and many react differently than Rhythmbox (With problems like slow startup, etc).

I reinstalled all the "libatk*" family of libraries, and with them, all the libraries that depend on them.Still no good.I modprobed, or whatever, and nothing.

So, me being a helpless linux noob, what do you suggest? I will NOT accept suggestions with the words f**k or hell like I did last time.;) 

Thanks! :cool:

---

### Post by Havoc on 2005-12-05
Ok, I found the solution, but I don't think you give a damn, do you?

It was Assistive Technologies acting up on me.

---

### Post by Suzan on 2006-01-03
I'm interessted... the same happened to me. 

Whats your solution?

---

