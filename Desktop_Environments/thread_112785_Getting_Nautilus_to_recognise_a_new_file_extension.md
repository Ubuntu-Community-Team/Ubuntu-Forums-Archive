---
title: "Getting Nautilus to recognise a new file extension"
date: 2006-01-05
forum: Desktop Environments
---

### Post by brick on 2006-01-05
Hi

I'm using a CAD program under Breezy, and would like Nautilus to recognise the filetype. Currently, Nautilus thinks it is a gzip file.  The files I need to recognise have the extention .cfx.  I tried making the file

~/.local/share/mime/packages/Override.xml with

```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info
xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="application/x-extension-cfx">
<comment>CADFEKO Model file</comment>
<glob pattern="*.cfx"/>
</mime-type>

</mime-info>

```

When I do this, Nautilus still thinks .cfx files are gzip archives! What do I need to change?

Thanks 
Neilen

---

### Post by psychicdragon on 2006-01-05
I think this is what you're looking for:```
update-mime-database /home/you/.local/share/mime
```

---

### Post by brick on 2006-01-09
Hi

update-mime-database did the trick, thanks!

---

