---
title: "Ubuntu TryIt Live Mode"
date: 2014-02-19
forum: Desktop Environments
---

### Post by RU-XerYuS on 2014-02-19
I'd like to get Ubuntu's "Try It" Mode as useable and as close to Puppy Linux as possible. Found a great article "Bypass Ubuntu Try it" allowing you to go straight to Desktop (Awesome!). Truecrypt is about the only software I can install where its' up and running (no dependency issues). My Docs are secured in a Truecrypt container with a script to link 'em in my "Try it" Home folder making things very multi-everything. 
Hoping to find ways to install Gnome 3, Wine, gnome-tweak-tool, Tomboy, KeepNote & Restricted Extras while in this "USB Mode" or "Try it" Mode (Without having to use the internet). Tried installing tomboy-1.15.1.tar.xz but came across a dependency needing gnome-doc-utils >= 0.17.3. Want to be able to script the install of gnome-doc-utils followed by the installation of tomboy and hopefully its up and running. 
Do software programmers bundle and package software along with their dependencies? If not, hoping to find links to relevant info on accomplishing this. Big fan of Gnome 3. In addition, Lupu (PuppyLinux) is a great alternative, but if I can do it with Ubuntu...

---

### Post by ian-weisser on 2014-02-19
> **RU-XerYuS said:**
> ...as useable and as close to Puppy Linux as possible.
I don't understand what that goal means.

> **RU-XerYuS said:**
> Do software programmers bundle and package software along with their dependencies?
No, for good reason. That would defeat the purpose of package management, lead to a morass of multiple versions of the same software installed all over the place (Windows and OSX do that), and that would be utterly impossible for volunteers like us to support.

And community support is one big reason Ubuntu is free of charge.

For offline package management, look at the apt-zip and apt-offline packages. Or Synaptic's offline script creator.

---

### Post by RU-XerYuS on 2014-02-21
Thank you for the information... another big reason to stick with Ubuntu. I was unflamed, received helpful facts and gained the exact info I needed. Ubuntu rocks hard! Woohoo! Bitches!!! *sorry... that's just my thing*.

---

