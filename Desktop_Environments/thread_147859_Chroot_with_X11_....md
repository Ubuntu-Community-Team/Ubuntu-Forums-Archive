---
title: "Chroot with X11 ..."
date: 2006-03-21
forum: Desktop Environments
---

### Post by dbee on 2006-03-21
So I'm doing a chroot so that I can get a 32bit environment working on my 64bit system.

How do you get X to work on a chrooted system ...?

I keep getting this error ...
> 
_X11TransSocketINETConnect() can't get address for localhost:6000: Name or service not known


I think it's an X problem from what I've googled ... 

thanks

---

### Post by amadeujr on 2007-11-25
Hi, I think that your problem is the missing of /proc and /dev reflect the host ones. So try:

   1. Insert on the /etc/fstab:
# chroot
/dev            YOUR_CHROOT_DIR/dev     none    bind 0 0
/proc           YOUR_CHROOT_DIR/proc    none    bind 0 0
/tmp            YOUR_CHROOT_DIR/tmp     none    bind 0 0

   2. Execute as root:
mount -a
   
   3. Try again your program on jail. Tip: I suggest you to use the schroot program to more fine grain configuration, like common users permissions to use some programs. See an example for schroot environment setup: [http://base.thinkevolving.org/sci:cs:linux:etchinstall](http://base.thinkevolving.org/sci:cs:linux:etchinstall)

Another important thing: Make sure that you have execute "xhost +"  before. This it makes your X session acessible by others programs (like these in the chroot).

Good luck!
Amadeu - powered by Debian !!! :guitar:

---

