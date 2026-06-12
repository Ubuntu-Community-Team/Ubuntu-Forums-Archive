---
title: "OS X fonts not seen by system"
date: 2007-12-24
forum: Desktop Environments
---

### Post by ubukool on 2007-12-24
Hi there,

I've been trying to make Gutsy look more like OSX and have downloaded and installed some OSX fonts (aquaBase, Lucida Grande and others) in the fonts folder as root by typing fonts:/// into the location bar in Nautilus and dragging the fonts into the folder.  I've also run 

sudo fc-cache -f -v

and there doesn't seem to be any problem with compiling a new fonts list, but when I restarted the system, the fonts aren't there and they don't show up in Openoffice either.  I've noticed that if I look at the fonts folder as root, the fonts are there, but when I look as a normal user, they don't show up.

Does anyone know what's going on and how I can get the system to see and use the fonts?

Thanks in advance for any help :)

---

### Post by ubukool on 2007-12-24
well, I always seem to be the one answering my own questions!

I've found a solution by simply putting the fonts into the '.font' folder in my /home folder.

Thank you, I'm sure you were going to reply....:

---

### Post by jongkind on 2007-12-24
> **ubukool said:**
> Thank you, I'm sure you were going to reply....:
I would have replied something different. Are you sure your solution works? I think that it must be .fonts instead of .font

---

### Post by ubukool on 2007-12-24
Hi jongkind,

Yes, they are in '.fonts', you're right  I don't know why I can't put them in the usr/share folder and have them work.  I don't suppose it makes any difference though?  Any thoughts?

Thanks for replying :)

---

### Post by jongkind on 2007-12-24
Make sure that the both the owner and the group of these fonts must be root. Others must have read access. So e.g.:

sudo mkdir /usr/share/fonts/truetype/osx-fonts
mv /where_ever_you_downloaded_your_fonts/* /usr/share/fonts/truetype/osx-fonts/*
chown -R root /usr/share/fonts/truetype/osx-fonts
chgrp -R root /usr/share/fonts/truetype/osx-fonts
chmod -R 755 /usr/share/fonts/truetype/osx-fonts
sudo fc-cache -fv

---

