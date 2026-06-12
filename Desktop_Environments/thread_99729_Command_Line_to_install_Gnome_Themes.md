---
title: "Command Line to install Gnome Themes??"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Ozbboy on 2005-12-06
Hi guys,

n00b question again:

Just wondering if there was a command line way of installing multiple gtk themes? I just download a whole bunch of things from art.gnome.org and I'd like to install them all in one hit if possible.. 

Clicking annoy's me ;) k

Thankx in advance

---

### Post by 23meg on 2005-12-06
Just do a wildcard tar extract to your ~/.themes folder.

---

### Post by plcarvalho on 2005-12-06
Change to the directory where you have all the themes and unpack all of them to the /usr/share/themes or ~/.themes  dirs like:

```
tar xfvz *.tar.gz -C ~/.themes
```

or if you want them to be available to all users:

```
sudo tar xfvz *.tar.gz -C /usr/share/themes
```

Long live the CLI! ;)

---

### Post by Ozbboy on 2005-12-06
cool thanks for that :D

---

### Post by front243 on 2005-12-06
If you want a gui install do 

**sudo apt-get install gnome-art**

This will install a new app under system/Preferences/Art Manager. It will let you download themes from art.gnome.org and install them with a gui-interface.

---

