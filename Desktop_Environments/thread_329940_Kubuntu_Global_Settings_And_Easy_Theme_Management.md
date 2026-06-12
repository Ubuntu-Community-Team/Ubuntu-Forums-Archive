---
title: "Kubuntu Global Settings And Easy Theme Management"
date: 2007-01-02
forum: Desktop Environments
---

### Post by AragornEstel on 2007-01-02
Hello all,
"Somewhat" newb here. I was introduced to the linux world about 6 months ago, and I believe I'm doing quite well. I catch on easily, and am currently "running" Kubuntu Dapper through vmware. I find this a great solution while I wait for my free cds.

Anyway, back to my question. I have successfully installed themes, and have been trying things such as xpde, and other kde-look themes. I was wondering how to install themes globally. For instance if I install in my original user, those themes are not accesible to the second user and vice versa. How do I install themes(or in anything else) globally?

My other question was what program for KDE is there that will allow me to customize EVERYTHING-KDM, windows decor, style, colors, fonts-easily and effectively and globally. My current aim is to make everything in kubuntu look like xp(stupid-yes I know I dont' like xp either) so I can fool my sister into using it without knowing it :) I know such questiosn are asked far too much, but I didn't have much success searching the forums.

Thank you for all your time and effort into the ubuntu project, and in fact to the entire linux community.

---

### Post by aysiu on 2007-01-02
To customize KDM through the GUI, you'll need to install the KDM theme manager (kind of pain, actually) or unzip themes to /usr/share/apps/kdm/themes and edit /etc/kde3/kdm/kdmrc appropriately.

A one-top place to edit everything else is Alt-F2 ```
kcontrol
``` or if you want to edit them for root ```
kdesu kcontrol
```

---

### Post by AragornEstel on 2007-01-02
Yeah, I'm quite familiar with kcontrol and I believe KDM is already installed isn't it? But I'm somewhat confused as to what the fuction of the "Theme Manager" under kcontrol actually customizes?

EDIt:
And kcontrol only changes settings for current user.

---

### Post by aysiu on 2007-01-02
KDM is already installed, but I thought you were talking about managing KDM themes. For that, you need to either install the KDM theme manager (more trouble than it's worth--trust me) or edit the text file /etc/kde3/kdm/kdmrc manually.

The theme manager in KControl manages the themes once you log in (what your windows look like when you have programs open, what your panel looks like). KDM themes manage what your login screen looks like.

---

### Post by AragornEstel on 2007-01-02
Ok, so how would I go about installing DESKTOP themes into some "root" directory where it would show up in kcontrol for all users?

---

### Post by aysiu on 2007-01-02
Probably you'd extract the theme to /usr/share/themes

---

### Post by totya on 2007-01-04
If my memory serves well, here's the way how can you install kdm themes:

To Install it in ubuntu/kubuntu/etc just uncompress it and put it in:

/usr/share/apps/kdm/themes/

and edit /etc/kde3/kdm/kdmrc

the line

Theme=/usr/share/apps/kdm/themes/whatever

with

Theme=/usr/share/apps/kdm/themes/Your_theme

---

