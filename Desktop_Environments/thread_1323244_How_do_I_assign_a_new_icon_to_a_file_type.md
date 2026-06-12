---
title: "How do I assign a new icon to a file type"
date: 2009-11-11
forum: Desktop Environments
---

### Post by Jimtuv on 2009-11-11
I have upgraded to Karmic 9.10 and noticed that my icons for blend file type is blank. That is for the Blender 3d modeling program. How do I reassign the icon for this type.

so far I tried 

```
sudo gedit /etc/mime.types
```

then added

```
model/blend                blend
```

and saved

to set up a new mime.type for blend

and put a model-blend.svg in the /usr/share/icons/gnome/scalable/mimetypes folder. didn't work.

any ideas?

---

### Post by Amix on 2009-11-11
Look at this
[http://ubuntuforums.org/showthread.php?t=302549](http://ubuntuforums.org/showthread.php?t=302549)
thanks

---

### Post by Jimtuv on 2009-11-12
> **Amix said:**
> Look at this
[http://ubuntuforums.org/showthread.php?t=302549](http://ubuntuforums.org/showthread.php?t=302549)
thanks

Thanks Amix that worked sort of. Here is what I did to fix this.

I downloaded assogiate using the software center

then I launched it (file type manager) and used the search to find blender.

I edited the blender file type and changed the default icon 

This did not work.

So then I added a new blend type set up exactly like the old one and chose the new icon.

model/blend

with the associations of

*.blend*
*.BLEND*
*.blender*

you need the following asterisk because blender adds a number after .blend to show older versions of a file.

now I quit and then went to a blend file and right clicked > properties and deleted the file associations.

Then I closed that out and right clicked > Open with other application and typed blender -w in as the command.

Now everything works great!

---

### Post by Amix on 2009-11-12
Congratulations!
Thanks ;)

---

