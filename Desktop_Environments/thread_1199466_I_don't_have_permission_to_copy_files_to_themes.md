---
title: "I don't have permission to copy files to themes?"
date: 2009-06-29
forum: Desktop Environments
---

### Post by Cydia on 2009-06-29
So I've downloaded the WASP 0.7.1 theme from Gnome-Look and I would like to install it. I'm following the instructions on the page and it says I need to copy the files into. var/share/themes put when I do it say's I don't have permission. So I view the permissions and it says the root and create, delete and access the files. I go to System>Administration>Users and Groups and I click myself and view properties>Advanced and set myself as the root "main group". I'm not sure if I'm doing it right but that makes sense to me but it still won't allow me to copy the files. 

I'm the only user on my NetBook.

---

### Post by sharkbite1414 on 2009-06-29
open a terminal and type:

```
sudo cp <WASP's file location> /var/share/themes
```

---

### Post by mdgrech on 2009-06-29
The files are owned by root, your an admin user but not the root thus you can't add/modify those directories.  You need to open nautilus (the file browser) as root.

Use this command:
sudo nautilus

Go ahead and copy over what you need.

---

### Post by Lorem Ipsum on 2009-06-30
Hi Cydia!

If the theme you are trying to install is this:

[http://gnome-look.org/content/show.php/Wasp?content=104167]("http://gnome-look.org/content/show.php/Wasp?content=104167")

...well, i'm the author of the theme :)

i don't know where you have read "var/share/themes", but the correct one is "/usr/share/themes/". 

Here is 4 simple steps to install Wasp (or likely any other theme):

[B]1) press Alt+F2 on you keyboard
2) a dialog should appear, in the entry field insert "gksu nautilus /usr/share/themes/" and press Enter
3) maybe you will be asked to insert your user password, provide it
4) a Nautilus window should appear in to the correct directory, now just copy "Wasp", "Wasp-Alt" and "Wasp-Hard" directory there[/B]

If you still having problem don't hesitate to ask :)

ciao!

---

### Post by Seq on 2009-06-30
As noted on the themes page, you can copy it to "~/.themes". Since this is in your home directory, you have write permissions to it. Also, it is easier to back up /home and ensure you have everything for when you upgrade or migrate to a new machine.

---

### Post by Cydia on 2009-06-30
Thank you everyone for your help, my HP Mini is running great with Ubuntu better than it would ever run Windows. Lorem Ipsum I bow to you for making such a beautiful theme.

---

