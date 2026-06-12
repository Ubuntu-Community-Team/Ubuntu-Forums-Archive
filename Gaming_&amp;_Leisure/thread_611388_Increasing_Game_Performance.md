---
title: "Increasing Game Performance"
date: 2007-11-12
forum: Gaming &amp; Leisure
---

### Post by synd7 on 2007-11-12
After recently discovering that the ETQW demo runs on my computer (not well though :D) i was wondering if anyone has any special tweaks to their system to squeeze out any more 3d performance in games?

Right now i'm thinking about installing fluxbox or something similar and logging into that for gaming.

Any other tips?

---

### Post by cogadh on 2007-11-12
It would really help to know something about your hardware (processor, RAM, video card), otherwise, we are just spitballing ideas.

As for shooting the first spitball, you can try running the game in it's own X session without your window manager running. All of the resources that normally go to the window manager would be freed up for use by the game. You could automate the process some by creating a launch script that you could use to start the game. Here is an example of one that I use for running Windows games through Wine in their own X session, it could easily be modified to work with most games:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```

---

### Post by synd7 on 2007-11-12
I remember seeing a script like that before somewhere, i'll give it a go in a minute. I'm not sure whether it will work, the problem of the fglrx drivers not restarting X never got solved for me, even with the new 8.42 drivers

As for system specs:
2GHz pentium 4
512M RAM
ATI Radeon 9800

---

### Post by mbradlcu on 2007-11-12
that's a great suggestion using a dedicated X session,, I also found either building a kernel with low latency settings or using the packaged lowlatency kernel made a huge difference.. you may also be able to squeeze a few more fps over clocking your vid card. If you're using an nvidia care here's the line that need to be added so that the overclock option will be available using the 'nvidia-settings' program.

> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
#    Driver         "vesa"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"
    Option  "AddARGBGLXVisuals" "True"
    Option  "DisableGLXRootClipping"    "True"
Option      "Coolbits" "1"


it's the Coolbits option that does it.
if you need help building a low latency kernel I have a little faq, it's actually very easy.

---

### Post by synd7 on 2007-11-13
Does anyone know where i might find where i might find a prepackaged low latency kernel? I would build one but i really cant be bothered at the moment, i might have a go after my exams are finished.

As i expected, the new session script didnt work for me, first i didnt have permissions to work with X, then after using sudo (perhaps not a great idea) i got a black screen.

---

### Post by Sockerdrickan on 2007-11-13
I don't need a low latency kernel to get full fps on ultra so I doubt it helps.

---

### Post by mbradlcu on 2007-11-13
well here's the qnd:
```

apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.tar.bz2
tar -jxvf linux-2.6.22.tar.bz2
ln -s linux-2.6.22 linux
cd /usr/src/linux
cp /boot/config-`uname -r` ./.config 
make menuconfig
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-{some_custom_name_here} kernel_image kernel_headers
cd /usr/src/
dpkg -i linux-image-2.6.22-custom_2.6.18.1-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.22-custom_2.6.18.1-custom-10.00.Custom_i386.deb

```

as for a working dedicated X session this one works for me,, yea it need to be run as root,, but,,:
```

#!/bin/sh
old_user=$USER
old_user=$1
echo "your_passwd" | sudo -S  /etc/init.d/gdm stop
sudo  X :1 -ac -br &
export DISPLAY="localhost:1"
xterm -bg black -fg green
sleep 1
su - $old_user 'xterm -bg black -fg green'
sleep 1
kill `cat /tmp/.X1-lock`

```

---

### Post by mbradlcu on 2007-11-13
> **Tux0r said:**
> I don't need a low latency kernel to get full fps on ultra so I doubt it helps.

no offense,, but have you benched the difference? if it doesn't make a difference that's great! but  on my system the benchmarks I ran using doom3/etqw had an appreciable improvement. note I don't have a multi core cpu so I may be opening up the cpu bottle neck.. seriously it was ~%14 fps increase!
thanks!

---

### Post by Luksion Knight on 2007-11-13
hey what kind of programming language is that? i was wanting to modify it so i could input a command (i dont know if theyre called strings/function headers in all languages) and have it launch a function which launches a particular game.

---

### Post by cogadh on 2007-11-13
That's just a shell script, kind of like a batch file in DOS or Windows. Pretty much any command that you could run in a terminal could be included in a shell script. There is a decent shell script beginner's how-to here:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by synd7 on 2007-11-13
After a quick google on low latency options, i found a page on the openSUSE forums about recompiling for ETQW performance, it basically came down to 1000Hz timer and preemptable kernel

The kernel is compiling now, hope it works *crosses fingers*

---

### Post by Mblackwell on 2007-11-13
You could have just used apt and gotten [linux-image-rt](http://packages.ubuntu.com/gutsy/metapackages/linux-image-rt).

---

### Post by synd7 on 2007-11-13
oh dammit, i had searched for a the low latency kernel present in feisty but i couldnt find it. Looks like they changed the name :D

compiling the kernel went fine but rebuilding the fglrx module crapped out on me: [http://ubuntuforums.org/showthread.php?p=3762133](http://ubuntuforums.org/showthread.php?p=3762133)

---

### Post by RonP on 2007-11-13
> **mbradlcu said:**
> well here's the qnd:
```

apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.tar.bz2
tar -jxvf linux-2.6.22.tar.bz2
ln -s linux-2.6.22 linux
cd /usr/src/linux
cp /boot/config-`uname -r` ./.config 
make menuconfig
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-{some_custom_name_here} kernel_image kernel_headers
cd /usr/src/
dpkg -i linux-image-2.6.22-custom_2.6.18.1-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.22-custom_2.6.18.1-custom-10.00.Custom_i386.deb

```

as for a working dedicated X session this one works for me,, yea it need to be run as root,, but,,:
```

#!/bin/sh
old_user=$USER
old_user=$1
echo "your_passwd" | sudo -S  /etc/init.d/gdm stop
sudo  X :1 -ac -br &
export DISPLAY="localhost:1"
xterm -bg black -fg green
sleep 1
su - $old_user 'xterm -bg black -fg green'
sleep 1
kill `cat /tmp/.X1-lock`

```

ok you openned a can of worms for me. I used to do this with windows in the old days to squeeze out performance. How do i get this to work with a game i am using ? if i need to be SU to use it how do i do all this 

Yes i am new ...

---

### Post by Dapman01 on 2007-11-13
Where do I find that guide on how to make a low latency kernel

---

### Post by mbradlcu on 2007-11-13
ahh, well it's a fun can of worms! basically each line on the top code block needs to be run as root or as most folks like to do use sude,, eg:
```

sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

```
the part that's a little tricky to illistrate is what you'll need to change/set when you envoke 'make menuconfig'
it's under the "Processor type and features - > "
the setting that need to be changed are:
"Timer frequency" set to 1000 HZ
and
Preemption Model Preemptible Kermel (low-latency Desktop)

the just run the rest of the commands and it should build... but as another post mentioned I believe there's already a pre-build packaged low-latency kernel available from apt,,, but where's the fun in that ; )

let me know if you need any help or have any questions.. have fun!

---

### Post by Mblackwell on 2007-11-13
> **Dapman01 said:**
> Where do I find that guide on how to make a low latency kernel

sudo apt-get install linux-image-rt

It installs a real-time preemption kernel. Also good for audio apps.

---

### Post by synd7 on 2007-11-13
Ok, i downgraded back to 2.6.22 (using the rt kernel) and i'm getting the same error as in my other post: [http://ubuntuforums.org/showthread.php?p=3762133](http://ubuntuforums.org/showthread.php?p=3762133)

Has this happened to anyone else? I've tried completely removing fglrx and reinstalling it, module still wont compile.

also, i switched to the radeon driver for when i recompiled the fglrx module and glxinfo is giving me this:
```
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

```

---

### Post by mbradlcu on 2007-11-14
it's never a good thing to google your problem and a top his is your own post ; (

seems some one had your issue and was able to at least compile the module,, but then had problems trying to shut down X cleanly.. anyway if you haven't already seen this link maybe it can offer some suggestions,, I'll quote the part that seems most interesting:
> 
I grabbed the 8.40.4 fglrx code from ATI and applied two patches (/forums/showthread.php?t=5675&highlight=patch&page=2) found in these forums. The code builds and I get acceleration as I did before. Cool.

[http://www.phoronix.com/forums/archive/index.php/t-5816.html]("http://www.phoronix.com/forums/archive/index.php/t-5816.html")

I don't use an ati card so sorry I can't help more..

---

### Post by synd7 on 2007-11-14
I found out what the problem was. fglrx 8.42 doesnt have 2.6.23 support and the -rt kernel was compiled with paravirtualisation support which causes the errors.

I recompiled it without paravirtualisation and its working well, much more responsive.

One more thing, does anyone know which bottlenecks affect which settings in the game?

ie. a memory bottleneck might affect what quality textures are best
bottleneck in the graphics card affects the quality of models can be used, etc

---

### Post by pyro_xp2k on 2007-11-18
If you're interested, here's the patch to get fglrx working with the 2.6.23 kernel.  Apply this in [FONT=Courier New]/usr/src/modules/fglrx[/FONT] prior to compiling the kernel.

Also, to get fglrx working after applying the real time patch, edit [FONT=Courier New]/usr/src/linux/kernel/rcupreempt.c[/FONT]
and replace all instances of  [FONT=Courier New]EXPORT_SYMBOL_GPL[/FONT] with [FONT=Courier New]EXPORT_SYMBOL[/FONT].
Save that and compile the kernel and everything should work fine.

Thank *JohnG_ie* for the latter info.

---

