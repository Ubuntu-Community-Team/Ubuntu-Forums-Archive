---
title: "Generated Cairo Dock?"
date: 2008-12-31
forum: General Help
---

### Post by J03y on 2008-12-31
Hello, I have Intrepid amd64 but cairo dock doesn't work. I tried installing it from the repositories and the "deb" package. I heard from someone saying that the repositories where empty and didn't work. Anyways, yesterday I happened to ran into a thread here in the forums and the thread starter said that he generated his "full working cairo dock" and attached a link of his cairo dock in the thread but I couldn't download it since I was doing other things. Earlier I was trying to find the thread but I couldn't find it so if anyone knows of which thread I'm talking about could you please put a link of the thread or maybe a working guide that helps me on how to install cairo dock and get it to work properly. It would be very appreciated. Thank you :)

---

### Post by SonnHalter on 2008-12-31
I had your problem. i used this :

> **]Please first enable the universe repository:

Open System &#8594 said:**
> 
enable "Community Maintained open source software (universe)"
Close and confirm the repository reload.

Then open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:

sudo aptitude update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo aptitude install cairo-dock

give your user password when requested, you don't see nothing when you type it, then press enter.



Then you must add the cairo-dock to start when you login, so go to menu:

System &#8594; Preferences &#8594; Sessions

Press to "+ Add" button and add "cairo-dock"

Name: Cairo-dock
Command : /usr/bin/cairo-dock
Comment: nothing or what you want

Save

Then thick the check box of just added Cairo-dock to make it start when you login...

then log out an login.


make sure your make autohide off.


good luck :P

---

### Post by fabounet on 2009-01-01
this method will perform a dist-upgrade !
moreover, the version of cairo-dock present in the Ubuntu's repository is very outdated, so I would recommend to avoid it.
if you have a .deb on your hard disk, just double click on it, and install it with GDebi

---

### Post by loomsen on 2009-01-02
You can try if my pkges work for you... Link in my sig.

---

