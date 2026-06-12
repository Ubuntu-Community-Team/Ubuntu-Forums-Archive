---
title: "Clear gedit find history"
date: 2009-05-02
forum: General Help
---

### Post by ayonkhan on 2009-05-02
A little drop down in gedit (Ctrl + f) where it shows you everything you typed to find before. Now I would like to know how to clear this?

---

### Post by _Purple_ on 2009-05-02
My search history saved in .gconf/apps/gnome-settings/gedit/%gconf.xml. Delete this file by typing this in terminal:


```
rm ~/.gconf/apps/gnome-settings/gedit/%gconf.xml
```

---

### Post by zvacet on 2009-05-02
Every command you typed is saved in **~/.bash_history** .Clear all commands in that file if that is what you want to do.

---

### Post by ayonkhan on 2009-05-02
Sorry. Not working.
```
ayonkhan@ayonkhan-desktop ~/Desktop $ rm ~/.gconf/apps/gnome-settings/gedit/%gconf.xml
rm: cannot remove `/home/ayonkhan/.gconf/apps/gnome-settings/gedit/%gconf.xml': No such file or directory
```
Please note that I'm currently using Linux Mint 6 “Felicia”.

---

### Post by _Purple_ on 2009-05-02
> **ayonkhan said:**
> Sorry. Not working.
```
ayonkhan@ayonkhan-desktop ~/Desktop $ rm ~/.gconf/apps/gnome-settings/gedit/%gconf.xml
rm: cannot remove `/home/ayonkhan/.gconf/apps/gnome-settings/gedit/%gconf.xml': No such file or directory
```
Please note that I'm currently using Linux Mint 6 “Felicia”.

I was talking about intrepid. Sorry I am not sure about Linux Mint 6 Felicia configuration file.

---

### Post by Brandon Williams on 2009-05-03
Try this
```
gconftool-2 --unset /apps/gnome-settings/gedit/history-gedit2_search_for_entry
```

It works for gedit 2.26.1 in Jaunty. I don't know about other versions of gedit, though.

---

### Post by ayonkhan on 2009-05-03
> **Brandon Williams said:**
> Try this
```
gconftool-2 --unset /apps/gnome-settings/gedit/history-gedit2_search_for_entry
```

It works for gedit 2.26.1 in Jaunty. I don't know about other versions of gedit, though.
Sorry, it's not working.

---

### Post by Brandon Williams on 2009-05-04
Hmmm ... what version of gedit are you using? That is the correct key for versions from 2.22.3 (Hardy) to 2.26.1 (Jaunty). Does Linux Mint use a customized gedit for some reason?

Try searching for 'gedit' in gconf-editor (Edit->Find ... Search For: gedit). See if you can find some other gedit key with a history list in it. Or maybe check the 'Search also in key names' box and search for 'history'.

---

### Post by ayonkhan on 2009-05-04
Gedit version is 2.24.2.

---

### Post by Brandon Williams on 2009-05-04
Did you find the correct key name with a search in gconf-editor?

---

### Post by ActionParsnip on 2010-06-07
Mint isn't supported here. Mint is NOT Ubuntu. Mint has it's own forum:
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by wojox on 2010-06-07
> **ActionParsnip said:**
> Mint isn't supported here. Mint is NOT Ubuntu. Mint has it's own forum:
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Action,

   This is from 5/09?

---

### Post by Dayofswords on 2010-06-07
> **wojox said:**
> Action,

   This is from 5/09?
[IMG]http://farm3.static.flickr.com/2536/3739013167_c03b7660d3.jpg?v=0[/IMG]

---

### Post by kuangyujing on 2010-09-07
Is this thread active?  Try this. (in GNOME 2.30)
```
rm -f ~/.recently-used.xbel
```

---

