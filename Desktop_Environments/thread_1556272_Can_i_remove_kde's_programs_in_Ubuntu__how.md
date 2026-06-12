---
title: "Can i remove kde's programs in Ubuntu ? how ?"
date: 2010-08-19
forum: Desktop Environments
---

### Post by Vahids on 2010-08-19
I don't like KDE's program (like Amarok or Vlc or kaffein and any KDE's program) cus i think KDE's programs are mane argument to slow down speed of my ubuntu.

I'd rather a absolute gnome's environment without any KDE efficacious. 

I'd rather to remove all KDE's program from my source.list if possible.


Sorry for my Eng and Thanks.

---

### Post by nbkr on 2010-08-19
Removing it from the sources.list is not necessary and not possible. You don't specify applications on the sources.list, but repositories. Those repositories contain most of the software that can be installed. 

As I said, that _can be installed_. That doesn't mean all those software is installed.

If you want to remove an application you can use the command ```
sudo apt-get remove name_of_the_software
``` or the Software Center.

---

### Post by Vahids on 2010-08-19
> **nbkr said:**
> Removing it from the sources.list is not necessary and not possible. You don't specify applications on the sources.list, but repositories. Those repositories contain most of the software that can be installed. 

As I said, that _can be installed_. That doesn't mean all those software is installed.

If you want to remove an application you can use the command ```
sudo apt-get remove name_of_the_software
``` or the Software Center.
well ,
How do i know about programs, that be a KDE or GNOME ?

for example
"Mplaye or VLC or Gimp" Which one is Gnome and which one is KDE ? and how do you know ?

---

### Post by nbkr on 2010-08-19
MPlayer and VLC are neither part of the KDE Project nor do they use KDE libraries. Gimp makes use of the gtk-libs which are also used by Gnome. So that would make it a Gnome application - or at least a more "gnomish" application than the rest.

Figuring out if something is a KDE application isn't so easy. You will have to look at the dependencies to find out if the application needs anything KDE related.

---

### Post by oldos2er on 2010-08-19
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by AHoneybun on 2011-03-23
ok so the xubuntu worked for me but kubuntu installed with just KDE listed on the session list so I don't think it will work but I will try it, thanks.

EDIT: the xbuntu remove command removes all of it kubuntu and xubuntu packages too.

---

