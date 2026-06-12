---
title: "gdm doesn't show my photo at face browser"
date: 2008-09-15
forum: Desktop Environments
---

### Post by abacate_vw on 2008-09-15
I'm using hardy heron 8.04.1 32-bit.

I tried to changed my photo using /usr/bin/gdmphotosetup and system -> preferences -> about me. Both updated the .face file at my home folder.

But I'm still getting nobody.png at logon screen.

---

### Post by Pro-reason on 2008-09-15
Do this:

```

ln -s ~/.face ~/.face.icon
```

I don't know why it's necessary.

---

### Post by abacate_vw on 2008-09-16
Thank you for your reply but it didn't work out.

---

### Post by BrainwreckedTech on 2009-05-27
This will give you all the details on how the face browser works: [http://projects.gnome.org/gdm/docs/2.14/overview.html#facebrowser](http://projects.gnome.org/gdm/docs/2.14/overview.html#facebrowser)

I think the default MaxIconWidth/MaxIconHeight in Ubuntu is 64.  But if you used gdmphotosetup or the About Me applet, that should have been taken care of.

Not sure of the valid file types, but I know for sure JPG and PNG works.  Again, gdmphotosetup and About Me should take care of this.

The only thing left I can think of that would stop you is that GDM will refuse to load images over NIS and NFS.  If your /home directory is mounted remotely, a simple link like this will trick GDM into thinking the files are local:

```
ln -s /home/[user]/.face /usr/share/pixmaps/faces/[user].[ext]
```

---

