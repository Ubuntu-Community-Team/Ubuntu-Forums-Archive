---
title: "Change document paths"
date: 2011-01-16
forum: Desktop Environments
---

### Post by Depravitus on 2011-01-16
Hello everyone,

I am wondering how to change the default paths for Pictures, Documents, Music, etc to different paths (on a different partition within the same HDD). What's the cleanest way of going about this?

Thank you in advance,

- Depravitus

---

### Post by rvm1989 on 2011-01-17
hi, 
well assuming it that partition is already mounted, say in /media/stuff

you can simply move the folders like Pictures to /media/stuff/
and create a symbolic link to those "new" directories
following teminal commando's will do the trick for your Pictures.
and assuming that my account name is MY_USER_NAME

```

mv /home/MY_USER_NAME/Pictures /media/stuff/
ln -s /media/stuff/Pictures /home/MY_USER_NAME/Pictures

```

---

### Post by e_torano on 2011-01-17
If you've got Ubuntu Tweak installed, you can use that to easily change them.

---

### Post by Krytarik on 2011-01-17
I also recommend doing this with the tool "Ubuntu Tweak", altough there is definetely another, more non-GUI way, to also achieve it. It offers to set many other hidden options also.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

To install it via PPA, and thus include it in the update process:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```After the installation you will find it in "Applications -> System Tools".

---

### Post by Depravitus on 2011-01-17
Whoops! I have Ubuntu Tweak, but never went past the login screen editor portion of it (which seems to not function properly on 'Meerkat').

Thanks for bringing that to my attention guys. :) 

- Depravitus

---

### Post by Depravitus on 2011-01-17
Actually the change doesn't seem to be working. 

Perhaps I need to auto-mount the external partition somehow?

*Edit* Nevermind, I figured it out. I had to add the new paths to Ubuntu's directory list before setting them as defaults.

- Depravitus

---

