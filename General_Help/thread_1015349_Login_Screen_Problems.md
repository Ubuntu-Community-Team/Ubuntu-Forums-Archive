---
title: "Login Screen Problems"
date: 2008-12-18
forum: General Help
---

### Post by dustinadamsmith on 2008-12-18
I am installing Ubuntu 8.10 on a Dell Inspiron 1520 and up till a moment ago everything was working fine. Then I thought I would try to pretty tings up a bit and added a new login screen theme. Now whenever I try to start up the machine the login screen never appears. It just gives me a light orange background and the mouse pointer. Could someone please tell me how to get around this?

---

### Post by 1packer on 2008-12-19
I've never had the problem you say you're having, so I just want to get an idea of what you did to add a login screen.
I am going to assume you can get into machine since you posted this? If so, have you tried using one of the defaults and has it worked?
If it works it probably is a problem with adding them. My normal approach is to download a GDM file from Gnome-look, which all come as .tar.gz, then I just use the install button under the local tab of the Login Window(System-Administration-Login Window). This uses the .tar.gz file, so they don't need to be extracted. I have always had the image display, although they aren't selected automatically.

Let me know how things go, I most likely won't be able to do much more advanced then this, but someone else should see it as well.

---

### Post by ubunt22rock on 2008-12-20
I have exactly the same problem. I use 8.04. And I CANNOT get into the system. its obvious anyone cant get in if u cant get the login screen

---

### Post by shalomhk on 2008-12-20
[FONT="Arial"][/FONT]
I have the exact problem you're talking about. What happened was 

a) you installed a corrupted GDM login screen
b) you forgot to select a GDM screen by actually clicking the radar button next to it
c) you deleted/uninstalled all default GDM screens without replacing them

What to do about it? :confused:

I have no idea, that's why I'm here :P

---

### Post by ubunt22rock on 2008-12-20
I guess its a corrupt login screen in my case. buti dunno what to do about it. I am not sure it i should edit something in the .gnome2 folder in my home. I request some pro to come post

---

### Post by 1packer on 2008-12-22
Have you tried booting into recovery mode? That may load a different kernel that might let you in. Otherwise I think you will have to use a live cd to try and recover it, or reinstall. That's as far as my knowledge goes, hopefully you don't have to reformat though.

---

