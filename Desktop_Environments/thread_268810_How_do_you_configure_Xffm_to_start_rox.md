---
title: "How do you configure Xffm to start rox ?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Gzou on 2006-09-30
Hi everyone,

I've just upgraded my Xubuntu from Breezy to Dapper and find the change really sweet :) But i've got one or two problems that have shown up...

First thing that surprised me after the upgrade was that I had file icons for the files in my Home folder up on my desktop ! "Hey, that's cool" But when I come to double-click on a folder i get a popup window saying "Launch Error ! unable to launch name-of-folder, the associated application could not be found or executed." So I went into the File Manager Settings from the Xfce menu, and I don't see anything that lets me choose what application to launch as a File manager. Right now I've got Rox and I like it pretty much, so I was wondering in anyone knew what to do to make rox launch each time I click on one of the Folder icons.

Thanks In advance !

---

### Post by mac57 on 2006-09-30
I'm afraid that you are stuck with Thunar - I don't know of any way to change the association. So, go the other way. Start up Rox as part of your .xinitrc, specifying the --pinboard option and you will have good ol' rox desktop just as you know and love it.

---

