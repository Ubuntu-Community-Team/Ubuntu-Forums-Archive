---
title: "Gnome's Gnagging Tooltips"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ubitux on 2005-10-14
The new look for gnome 2.12 is great -- however, with no way to turnoff those nagging tooltips (balloon help) throughout the panel and desktop I think I'll migrate back to KDE.

I appreciate that some people enjoy the context help for tooltips -- especially new users, but must it be forced upon all users?  In just a few days it has already become an annoyance; always popping up over other menu options etc.   Maybe (hopefully), I've overlooked something, but I can't seem to find a way to change the tooltip settings.  

Does anyone else feel the same?  Have I just missed an easy configuration modification, or am I the only one that would rather not have tooltips for every icon in both the panel and the application toolbars?  :confused:

---

### Post by Danshaku on 2006-01-02
People please! I even changed to use Xfce4 instead gnome, but i find those little buggers in here too! I realy hate those tooltips, I realy do. So please people, if somebody could help us?

---

### Post by Bou on 2006-01-02
I'm almost sure there is a way to lose them :confused:

---

### Post by amohanty on 2006-01-02
Applications->System->Configuration Editor 
Browse to apps/panel/global
uncheck tooltips_enabled

That only does it for panel's afaik.
It can also be accessed via the following file
aseem@kandinsky:~$ cat .gconf/apps/panel/global/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="tooltips_enabled" mtime="1136232070" type="bool" value="false">
        </entry>
</gconf>


HTH

---

### Post by kperkins on 2006-01-02
What amohanty said.

---

### Post by CocoAUS on 2007-02-28
gconf-editor and manually editing both fail to disable the tooltips.  They're still there!  Is this a bug?

---

### Post by TripleE on 2007-03-12
Check out this [post]("http://ubuntuforums.org/showthread.php?t=353177")

---

