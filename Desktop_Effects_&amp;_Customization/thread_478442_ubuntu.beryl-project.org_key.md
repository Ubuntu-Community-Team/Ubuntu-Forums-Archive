---
title: "ubuntu.beryl-project.org key"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by sheds on 2007-06-19
Hey there.

I've been trying to install beryl on a feisty fawn beryl installation with the 2.6.20-16 kernel using gnome. Everything looks very easy, but i ran into an unexpected problem. There is a part in the manual that says i should insert some line in /etc/apt/souces.list and then download a key for it. When i type "wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -" i get the following error:

--09:08:22--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 80.77.247.17, 82.140.42.54, 88.191.250.18, ...
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:08:23 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

Is there a way to look for the key somewhere else or is it no longer available and i should install beryl some other way?

Thanks in advance.

---

### Post by TobyKY76 on 2007-06-19
When I installed Beryl, I used Synaptic Package Manager.  I believe you have to have the universe sources marked.  Just scroll down to Beryl and select Emerald Themes and install.

---

### Post by sheds on 2007-06-20
I am not familiar with synaptic. Usually i console everything down. Nevertheless, i checked that the universe thing was selected and installed all beryl-related things that i could find there listed.

That didn't do it though.

Bit more help here. Thanks in advance.

---

### Post by sheds on 2007-06-24
I've been trying to install beryl now several times. And every single time i get the same result.

Here's a summary brief:

1. glxinfo | grep direct yields direct rendering: Yes.

2. apt-get install beryl beryl-manager emerald-themes installs with no problems.

3. When starting up beryl-manager, gnome window manager is started by default.

4. When selecting beryl window manager, the desktop starts trying to change things but then returns to the gnome window maker.

Gathering a bit of info, i think that beryl has been installed all right, but something is preventing it from loading up right. I do get the red beryl-shaped icon when loading beryl-manager. But none of the functions are available yet.

---

### Post by sheds on 2007-06-29
Hey, i just noticed that despite de error message, there is something resembling a key in my home folder. It's titled 'root@lupine.me.uk.gpg'. Obviously it's not in the right place or it's not the right file, cause when doing the command to update, i get errors. Do i need to put it somewhere in specific for the update to find it and use it to download the files required to carry on with installing beryl?

Thanks for the help dudes.

---

### Post by FuturePilot on 2007-06-29
System>Administration>Software Sources
Then go the the Authentication tab and click Import Key File. Then find your key. Then close it.
You may have to do a ```
sudo apt-get update 
```afterwards
But Beryl is already in the Ubuntu repos.

---

### Post by sheds on 2007-06-29
I am just following the instructions there.

I didn't see that in the sources when i was looking for the beryl line. Weird thing is, i got it installed, but something is missing cause it won't load completely.

---

### Post by Mr Greencastle on 2007-06-29
If you are on an ATI card, you may have to go with installing Xgl,
Instructions here: [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

---

