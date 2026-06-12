---
title: "[SOLVED] download installer"
date: 2008-12-20
forum: Desktop Environments
---

### Post by tropdoug on 2008-12-20
can anyone tell me what to do when I download a tar.gz package from the net, ie frostwire, in Ubuntu I could open and install it through an automatic installer. In Kubuntu Ark wont do anything and I don't know the name of the installer package that ships with KDE 4, it doesn't appear in any menu either. 

A little help would be most apreciated 

Doug

---

### Post by Ender41 on 2008-12-20
> **tropdoug said:**
> can anyone tell me what to do when I download a tar.gz package from the net, ie frostwire, in Ubuntu I could open and install it through an automatic installer. In Kubuntu Ark wont do anything and I don't know the name of the installer package that ships with KDE 4, it doesn't appear in any menu either. 

A little help would be most apreciated 

Doug

 Did the website you downloaded it from have some instructions ?
For tar.gz the terminal extraction method is tar zvxf nameoffile
Then you usually need to cd into the created directory and read the README file for instructions about how to install it.

Depending on how it was built it can be as simple as ./configure to make make install etc.

Just had a look at the website for the project, just download the deb.
open a terminal cd to the directory you downloaded it to and sudo dpkg -i frostwi(hit Tab to autocomplete) enter and it should install fine.


Ender

---

### Post by tropdoug on 2008-12-21
Thanks Ender, that worked a treat, and I also realised after doing a little searching, that the program I remembered from gnome was Gdebi-gtk which gives me the GUI that I was used to. 

I installed that via synaptic which is a breeze

Once again Thanks

---

