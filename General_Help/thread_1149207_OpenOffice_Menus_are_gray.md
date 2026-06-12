---
title: "OpenOffice Menus are gray"
date: 2009-05-05
forum: General Help
---

### Post by jdfoote on 2009-05-05
My OpenOffice applications seem to be opening with a different window manager. The menu items are a dark gray color. I can't figure out why it's doing it. Any ideas?

See screenshot at [http://www.flickr.com/photos/31764097@N00/3502786255/](http://www.flickr.com/photos/31764097@N00/3502786255/). Picasa does the same thing - is it possible the OOo is running in Wine for some reason?

---

### Post by lavinog on 2009-05-05
I think picassa uses wine to run.
what is the output of
```
whereis oowriter
```
if you run oowriter from the terminal does the same menu come up?

It does look like it is running in wine.
Is this jaunty?

---

### Post by jdfoote on 2009-05-06
Output from 
```
whereis oowriter
``` is
```
oowriter: /usr/bin/oowriter /usr/share/man/man1/oowriter.1.gz

```

Running it from the terminal gives me the same gray menus.

---

