---
title: "Change Feisty Main Menu icon?"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by seanmcgpa on 2007-05-10
Anyone know how to change the Main menu icon in Feisty?

I have googled a few (seemingly older) sites with solutions ranging from changing the distributor icon, or making changes to the gnome conf.  That Ubuntu icon is persistent, it doesn't want to leave ...

Any hints?  Thanks so much.

Sean

---

### Post by kpolice on 2007-05-10
There should be a thread somewhere in this forum, I don't remember where though but it was long. First delete your icon cache and try again.

---

### Post by tajmox on 2007-05-18
The icon is located at /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

simply change this png out with another 48x48 png file and then restart panel

If that doesn't work - do what Kalel said on this page:
[http://ubuntuforums.org/showthread.php?t=351296&page=2](http://ubuntuforums.org/showthread.php?t=351296&page=2)

---

### Post by Izobalax on 2007-05-18
It all depends on what icon theme you're using. 

If you're using an icon theme ***other*** than the ones pre-existing on your system, you can look in the .icons directory folder in your home. Have a look in the icon theme folder you're using and you should find the "distributor-logo" file. Simply replace it with the one you want and then link your icons to root.

If you're using a standard icon theme, or the icon theme you're using uses the standard "distributor-logo" file, then find that, mentioned above, and replace it there. 

Don't forget to link your icons to root and restart X.

Don't forget the icon you want should ideally 48x48 with transparency.

I'll post more in detail when I get home. :grin:

/izo

---

### Post by mrgnash on 2007-06-05
Simply does not work.

---

### Post by DalaiDakkar on 2007-06-17
This give me headache a time ago, the answer is here:

2. run gconf-editor
3. navigate to /app/panel/objects

find a object_x with the "object_type=menu-object".

(my main menu is "object_8")

4. tick up "use_custom_icon"
5. change "custom_icon" value to the image path.

source:
[http://www.gnome-look.org/content/show.php?content=42926](http://www.gnome-look.org/content/show.php?content=42926)

Cheers!

---

### Post by deepclutch on 2007-06-22
^^ this doesnt work.any

---

### Post by deepclutch on 2007-06-30
> **deepclutch said:**
> ^^ this doesnt work.any
No,it is working.am wrong :D

---

### Post by Gerontius on 2007-08-08
doesn't work for me :confused:

---

### Post by monkeylin on 2007-08-09
> **seanmcgpa said:**
> Anyone know how to change the Main menu icon in Feisty?

I have googled a few (seemingly older) sites with solutions ranging from changing the distributor icon, or making changes to the gnome conf.  That Ubuntu icon is persistent, it doesn't want to leave ...

Any hints?  Thanks so much.

Sean

Go [here]("http://ubuntuforums.org/showthread.php?t=505669&page=2"), and give it a shot,


LIn.

---

