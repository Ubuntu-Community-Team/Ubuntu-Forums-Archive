---
title: "how to create desktop shortcut for kmag in ububntu"
date: 2008-02-16
forum: Desktop Environments
---

### Post by RoBo5050 on 2008-02-16
Hello forum members,
   
I have finished downloading kmag and some other related apps and
installed them with the Debioan package installer;the problem I am currently having-I AM a newbie to Linux/Ubuntu-is that I want to make a shortcot for kmag magnifier on the desktop,but can not locate the
kmag magnifier only from the gnome command terminal!!!

Once I launch kmag via the terminal, the program gives me an option of creating a shortcut,but there is no path shown forthe kmag
program (I am having a very hard time switching from ms windows to Linux-based Ubuntu,so please keep that in mind) to create a shortcut on the gnome desktop!!:confused:

How may I create a shortcut for kmag on the desktop with the gnome terminal???

I thank all forum members in advance for the reply!

---

### Post by nemilar on 2008-02-16
In the terminal:

```
which kmag
```

Will show you where the kmag file is located (assuming the name of the program is 'kmag', replace it with 'kmagnifier' or whatever the name is).

Then, right click on the desktop and select 'Create Launcher.'  For the "command" field, enter the location of the kmag file you got in the terminal.  'Name' will be the text that appears under the icon; select the icon using the icon box in the upper left corner.

Hope this helps!

---

