---
title: "Moving Files"
date: 2004-10-18
forum: General Help
---

### Post by jdelo on 2004-10-18
I'm fairly new to this whole "sudo" thing. I have installed XMMS and I want to install some skins. Could some one tell me the command to move a file to the  
 skins directory? I know this is a dumb question , sorry. :oops: 

Thanks,
Jeff

---

### Post by Robin Mehner on 2004-10-18
To move files via bash you have the command named "mv", example usage:
```

mv file.extension targetdir/

```

if you need root rights to move the file just prepend "sudo" to the command:
```

sudo mv file.extension targetdir/

```

It will ask you for your user password.

For further informations just type "man mv" and "man sudo". If you want to move the files in a GUI like nautilus you just have to type "sudo nautilus" to start Nautilus with root rights. Hope that helped

---

### Post by LongTooth on 2004-10-18
If you don't mind me saying so, this looks like a lot of trouble. May I offer an easier solution. After uncommenting the 'universal' line in my repositories, I was able to do a 'sudo apt-get install xmms-skins'. Got several to choose from. Check that out.

---

### Post by jdelo on 2004-10-18
Thank you both for your help....great info! Another reason I like Ubuntu, nice users that help newbies like myself.

Thanks,
Jeff

---

### Post by FLeiXiuS on 2004-10-18
The 'mv' command is used for moving and renaming files/directories under linux.  

```
man mv
```
for more information

---

### Post by im_ka on 2004-10-18
you can start nautilus with root privileges:

```
sudo nautilus
```

or you can use one of my favourite apps, midnight commander.

```
sudo apt-get install mc
```

and start it with sudo

---

