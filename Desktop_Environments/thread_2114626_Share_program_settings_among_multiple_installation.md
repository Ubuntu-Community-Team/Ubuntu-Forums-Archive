---
title: "Share program settings among multiple installations"
date: 2013-02-10
forum: Desktop Environments
---

### Post by papalagi on 2013-02-10
Hi everybody,

since i use a few computers for work, i'd like to have the program settings shared between the different ubuntu installation

ie: in the ~/.gimp-2.8 directory are stored my settings for Gimp, is there a way to make Gimp read the settings from a directory in Ubuntu One or Dropbox?

maybe creating links?

it seems to me like a very simple idea, but googling it i couldn't find any answer

cheers!

---

### Post by SeijiSensei on 2013-02-10
You could designate one computer as the "server" and export its /home with NFS.  Then you would mount the exported share as /home on each machine you work with.

---

### Post by papalagi on 2013-02-10
> **SeijiSensei said:**
> You could designate one computer as the "server" and export its /home with NFS.  Then you would mount the exported share as /home on each machine you work with.

yes, this is true, but i don't want to sync the whole /home, and since the computers i use are not part of the same network, i need a service that works over the web (and simple!)

---

### Post by LewisTM on 2013-02-10
Just move your .gimp-2.8 directory to Dropbox, create a link there and move it back to your home directory. Make sure the link is also called .gimp-2.8. That way you have a symlink in your home and the original in your Dropbox folder. 

Rinse and repeat as desired. This works perfectly for games and applications. 

Cheers!

---

### Post by papalagi on 2013-02-11
> **LewisTM said:**
> Just move your .gimp-2.8 directory to Dropbox, create a link there and move it back to your home directory. Make sure the link is also called .gimp-2.8. That way you have a symlink in your home and the original in your Dropbox folder. 

Rinse and repeat as desired. This works perfectly for games and applications. 

Cheers!

Thank you LewisTM, i'm going this way!

---

### Post by stinkeye on 2013-02-11
Adding to **LewisTM's** solution.
Make sure you have a home backup or at least a gimp backup first.

I'm using ubuntu one here. Just substitute ubuntu one with dropbox.

Easiest way to link your config is to open 2 nautilus windows and drag and 
drop your **.gimp-2.8** folder to the ubuntu one folder.
Then drag and drop **.gimp-2.8** using the middle button back to your home folder
and choose "Link Here" after mouse release.

PS. I also create a file called **show_hidden **in my ubuntu one folder just to remind myself
that I have hidden config files.

---

### Post by papalagi on 2013-02-11
> **stinkeye said:**
> 
Easiest way to link your config is to open 2 nautilus windows and drag and 
drop your **.gimp-2.8** folder to the ubuntu one folder.
Then drag and drop **.gimp-2.8** using the middle button back to your home folder
and choose "Link Here" after mouse release.

Thank you stinkeye, the system is Very good, marking as SOLVED

---

### Post by stinkeye on 2013-02-11
> **papalagi said:**
> Thank you stinkeye, the system is Very good, marking as SOLVED
Oh, good.
Just make sure you do a regular backup of your home directory and 
include your Ubuntu one or dropbox folder in the backup because that's where
your gimp config now resides.

---

