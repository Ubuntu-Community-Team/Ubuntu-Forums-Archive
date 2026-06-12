---
title: "E17 Users Read"
date: 2006-10-04
forum: Desktop Environments
---

### Post by blamecanada on 2006-10-04
How do I customize my user menus in e17? I know in e16 it involved editing the .menu files, but from what I gather e17 takes a new approach. Am i able to set up menus the way i want?

---

### Post by blamecanada on 2006-10-05
Bump

---

### Post by Feanor on 2006-10-05
Simply open configuration -> applications then you've on the left the available applications and on the right destination folders. Now you may want to add an application to your favourites applications (for example) so you must select "favorites" on the right, select the app on the left and click "add application". This way to custom menu, ibar, engage and whatelse you want.

PS: if on the left there's only the "Debian" folder, click on "sort application" and the apps currently available will appear. I don't know if this is a bug, but it looks strange to me.

Cheers

---

### Post by blamecanada on 2006-10-05
Thanks, Ill give that a shot, one question about engage though, whenever i run it i get a large black box around it, is this due to  the fact that i have a moving background?

EDIT How do i change the icon in the menu, from what i gather it has to deal with the eap file for each application? How would i go about editing that?

---

### Post by Feanor on 2006-10-06
.eap it's going to be replaced by .desktop so I suggest you to use this format. Anyway you can create/edit applications from the configuration -> applications menu. 

Engage shows a big black box also to me, and I tried with static edje (normal pictures are converted in .edje when you select them in the wallpapers settings) and it's the same. I think is an issue or a bug... I can't understand well your request on EDIT, sorry for my low English knowledge :neutral: but if you want to know how to add apps to engage, simply copy the .desktop file of the app in the direcorty ~/.e/e/application/bar/engage or try graphically with the same procedure you use to edit menus

---

