---
title: "ld_static problem"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Sciamano on 2006-08-03
Hi everybody.
I had to reinstall Windows, and of course Grub was missing after the install.
I tried various guides to recover it, but failed, so I made a backup of my Ubuntu installation, reinstalled Ubuntu, and then overwrote the installation with my backupped files.

Now everything seem to work, except for the following error at startup:

```
ld_static: cannot open output file /lib/modules/2.6.15-26-386/volatile/xxxxxx.ko : Read-only file-system

```

where xxxxxx stands for the name of each file in the /lib/modules/2.6.15-26-386/volatile/ directory (the error shows as many times as the number of files in that dir).

I already tried to chmod +wx those files but did not work.

Any idea/solution/suggestion?
Thanks
Luca

---

### Post by Aypok on 2006-08-03
I've just run into exactly the same problem, although with a slightly different kernel (2.6.15-23-386, I think)... When I get that message, I can Ctrl+D ("exit") the CLI and let the system continue booting. I get to GDM - which lets me log in - but when Fluxbox starts to load I get an error message ("This session lasted less than ten seconds, please contact your system administrator" - or something similiar), at which point I get dumped back to GDM.

From previous experience, this error shows up when it cannot write to the root partition (more specifically, the /tmp/ dir) - either due to lack of disk space (there is 35GB free) or that the FS is read-only -  as it seems to be in this case.

I have other kernels installed (I tried 2.6.15-23-k7, or something similar) which doesn't seem to suffer from this "ld_static" problem, but it still seems to have the same outcome: the root partition is read-only and I cannot load Fluxbox/GNOME.

I've tried chmodding the drive as Sciamano has done, but, again, got the same result.

I'd really appreciate it if anyone out there has a solution to this problem. The only solution that I can currently think of is to reinstall Ubuntu - which isn't ideal. Thanks in advance.

---

### Post by Sciamano on 2006-08-03
Well I actually only receive that error message, but the PC never stops and the boot goes on. So it's a little different problem than Aypok's.
But still, I guess that if we can find a solution, it would work for both of us.

---

### Post by Sciamano on 2006-08-03
.

---

### Post by Aypok on 2006-08-04
I gave up and decided to just reinstall Ubuntu... After I had backed up the /etc/, /usr/ and /var/ directories, that is. Then, after I had reinstalled, I copied these three dirs over the new ones.

Should you plan to take this route, be sure to "chmod 4755 /usr/bin/sudo" and "chmod 0440 /etc/sudoers" after you copy across the old dirs. For some reason, my copies didn't keep their full permissions - meaning that I couldn't "sudo" on my new installation. I had to boot to a live CD again and chmod the files from there.

I'm sure there will be other binaries which need the same treatment, but you can do them from within the install once you have sudo back.

I hope that's of some use to you. If not; good luck on finding a solution.

---

### Post by Sciamano on 2006-08-05
Thanks for the hints, but since everything looks like it works fine, I'm staying as it is... If anything goes wrong in the future, I'll probably just install Ubuntu again from scratch.

---

### Post by Jebenko on 2006-10-09
I had also a few messages like this:

ld_static: cannot open output file /lib/modules/2.6.15-26-386/volatile/xxxxxx.ko : Read-only file-system
When u take a look at the /lib/modules/ into other kernels you cen see that they are empty in the subfolder volatile. So I asumed that the system creates this at boot and simly deleted all from the folder volatile  rebooted and all works fine now.

---

### Post by simpsonsfan74 on 2006-12-10
I have the same problem, but it only happens when a filesystem needs to be checked on booting (after every 20 mounts of the FS).  I tried deleting the contents of /lib/modules/2.6.15-27-386/volatile, but it didn't help any.  My problem started upon restoring a backup of my system.  I think it might have to do with the fact that my backup was created (with "dar") while Ubuntu was running.  Has anyone else had problems from creating a backup from a running system?

---

### Post by simpsonsfan74 on 2006-12-14
Hmmm... interesting.  I just deleted the /lib/modules/2.6.15-27-386/volatile directory, then re-created it, and it fixed my problem, just Jebenko said.  The only thing is I already tried this and it didn't work!  Maybe I didn't delete the .mounted file or something.  Oh well, it's fixed now!

---

### Post by delfick on 2006-12-17
i have the same problem

it came after i moved ubuntu to a different partiton by copy and pasting them over....

what chmod number should the filesystem be ??

i.e. how do i give the filesystem the right permissions ?? (i'm assuming via chmod)

also deleting the volatile directory didn't solve my problem as the boot messages just said

mkdir: cannot create folder : read-only file system (or something like that anyways :D)

also, does the boot messages get saved anywhere ?? (found this [http://www.ubuntuforums.org/showthread.php?t=49925&highlight=boot](http://www.ubuntuforums.org/showthread.php?t=49925&highlight=boot) but it doesn't work :( :( :( ) (nothing comes up in /var/log/boot )

also, maybe related, maybe not, but bootchart doesn't put any charts in the /var/log/bootchart folder :(

---

### Post by delfick on 2006-12-18
anyone ?? :D

---

### Post by delfick on 2006-12-19
so no-one knows how i can make my filesystem have the correct file permissions ??

please :D

---

### Post by delfick on 2006-12-21
please excuse my persistance, but i don't want to make another thread for the same thing...

*bump*

:D

---

### Post by Jon Smid on 2007-07-20
Dear,

I bumped into this very same issue after cloning my Ubuntu Feisty for use on an encrypted partition.

The details are in /sbin/lrm-manager

The solution is to remove /lib/modules.../volatile/.mounted

Next reboot it is ok.

---

