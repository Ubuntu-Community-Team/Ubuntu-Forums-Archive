---
title: "Uninstalling Kaffeine"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Glass_Onion on 2006-03-18
I tried to install Kaffeine Player through the Add Aplications program. After a few seconds my moniter started throwing phycodelic colours at me so I had to do the Ctrl Alt Backspace thing. It apeared to have installed when I logged back in but I keep getting told errors about how it hasn't. Can anyone telling me how to uninstall it so I can install it properlly?

Also, can someone give me a link to a cheat sheet for Terminal commands in Ubuntu to help me learn all of these things quicker?

Thanks in advance. :)

EDIT: I acidently put this here instead of  Absolute Beginner Talk. Sorry! Is it possible for this to get moved for me?

---

### Post by JamesNorris on 2006-03-19
I *think *the command you need is "dpkg-reconfigure kaffeine"
but I might be wrong.

If it don't work, you could always try
> sudo apt-get -f install
for good measure.

Which should fix any problems encountered by you resetting X if it was still running apt

If not, all I can reccomend is
> sudo apt-get remove kaffeine
sudo apt-get install kaffeine

---

