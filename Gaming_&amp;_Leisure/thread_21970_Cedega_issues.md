---
title: "Cedega issues"
date: 2005-03-24
forum: Gaming &amp; Leisure
---

### Post by TravisNewman on 2005-03-24
OK I just recently installed Cedega 4.3. I didn't have it installed previously (hadn't bothered yet, and hadn't played any Windows games). But now, whenever I try to play any game, I get error=21. Weird thing is, I can open the games in Crossover but they suck hard in Crossover (and why wouldn't they?). I've followed steps to fix this that I've found all over the web, basically disabling prelinking, etc. Most instructions were RedHat/Fedora specific. I'd love to get this working. Anyone know how I might?

---

### Post by TravisNewman on 2005-03-24
OK so apparently you can't run from a windows partition.

Anyway, the video in hl2 doesn't run. Like the guy at the beginning with the valve/faucett thing coming out of his head, and the g-man talking to you at the beginning and end of the game.

Also, sometimes when loading a game, it will act like it's loading then kick back to the menu.

So it seems that either the libraries in Hoary, or the Cedega updates, have borked things a bit.

---

### Post by leech on 2005-03-25
As a side note, you should be able to play them off your windows drive, but I think you need the 'exec' option in your /etc/fstab entry for that partition/drive.

Leech

---

### Post by jdodson on 2005-03-25
[QUOTE=panickedthumb]OK I just recently installed Cedega 4.3. I didn't have it installed previously (hadn't bothered yet, and hadn't played any Windows games). But now, whenever I try to play any game, I get error=21. Weird thing is, I can open the games in Crossover but they suck hard in Crossover (and why wouldn't they?). I've followed steps to fix this that I've found all over the web, basically disabling prelinking, etc. Most instructions were RedHat/Fedora specific. I'd love to get this working. Anyone know how I might?[/QUOTE]

i got this error too.  i don't have a windows partition!?!  wonder if there is a fix that works for this one.  ?

ill hack around on this and let you know if i come up with anything.

---

### Post by Snocrash on 2005-03-26
From transgaming.org
-----------------------------------------------------
Summary
------------
To solve error 21 problems you need to:
disable prelink
turn off exec-shield
enable legacy VA_LAYOUT (2.6.9 kernel)
enable exec mount option

Check below for more information on the problems and details on fixing them.

More information
--------------------
Prelink is a new set of functionality, available in newer glibc versions
and distributions such as Fedora Core 1, designed to reduce the startup
time for applications which use dynamic libraries. The loading speed
improvements are achieved by preassigning the addresses of various dynamic
linked libraries that will be placed in memory. Thus, relocations will not
have to be performed by the dynamic loader when loading the application.
Unfortunately, more often than not, libraries are prelinked into addresses
which are incompatible with Windows programs.

Windows programs generally use a trick, similar to Prelink, to reduce the
size of the executable and improve start times. This trick
assumes, quite rightly for a Windows program, that the address 0x400000
is always available. Thus when Cedega attempts to load the Windows
executable into the starting address, and it's not available, Cedega will
fail to start the program with an error message mentioning
"stripped relocation records" and "address 0x400000 not available".

Exec-shield is a kernel level solution
([http://people.redhat.com/mingo/exec-shield/ANNOUNCE-exec-shield](http://people.redhat.com/mingo/exec-shield/ANNOUNCE-exec-shield))
which remaps executable code to a lower memory address with the
intention of eliminating ASCII based code overflow attacks. The
new location of the executable has the potential of conflicting
with the required windows range which will result in the same error
message as with Prelink.

The solution to the problems these two new technologies create is to
disable them so that they don't affect any Cedega libraries or executable
code.

To disable automatic prelinking in the future, edit /etc/sysconfig/prelink
and set PRELINKING to no by making sure the following line is present:
PRELINKING=no
Then execute the cron job, most likely /etc/cron.daily/prelink, to
reverse the Prelink for all of your libraries or manually run:
$ prelink -ua

To disable exec-shield you can either use the boot time option
"exec-shield=0" or it may be changed, before running Cedega, by typing
either:
$ echo 0 > /proc/sys/kernel/exec-shield
or
$ sysctl -w kernel.exec-shield=0

In addition, newer Fedora Core 2, Fedora Core 3, and other 2.6.9 kernels also
require support for legacy VA layout to be enabled. This can be done
via the command:
$ echo 1 > /proc/sys/vm/legacy_va_layout
before running Cedega (this is required after every boot).
To enable legacy VA Layout at boot time, edit /etc/sysctl.conf
and add the following:
vm.legacy_va_layout = 1

Information about this can be option found on the fedora announce mailing list:
[http://www.redhat.com/archives/fedora-announce-list/2004-August/msg00025.html](http://www.redhat.com/archives/fedora-announce-list/2004-August/msg00025.html)

Some distributions version of mount now run with the noexec option unless otherwise specified. Running games from a partition mounted with noexec can cause an error = 21
To fix this issue edit the /etc/fstab and modify the partition line by removing the noexec option and adding the exec switch to the mount options. For example:
change
/dev/hda1 / ext3 errors=remount-ro,no-exec,defaults 0 1
to
/dev/hda1 / ext3 errors=remount-ro,exec,defaults 0 1

If neither exec nor noexec appears in the line it is recommended that you add it.

To remount the partition run (as root):
mount -o remount /
-----------------------------------------------


Hope this helps.....Cedega runs fine for me.

-Sno

---

### Post by TravisNewman on 2005-03-26
Yeah I've done all that ;)
Thing is, the readme for 4.3 says that it's fixed most of this, but it hasn't apparently.

Anyway, I DO have the exec in every partition that could possibly matter. That didn't help-- still couldn't run games from fat32 partitions. 

Though that doesn't really matter. If I can get this working I'll get rid of Windows (again). I had it on initially for testing some things, and then for Half-Life 2 ;)

---

### Post by jdodson on 2005-03-26
ok i got cedega 4.2.1 working.  the latest just did not want to fly.... oh well. 4.2.1 was good.

anyways what i did was install 4.2.1 and when it barfed on my when i wanted to install a game i ran this command as root.  somehow running the command as sudo does nothing:

echo 0 > /proc/sys/kernel/exec-shield 

and the game would install(warcraft 3 specifically).

anyways, fwiw.

---

### Post by saik0 on 2005-03-28
Someone already mentioned this but by adding exec to your fstab you will fix the error=21 problem, this includes fat32 partitions. And as far as I know Cedega 4.3 does indeed fix the prelink, VA shield, and pthread problems it's had in the past. Happy gaming =)

---

### Post by digby on 2005-03-28
[QUOTE=jdodson]ok i got cedega 4.2.1 working.  the latest just did not want to fly.... oh well. 4.2.1 was good.

anyways what i did was install 4.2.1 and when it barfed on my when i wanted to install a game i ran this command as root. somehow running the command as sudo does nothing:

echo 0 > /proc/sys/kernel/exec-shield 

[/QUOTE]

I tried this, but it simply returned 
```
root@dreadnaught:/home/matt # echo 0 > /proc/sys/kernel/exec-shield
bash: /proc/sys/kernel/exec-shield: No such file or directory
```

Any ideas?  I'm out of my league here.

---

### Post by jdodson on 2005-03-31
[QUOTE=digby]I tried this, but it simply returned 
```
root@dreadnaught:/home/matt # echo 0 > /proc/sys/kernel/exec-shield
bash: /proc/sys/kernel/exec-shield: No such file or directory
```

Any ideas?  I'm out of my league here.[/QUOTE]

i got that error when i ran the command as sudo..... i ran it later and it was fine.  i really am not sure.  i googled around till i found the answer, try that.

---

### Post by digby on 2005-04-01
What error did you get when you first tried to install WC3?  Did it start with ```
matt@dreadnaught:/media/cdrom$ cedega install.exe
wine: Unhandled exception, starting debugger...
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
```

I've googled around and found a lot of info on prelinking and disabling exec-shield, but my system doesn't seem to have either of those. 'Locate prelink' returns nothing but a few open office files.  So I'm just trying to detirmine if we have the same problem or if I need to be looking for something else.

---

### Post by Muchacho_Gasolino on 2005-04-01
I've got Cedega 4.3 and World of Warcraft running pretty well. I havent messed with anything major, pretty much a stock Hoary install(AMD64). When I first installed the game I had some trouble, had to reinstall the game and point2play a few times, but once the game started working, no trouble from cedega. I will post my p2p and WoW configs if you guys think they would be helpful. 
BTW, if you want to play WoW in opengl with the new patch, you gotta go to the WoW forum on transgaming.org and dl a patch.
Also, as far as I know 4.3 does fix all prelinking and legacy problems(at least never heard anyone complaining on the cedega forums), so I don't think thats the problem.

---

### Post by digby on 2005-04-02
Upgrading to 4.3 seems to have fixed the problem.  Thanks... now to get sound working correctly...

---

### Post by jdodson on 2005-04-04
[QUOTE=digby]I tried this, but it simply returned 
```
root@dreadnaught:/home/matt # echo 0 > /proc/sys/kernel/exec-shield
bash: /proc/sys/kernel/exec-shield: No such file or directory
```

Any ideas?  I'm out of my league here.[/QUOTE]

try this instead as root:

sysctl -w kernel.exec-shield=0

---

### Post by digby on 2005-04-07
Thanks, but I already switched from 4.2.1 to 4.3.  I didn't have any trouble with the latter.

---

### Post by VerrNum on 2005-04-11
[QUOTE=digby]Thanks, but I already switched from 4.2.1 to 4.3.  I didn't have any trouble with the latter.[/QUOTE]
 Hi,

i am playing Frozen Throne too, with Cegeda 4.3.1

I installed last ATI driver, and performances are OK :

fgl_glxgears
2423 frames in 5.0 seconds = 484.600 FPS
2720 frames in 5.0 seconds = 544.000 FPS
2291 frames in 5.0 seconds = 458.200 FPS
1669 frames in 5.0 seconds = 333.800 FPS
2649 frames in 5.0 seconds = 529.800 FPS
2969 frames in 5.0 seconds = 593.800 FPS

glxgears
14230 frames in 5.0 seconds = 2846.000 FPS
14903 frames in 5.0 seconds = 2980.600 FPS
15141 frames in 5.0 seconds = 3028.200 FPS
14169 frames in 5.0 seconds = 2833.800 FPS
14112 frames in 5.0 seconds = 2822.400 FPS
15223 frames in 5.0 seconds = 3044.600 FPS

But Frozen Throne is very very SLOW !!
It is unplayable when there are many units ...

I tried it, by --opengl ..

Does need any else setting to work coorectly ?

Thanks to help !!!

---

### Post by VerrNum on 2005-04-12
[QUOTE=VerrNum]Hi,

i am playing Frozen Throne too, with Cegeda 4.3.1

I installed last ATI driver, and performances are OK :

fgl_glxgears
2423 frames in 5.0 seconds = 484.600 FPS
2720 frames in 5.0 seconds = 544.000 FPS
2291 frames in 5.0 seconds = 458.200 FPS
1669 frames in 5.0 seconds = 333.800 FPS
2649 frames in 5.0 seconds = 529.800 FPS
2969 frames in 5.0 seconds = 593.800 FPS

glxgears
14230 frames in 5.0 seconds = 2846.000 FPS
14903 frames in 5.0 seconds = 2980.600 FPS
15141 frames in 5.0 seconds = 3028.200 FPS
14169 frames in 5.0 seconds = 2833.800 FPS
14112 frames in 5.0 seconds = 2822.400 FPS
15223 frames in 5.0 seconds = 3044.600 FPS

But Frozen Throne is very very SLOW !!
It is unplayable when there are many units ...

I tried it, by --opengl ..

Does need any else setting to work coorectly ?

Thanks to help !!![/QUOTE]
 Hi again,

Does someone can post or mail me his cedega config file.
I will can compare with mine..

I will try too to reinstall it, cause at this time, i am using a installed version from an existing windows..

Thanks a lot

---

