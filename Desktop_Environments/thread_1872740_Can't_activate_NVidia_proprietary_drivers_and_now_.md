---
title: "Can't activate NVidia proprietary drivers and now it won't even boot"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Sciamano on 2011-10-31
Hi!
I've installed Ubuntu 11.10 on my PC with NVidia GTS250.
The live CD worked like a charm, it detected the right display resolution and everything. So I installed the OS, but after reboot, it would show the wrong resolution.
I checked the display settings, but the right resolution won't even be listed. Then I tried activating the NVidia drivers, but it failed.
I then tried to run nvidia-xconfig (no success here either) and when I rebooted, the system hung at the splash screen (the one with the Ubuntu logo and the 5 red/white dots). I tried more times but it always hangs at the splash screen.
What should I do? :(
Thanks

---

### Post by branoic on 2011-10-31
Hi

I am experiencing the same problem, but I have an Nvidia 130M.

I just made a new install of 11.10 and I got the wrong resolution right now. Then I tried to activate the
Nvidia drivers through the terminal like you and also got stuck on the splash screen.

So I made another new installation and still have the same problem. When I try to activate the
Nvidia drivers through "Additional Drivers" I get this error message:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

Which says a lot more, but this is what I found that has to do with Nvidia:

2011-10-31 19:34:02,731 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-31 19:34:02,731 DEBUG: nvidia.available: falling back to default
2011-10-31 19:34:02,766 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-31 19:34:02,766 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase

Thanks in advance!

---

### Post by 23dornot23d on 2011-10-31
This line - Nvidia 173 ..... is the older driver you appear to be using and may not work ..... try the 

nvidia-current

driver ...... basically means removing what you have got now and re-installing the newer one ......

> 
2011-10-31 19:34:02,731 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
Here is what I do when my Nvidia Card does not work .... 

First ...... run synaptic .......

then search for Nvidia ...... remove everything that starts with Nvidia

now check which kernel you are running ....... make sure the headers are there for the kernel version you have  ..... to find your kernel type ....

uname -a

Now you could try these commands below or wait for someone that knows what they
are doing ......

sudo rm /etc/X11/xorg.conf

sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install nvidia-settings

sudo aptitude install nvidia-current

watch and make sure it installs correctly with no [COLOR=Red]**FAIL **[/COLOR]markers anywhere ....

re-create xorg.conf (I think its ... )

[sudo **nvidia-xconfig**]("http://linux.die.net/man/1/nvidia-xconfig")

reboot cross your fingers and hope for the best ....... :grin:

add some more information from the logs if it fails on the newer driver  ...... ;)

_____________________________________________________________

@Sciamano try the same ..... but you did not show your error log ..... this may help ......

look in administration >>> log file viewer 

look for the kern log and syslog  (xorg logs may be there but on my latest were not) logs ..... latest relevant information .....

---

### Post by Sciamano on 2011-10-31
I kind of solved by reinstalling Ubuntu from scratch. This time I unchecked the "update packages while installing" flag, let it install, and activated (successfully) the nvidia drivers BEFORE updating everything else.
It seems like it worked.

---

### Post by 23dornot23d on 2011-10-31
Good to hear ....

When you type this below in a terminal window - to get a terminal press ( Ctrl+Alt+t ) together.

**nvidia-settings **

What does it show as the driver in use ..... ( main thing is you are working again .. )

should look similar to this if nvidia-settings is/are installed ....

[IMG]http://img88.imageshack.us/img88/6972/nvidia280.jpg[/IMG]

---

### Post by Sciamano on 2011-11-03
Yep, it looks like that. Everything looks fine now. THanks!

---

