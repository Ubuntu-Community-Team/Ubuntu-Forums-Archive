---
title: "Alternative to using /bin/ or /usr/bin/"
date: 2009-05-29
forum: General Help
---

### Post by Primefalcon on 2009-05-29
As stated in the title When making my own scripts and wanting them to be available to all users is there an alternative to putting them in one of the 2 above locations... maybe make a special folder in / for special scripts such as /customScripts/ and then make Ubuntu recognize that as well....

I am guessing there is a configuration file that does this so I could probably grep through all the files on this computer for files that contains  /usr/bin and then examining said files

but to save time going through such a time consuming task I am hoping someone here knows off hand, thanks :D

---

### Post by cariboo on 2009-05-29
The place to put scripts and custom programs is /usr/local/bin

---

### Post by luctor on 2009-05-29
actually you can put scripts or programs in any folder, but you need to add that folder to the $PATH
[http://ubuntuforums.org/showthread.php?t=969](http://ubuntuforums.org/showthread.php?t=969)

---

### Post by InlawBiker on 2009-05-29
True but it's customary to use /usr/local/bin, or /usr/local/src for source package, etc.  A lot of systems use /opt for 3rd party installed applications.  Personally I put my own scripts into /home/username/bin and add that to my path.

---

### Post by Primefalcon on 2009-05-29
ahh save the $PATH variable in /etc/profile :-) thx

---

### Post by Primefalcon on 2009-05-29
> **InlawBiker said:**
> True but it's customary to use /usr/local/bin, or /usr/local/src for source package, etc.  A lot of systems use /opt for 3rd party installed applications.  Personally I put my own scripts into /home/username/bin and add that to my path.
So do I I have a bunch of script in mu /home/<usrname>/bin folder. But I was Looking for a global alternative in this case

---

### Post by Primefalcon on 2009-05-29
Ok I put 

```
$PATH="/binCustom/"
```

in my /etc/profile but I am getting this when I try and source it

```
brad@blackbeard:~$ . /etc/profile
bash: /home/brad/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games=/binCustom: No such file or directory
brad@blackbeard:~$ 
```

---

### Post by Primefalcon on 2009-05-29
NVM i am just using 

> The place to put scripts and custom programs is /usr/local/bin

Since on checking that is an empty directory so suits my use perfectly :-), thx

---

### Post by fballem on 2009-05-29
> **Primefalcon said:**
> So do I I have a bunch of script in mu /home/<usrname>/bin folder. But I was Looking for a global alternative in this case

No - usr/local/bin and usr/local/source are the actual names of the folders, not place holders. If you open up nautilus and look under FileSystem, you will see them. I have attached a screenshot of the usr/local folder in my system, showing bin, local, and several other subfolders.

Hope this helps,

---

### Post by kerry_s on 2009-05-29
i just create /bin in my home folder, it's automatically added when you log in if there.

---

