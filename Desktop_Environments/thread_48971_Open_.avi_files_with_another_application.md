---
title: "Open .avi files with another application?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by tubunu2005 on 2005-07-14
I would like to open .avi files with another application, VLC in particular.

So I chose an .avi file and tried to "Open with Other Application". In the application list, I wanted to choose VLC but I got the following error message:

"Could not add application"

(same problem with all other listed applications)

Tubunu

---

### Post by varunus on 2005-07-14
When you select VLC, you get the application add error?  When exactly?  Your post isn't completely clear...is it after you add VLC?  Or can you not select VLC?

Try right clicking the file, choosing properties, going to open with, and adding VLC there...does that work?

---

### Post by angkor on 2005-07-14
[QUOTE=varunus]Try right clicking the file, choosing properties, going to open with, and adding VLC there...does that work?[/QUOTE]

Same thing here, The error comes up after selecting vlc from that menu.

---

### Post by Caboto on 2005-07-14
I've got the same problem. VLC ("VLC for Gnome/GTK" to be exactly) does not work. That version uses the command wxvlc (or something similar).
Try the Open With Thingie and use the custom command "vlc". That should work...

---

### Post by angkor on 2005-07-14
Yup, works perfectly...

---

### Post by tubunu2005 on 2005-07-14
[QUOTE=Caboto]I've got the same problem. VLC ("VLC for Gnome/GTK" to be exactly) does not work. That version uses the command wxvlc (or something similar).
Try the Open With Thingie and use the custom command "vlc". That should work...[/QUOTE]
vlc doesn't work either I'm afraid.

Tubunu

---

### Post by angkor on 2005-07-14
Hmm, strange...I did get the same error as you got with the default vlc in the list. But if I use 'custom command' and then 'vlc' it works fine. Do you get the same error again?

---

### Post by Caboto on 2005-07-14
[QUOTE=tubunu2005]vlc doesn't work either I'm afraid.

Tubunu[/QUOTE]
You can start vlc by typing vlc in command line, or? Did you compiled it from source or got it via apt-get/synaptic?

---

