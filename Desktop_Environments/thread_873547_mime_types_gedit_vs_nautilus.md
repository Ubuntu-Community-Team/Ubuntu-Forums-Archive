---
title: "mime types: gedit vs nautilus"
date: 2008-07-29
forum: Desktop Environments
---

### Post by siman on 2008-07-29
i have a rather fresh ubuntu 8.04 install. i did not mess with mimetypes, but have this problem:

when i do gnomevfs-info myjavascriptfile.js it get:

MIME type         : application/javascript

also in nautilus in the type column i correctly get

Javascript Program

However, when i open that file in gedit and hover over the file-tab it says "Mime-type: C source code" :(

this bothers me, because syntax highlighting does not switch on correctly for obvious reasons.

///

on my laptop i have the same problem, even after i added a custom mime-type (Override.xml in home-dir) which i called "application/helmascript". this mime-type gets recognized in nautilus and with the gnomevfs-info BUT AGAIN not in gedit.

any ideas? i must be doing smth very wrong :(

---

### Post by forger on 2008-07-29
rather fresh install? did you keep your home "/home" partition and formatted just the root "/" partition? some mimetypes might have been saved

Anyway, this might help, open up your terminal and execute the following commands:
```
rm -rf $HOME/.local/share/mime/*
sudo update-mime-database /usr/share/mime/
gtk-update-icon-cache /usr/share/icons/Human/
sudo apt-get install --reinstall libgtksourceview2.0-0 python-gtksourceview2 gedit gedit-common

```
Once the above is done, log out and log back in

---

### Post by siman on 2008-07-29
thanks for your time. i did all that:

```
rm -rf $HOME/.local/share/mime/*
sudo update-mime-database /usr/share/mime/
gtk-update-icon-cache /usr/share/icons/Human/
sudo apt-get install --reinstall libgtksourceview2.0-0 python-gtksourceview2 gedit gedit-common

```

now nautilus and gedit agree, that my javascript files are "c source code".

I will now try redo this. basically create Overrides.xml in ~/.local/... and doint update-mime-database on that folder.

update: i filled in the xml via gedit and did update mime database. after that, nautilus recognizes my JS files. but gedit does not care, it's still c source. i will try restart *sigh*

```

<?xml version='1.0'?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
 <mime-type type="application/javascript">
    <alias type="application/x-javascript"/>
    <alias type="text/javascript"/>
    <sub-class-of type="text/plain"/>
    <comment>JavaScript Helma program</comment>
    <glob pattern="*.macros.js"/>
    <glob pattern="*.actions.js"/>
    <glob pattern="*.js"/>
  </mime-type>
</mime-info>

```

11:41:45 oberhams@oberhams-desktop:~$ gedit /home/oberhams/.local/share/mime/packages/Overrides.xml 
11:42:07 oberhams@oberhams-desktop:~$ update-mime-database ~/.local/share/mime/

---

### Post by forger on 2008-07-29
you could post a bug about it :)
[https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

found one:[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/64869](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/64869)

---

### Post by siman on 2008-07-29
thanks, that fixed it.

the "patch" that was provided was specifically changing the javascript mime-entry. they added
```

<magic priority="30">
      <match value="/*" type="string" offset="0"/>
      <match value="//" type="string" offset="0"/>
    </magic>

```

now gedit automagically uses JS syntax highlighting on all JS files and even the mime-type that is shown when i hover over the file-tab in gedit is correct.

---

