---
title: "No applications showing in DASH"
date: 2023-07-11
forum: Desktop Environments
---

### Post by pjstock on 2023-07-11
After  a failed upgrade from 20.04 I was able to get 20.04 back and working but there were no applications showing when I clicked in DASH.
Nothing. 

Then my system prompted me to upgrade to 22.04 which I did.
On restart however I still have no applications in DASH.

Can they actually be Gone?
Or are they just hidden and not displaying for some reason?
I'd love to not have to reinstall everything.

---

### Post by ActionParsnip on 2023-07-12
Possibly this
[https://askubuntu.com/questions/334151/dash-from-unity-does-not-showing-applications](https://askubuntu.com/questions/334151/dash-from-unity-does-not-showing-applications)

---

### Post by Dennis N on 2023-07-12
Dash is sometimes confused with Dock. Ubuntu hides the Dash and replaces it with the Ubuntu Dock (a gnome shell extension). The Gnome Dash only appears in the Activities Overview, on the bottom, and then only if a Dock is not being used. So did you really mean "No applications showing in Dock?" The causes of the problem would be different.

A 'dock' could also be the 'Dash to Dock' gnome-shell extension, or even Plank.

---

### Post by pjstock on 2023-07-22
thank you.

This tip (found in that link you sent me) fixed my "missing" applications.


"Try to remove and re-install unity-lens-applications

sudo apt-get purge unity-lens-applications    
sudo apt-get install unity-lens-applications 

Edit: Log off & login. If doesn't work restart your system (see comments)"

---

