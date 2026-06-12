---
title: "K3bSetup"
date: 2005-02-01
forum: Desktop Environments
---

### Post by indygreen on 2005-02-01
Hello all.

I've been trying to get K3b to work but I haven't had a lot of luck.  I read the post about Graveman but it doesn't look like it burns DVDs.  

I have a couple of config issues and I need to run K3bSetup to correct them.  Unfortunately, when I click on the K3bSetup button, nothing happens.  I can't seem to find an install for the K3bSetup either just in case I don't even have it installed.

If I'm not able to get this working, are there other DVD burning utilities out there that someone can recommend?

Thanks.

---

### Post by neilmc on 2005-02-02
k3bsetup should be in /usr/bin if you used apt-get or synaptic.

By default there isn't a launcher icon for it. Try typing k3bsetup in the terminal under system tools.

Also see my comment on k3bsetup here [http://ubuntuforums.org/showthread.php?t=13595](http://ubuntuforums.org/showthread.php?t=13595)

---

### Post by indygreen on 2005-02-03
Thanks for the info.  Unfortunately, k3bsetup doesn't seem to be installed on my machine and it's not available for download utilizing synaptic.

---

### Post by kleeman on 2005-02-03
That's wierd I looked in my k3b package and its there alright: /usr/bin/k3bsetup
Maybe its only in the latest backport packages I have installed.

---

### Post by shmonkey on 2005-02-03
kdesetup is part of kdebase, so make sure you have this installed

Regards

Shmonkey

---

### Post by Chrisb319 on 2005-02-04
when I try and set it up it says I have the wrong password when I don't

---

### Post by kleeman on 2005-02-04
Yeah I noticed that too. Must be that kde is screwed re passwords. Try launching k3bsetup from a root terminal (applications--> System Tools --> root terminal

---

### Post by jdodson on 2005-02-04
try running k3b as root.  i know this seems odd but give it a shot.

run it "gksudo k3b".

if you "sudo k3b" you will fsck up your .ICEauthority file.  

something was amiss with the k3b in warty, i hope it gets fixed in hoary.

---

### Post by Chrisb319 on 2005-02-04
[QUOTE=jdodson]try running k3b as root.  i know this seems odd but give it a shot.

run it "gksudo k3b".

if you "sudo k3b" you will fsck up your .ICEauthority file.  

something was amiss with the k3b in warty, i hope it gets fixed in hoary.[/QUOTE]

that did the trick.

---

### Post by neilmc on 2005-02-05
[QUOTE=jdodson]try running k3b as root.  i know this seems odd but give it a shot.

run it "gksudo k3b".

if you "sudo k3b" you will fsck up your .ICEauthority file.  

something was amiss with the k3b in warty, i hope it gets fixed in hoary.[/QUOTE]

It works perfectly in warty as a normal user. There is a trick though. You must first specify a password for the  root user. sudo passwd root

Once you do that run k3bsetup as a normal user and it will tell you that some of its components need root access and it will ask for the root password (not the user password that you sudo with). There is also a tick box for k3b to remember the password.

After that you can launch k3b as a normal user with no need for gksudo

---

### Post by depaul on 2005-02-07
[QUOTE=jdodson]try running k3b as root.  i know this seems odd but give it a shot.

run it "gksudo k3b".

if you "sudo k3b" you will fsck up your .ICEauthority file.  

something was amiss with the k3b in warty, i hope it gets fixed in hoary.[/QUOTE]
 And if you did mess up your ICEauthority (as i did), any clue how to fix it?

Re, nevermind, already found something on the forum.

---

### Post by mirtux on 2005-02-07
You can change again ownership of .ICEAuthority to the user of the directory in  which the file is located.
 
 Hope this helps,
 MC

---

