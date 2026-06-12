---
title: "nvidia drivers problem"
date: 2009-03-13
forum: General Help
---

### Post by overburn on 2009-03-13
hello

i have a tiny problem with installing nvidia drivers. 
the 173 and 177 that i can get with ubuntu are pretty slow .
so i decided to get the 180 from the nvidia website.

i ctrl-alt-backspace to restart x
i ctrl-alt-f2 to exit to command prompt
i type "/etc/init.d/gdm stop"
gdm stops
i install the drivers, but when i try to /etc/init.d/gdm start, i get a red fail. 
so i type "halt" and the system shuts down
when i start it again i get an error that i don't have an nvidia graphics card and i get some failsafe choices, of which only the "boot in limited graphics mode" works :( 

my system is:
ASUS P5V-VM ultra motherboard
intel Pentium D930 cpu @ 3ghz
Leadtek PX9600GT (Geforce 9600GT with 512mb gddr3 , don't remember the frequencies)
and 1x2gb kingmax ddr2

any help would be truly appreciated.
thanx :)

---

### Post by Sjeti on 2009-03-13
From my personal experience, the non-repository drivers almost never work.

Try and reinstall the repository drivers.  Its better to be slow than to be in VGA standard.

---

### Post by GenePayne on 2009-03-13
I had the same problem, and the post right before me illuminated this issue. I am going to stop trying to install drivers from nvidia and go with the repository driver. So thanks, Sjeti.

In the meantime, I was able to get back to my previous screen resolution (minus the fancy compiz graphics) from the bootloader menu. If you have the standard bootloader options from power-up, then you will have a recovery mode for the most recent kernel you're running. (probably 2nd line in the bootloader). This isn't a substitute for getting the right driver, but at least in the meantime you should have your previous screen resolution, so you don't have to deal with the painfully-low VGA resolution when you boot in "limited graphics mode."

---

### Post by Xero Xenith on 2009-03-13
You can have the best of both worlds - using a PPA to get the latest NV drivers (180.29) via a repo. This worked wonders for me, and [this guide seems to document it well]("http://samet.kilictas.com/how-to-install-nvidia-driver-18029-on-your-ubuntu/").

---

### Post by s7ewie on 2009-03-14
I had a similar problem with nvidia 180.29.
Do you have installed the nvidia-kernel-common package?
To check, run:

sudo dpkg -l | grep nvidia-kernel-common

In case you got some output starting with
ii  nvidia-kernel-common
it means you have this package installed. In this case, you can try this:

sudo apt-get remove nvidia-kernel-common
/etc/init.d/gdm stop
sudo ./NVIDIA-Linux-x86-180.29-pkg1.run

Follow the instructions (usual install procedure).

Make sure that your /etc/X11/xorg.config has in the "Device" section the "nvidia" selected as driver. Like this:

Driver         "nvidia"

In case it's not, you can set it yourself, or go the safer way and run
sudo nvidia-xconfig

Reboot.

Hope this helps and please don't be offended if some of the explanations are too n00bish; I just wanted to make sure it's easily understandable.

---

### Post by arapa on 2009-03-14
I just spent a couple of months fighting with these drivers. The nvidia-glx-173's are the only driver I can get running on my 9800-GTX+ cards.

---

### Post by bkaplan on 2009-03-14
> **s7ewie said:**
> I had a similar problem with nvidia 180.29.
Do you have installed the nvidia-kernel-common package?
To check, run:

sudo dpkg -l | grep nvidia-kernel-common

In case you got some output starting with
ii  nvidia-kernel-common
it means you have this package installed. In this case, you can try this:

sudo apt-get remove nvidia-kernel-common
/etc/init.d/gdm stop
sudo ./NVIDIA-Linux-x86-180.29-pkg1.run

Follow the instructions (usual install procedure).

Make sure that your /etc/X11/xorg.config has in the "Device" section the "nvidia" selected as driver. Like this:

Driver         "nvidia"

In case it's not, you can set it yourself, or go the safer way and run
sudo nvidia-xconfig

Reboot.

Hope this helps and please don't be offended if some of the explanations are too n00bish; I just wanted to make sure it's easily understandable.

I'd appreciate someone's help:
when I issue the command

/etc/init.d/gdm stop

from a terminal, I get a black screen with flashing cursor that I can't figure out how to get past.  The only thing I can do is hard reboot or <ctrl><alt><del> to reboot.  What am I doing wrong?

TIA for any help.

---

### Post by s7ewie on 2009-03-14
I wasn't explicit enough..

So, as **overburn** said, you should first logout of GNOME, then change to a text terminal:
> ctrl-alt-f2 to exit to command prompt
Works with any F key up to F6.

Actually, you could do the switch even after stopping gdm from a terminal, but it's not really a clean shutdown of gdm.

---

### Post by bkaplan on 2009-03-14
Thanks. Turns out that my system wasn't recognizing my wireless keyboard's ctrl-alt-f2.  Once I plugged in a wired kb, the remainder worked fine.

Notwithstanding, even with the newest recommended NVIDIA drivers for my geForce FX 5500 (173.14.18), installed as above, my monitor still flashes on and off repeatedly, and soon my system hangs.  Cannot figure this out for the life of me.  If anyone knows of a post on point (I've been researching this for weeks now on ubuntuforums.org and nvidia.com), I'd really appreciate a link ...

---

### Post by arapa on 2009-03-14
Have you looked through the nvnews linux forum?

This is from - [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

> [B]
Debian GNU/Linux or [K]Ubuntu with Xorg 7.x[/B]

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.


If you require further assistance after following the instructions above, please see: [http://www.nvnews.net/vbulletin/showthread.php?t=46678]("http://www.nvnews.net/vbulletin/showthread.php?t=46678").

---

### Post by bkaplan on 2009-03-15
Thanks.  I did see these posts on the nvnews linux forum.  I've had no success following those recommendations either.

Clearly, the nvidia drivers are enabled, but there is a conflict that I can't understand.  My screen flickers on and off with repeating regularity, then the system slows and eventually crashes with a geometric pattern showing on my screen (likely remnants of what was being painted to screen at the time of the crash).

Any ideas?  I've used the drivers from intrepid repos, drivers from nvidia directly, purging all known remnants of each prior to loading the next set.  nvidia kernels installed with package, or compiled at runtime by the nvidia installer.

Interestingly, my system used to work correctly with the installed repo drivers on fully updated Intrepid. It is only recently that the drivers have stopped working/started crashing (maybe early January 09) and I haven't been able to reenable them since.  I'm guessing that an update caused an incompatibility, but don't have the knowledge to figure out what happened or to fix.

Again, thanks for any ideas.

---

