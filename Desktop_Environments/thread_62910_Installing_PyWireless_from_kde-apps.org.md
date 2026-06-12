---
title: "Installing PyWireless from kde-apps.org"
date: 2005-09-06
forum: Desktop Environments
---

### Post by jhuff on 2005-09-06
I would like to install PyWireless from kde-apps.org.  I need help on learning how to manually install programs not in Synaptic.  Can anyone suggest the best way to go about this?

---

### Post by daller on 2005-09-19
If they are .deb-files, simply install kpackage, and click the deb!

---

### Post by Freddy on 2005-09-19
If you can't find any .deb packs there are 2 choices, either try to convert a .rpm pack with a little help from alien, fire up your console and move to the folder with the .rpm file, write "sudo alien filename.rpm" after that if everything went well you should have a .deb file there to, Now write dpkg -i filename (-i for install) this could work and sometimes it even does :).

The other slighty more complex way to do it is to compile the app yourself, just download the source, untar it in a folder and you should find some kind of readme file inside, but beware of the dependency hell :)  /// Freddan

---

### Post by jhuff on 2005-09-20
Were is a good place to learn about compiling programs?  The only file available is a tar file so I guess it will need to be compiled.  There must be some way to deal with the dependency issues.

---

