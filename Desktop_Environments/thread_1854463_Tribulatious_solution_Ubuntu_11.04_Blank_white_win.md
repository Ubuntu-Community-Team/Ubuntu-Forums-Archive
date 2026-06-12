---
title: "Tribulatious solution: Ubuntu 11.04: Blank white windows when resize or fullscreen"
date: 2011-10-04
forum: Desktop Environments
---

### Post by g000we on 2011-10-04
Dear fellow Ubus,

The issue: Whenever an opened window was full size of the screen or if it was larger than 1/4 of the screen, the window would go white/blank. I found the window still functioned, but the elements weren't visible.

I am going to try to write how I solved my problem, although there were many tribulations.

My system: Laptop, Ubuntu 11.04 with Gnome as the main GUI, NVIDIA Go 6500 graphics card, 64bit cpu.

After a bug post [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717)
I downloaded NVIDIA-Linux-x86_64-280.13.run from the NVidia website.
(note* I now see that x86 might not be the best thing for 64 bit cpu)

I needed to run the script outside of xserver, so I enabled on the keyboard ctrl+alt+backspace to represent shutdown x server. It did work but I couldn't understand why there wasn't a CLI prompt i.e. "user@machine:~#_" ! (later* I remembered ALT+F1-F4 etc.)

I restarted Ubuntu holding shift and then running recovery as root.
I alt+f2 to another text login screen and logged in.

I ran the script in the CLI prompt from the ALT+f2, it installed things (using #sudo sh ./NVIDIA...run)
I restarted the computer. 
A Nvidia symbol/full screen picture flashed on the screen like Ubuntu had a twitch, when starting X.
However tense and dubious I was, it ran ok.

The issue with white screen still existed.

I looked on a previous suggestion, and in frustration didn't consider the outcome.
I #sudo apt-get remove --purge nvidia* (while still in X)

The next time I rebooted it errored (understandably as i'd deleted everything nvidia) to a pure CLI prompt

I tried #nvidia-xconfig then #startx
Still failed.

In panic, I tried to reinstall the nvidia using #sudo apt-get install nvidia-common and #sudo apt-get install nvidia* 

The logs (/var/logs/kern.log and the X windows log, command #cat kern.log | grep "Oct  4", with two spaces between Oct and 4) were highlighting issues:

The NVRM stated that the modules for the Nvidia for the Client was version 270.41.06 and the Kernel version was 280.13.

I installed lynx (#sudo apt-get install lynx) and then surfed the internet via the text based browser.

From suggestions from Feroda and Mint users having problems;
I did a #locate nvidia* | less
And scrolled through the different locations. I noticed that the /usr/ files were 270.41.06 and the normal lib files were 280.13 as stated in the error.

I logged in as my user, then ran #nvidia-uninstall (uninstalling the user modules I installed from the script, it could have been using #sudo, I can't recall)

I then restarted the computer thinking I'd need to rebuild Ubuntu and it would restart with errors. 

Ubuntu started as normal (WT..!)
And the issue isn't there. (Aih?)

There might have been other things I did, but for the life of me, I can't remember.
Still, it looks fixed :lolflag:
I hope this helps, although I'm not entirely sure it's useful.

P.S. I'll edit/add to this post if the problem comes up again.

NOTE: The issue has returned. Back to square 1.

---

### Post by g000we on 2011-10-05
Dear fellow Ubus,

I regret that the issue has arisen again and isn't solved.
:(

g000we

---

