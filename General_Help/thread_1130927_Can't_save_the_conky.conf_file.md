---
title: "Can't save the conky.conf file"
date: 2009-04-20
forum: General Help
---

### Post by LethalBoy on 2009-04-20
Hello,

I'm using ubuntu 8.10 and I am trying to save the conky.conf file but when I click '''Save'' it says error because I dont have permissions to do that.

What can I do

---

### Post by aeiah on 2009-04-20
where is the conky.conf file located?

---

### Post by LethalBoy on 2009-04-20
/etc/conky/

---

### Post by VCoolio on 2009-04-20
If you're trying to make a config file to have conky show all kinds of geeky stuff like you find in the huge thread in the community cafe, then just save it in your home folder or better, in a folder conky in your home folder. That way you don't need to have root rights every time you want to change it. And you can put all your conky stuff like scripts and other configs there. Then run conky with
```
conky -c /home/[you]/conky/yourconkyconfig
```
The file in /etc/conky is the default for if you don't specify the config to use with the -c variable. If you really must change the file in /etc then run ```
gksudo gedit /etc/conky/conky.conf
```

---

