---
title: "Is Ubuntu now Kubuntu?"
date: 2006-05-06
forum: Desktop Environments
---

### Post by seatea on 2006-05-06
I applied the updates on May 4, 2006 for Breezy and the next time I rebooted,  the blue Kubuntu logo showed up as the system loaded instead of the orange-brown Ubuntu logo. After everything loaded, the computer did go into the gnome display manager as before. Was this supposed to happen with this update?

---

### Post by Ramses de Norre on 2006-05-06
```
sudo update-alternatives --config usplash-artwork.so
```
And choose the ubuntu one, I had that issue when I installed kubuntu-desktop next to ubuntu-desktop.

---

### Post by kmartinson on 2006-05-06
I had the same issue with xubuntu (apt-get install xubuntu-desktop) but not right away...just one day the splash screen switched to xubuntu. Thanks Ramses for the fix.

---

### Post by seatea on 2006-05-06
Thanks  for the fix for this occurrence. I was wondering  if my update had gone wrong. I also have Kubuntu installed in addition to gnome, but  I could not warm up to using it and have stayed with gnome. I remember reading tha tMark Shuttleworth had indicated a prefernce for Kubuntu and thought that perhaps there was going to be a switch to Kubuntu in the future.

---

### Post by seatea on 2006-05-06
I tried the fix out: "sudo update-alternatives --config usplash-artwork.so" and found two choices. I did not see one for ubuntu. Here are my choices: 

"*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so".

Selection 2 was the  default and I changed to selection  1. When I restarted, the same Kubuntu logo showed up. I guess I am now missing the ubuntu spalsh?

---

### Post by az on 2006-05-06
[QUOTE=seatea] I remember reading tha tMark Shuttleworth had indicated a prefernce for Kubuntu and thought that perhaps there was going to be a switch to Kubuntu in the future.[/QUOTE]


No.  What he said was that he had Kubuntu installed on his laptop.  He still had Ubuntu installed on his desktop(s).  Some people quoted him and took that out of context to mean that he prfered Kubuntu.

---

