---
title: "How to make Ubuntu responsive"
date: 2006-01-19
forum: Desktop Environments
---

### Post by lvt on 2006-01-19
I frequently do video encoding with Ubuntu. While these encoding programs are 
running, I browse the web, check email, write reports, ... But this seems to be a
hurdle since the video encoding process takes all the disk for its I/O and leaves
other processes hungry.

The problem, as I found, is in the default IO scheduler (anticipatory) of Linux that
tries to optimize bandwidth way over responsiveness.

So in short, to solve this, all you need to do is change the io scheduler to CFQ,
one that balance the two better in this case (and most desktop case I guess).

I put the following in "/etc/rcS.d/S08iosched" (excluding the dash lines):
---------------------------------------------------------------
#!/bin/sh
for f in /sys/block/*/queue/scheduler; do
        echo cfq > $f
done
---------------------------------------------------------------

And then reboot. Voila, now all my programs starts quickly even when the PC is
under high IO load (high CPU load did not really matter to this).

Good luck.

---

### Post by towsonu2003 on 2006-01-19
can someone confirm with a sandbox that this works? (no offense intended)

---

### Post by hw-tph on 2006-01-19
[QUOTE=towsonu2003]can someone confirm with a sandbox that this works? (no offense intended)[/QUOTE]

Technically it works. You can verify if by cat'ing the changed files.

However, the suggested script doesn't implement the features a Debian init script should. Compare /etc/init.d/skeleton. Also, creating actual files in the runlevel directories breaks the Debian policy and update-rc.d utility. Create the script in /etc/init.d and create symlinks in the runlevel directories instead.


Håkan

---

### Post by nocturn on 2006-01-19
You can set the scheduler at boot time with a kernel parameter.  I don't remember which one, but google can tell you.

Put it in grub and there you go.

---

### Post by hw-tph on 2006-01-19
To have the scheduler set to cfq on boot, pass **elevator=cfq** to the kernel.

You can edit /boot/grub/menu.lst and add it to the kernel line for your current kernel, and add it to the end of the #nonaltoptions line to have it automatically applied to future installed kernels (do not remove the # at the beginning of the line!).


Håkan

---

### Post by dcstar on 2006-01-19
[QUOTE=hw-tph]To have the scheduler set to cfq on boot, pass **elevator=cfq** to the kernel.

You can edit /boot/grub/menu.lst and add it to the kernel line for your current kernel, and add it to the end of the #nonaltoptions line to have it automatically applied to future installed kernels (do not remove the # at the beginning of the line!).

Håkan[/QUOTE]
I found some related documentation for those who are curious about the difference between the "Completely Fair Queuing" or "Anticipatory" IO schedulers:

[http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)

---

### Post by lvt on 2006-01-20
I just found a better way which make ubuntu much more responsive, near real
time, which may work for everyone.

Using the newest stable kernel 2.6.15.1 from [www.kernel.org](www.kernel.org), the machine
is trully flying, either with AS or CFQ scheduler, much better than current cfq. 
The only down side is that the splash screen is blank at boot (perhaps 
due to function naming convention changes in the kernel). If no splash is used 
then it is fine. Everything else is like before.

[This is for intermediate user] The steps I used were:

- download the new kernel to /usr/src.
- uncompress it.
- install the linux-tree package using aptitude (to get the ubuntu patches).
- apply the ubuntu patch 2.6.12 to the 2.6.15 kernel.
- use the /boot/config-2.6.12-9-i386 for new kernel's config.
- enable kernel preemption.
- remake the kernel with "make-kpkg buildimage".
- install the new kernel with "dpkg -i".

It seems the new kernel has much better io scheduling algorithms. Either AS
(anticipatory) or CFQ scheduler results in almost identical behaviors under high
load or under low load. Firefox/Openoffice all starts in 1-3 seconds. It would be
nice if the ubuntu team incorporate this new kernel in the next release. So far
I have found only better things. The splash screen should be easy for the team
to fix - I think.

Good luck.

lvt

---

### Post by hw-tph on 2006-01-21
[QUOTE=lvt]It would be nice if the ubuntu team incorporate this new kernel in the next release. So far I have found only better things. The splash screen should be easy for the team to fix - I think.[/QUOTE]

The 2.6.15 kernel is already in the Dapper development repositories if I'm not mistaken.


Håkan

---

### Post by John.Michael.Kane on 2006-01-29
does this get placed in grub menu like this elevator=cfq or this way #elevator=cfq

this is how it is i placed it .```
## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash
elevator=cfq

```

---

### Post by hw-tph on 2006-01-29
No. This is the way to do it:

```
# nonaltoptions=quiet splash elevator=cfq
```

This will make it appear on new kernel entries (installed in the future). You can tack it onto the existing kernel entry manually.

Håkan

---

### Post by virgule on 2006-03-19
A little bit better yeah! Check this out. Running:
```

time ps -ely

```
From tty1 would take ~2.226 'real' seconds with scheduler set to anticipatory (default). Now, with cfq, it the same command take 0.382 'real' seconds. Amazing. I am chocked and amazed. That is great. Superb... wow. Me Likes..

PS. The kernel arguments has been fed to BootX and the script you provided is now living in /etc/rcS.d/

---

### Post by geofs on 2006-04-16
[http://ubuntuforums.org/showthread.php?p=926992](http://ubuntuforums.org/showthread.php?p=926992)

---

