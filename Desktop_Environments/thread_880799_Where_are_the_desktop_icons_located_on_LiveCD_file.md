---
title: "Where are the desktop icons located on LiveCD filesystem?"
date: 2008-08-05
forum: Desktop Environments
---

### Post by bravespear on 2008-08-05
This may be a dumb question, but where are the Desktop icons pulled from on a LiveCD?

I have created a custom LiveCD for my employer based on Kubuntu Hardy 8.04. I need to add some icons to the LiveCD desktop for users easy access to applications.

After running debootstrap to get the base system and installing the kernel, packages and kde-core, I look in the /home folder for the default Ubuntu user's folder to drop the icons in, but the /home folder is empty. After booting the livecd there is an Ubuntu home folder, so it has to get the info from somewhere, I just need to know where I can put these icon's in the filesystem so they will show up on /home/Ubuntu/Desktop when the LiveCD has finished loading.

Thanks!

---

### Post by Tim Sharitt on 2008-08-05
The reason you cannot find a user folder is because the live session user account is created when the live cd boots via a script in the initial ram disk which is the initrd.gz in the casper folder of the live cd.
The adduser script in the scripts folder of initrd handles the setup of the account. I suppose it would be possible to edit this script to either create the desktop icons, or (probably easier) link to a launcher placed elsewhere on the squashfs. I've never tried it myself so I don't know how well it would work.

---

### Post by bravespear on 2008-08-05
Thanks for the reply.  How about placing icons on the KDE menu? Or any other workarounds.  I'm approaching a deadline and would love to be able to just drop the icons somewhere, rather than having to create them.  Any other workaround ideas?

If not, do you have any idea how I would do what you are suggesting?

---

### Post by bravespear on 2008-08-05
I found out a way to do it.  

I created a folder called Desktop in /etc/skel/

```
mkdir /etc/skel/Desktop
```

I added my icons to the Desktop folder and it gets pulled in when the Users Desktop is created. 

Any mods can mark this as [SOLVED]

---

