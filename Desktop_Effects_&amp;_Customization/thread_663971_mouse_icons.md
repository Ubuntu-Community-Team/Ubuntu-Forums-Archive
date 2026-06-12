---
title: "mouse icons"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by fenixfox on 2008-01-10
Just wanting to install and find different mouse icons (i.e. pointers) Not sure how to do that yet.

---

### Post by Forlong on 2008-01-10
Get 'em here: [http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=36](http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=36)

Then open the Appearance menu and just drag & drop the file(s) in there to install the theme.

---

### Post by fenixfox on 2008-01-10
I downloaded a set of pointers. I tried dragging and dropping into pointers under customize in appearance. Nothing happened

---

### Post by fenixfox on 2008-01-10
I apologize but I'm still not really used to how to work things. I have the file I want. 

1. Create the directory ~/.icons if you don't have it.
2. Create the directory ~/.icons/default you don't have it.
3. Create a text file named index.theme inside it if you don't already have it.
4. Edit the index.theme file so it look like this:

[Icon Theme]
Inherits=DeepSky

5. Copy the DeepSky directory inside this archive to ~./icons so it looks like ~./icons/DeepSky
6. Logout to apply the cursors.

I created file in my home folder named icons. I also created one in my home folder named icons/default. I made the index file. I then copied DeepSky file to the icons file I created. I logged out then back in and nothing happened.  If someone has the time how would I do all this from the terminal?

---

### Post by Forlong on 2008-01-11
Oh, well. That particular icon-theme seems to be not compatible.

The important thing is, that the folder to create needs to be named **.icons** (the dot is important).

Most probably, you already have that folder. In Nautilus press [Ctrl]+[H] - then all hidden folders will appear (hidden folders are the ones starting with dots).


But I recommend trying out a compatible icon theme first.

---

