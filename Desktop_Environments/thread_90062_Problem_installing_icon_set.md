---
title: "Problem installing icon set"
date: 2005-11-14
forum: Desktop Environments
---

### Post by derbaschti on 2005-11-14
Hi,

I am trying to install the "Gentoo" icon set on my desktop. Following instructions in the Gnome artwork FAQ, I downloaded the tarball and extracted it to ~/.icons. I suppose the theme should now show up in the Gnome Theme Manager, but it doesn't. 

Any suggestions? 

Sebastian.

---

### Post by frodon on 2005-11-14
To install an icon theme, the easiest way is to drag and drop the tarball in the Gnome Theme Manager. You will receive an error message if the install failed.

---

### Post by derbaschti on 2005-11-14
[QUOTE=frodon]You will receive an error message if the install failed.[/QUOTE]

Unfortunately, this is exactly what happened...

---

### Post by frodon on 2005-11-14
hum, i think that if you really want this icon theme you should try to download it in another site. Sorry, no more ideas.
However you could create a thread in the ubuntu art talk section of the forum, there's some experts there !

---

### Post by derbaschti on 2005-11-14
Great idea! I didn't notice this section so far... :oops:

---

### Post by Indigo7 on 2007-07-11
Is there a way to install Icon themes so that they're available for all users? My son likes the one I'm using, but it seems silly to have to install for each user.

Cheers!

---

### Post by frodon on 2007-07-11
It is how it works, separate users with separate set of themes. However if you wish to quickly copy all the theme you have and make them available for your son's account then just copy the content of your .themes and .icons folders in the .themes and .icons folders of your son account.
Using command lines it would make something like that :
```
cp -r /home/your_username/.themes/* /home/your_son_username/.themes/
cp -r /home/your_username/.icons/* /home/your_son_username/.icons/
```And if you don't want to copy the files then maybe you can just make symbolic links.

---

### Post by Indigo7 on 2007-07-11
> **frodon said:**
> It is how it works, separate users with separate set of themes. However if you wish to quickly copy all the theme you have and make them available for your son's account then just copy the content of your .themes and .icons folders in the .themes and .icons folders of your son account.
Using command lines it would make something like that :
```
cp -r /home/your_username/.themes/* /home/your_son_username/.themes/
cp -r /home/your_username/.icons/* /home/your_son_username/.icons/
```And if you don't want to copy the files then maybe you can just make symbolic links.

Easy enough. Thanks!

---

