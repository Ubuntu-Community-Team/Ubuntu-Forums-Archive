---
title: "How to get permission to edit xorg.conf file"
date: 2005-11-16
forum: Desktop Environments
---

### Post by TeMa on 2005-11-16
I am a newbie and just installed Ubunto on my Toshiba tecra 8000.

Accordig to some replies on this forum, I need to modify the /etc/X11/xorg.conf file. unfortunately this is owned by the user root.

Does anybody know how I can get permission to edit and change this file?

I seem to get stuck with the sudo an su commands.

Any help would greatly be appreciated.

Thanks,

TeMa.:(

---

### Post by Kyral on 2005-11-16
Thats the way you are supposed to gain root, with sudo.

wiki.ubuntu.com/RootSudo

---

### Post by tagg3rx on 2005-11-16
use the following command

sudo gedit  /etc/X11/xorg.conf

It took me a little to figure that out as well

:KS Tagg3rX :KS

---

### Post by ivanhelguera on 2005-11-16
It is not unfortunate that you cannot edit this file at will - it affects the  the entire X environment, the "windows" of linux. Making changes to it could easily result in disabling the graphic, windows-like mode. 

Actually, you should make a backup of the original file BEFORE you edit: 

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

```

I imagine you tried 
```

sudo gedit /etc/X11/xorg.conf

``` 
You provide your password then
and CAREFULLY edit the file. 

This way you will have the original file in case something goes wrong, so that you can go like

```

sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf

```

to have it restored. 
If you are stuck with a text mode screen , go on with 
```

startx

```

many useful info is  available at [http://help.ubuntu.com/starterguide/C/faqguide-all.html]("http://help.ubuntu.com/starterguide/C/faqguide-all.html")
have fun

IH
PS what do you meand by 'getting atuck' with sudo? Did you get to the terminal?

---

### Post by TeMa on 2005-11-16
I was mixing up all kind of commands and had problems with the syntaxes.
I am now able to edit the file. I am beginning to get a feeling how things work.
Getting better every hour. Thanks very much to all who helped.

TeMa

---

### Post by ferentix on 2005-11-16
This is what I got stuck on trying to get my mouse working. Thank god I figured I had to sudo it or I would still be using keyboard shortcuts for the entirety of a GNOME session :)

Hope you enjoy Ubuntu TeMa!

---

