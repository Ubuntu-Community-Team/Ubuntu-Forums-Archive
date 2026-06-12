---
title: "Panel not starting after login"
date: 2010-01-04
forum: Desktop Environments
---

### Post by MeanEYE on 2010-01-04
Today after update, which is irrelevant to this problem in my opinion, gnome-panel stopped showing on login.

But the weird thing is, when I start the panel manually from terminal everything starts up just fine. No errors, no warnings. It's like gnome never tries to start panel in the first place.

Tried everything, from reseting panel configuration to reinstalling the package. I tried to remove the package and then to login without the panel installed. What I got is a session crash and I was back on the login screen again. So, basically gnome does try to load gnome-panel but for some weird reason it doesn't show it. Before manually starting the panel from terminal I checked for existing processes of gnome-panel. There weren't any... :shock:

Anyway, I solved the problem by manually adding gnome-panel to startup applications. This is IMHO rather dirty method of fixing the issue but it works for the time being. I am interested if anyone had similar issues or does someone know where is the setting which starts gnome-panel on system login.

---

### Post by SalahTr on 2010-01-05
1- Open **Terminal** and execute 
```
gconf-editor
```
2- Go to
```
/desktop/gnome/session/required_components/panel
```
3- In **Panel**'s value enter
```
gnome-panel
```

---

### Post by Albert Net on 2010-01-09
What you describe is exactly what I am looking forward to, for I am using gnome-do, a docky approximately.

I use gconftool-2 to set the "panel" key to "0" or "", but nothing changes.

What is  the problem?

---

### Post by SalahTr on 2010-01-09
> **Albert Net said:**
> What you describe is exactly what I am looking forward to, for I am using gnome-do, a docky approximately.

I use gconftool-2 to set the "panel" key to "0" or "", but nothing changes.

Go to **Gnome-do Preferences** and select ***Start Gnome do at login***

---

### Post by Albert Net on 2010-01-09
I have done that. Gnome-do starts every time I log in. It did not work.

---

### Post by SalahTr on 2010-01-09
> **Albert Net said:**
> Gnome-do starts every time I log in. It did not work.
what do you mean Gnome-do started or not :???:

---

### Post by Albert Net on 2010-01-09
I set it as docky, so I can see it when I log in.

---

### Post by MeanEYE on 2010-02-10
> **SalahTr said:**
> 1- Open **Terminal** and execute 
```
gconf-editor
```
2- Go to
```
/desktop/gnome/session/required_components/panel
```
3- In **Panel**'s value enter
```
gnome-panel
```

Thank you very much! 

Finally I ended up installing system from scratch, since I had to fix some things and to properly make Linux *ONLY* machine :)

But, noted... I'll certainly use this sooner or later!

---

