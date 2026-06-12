---
title: "change root control theme"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by jaw1959 on 2007-10-29
Is there any way to change the control theme for the root user?  In my case, I use a mac osx type theme that makes all my progress bars, etc. look shiny and blue.   However, when I need to do an administrative task, such as install an update, or add a new package, I get a different control scheme, that doesn't match.  Unfortunately, when I most often see a progress bar is when I'm in the root user mode.  I also have a mac osx icon theme, but whenever I browse a mounted drive as root, I see things with different icons than my normal theme. It would be really nice if I could set that to match my normal user mode (It would be even nicer if it matched by default, but since I didn't write the software, who am I to complain).  Can this be done without major tweaking?  I don't want to mess with a lot of stuff to make this happen.  


As I was writing the above paragraph, the solution occurred to me, so I'll post it for anyone that has the same question.  All I needed to do was run "gksudo gnome-appearance-properties %F" from the command line, and I was now able to set the appearance for the root user.  I had to reinstall the theme elements I was using, but that was not a problem, since I keep all the files I need for my theme handy for when I reinstall.  

I hope this help helps...

:KS

---

### Post by bakster on 2007-10-29
Move or copy content  of your ~/.themes and ~/.icons folders to /usr/share/themes and /usr/share/icons.

---

### Post by FuturePilot on 2007-10-29
This should do the trick
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```

---

### Post by daengbo on 2007-10-29
I've tried this before, but have run into problems because the root setting daemon isn't running. I get this error when trying to run it: "** ERROR **: You can only run one xsettings manager at a time; exiting"

I've even tried changing the theme in gconf-editor, Nothing happened.

I'm not sure it'll work.

---

### Post by NoVista on 2007-11-07
Any success?

---

### Post by jenevg on 2008-01-25
I tried FuturePilot's suggestion. Works great!

---

