---
title: "banshee player quits once I plug in ipod"
date: 2005-12-14
forum: General Help
---

### Post by taseal on 2005-12-14
hey, I hope this is the app forum for this....

but the music player banshee quits once I plug my ipod in... anyone know why?

doesnt even start if its plugged in...

thx!

---

### Post by aysiu on 2005-12-14
Sounds like a job for:
[http://banshee-project.org/Bugs](http://banshee-project.org/Bugs)

---

### Post by thomas.mcmahon on 2005-12-14
[QUOTE=taseal]hey, I hope this is the app forum for this....

but the music player banshee quits once I plug my ipod in... anyone know why?

doesnt even start if its plugged in...

thx![/QUOTE]

I have this problem too, is your i
pod a mini?

---

### Post by RAOF on 2005-12-14
[QUOTE=aysiu]Sounds like a job for:
[http://banshee-project.org/Bugs](http://banshee-project.org/Bugs)[/QUOTE]
Except that this bug has probably been fixed in the latest version.  The ubuntu version is 0.9.7, the latest is 0.10.0 and there have been major ipod fixes along the way.

---

### Post by taseal on 2005-12-15
[QUOTE=thomas.mcmahon]I have this problem too, is your i
pod a mini?[/QUOTE]

its a nano :( 2gb btw

---

### Post by RAOF on 2005-12-15
If you want to try a more recent version of Banshee, I believe that someone's providing (**Warning: totally unofficial**) backports of the latest Banshee packages + the required mono libraries.  Just add
```

deb http://packages.filefind.net/ ubuntu-breezy dotnet p2p

```
to your sources.list, and you should be able to get the latest Banshee.  That will probably fix your problem.

---

### Post by taseal on 2005-12-16
[QUOTE=RAOF]If you want to try a more recent version of Banshee, I believe that someone's providing (**Warning: totally unofficial**) backports of the latest Banshee packages + the required mono libraries.  Just add
```

deb http://packages.filefind.net/ ubuntu-breezy dotnet p2p

```
to your sources.list, and you should be able to get the latest Banshee.  That will probably fix your problem.[/QUOTE]


ok thx, i'll look into that :)

---

