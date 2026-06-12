---
title: "lil help if u dont mind :\"
date: 2009-04-16
forum: General Help
---

### Post by matt12345 on 2009-04-16
Ok, so I was installing java (yes it's the right code) so when i type it in i get this:

 ```
"dkpg --configure -a"
```

---

### Post by SuperSonic4 on 2009-04-16
It means something went wrong with installing something earlier and you probably closed the terminal before completing the command (probably accepting the licence). In a terminal:

```
sudo dkpg --configure -a
``` will almost certainly solve that problem (to accept the licence agreement press **TAB** and then **Enter**

---

### Post by matt12345 on 2009-04-16
> **SuperSonic4 said:**
> It means something went wrong with installing something earlier and you probably closed the terminal before completing the command (probably accepting the licence). In a terminal:

```
sudo dkpg --configure -a
``` will almost certainly solve that problem (to accept the licence agreement press **TAB** and then **Enter**

```

matthew@matthew-desktop:~$ sudo dkpg --configure -a
sudo: dkpg: command not found
```


=\

---

### Post by gali98 on 2009-04-16
its dpkg.. spelled it wrong :P
Kory

---

### Post by matt12345 on 2009-04-16
> **gali98 said:**
> its dpkg.. spelled it wrong :P
Kory

thanks so far guys :P

but wats this?

```
matthew@matthew-desktop:~$ sudo dpkg --configure -a
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 23 changed, 2 added doc-base file(s)...
Registering documents with scrollkeeper...
matthew@matthew-desktop:~$ 
```

---

### Post by SuperSonic4 on 2009-04-16
That's what I get for just copy/pasting the first post XD

I'd imagine scrollkeeper is a dependency of java-common and the file registration could mean it indexed them for use. You could always try it's man page ```
man scrollkeeper
```

---

### Post by matt12345 on 2009-04-16
ok all worked good so far

```
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

im going to install it and c wat happens.

---

### Post by matt12345 on 2009-04-16
uh oh :(

```
matthew@matthew-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
matthew@matthew-desktop:~$ 

```

---

### Post by SuperSonic4 on 2009-04-16
Preface it with sudo to temporarily become root

If it was the last command you did you can do ```
sudo !!
```

---

