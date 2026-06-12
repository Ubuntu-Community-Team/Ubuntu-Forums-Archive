---
title: "Create DVD's"
date: 2005-02-20
forum: Desktop Environments
---

### Post by techn9ne on 2005-02-20
How can I take home movies from my hard drive and put them on a DVD disc that will be readable by DVD players?

---

### Post by Device on 2005-02-20
k3b helps you

---

### Post by techn9ne on 2005-02-20
k3b will burn a data cd but how do i convert the avi/mpg into dvd video format?

---

### Post by kassetra on 2005-02-20
[QUOTE=techn9ne]k3b will burn a data cd but how do i convert the avi/mpg into dvd video format?[/QUOTE]
 
 1. first you have to change your data into the "dvd video format" by using [qdvdauthor]("http://qdvdauthor.sourceforge.net/") (or the command line tools dvdauthor)
 Then you can burn it to dvd with k3b like this:
 
 1. Navigate the file system tree (left pane) to the directory that holds the DVD 			file structure created by QDVDAuthor. 
 2. Drag the VIDEO_TS directory from the top 			right pane to the "K3b data project" tree on the bottom pane.
 3. Save the config file in a location of 			your choosing, I put it in the same directory as the AUDIO_TS and VIDEO_TS 			directories. 
 4. When you're ready to burn, click the "Burn" icon and a dialog will 			pop up. 
 [color=Sienna]*Just make sure the "Simulate" checkbox is not checked.* [/color]
 5. Click this 			dialog's Burn button and wait for it to finish

---

