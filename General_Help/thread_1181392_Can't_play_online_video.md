---
title: "Can't play online video"
date: 2009-06-07
forum: General Help
---

### Post by pitroadrush on 2009-06-07
Hello everyone, I just finally installed Ubuntu using Wubi.
Now I can't see not online stream videos like youtube, break.com etc.
I click to download the flash and this error shows:
Error: Wrong architecture 'i386'
Do I need to install something else, 
Thanks,

---

### Post by Tipped OuT on 2009-06-07
Are you using 32-Bit or 64-Bit version of Ubuntu?

---

### Post by pitroadrush on 2009-06-07
> **Tipped OuT said:**
> Are you using 32-Bit or 64-Bit version of Ubuntu?
 
I'm using the 64 bit 9.04 Ubuntu

---

### Post by ChaiTan on 2009-06-07
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Ocxic on 2009-06-08
> **ChaiTan said:**
> [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

The above method is not needed with 9.04, nor is 9.04 covered; just:

"sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree"

from a terminal will get you going; don't forget to restart firefox after installing.

---

### Post by pitroadrush on 2009-06-08
> **Ocxic said:**
> The above method is not needed with 9.04, nor is 9.04 covered; just:
 
"sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree"
 
from a terminal will get you going; don't forget to restart firefox after installing.
 
Nice!!!! I'm doing it right now and it is booting! let you know how its going, 
Something in the terminal came out about java, some type of agreement. 
I'll let it still for another 10 more minutes, by far I can see the stream videos.
keep all posted!
:p

---

### Post by 3rdalbum on 2009-06-08
I'm hoping the Java license agreement is still being displayed on the screen. You need to press the Tab key to highlight the "I Agree" button, and then press the Space bar to select it.

Then the installation can continue.

If you've already closed the window, you will need to run the "sudo apt-get --configure -a" command in a terminal to get back to the license agreement screen and fix the package management system.

Bit of an oversight there, they should have instructions for how to highlight the "I Agree" button as not everyone has used a text-based GUI before.

---

### Post by pitroadrush on 2009-06-08
> **3rdalbum said:**
> I'm hoping the Java license agreement is still being displayed on the screen. You need to press the Tab key to highlight the "I Agree" button, and then press the Space bar to select it.

Then the installation can continue.

If you've already closed the window, you will need to run the "sudo apt-get --configure -a" command in a terminal to get back to the license agreement screen and fix the package management system.

Bit of an oversight there, they should have instructions for how to highlight the "I Agree" button as not everyone has used a text-based GUI before.

I try your aproach did not work i did the [COLOR="Black"]"sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree[/COLOR]

I can see the stream video now but some files had some issues and I try this aproach that it says on the terminal **"apt-get -f install"**
i do it and this shows : [B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/B]
Should not worry about it? 
help please 
many thanks,

---

### Post by Agent ME on 2009-06-08
Did you forget the "sudo" part to the command?

---

### Post by pitroadrush on 2009-06-08
> **pitroadrush said:**
> I try your aproach did not work i did the [COLOR="Black"]"sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree[/COLOR]

I can see the stream video now but some files had some issues and I try this aproach that it says on the terminal **"apt-get -f install"**
i do it and this shows : [B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/B]
Should not worry about it? 
help please 
many thanks,

Ok now the update manager says : 5 broken packages on your system! Use the "Broken" filter to locate them.
so what's the next step?

---

### Post by pitroadrush on 2009-06-08
> **pitroadrush said:**
> Ok now the update manager says : 5 broken packages on your system! Use the "Broken" filter to locate them.
so what's the next step?

Ok I got it working but can't see stream video with opera.

---

### Post by pitroadrush on 2009-06-09
> **pitroadrush said:**
> Ok I got it working but can't see stream video with opera.
 
anybody?

---

