---
title: "Cursor problem in Lucid"
date: 2010-05-23
forum: Desktop Environments
---

### Post by chaopoch on 2010-05-23
No matter what cursor theme I choose, every time I move the cursor from any application window to desktop, it becomes the default theme; then I move it back to the application window, the cursor will changes back to the theme I choose .

I ever tried to create a ~/.Xdefaults with content as follows, but still no success.

[COLOR="Green"]Xcursor.theme:  TheCandyman[/COLOR]

Thanks for help.

---

### Post by Snoober on 2010-05-24
Same problem here

---

### Post by Snoober on 2010-05-24
Actually, this worked for me:

[http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html")

---

### Post by Linye on 2010-05-25
^^^^ 

Worked for me too. Thanks for posting!

---

### Post by hok00age on 2010-05-25
> **chaopoch said:**
> No matter what cursor theme I choose, every time I move the cursor from any application window to desktop, it becomes the default theme; then I move it back to the application window, the cursor will changes back to the theme I choose .

I ever tried to create a ~/.Xdefaults with content as follows, but still no success.

[COLOR="Green"]Xcursor.theme:  TheCandyman[/COLOR]

Thanks for help.
Run:
```
sudo gedit /etc/alternatives/x-cursor-theme
```

You'll get:
```
[Icon Theme]
Name = Oxygen White
Comment = Oxygen mouse theme. Oxygenize your desktop!
Inherits = oxy-white
```

Name = Cursor theme name (or fill as you want)
Comment = (optional)
Inherits = FOLDER NAME OF YOUR CURSOR THEME (usually saved in /usr/share/icons)

Now, change your cursor theme gnome-appearance-properties

Hope this will help you

---

### Post by TerminX on 2010-06-04
I wouldn't recommend just editing the index.theme from whatever theme you have selected like that instead of just changing the configured theme.  The change will revert as soon as the package containing that theme is upgraded, and it's never a good idea to just randomly edit non-conf files like that.

Instead, use 'sudo update-alternatives --config x-cursor-theme' or manually symlink /etc/alternatives/x-cursor-theme to one of the other .theme files in /etc/X11/cursors or /usr/share/icons/<themename>.

---

### Post by Snoober on 2010-06-04
> **TerminX said:**
> I wouldn't recommend just editing the index.theme from whatever theme you have selected like that instead of just changing the configured theme.  The change will revert as soon as the package containing that theme is upgraded, and it's never a good idea to just randomly edit non-conf files like that.

Instead, use 'sudo update-alternatives --config x-cursor-theme' or manually symlink /etc/alternatives/x-cursor-theme to one of the other .theme files in /etc/X11/cursors or /usr/share/icons/<themename>.

Perfect! Thank you. That does work much better and is easier. I had no idea. Now hopefully this compiz bug will be fixed soon.

---

### Post by bluepicaso on 2010-06-19
NOthing above worked for me i tried this

$ compiz --replace in the terminal. this worked for me..

I'm using Ubuntu 10.04

---

### Post by gax on 2010-06-26
> **bluepicaso said:**
> nothing above worked for me i tried this

$ compiz --replace in the terminal. This worked for me..

I'm using ubuntu 10.04


+1

tanks!

---

### Post by carbine83 on 2010-06-30
Nice one thanks, this was driving me mad! I see a few people have had this problem, so I guess it's a nice little bug , hope they sort it soon!

---

