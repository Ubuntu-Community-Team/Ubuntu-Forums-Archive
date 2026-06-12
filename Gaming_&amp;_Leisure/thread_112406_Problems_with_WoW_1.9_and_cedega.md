---
title: "Problems with WoW 1.9 and cedega"
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Grafster on 2006-01-04
So I'm having trouble getting WoW to work. I've downloaded and successfully installed the new patch (thank you filefront) but I can't actually play.

The cedega GUI play button doesn't launch the problem and in the command line the following error is generated

******************************
user@usernet:~/Games/World of Warcraft$ cedega WoW.exe
Warning: Language 'en_JP' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
wine: Unhandled exception, starting debugger...
********************************
The language stuff at the top is very standard when I used to use the command line.
The game not launching and unhandled exceptions are new as far as I can tell.

Any successful Ubuntu people running 1.9?

---

### Post by mcmuffy on 2006-01-04
Have you tried switching the sound from ALSA to OSS?

---

### Post by vyktor69 on 2006-01-04
I've had a similiar issue after installing the Wow 1.9 patch. Everything was working fine with the 1.8.4 version using cedega 4.3 and now the Login screen doesn't even come up. Nothing else on the setup has changed except for the addition of the patch. 
BTW, I've also tried uninstalling cedega and running with wine 0.9.4 and I get the exact same errors. :confused:

---

### Post by vyktor69 on 2006-01-05
Nevermind all my problems (with WoW at least) were solved by going to this thread. [http://ubuntuforums.org/showthread.php?t=92367](http://ubuntuforums.org/showthread.php?t=92367)
Look at the last page (currently 16) I installed the wow-wine_0.9.1 instead of cedega or wine 0.9.5 (latest on synaptic) and it works great. I could even change video settings in game without having the game or computer crash like it did using Cedega 5.0.3
:razz:

---

### Post by hvar on 2006-01-06
I had some problems as well, I got the help I needed here: [http://transgaming.org/forum/viewtopic.php?t=5028](http://transgaming.org/forum/viewtopic.php?t=5028)

I removed cedega 4.4.3 and installed 5.0.1 too:
apt-get remove point2play 
dpkg -i cedega_5.0.1_i386.deb 
[http://transgaming.org/forum/viewtopic.php?t=4851](http://transgaming.org/forum/viewtopic.php?t=4851)

---

