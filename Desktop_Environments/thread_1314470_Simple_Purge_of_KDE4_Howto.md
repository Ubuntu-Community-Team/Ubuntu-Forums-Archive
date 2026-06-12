---
title: "Simple Purge of KDE4 Howto"
date: 2009-11-04
forum: Desktop Environments
---

### Post by L14UX_1NS1D3 on 2009-11-04
Hello all. 
I recently wanted to try out the latest version of kde on Ubuntu 9.10. So I fired up Synaptic and clicked on "Kubuntu-desktop". Downloaded the 500+ megs of software with the letter "k" in it. After logging out and then logging into kde4 I poked around the desktop environment abit. It seemed abit slower then gnome with desktop effect enabled.
My conclusion of Kde4 is it feels somewhat "limited". The plasma widgets are a nice touch but beyond that and the software that comes preinstalled with kubuntu is fine for using as it is but once you start messing with other software it's pretty easy to get tangled up in different rendering frameworks; kwin, QT,Gtk - it just doesn't seem unifying. 

So after playing in KDE I booted back into gnome and did a simple 'sudo apt-get purge kubuntu-desktop' and it unistalled without a hitch. But the problem was, I still had a crap load of other kde software I didn't want on my system. So on a whim I opened another terminal and did:

"sudo apt-get purge kde*"

I didn't realize that it would work! with having done that I was able to claim back 500+ mb of hard drive space. If you ever need to get rid of software under a certain name you can append a "*" to the apt line.

---

