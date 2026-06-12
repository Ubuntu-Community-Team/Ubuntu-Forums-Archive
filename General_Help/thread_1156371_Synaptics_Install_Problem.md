---
title: "Synaptics Install Problem"
date: 2009-05-11
forum: General Help
---

### Post by zzzBrett on 2009-05-11
I am trying to install Amarok on my desktop with Ubuntu 9.04.  When I mark it for install, it gives the error "Could not mark all packages for installation or upgrade." It goes on to list dependencies then says "but it is not going to be installed" for each.

Maybe something wrong with my repositories? But it seems that all are checked.

Suggestions?
Thanks

---

### Post by zzzBrett on 2009-05-11
bump

---

### Post by subjugater on 2009-05-11
> **zzzBrett said:**
> I am trying to install Amarok on my desktop with Ubuntu 9.04.  When I mark it for install, it gives the error "Could not mark all packages for installation or upgrade." It goes on to list dependencies then says "but it is not going to be installed" for each.

Maybe something wrong with my repositories? But it seems that all are checked.

Suggestions?
Thanks

Did you try to install via terminal?

---

### Post by zzzBrett on 2009-05-11
> **subjugater said:**
> Did you try to install via terminal?

Same Result

---

### Post by zzzBrett on 2009-05-12
bump

---

### Post by navneeth on 2009-05-12
Perhaps posting the terminal output would help?

---

### Post by zzzBrett on 2009-05-12
> **navneeth said:**
> Perhaps posting the terminal output would help?

No problem:

```
user@user-desktop:~$ sudo apt-get install amarok
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
          Depends: libqt4-opengl (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-test (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-webkit (>= 4.5.0~+rc1) but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.1.96) but it is not going to be installed
E: Broken packages

```

---

### Post by navneeth on 2009-05-12
I think some of the packages were either corrupted or not properly installed.

Try...

```
sudo apt-get -f install
```

---

### Post by zzzBrett on 2009-05-12
> **navneeth said:**
> I think some of the packages were either corrupted or not properly installed.

Try...

```
sudo apt-get -f install
```



Still didn't work:

```
user@user-desktop:~$ sudo apt-get -f install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
          Depends: libqt4-opengl (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-test (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-webkit (>= 4.5.0~+rc1) but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.1.96) but it is not going to be installed
E: Broken packages

```

---

### Post by navneeth on 2009-05-12
-f install will do. Anyway, how about...

```
sudo apt-get build-dep amarok
```

? If it works, try installing amarok then.

---

### Post by zzzBrett on 2009-05-12
> **navneeth said:**
> -f install will do. Anyway, how about...

```
sudo apt-get build-dep amarok
```

? If it works, try installing amarok then.



```
user@user-desktop:~$ sudo apt-get build-dep amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for amarok could not be satisfied.

```

...and I think its not only amarok that is doing this.  I don't remember which packages, but this is happening every now and then.

---

### Post by navneeth on 2009-05-12
Hmm, I'm afraid I'm out of ideas right now. Sorry. What I usually do when I'm faced with problems of corrupted or broken packages, is to clear /var/cache/apt/archives of the troublesome package files and re-download them to see if they come out correctly.

---

### Post by zzzBrett on 2009-05-12
> **navneeth said:**
> Hmm, I'm afraid I'm out of ideas right now. Sorry. What I usually do when I'm faced with problems of corrupted or broken packages, is to clear /var/cache/apt/archives of the troublesome package files and re-download them to see if they come out correctly.

Cleared the cache, same result.  Thanks for trying to help, though.  Maybe someone else will come along with a solution :)

---

### Post by zzzBrett on 2009-05-12
I might have come on to something - it seems that all KDE-based applications have that same result.  Could that be any kind of indication as to the problem?

---

### Post by zzzBrett on 2009-05-12
bump

---

### Post by zzzBrett on 2009-05-13
bump.. any ideas?

---

### Post by zzzBrett on 2009-05-13
bump

---

