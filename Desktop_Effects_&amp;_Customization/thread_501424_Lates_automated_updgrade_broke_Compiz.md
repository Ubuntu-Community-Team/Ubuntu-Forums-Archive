---
title: "Lates automated updgrade broke Compiz ??"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by Kari_Juhani on 2007-07-15
installed Compiz Fusion and it worked well...  today i took an automated update and after reboot Compiz wont work...  and Panel is over application...

When i run "compiz --replace"  get this :

kari@amd64-desktop:~$ compiz --replace
Checking for Xgl: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070709 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5842): Wnck-WARNING **: Unhandled action type (nil)

...... and so on.. same error forever..


Anyone ?
Kari

---

### Post by hyperair on 2007-07-15
Ok the problem here isn't the gtk-window-decorator problem, it's the version mismatch problem. Seeing that you've encountered this problem I take it that you're using Trevino's repository, as vorian's repository never had this problem for me. Anyway, just try adding the vorian repository..
```

deb http://debs.vorian.org feisty extras
deb-src http://debs.vorian.org feisty extras

```
to your /etc/apt/sources.list file, or you can add it in System->Administration->Software Sources under third party repositories. Then update all the packages on your system.
```

sudo apt-get update
sudo apt-get upgrade

```

Once you've gotten the update done, reload compiz if it's running:
```
compiz --replace
```

At least, this is what recovered my system. I don't know if it'll work on yours.

---

