---
title: "Changing a white background to transparent in the GIMP"
date: 2006-09-10
forum: Desktop Environments
---

### Post by srunni on 2006-09-10
Hi,
Does anyone know how I can change a white background to transparent in the GIMP? I recently installed grsync, the GTK frontend for rsync, and I had to manually create an entry for it in the KMenu. When I had to add an icon for the item, I used [http://samba.anu.edu.au/rsync/newrsynclogo.jpg](http://samba.anu.edu.au/rsync/newrsynclogo.jpg) . The only problem is that that image has a white background, which looks really bad in the KMenu, as the rest of the icons have a transparent background. Could someone either explain to me how I can change a white background to transparent in the GIMP or modify the image I linked above and upload the corrected version here?

Thanks

---

### Post by Rondonjin on 2006-09-10
This is how it was explained to me:

Add an alpha channel, do an automatic select on the background color. Cut that selected color, save the whole thing as a gif, (indexed palette) or a png, (RGB mode)

Wayne

---

### Post by srunni on 2006-09-12
I'll try to figure out exactly what that means sometime ;)
Apparently all I had to do was shut down Kicker and restart it, and there happened to be a default icon for Grysnc, so I didn't need it in that particular case, but I've needed it before, so I'll be sure to see if I can get that to work.

---

