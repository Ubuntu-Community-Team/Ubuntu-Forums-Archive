---
title: "Change the trash icon"
date: 2007-03-11
forum: Desktop Environments
---

### Post by mrmonday on 2007-03-11
Hi everyone,

I have managed to add a trash icon to my desktop, however I want it to be big. I used the stretch icon feature, but the icon becomes blurry. I have found an svg icon, which are supposed to be scalable, but how do I change the icon to the svg. 

Thanks for your help.

---

### Post by jimbo99 on 2007-03-11
I'm going to partially reply to this.  First, the gnome developers didn't program a bug on this one, it is actually a feature that you can't change the trashcan icon via right click properties.  It is, in my opinion, incompetence.

The way you have to change it is to find the theme you are using and then copy that icon over every possible version of the icon in all the folders under that theme.  This could mean you copy that file 10-20 times into various folders under that theme.  Essentially it is multiple times for in each folder for each size of icon.

I know I sound harsh on this one but the guys that wrote this were ex-os6+ programmers on the mac and they brought a certain level of absolute incompetence to the PC world.  That is:  they believed that they should carry all predefined notions from the Macintosh OS to the PC.  That just isn't so.  They needed to rethink everything including making sure that absolutely everything is customizable via dialog boxes, menus, etc.

That question gets asked over and over and almost no one responds.  Someone needs to write a simple program that identifies the theme, allows you to select the icons, and then replaces the appropriate instances of the icon in the theme with the one you selected.  This isn't hard, and the programmers for this should have done that already.  They are busy working on 2.2 of gnome and what do you want to bet they won't even consider addressing this little bit of incompetence?

---

### Post by catoctin on 2007-03-25
I am able to put the Trash icon on the desktop this way:

- right click on desktop

- select "Create Launcher"

- in the Create Launcher window fill out the following

- Type - **file**

- Name - **trashnamehere**

- Location - **Trash:**

- Comment - **whatever**

- Icon - select your icon

Hope this helps

---

### Post by mrmonday on 2007-03-26
Thanks, I have done this... However, it doesn't change automatically if it has something in it :(

Thanks anyway.

---

### Post by sagara on 2007-03-31
To get the trash can to work correctly I'd recommend you follow the instructions given on this thread: [http://ubuntuforums.org/showthread.php?t=390429](http://ubuntuforums.org/showthread.php?t=390429)

Just scroll down to the end and you will see:

1. Hit **alt-F2** and run 'gconf-editor'
2. browse to apps/nautilus/desktop
3. enable 'trash_icon_visible'

Using that method the trash can icon will change if you delete files.

---

### Post by mrmonday on 2007-03-31
Thanks sagara, but I have already tried that... I get a very blurry icon when I enlarge it. I will stick with  catoctins method for now.

Thanks anyway.

PS Does anyone know what I can do to recommend this a a feature for feisty, to change the icon to an SVG?

---

### Post by sagara on 2007-03-31
If you get a blurry icon after enlarging the trash can, it must be because the icon is not resize-compatible ^_^;; 

Are you using a .png or .svg icon?

---

### Post by ComplexNumber on 2007-03-31
> **mrmonday said:**
> Hi everyone,

I have managed to add a trash icon to my desktop, however I want it to be big. I used the stretch icon feature, but the icon becomes blurry. I have found an svg icon, which are supposed to be scalable, but how do I change the icon to the svg. 

Thanks for your help.
i'm surprised nobody has asked this, but what icon theme are you using? 

with many themes, they can usually be roughly divided into the following:
-all scalable
-some scalable and some in fixed resolutions such as 64x64, 32x32, etc
-all fixed resolutions.

it may well be that the trash icon only exists in the 48x48 folder and lower resolutions.thats why it will be blurry if you try to stretch it.

---

### Post by mrmonday on 2007-04-01
I am using the default 'Human' icon theme, however now you mention it, the other trash icons are stored in different folders with different names... could this be it?

---

### Post by Brausen on 2007-04-16
mrmonday,

The solution is very easy. The icons of the Human theme is in this folder:

Empty icon: /usr/share/icons/Human/48x48/places/user-trash.png
Full icon: /usr/share/icons/Human/48x48/status/user-trash-full.png

You must replace it with your new icons.
It works to me, I hope that works for you.

Remember, make a backup of this old icons before.

---

### Post by Redenbacher on 2007-10-19
> **Brausen said:**
> mrmonday,

The solution is very easy. The icons of the Human theme is in this folder:

Empty icon: /usr/share/icons/Human/48x48/places/user-trash.png
Full icon: /usr/share/icons/Human/48x48/status/user-trash-full.png

You must replace it with your new icons.
It works to me, I hope that works for you.

Remember, make a backup of this old icons before.

I just followed those instructions with no results. I replaced all instances of the trash icon with my preferred icon in the Human theme and came up with nada, any other ideas?

---

