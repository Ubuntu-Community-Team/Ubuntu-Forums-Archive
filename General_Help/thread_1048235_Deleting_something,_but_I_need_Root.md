---
title: "Deleting something, but I need Root"
date: 2009-01-23
forum: General Help
---

### Post by Nino1110 on 2009-01-23
Hello, I just extracted a .rpm file, but it gone wrong.
Anyone know how I can delete this? Simple right click and delete doesn´t work.
Ubuntu says I don´t have enough rights or something.
Anyone know how I can delete it by using a terminal and hit up something like sudo delete *name of the deb file*

Thank you very much!

---

### Post by gjoellee on 2009-01-23
try this command:
```
gksu nautilus
```then find the file and delete it

> Anyone know how I can delete it by using a terminal and hit up something like sudo delete *name of the deb file*
you can use the "rm" command.
```
sudo rm /path/to/the/file
```
NOTE: Only use the rm command when you know exactly what you are doing! This can seriously harm your system if used wrong

---

### Post by Nino1110 on 2009-01-23
Thank you, RM works, but I can´t delete maps with it..
And that´s the problem, I want to delete the map.

Edit:

Never mind, is works with gksu Nautilus, thank you very muych!

---

### Post by jespdj on 2009-01-23
With "map", you probably mean "folder" or "directory".

You can delete directories like this:
```
sudo rm -rf /path/to/directory
```
BE CAREFUL with this command, check if you entered the right path before you press Enter! If you delete the wrong directory, you can do serious damage to your system!

---

### Post by sisco311 on 2009-01-23
> **Nino1110 said:**
> Thank you, RM works, but I can´t delete maps with it..
And that´s the problem, I want to delete the map.

to delete directories use the -r flag:
```
rm -r /path/to/dir
```

you can list the content of the directory with ls:
```
ls /path/to/dir
```

to get a description about a command:
```
man *command*
```
e.g.
```
man rm
```


be careful, as root you can delete any file (including important system files)

---

### Post by Nino1110 on 2009-01-23
Thank you guys for the fast replies! It´s all clear, problem fixed!
Thanks!

---

### Post by grndslm on 2009-01-23
I'm curious as to why one would run 

gksu nautilus

...instead of...

sudo nautilus

????

---

### Post by sisco311 on 2009-01-23
> **grndslm said:**
> I'm curious as to why one would run 

gksu nautilus

...instead of...

sudo nautilus

????

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by PriceChild on 2009-01-23
Great link in the above post, but also... *please please please* don't install rpm packages. They are  not designed to work with your Ubuntu system. Use software from the  Ubuntu repositories, and if you're trusting of the source/workmanship of the packager other repositories or even .deb's.

---

