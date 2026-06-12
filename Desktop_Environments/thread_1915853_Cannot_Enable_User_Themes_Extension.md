---
title: "Cannot Enable User Themes Extension"
date: 2012-01-27
forum: Desktop Environments
---

### Post by Jeff A. on 2012-01-27
I've added the web upd8 repository, installed gnome tweak tool, and installed shell extensions.  When i go to enable them in advanced settings, there is a yellow triangle by the switch box that says *"extension does not support shell version"*

I'm using gnome shell, just installed it a few minutes ago.  Anybody have any idea what might be wrong??

---

### Post by Frogs Hair on 2012-01-27
I'm using the same PPA , so I would try the following  ```
sudo apt-get update && sudo apt-get upgrade 
```
logout and in or restart . Additional extensions can be found here . [https://extensions.gnome.org/#page=1](https://extensions.gnome.org/#page=1)

---

### Post by Jeff A. on 2012-01-27
I ran the update and upgrade, it did install a couple things.  Restarted,but still no luck in gnome tweak tool.

I looked at your link also, but every extension listed was grayed out and said "incompatible with your version of gnome"

:confused:

---

### Post by Bobhuber on 2012-01-27
> **Jeff A. said:**
> I ran the update and upgrade, it did install a couple things.  Restarted,but still no luck in gnome tweak tool.

I looked at your link also, but every extension listed was grayed out and said "incompatible with your version of gnome"

:confused:
Make sure that web8 is the only PPA activated (ricotz disabled) and completely remove and reinstall gnome-tweak tool. Also a reboot was  required for me when I first reinstalled the tweak tool. As far as the website with extensions is concerned it is really wiggy. I use firefox and have to reload the browser occasionaly in order for the page to accept my Gnome install.

---

### Post by Jeff A. on 2012-01-27
> **Bobhuber said:**
> Make sure that web8 is the only PPA activated (ricotz disabled) and completely remove and reinstall gnome-tweak tool. Also a reboot was  required for me when I first reinstalled the tweak tool. As far as the website with extensions is concerned it is really wiggy. I use firefox and have to reload the browser occasionaly in order for the page to accept my Gnome install.

Alright i used syaptics to completely remove gnome tweak tool.  How can i go about making sure ricotz is disaled, and disable it if it isnt already?

Sorry, i'm not very experienced in Linux lol

---

### Post by Bobhuber on 2012-01-27
In synaptic go to settings-repositories-other software and make sure ricotz is unchecked or just remove it if installed.

---

