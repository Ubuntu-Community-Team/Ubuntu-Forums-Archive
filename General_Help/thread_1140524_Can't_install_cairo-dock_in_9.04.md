---
title: "Can't install cairo-dock in 9.04?"
date: 2009-04-27
forum: General Help
---

### Post by aufan19 on 2009-04-27
Hi everyone,

I am having issues installing cairo dock. I added what I think is the Jaunty repository to the end of my /etc/apt/sources.list by copying the code for Intrepid from the community documentation and replaced "Intrepid" with "Jaunty" but when I type "sudo apt-get install cairo-dock cairo-dock-plugins" I get a message saying that synaptic couldn't find the "cairo-dock-plugins" file. Am I doing the right thing?

By the way, how do you get the white box surrounding the terminal commands? I tried <code> and </code>, but that didn't appear to work.

---

### Post by Tipped OuT on 2009-04-27
Use Avant Window Navigator it's much better. Screenshot below.

---

### Post by emix101 on 2009-04-27
just try 
sudo aptitude install cairo-dock

---

### Post by pickarooney on 2009-04-28
> **Tipped OuT said:**
> Use Avant Window Navigator it's much better. Screenshot below.

It clearly isn't.

Cairo dock updated automatically for me when changing to jaunty, including the plugins package BUT the plugins themselves are nowhere to be found in the cairo interface. Which makes logging out a bit of a chore.

---

### Post by fabounet on 2009-04-28
repository for Jaunty wil be available for Cairo-Dock2 when the final release will be out
it's a matter of days now.
before that, you can try the RC packages on Berlios, or in try to force Synaptic to the 1.6.3.1.

---

