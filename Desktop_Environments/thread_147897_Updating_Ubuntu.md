---
title: "Updating Ubuntu"
date: 2006-03-21
forum: Desktop Environments
---

### Post by cobbweb on 2006-03-21
Hi, 
  I have a quick question about my new Ubuntu Desktop. Can I upgrade my OS version (i belive you can do this in debian) without having to re - install the whole OS on the system? Is this going to be avalable with Dapper? 

 Cobbweb

---

### Post by localzuk on 2006-03-21
Hi,

Yes you can. Simply edit the /etc/apt/sources.list to the newer version by changing all references of the old version to the new version (so if you want to update from breezy to dapper when it comes out, you change the every occurrance of 'breezy' to 'dapper') .

Then you simply run sudo apt-get update followed by sudo apt-get dist-upgrade and let it run the updates. Restart and voila... An upgraded OS.

---

### Post by cobbweb on 2006-03-21
man cant wait until dapper comes out .....:D :cool: \\:D/

---

### Post by klahjn on 2006-03-21
[QUOTE=localzuk]Hi,

Yes you can. Simply edit the /etc/apt/sources.list to the newer version by changing all references of the old version to the new version (so if you want to update from breezy to dapper when it comes out, you change the every occurrance of 'breezy' to 'dapper') .

Then you simply run sudo apt-get update followed by sudo apt-get dist-upgrade and let it run the updates. Restart and voila... An upgraded OS.[/QUOTE]


Awesome answer.....
From a console (terminal) you would like to type:     sudo gedit /etc/apt/sources.list
then replace "breezy" with "dapper".
I'm just restating it, no offense intended.

---

### Post by akiro.yamamoto on 2006-03-21
If you download the Dapper .iso file and burn the CD Gnome automatically detects
it and asks if you want to Perform an Upgrade or Run Package Manager (if you don't want a full upgrade).. 8)

---

### Post by localzuk on 2006-03-21
This sounds like an interesting feature - however it would only be of any use to people who haven't installed anything else would it not? As the updates for the non-cd based packages would have to be retrieved from the repositories anyway.

My guess would be that it would probably be quicker and easier to use the apt method... But then I do install a *lot* of extra stuff.

---

### Post by nocturn on 2006-03-21
[QUOTE=cobbweb]Hi, 
  I have a quick question about my new Ubuntu Desktop. Can I upgrade my OS version (i belive you can do this in debian) without having to re - install the whole OS on the system? Is this going to be avalable with Dapper? 

 Cobbweb[/QUOTE]

The plan is to push an update to update-manager in Breezy when Dapper releases.

It will notify you of the new release and give the option to upgrade from the GUI.

I hope they finish this in time.

---

