---
title: "Problem re-installing KDE"
date: 2005-12-29
forum: General Help
---

### Post by petteri on 2005-12-29
Hello,

I had KDE 3.4 installed and running just fine when I decided to upgrade it to 3.5 like a fool.  At some point duing the update is asked me if I wanted to do something like stop the KDE manager, I of course said yes! It then dumped me to a full screen command line interface.  So I re-booted, and am now stuck with Gnome.  I tried to reinstall KDE with the Synaptic Package manager but that didn't work so I tried the apt-get method and here is the error is gives me:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: kdewebdev but it is not going to be installed
       Depends: kdesdk but it is not going to be installed
       Depends: kdeaccessibility but it is not going to be installed
       Depends: kdevelop3 but it is not going to be installed
E: Broken packages


Can anyone help? Thanks!

P.S. Boy am I glad the the Gnome desktop still works!

---

### Post by adie273 on 2005-12-29
The same errors came up for me when installing KDE through synaptic.

I think its 'KDE-Desktop' you install, rather than 'KDE'. Which stops those dependancy issues. then once thats installed you can install other KDE packages intop of that.

(Could be wrong. but thats what i had to do)

---

