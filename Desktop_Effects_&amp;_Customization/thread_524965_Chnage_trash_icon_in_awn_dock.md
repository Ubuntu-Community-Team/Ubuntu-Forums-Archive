---
title: "Chnage trash icon in awn dock"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by mike868y on 2007-08-13
HOw would i go about changing the trash icon in awn dock? I looked in usr/icons but the only icon themes that are their are the defualt ones.. where are my installed icons located? OR is there another way to change the icon

---

### Post by conradlyn on 2007-08-14
i have the same problem.

my system icon set was a leopard style,and only that trash icon in awn is a tango style one, anybody has any idea to solve it ?

also,can any body tell me how to make the normal nautilus-window's tool bar without words but only icons ?

---

### Post by ayoli on 2007-08-14
go in your icon theme directory:
```
cd ~/.icons/your_icon_theme_name/scalable/places
```
and make links to have the correct icons name for empty and full trash:
```
ln -s user-trash.png gnome-stock-trash.png
ln -s user-trash-full.png gnome-stock-trash-full.png
```
> 
also,can any body tell me how to make the normal nautilus-window's tool bar without words but only icons ?
go to menu System > Preferences > Menu and toolbars and choose icons only in the dropdown menu.

---

### Post by FuturePilot on 2007-08-14
It's dependent on your icon theme that you have set.

---

### Post by conradlyn on 2007-08-15
> **FuturePilot said:**
> It's dependent on your icon theme that you have set.

it does not.

i am setting my system icon theme a leopard one,.you know, with this ,the trash bin should be a shining metal bin,but in awn,it's a comic tango one,what the hell ?

---

### Post by misfitpierce on 2007-08-15
can always put tango style one in icons folder just outside that folder and name leopard style one to same name and put in tango area or w/e icon is loading and restart X server CTRL+ALT+BCKSPC then see if it loads that way. I have forced mouse icons that way. lol :)

---

### Post by conradlyn on 2007-08-15
> **misfitpierce said:**
> can always put tango style one in icons folder just outside that folder and name leopard style one to same name and put in tango area or w/e icon is loading and restart X server CTRL+ALT+BCKSPC then see if it loads that way. I have forced mouse icons that way. lol :)

problem is,in my .icons folder,i can only find a folder of the cursors now used, no other folder of icons exists, that confused me a lot, am i wrong with the path ? it is in /root/.icons/  (i login as root):confused:

---

### Post by ayoli on 2007-08-15
> **conradlyn said:**
> problem is,in my .icons folder,i can only find a folder of the cursors now used, no other folder of icons exists, that confused me a lot, am i wrong with the path ? it is in /root/.icons/  (i login as root):confused:

if you use system icons they should be located under /usr/share/icons

btw, a note: log in as root is a bad idea IMO

---

### Post by conradlyn on 2007-08-15
> **ayoli said:**
> if you use system icons they should be located under /usr/share/icons

btw, a note: log in as root is a bad idea IMO

why log in as root is not good ? everyone seems to be saying the same thing.

but i still can't see any disatvanges, more over, i gain many conviniences, such as no need to type sudo in terminal and instantly browse any file  i want.

maybe those conviniences cost much when it come to be wrong and may even be un-rescuable,right ? please do tell me why and in that i will keep my system better. 

thanks.

---

### Post by ayoli on 2007-08-15
> **conradlyn said:**
> why log in as root is not good ? everyone seems to be saying the same thing.

but i still can't see any disatvanges, more over, i gain many conviniences, such as no need to type sudo in terminal and instantly browse any file  i want.

maybe those conviniences cost much when it come to be wrong and may even be un-rescuable,right ? please do tell me why and in that i will keep my system better. 

thanks.
we're goin a bit off topic but you may want to read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by petit.padavoine on 2007-08-15
> 
```
ln -s user-trash.png gnome-stock-trash.png
ln -s user-trash-full.png gnome-stock-trash-full.png
```

Sweet, worked perfectly! The gnome naming conventions are kinda annoying though, everytime I want to replace a particular icon, I never know where to look... So when different apps use different naming conventions, urgh!

---

### Post by ayoli on 2007-08-15
> **petit.padavoine said:**
> Sweet, worked perfectly! The gnome naming conventions are kinda annoying though, everytime I want to replace a particular icon, I never know where to look... So when different apps use different naming conventions, urgh!

I think the most complete icon theme with the right names are gnome and tango (located here: /usr/share/icons/Tango/  /usr/share/icons/gnome/ ).

---

### Post by jhernandez1270 on 2007-08-15
Conradlyn,

I got this from Sebatian Porta and it worked for me. Just replace 'user-trash-empty.png' and 'user-trash-full.png with the names of the icons you want.

 some themes don't have the icons for "gnome-stock-trash.png" and "gnome-stock-trash-full.png". That's why Awn it's displaying the wrong icon.
To solve this, you have to create symbolic links for those icons.
Go to the theme directory and on a terminal write:

ln -s user-trash-empty.png gnome-stock-trash.png

ln -s user-trash-full.png gnome-stock-trash-full.png

These file names are for the OSX theme. If you have a different theme you have to replace "user-trash-empty.png" and "user-trash-full.png" for the icons of your choice.

---

### Post by conradlyn on 2007-08-16
> **jhernandez1270 said:**
> Conradlyn,

I got this from Sebatian Porta and it worked for me. Just replace 'user-trash-empty.png' and 'user-trash-full.png with the names of the icons you want.

 some themes don't have the icons for "gnome-stock-trash.png" and "gnome-stock-trash-full.png". That's why Awn it's displaying the wrong icon.
To solve this, you have to create symbolic links for those icons.
Go to the theme directory and on a terminal write:

ln -s user-trash-empty.png gnome-stock-trash.png

ln -s user-trash-full.png gnome-stock-trash-full.png

These file names are for the OSX theme. If you have a different theme you have to replace "user-trash-empty.png" and "user-trash-full.png" for the icons of your choice.

thanks, man,really.

i have searched some folders to find the tango icons. but it seems  i can only find the empty icon,no full one.

further more, these icons are all svg format not png ones. maybe i will search later and deeper to make a change.(temporarily under windows ...:()

---

