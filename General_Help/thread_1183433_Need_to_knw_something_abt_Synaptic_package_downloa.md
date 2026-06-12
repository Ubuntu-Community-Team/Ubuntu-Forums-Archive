---
title: "Need to knw something abt Synaptic package download"
date: 2009-06-10
forum: General Help
---

### Post by thilina on 2009-06-10
Hello,
	I use ubuntu 8.10.When I try to install a package in "synaptic package manager" I can see a checkbox "Download  package files only".What does this mean? To where the downloaded packages are saved to?Can U reuse those files later?
								             Im a user on a limited bandwidth.So its easier for me to save the packages (which I install through synaptic package manager) that I download in the hard disk for later use.

---

### Post by Baelus on 2009-06-10
Synaptic is used to download and install programs from various repositories.

The default is to download and install, but can be set to download only.

It's unusual to have to change it from the default, as you'll most likely want to install the app that you've just downloaded.

AFAIK, the downloaded files are stored in the folder /var/cache/apt/archives. They are stored as standard .deb files.

Installing programs outside of synaptic (eg. through gdebi) may give you extra work to deal with. The advantage of using synaptic to manage the whole process comes from its ability to handle dependencies (i.e. packages that are required by the app you're wanting to use). It smooths out the process considerably.

This doesn't mean you can't download the files earlier, then use synaptic to install at a later time. That should work just as well as doing everything in one shot.

---

### Post by Lampi on 2009-06-10
download only means download but no install. In Ubuntu this means they get stored in /var/cache/apt/archives

You can switch to this directory and browse through the deb files stored in there, if you find the one you want to install now, you can open this with gdebi installer (right mouse button on this .deb file), or you can do it from terminal:

sudo dpkg -i <nameofthepackage>.deb

Edit: *Meep* - someone was faster ;-)

---

