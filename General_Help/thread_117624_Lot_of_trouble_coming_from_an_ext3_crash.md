---
title: "Lot of trouble coming from an ext3 crash"
date: 2006-01-15
forum: General Help
---

### Post by geearf on 2006-01-15
Hello,

I've had one system crash, and since then I cannot start ubuntu again.
At first I went to a live cd to restore some libs (I had a lot of lib XX bad elf header, so I copy them hand by hand....).
Then next boot same problem with other libs so same way out till I could boot under the rescue kernel.

Now this works and with dpkg and my other comp I've been able to get back apt-get, libc and stuff like that.

But still when I'm trying to boot, I cannot even log in the console, I just type my login, and it waits a little and then again ask for my login, not even my password (same if I try 'root' instead of my login).

I don't know what to do anymore,
I'm right now in the safe mode trying to reinstall some basic apps like ubuntu-minimal, coreutils, and such..

I don't have any more error messages, so I don't know what's up ...

Also if you knew anyway that my ext3 doest not screw itself again next time my comp freeze I'll be happy :)

Thanks,

edit : Most of this is okay now, I just still cannot log from the terminal, but it works from ssh or gnome.

---

### Post by southernman on 2006-01-15
I assume you've ran fsck. Other than that command (running in safe mode - and read only), not sure what else to try.

Good luck

---

### Post by geearf on 2006-01-15
Hello,

yes fsck did not help, it said the file system was good.

I am now reinstalling stuff little by little, but it would be cool to have something like apt-get install --reinstall XXX --reinstalldeps

cause I have to reinstall all dependencies by hand till everything works back :(

It may have something to do with prelinking so I disabled it now.

---

### Post by geearf on 2006-01-15
Oh by the way, I can log into the troubling comp by ssh, or by gnome, but not by the terminal, that is very strange ;(

---

### Post by geearf on 2006-01-18
This is very troublesome, if someone has an idea on this please :)

---

