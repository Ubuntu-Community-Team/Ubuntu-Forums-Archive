---
title: "downgrade gcc"
date: 2005-12-21
forum: General Help
---

### Post by one_ro on 2005-12-21
Hello all,

I have a problem installing vmware workstation 5.0 under Breezy; it complains with:
> Your kernel was built with "gcc" version "3.4.5", while you are trying to use "/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware Workstation cannot work in such configuration. Please either recompile your kernel with "/usr/bin/gcc" version "4.0.2", or restart usr/bin/vmware-config.pl with CC environment variable pointing to the "gcc" version "3.4.5".
I found a thread concerning this issue here:
[http://www.vmware.com/community/thread.jspa?threadID=26692&tstart=30](http://www.vmware.com/community/thread.jspa?threadID=26692&tstart=30)
where they advise downgrading gcc.
I can not consider:
- compiling the current kernel with gcc 4.0.2 (too cumbersome for me)
- using export CC=usr/bin/gcc-3.4 (already tried that once, didn't work...)

Could you please advise on how to downgrade gcc, please?
Thank you in advance.

---

### Post by 23meg on 2005-12-21
Do you have gcc 3.4 installed? You don't have to uninstall 4.0; install 3.4, and try again.

---

### Post by one_ro on 2005-12-21
Yeap, I do have gcc 3.4 installed... :(
This is what puzzles me: with the same gcc installation, I had absolutely no problems under Kubuntu 5.04 Hoary

---

### Post by MartinG on 2005-12-21
If you have gcc-3.4 installed it should work (as you already know:-) ). What message do you get when you run:```
export CC=gcc-3.4
sudo vmware-config.pl
```
If this is still saying it can't find gcc-3.4 then there's something funny about the gcc setup.

---

### Post by rattking on 2005-12-21
I have had some problems with this as well
what I did was
sudo -s
export CC=gcc-3.4
vmware-config.pl

and that worked fine for me..

---

### Post by one_ro on 2005-12-21
[QUOTE=rattking]I have had some problems with this as well
what I did was
sudo -s
export CC=gcc-3.4
vmware-config.pl

and that worked fine for me..[/QUOTE]
I did _exactly_ the same steps (Nth time)... everything runs ok, I even get a very encouraging:
> The configuration of VMware Workstation 5.0.0 build-13124 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

BUT, when I run it..., I get...
> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

snif-snif
](*,) 	:shock:

What can I do?

---

### Post by one_ro on 2005-12-21
Oh... even more, I just hit:
sudo /usr/bin/vmware-config.pl

and it does... nothing... absolutely nothing, it just freezes. It wouldn't accept anything until restart. 
Good thing I made a backup of my system before trying to install vmware...

---

### Post by tseliot on 2005-12-21
If you install the latest version of vmware (5.5.0) you won't need to export CC. Older versions might not work fine in Ubuntu (I had your problem)

---

### Post by MartinG on 2005-12-22
[QUOTE=one_ro]Oh... even more, I just hit:
sudo /usr/bin/vmware-config.pl

and it does... nothing... absolutely nothing, it just freezes. It wouldn't accept anything until restart. 
Good thing I made a backup of my system before trying to install vmware...[/QUOTE]If you don't want to update to 5.5 (and why not -- it's a free upgrade!) you probably need to use the vmware-any-any-update patch. The following while not *directly* relevant explains the process, written by the patch author.
[http://www.vmware.com/community/thread.jspa?messageID=76957&#76957](http://www.vmware.com/community/thread.jspa?messageID=76957&#76957)

---

### Post by one_ro on 2005-12-22
[QUOTE=MartinG]If you don't want to update to 5.5 (and why not -- it's a free upgrade!) you probably need to use the vmware-any-any-update patch. The following while not *directly* relevant explains the process, written by the patch author.
[http://www.vmware.com/community/thread.jspa?messageID=76957&#76957](http://www.vmware.com/community/thread.jspa?messageID=76957&#76957)[/QUOTE]
Thsnks Tseliot, thanks MartinG.
I would very much like to upgrade, but I _cannot_ download this version from the VMware website (don't know why, it just doesn't work). In order to just upgrade, I'd need to first install the 5.0 version and here I am stucked.
Is there another place where I could download the 5.5 version?
In the mean time, I will follow the above link and see what I can do.
Thanks again!

---

