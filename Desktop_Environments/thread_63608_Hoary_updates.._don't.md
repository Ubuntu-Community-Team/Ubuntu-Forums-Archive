---
title: "Hoary updates.. don't?"
date: 2005-09-08
forum: Desktop Environments
---

### Post by goldrush on 2005-09-08
As a newbie, I have just installed Hoary with no problems.
However,  after editing the repositories, apt-get update and apt-get install appear to work ok... lots of downloads, lots of upgrades etc.
But if I run the same again, a few minutes later, or on reboot.. Hoary simply goes through the same routing... downlaoding and upgrading lost... time after time.
Is it upgraded or not.. how do I check?

Further on 1 "upgrade" it kindly put desktop icoms on for my windows hard drives (which although I had mounted etc ok, I had been trying to place desktop icons without success.. but as soon a s I rebooted... they had gone)

---

### Post by Zodiac on 2005-09-08
[QUOTE=goldrush]As a newbie, I have just installed Hoary with no problems.
However,  after editing the repositories, apt-get update and apt-get install appear to work ok... lots of downloads, lots of upgrades etc.
But if I run the same again, a few minutes later, or on reboot.. Hoary simply goes through the same routing... downlaoding and upgrading lost... time after time.
Is it upgraded or not.. how do I check?

Further on 1 "upgrade" it kindly put desktop icoms on for my windows hard drives (which although I had mounted etc ok, I had been trying to place desktop icons without success.. but as soon a s I rebooted... they had gone)[/QUOTE]
 Sounds like your repos are messed up d00d....

---

### Post by goldrush on 2005-09-08
Hi Zodia
Thanx for the info.

Not certain why, but I have now found that using apt-get etc Hoary downloads and updates every time I try, but using Synaptic, it states system already updated (or similar) so I guess it has actually been updated 

Probably me having another "senior moment" as us over 70s call them :smile:

---

### Post by mlomker on 2005-09-08
Are you using Gnome or KDE for your desktop?  Getting the windows drives to show up is often a configurable item.

---

### Post by goldrush on 2005-09-10
Hi again
Sorry for the late response.
I am using Gnome.
Have used the usual.. media/windos file to automount 
This works ok, but as mentioned for some strange reason when I ran   apt-get update on one occasion it kindly placed icons on the desktop for my windows drives ... until I rebooted when they had gone.
Further apt-get updates did not replace them.
Similarly, if I run synaptic update, it shows my system up to date, but if I imedialtely run apt-get update it downloads and "installs" lots of items

 :???:

---

### Post by angkor on 2005-09-10
'sudo apt-get update' just refreshes your package info, it doesn't download or install any packages.

What happens if you: 

sudo apt-get update

sudo apt-get upgrade (=> if this keeps on installing packages of which synaptic says                       they're already installed, then something is wrong.

---

### Post by goldrush on 2005-09-10
Hey thanks... 
now the penny just dropped. :) 
apt-get Update ... means UPDATE files
Upgrade  ... means UPGRADE

Guess I'm too old for this technical stuff ........... better I went back to pen and paper............
except I can't rememder where I put my pen  :oops:

---

### Post by Seq on 2005-09-10
[QUOTE=goldrush]Hey thanks... 
now the penny just dropped. :) 
apt-get Update ... means UPDATE files
Upgrade  ... means UPGRADE

Guess I'm too old for this technical stuff ........... better I went back to pen and paper............
except I can't rememder where I put my pen  :oops:[/QUOTE]
Ahh, the constant upgrading was on the 'apt-get update' command? Thats nothing to worry about.

'update' simply tells apt to update it's local list of what packages are available from all of your apt sources. It doesn't actually apply any changes to your system. The 'upgrade' command actually does the neccessary changes.

---

