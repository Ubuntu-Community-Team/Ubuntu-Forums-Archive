---
title: "KDE 3.3.5: Edgy: File associations"
date: 2006-11-01
forum: Desktop Environments
---

### Post by JeffElkins on 2006-11-01
Howdy,

I'm having a recurring problem with KDE remembering file associations. For instance, I prefer xmms for mp3s over amarock. When I choose open with other, then remember, KDE does remember to use xmms, it defaults back to amarock. Is there a config file that I can edit to force my chosen app to be used?

---

### Post by sedd on 2006-11-01
If memory serves (I'm using Gnome at the moment) you can right click on a file, hit Properties, then click on the button with the file icon (Just to the left of the file name in the Properties dialog.) This will bring up another dialog (the mime-type editor) which you can use to adjust the priority of the applications that open this type of file. Move xmms up in the list, to the top, and it will be the default. If memory serves..

---

### Post by JeffElkins on 2006-11-01
Hey, thanks for the reply :)

Unfortunately, that's not working for me. I don't see any tab or clickable space that allows me to change the mime type for a desktop item. However, I was able to call kcontrol from the command line and change file associations there. Doing it that way, they seem to stick.

KDE bug, not (k)ubuntu! Thanks again for the reply.

Jeff

---

