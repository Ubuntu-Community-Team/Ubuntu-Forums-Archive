---
title: "How do i remove a program that i didnt install in from the repositories?"
date: 2009-04-24
forum: General Help
---

### Post by Macfunky on 2009-04-24
Anyone able to help me out with this?

EDIT : Ignore the "in" after install :P Can't edit it out of the title

Its a few installed few .deb packages that i'm looking to remove

---

### Post by enervation on 2009-04-24
If you know the name of the package, type:
sudo apt-get remove <packagename>
in a terminal.

Alternatively, open Synaptic Package manager and search for it, and use the right click menu to remove it.

---

### Post by mykrob on 2009-04-24
ummm... what program, and how did you install it? is it from source or from a .deb package?

---

### Post by m_2009 on 2009-04-24
If you installed them from .deb files, then open up synapyics package manager and any .deb packages that were installed should show up under "Installed (Local or obselete). This should show only .deb packages that arent from the repositories.

---

### Post by Dileeshvar on 2009-04-24
Generally you can go to 
synaptic package manager or add or remove programs
and just deselect them this will work is most cases :)

---

### Post by jamessnell on 2009-04-24
If you compiled from source and installed using make, then you may be able to run ```
make uninstall
``` from the source code directory. However, if you have no idea what I'm talking about, please definitely disregard.. And if you do have an idea, still, be careful, I suspect if this program is providing a dependency to something, you could have some ugliness on the other side.

When I install programs from source code on my ubuntu setup, I create directories for each application in /opt/

Then I manually create sym links for their binaries from the directory they compile in, over to somewhere such as /usr/bin/

---

