---
title: "XFCE4 themes"
date: 2012-03-15
forum: Desktop Environments
---

### Post by Linux_junkie on 2012-03-15
I've been downloading some XFCE4 themes and some in GTK+2.0 themes and whenever I select the GTK+2.0 theme the system goes really slow.  I have the GTK+2.0 engine installed and have copied the themes to /usr/share/themes directory.

---

### Post by 3Miro on 2012-03-15
The theme may be buggy. Can you post a link to the theme, I will try it on my machine.

---

### Post by Linux_junkie on 2012-03-20
Sorry for the delay, I only log on about one day a week.

Here's the link to the theme that I'm having problems with.

[http://xfce-look.org/content/show.php/BrushedMetal?content=134122](http://xfce-look.org/content/show.php/BrushedMetal?content=134122)

---

### Post by Toz on 2012-03-20
Just gave the theme a try and although I didn't notice a system slowdown, there were a ton of errors being logged to ~/.xsession-errors. Did some digging and found that the file/directory permissions on that theme were incorrect and many of the files/directories were not being accessed properly (hence all the error messages). I did a:
```

sudo chmod -R 755 /usr/share/themes/BrushedMetal/*
```
...to fix the permissions and that resolved the errors.

Unfortunately, I don't notice a difference in system performance.

---

### Post by Linux_junkie on 2012-03-20
Thanks for that.

---

### Post by Toz on 2012-03-20
Do you notice any change to performance after you adjust the permissions?

---

### Post by 3Miro on 2012-03-20
I also installed the theme and also fixed the permissions. There is a command that I found some time ago in this forum that goes through files recursively and changes the permissions of folders to 755 and files to 644. Here is the command:

```
find .  \( -type d -exec chmod -v 755 '{}' \; \) -o \( -type f -exec chmod -v 644 '{}' \; \)
```

However, even after I reboot Xorg I do feel a hit in performance. When I move between workspaces and if I have multiple windows opened, it takes xfwm half a second extra to redraw the content (this is compared to Adwita or Clearlooks themes). This doesn't sound like much, but I have Phenom II X6 3.2Ghz, 16GB RAM and Nvidia GTX570 with 2.5GB video RAM, so is a theme causes a noticeable slow down, there is something wrong.

It may not be an issue with the theme necessarily. This may be caused by a bug in the Nvidia driver or xfwm4. Linux_junkie, Toz what video cards do you guys have? I wonder if anyone with Gnome 2 can test that as the theme is made for Gnome + Metacity.

I have to admit, the theme does look cool.

---

### Post by Toz on 2012-03-20
I have a Compaq 6730b:
- Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
- 4 GB Ram
- Mobile Intel® GMA 4500MHD

---

