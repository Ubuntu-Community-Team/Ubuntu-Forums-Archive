---
title: "Sorry for this super simple question....but:"
date: 2009-03-09
forum: General Help
---

### Post by daisyfoofpoof on 2009-03-09
What's the path to the trash bin in intrepid?  I wanna create a desktop shortcut to it, but dragging it from my panel doesn't work.

---

### Post by spcwingo on 2009-03-09
I'm almost certain that it's the same as Hardy (what I'm currently running).  That path would be /home/user_name/.local/share/Trash/  Of course replace user_name with your user name.  ;)

---

### Post by jellybaby on 2009-03-09
Hi,

start a terminal and type "gconf-editor";
choose apps->nautilus->desktop.
There are checkboxes for various options.

Enjoy!

---

### Post by joey-elijah on 2009-03-09
OR to add it properly - 

alt+f2 then run gconf-editor.

go to

apps > nautilus > desktop 

on the right side look for the entry called: -

**trash_icon_visible**

check the box and that's it.

---

### Post by deconectat on 2009-03-09
right click on your desktop -> create launcher... ->
Type: Location
Name: Trash
Location: trash:///

That's it! :)

LE: It seems I don't type fast enough...

---

### Post by speedwell68 on 2009-03-09
I was going to say you can do this with Ubuntu Tweak, it is under the 'Desktop' tab.  You can make lots of other subtle changes easily with Ubuntu Tweak.  You can download the latest Ubuntu Tweak from GetDeb.com.  Or there is a version in the repositories, IIRC.

---

### Post by nu2this on 2009-04-19
This isn't a silly question. This is so common maybe a sticky should be made of it, or the devs might consider making a desktop trash bin default.

---

