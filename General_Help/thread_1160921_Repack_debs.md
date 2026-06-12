---
title: "Repack debs"
date: 2009-05-16
forum: General Help
---

### Post by Orlsend on 2009-05-16
I came across a program that I think its called *dpkg-repack*, basically I found out about it a blog where it was used for backing up every single installed Program. I am aware it can repack single programs to but I am not sure how. Does anyone know? or even better does anyone know one similar app that has a GUI?

Thanks!

---

### Post by IanW on 2009-05-16
Debs for all your currently installed programs* already exist in Places/Computer/Filesystem/var/cache/apt/archives
Just burn them to CD/DVD to back up. After reinstalling Ubuntu, mount the CD/DVD and "sudo dpkg -i /media/cdrom0/*.deb"

*(in fact everything that has been updated or installed via Synaptic/Update Manager since you installed Ubuntu)

---

### Post by cmost on 2009-05-16
If you want to repackage individual programs, say Nautilus to enable rgba, etc., you can do so very easily with existing software.  I use debuild.  Here's how:

Say you want to rebuild the package nautilus with the rgba patch:

1.  Create a working directory Nautilus somewhere in your /home/user directory.
2.  Change to the working folder; open a gnome-terminal, and issue the command:  sudo apt-get source nautilus
3.  Grab all the dependencies needed to rebuild Nautilus.  Issue this command:  sudo apt-get build-dep nautilus
4.  Apply rgba patches to the source directory or make other changes as you desire.  Obviously only YOU know what you want to do and it's up to you to figure out specifically how to do it for the particular package you're rebuilding.
5.  Rebuild a new deb for installation.  Change to the source directory and issue the command:  sudo debuild -us -uc 
6.  Now if you look in the parent directory you should find a brand new, recompiled .DEB file ready for installation.
7.  Install the new DEB file by changing to the parent directory and issueing the command:  sudo dpkg -i *.deb
8.  To ensure Apt (or Synaptic) doesn't "upgrade" your custom deb with the stock version available in the repositories, you can PIN the package in /etc/apt/preferences file.  Pinning the packages in the preferences file ensures that both Apt AND Synaptic respect your preferences.  Using Synaptic's GUI pinning interface only affects Synaptic and not Apt at the command line.  Use Gedit to open this file as root:  sudo gedit /etc/apt/preferences.  Copy the following lines into this file (modify for your package name).  In the case of Nautilus, there are three files to be pinned as three DEBs were created:

Package: nautilus
Pin: version 2.26.2-0ubuntu1*
Pin-Priority: 1001

Package: nautilus-data
Pin: version 2.26.2-0ubuntu1*
Pin-Priority: 1001

Package: nautilus-dbg
Pin: version 2.26.2-0ubuntu1*
Pin-Priority: 1001

The Pin-Priority of 1001 ensures that Apt NEVER upgrades your Debs with another version.

Good luck!  :p

---

