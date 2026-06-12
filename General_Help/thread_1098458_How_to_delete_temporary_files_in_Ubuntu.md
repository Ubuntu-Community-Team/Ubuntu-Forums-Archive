---
title: "How to delete temporary files in Ubuntu?"
date: 2009-03-17
forum: General Help
---

### Post by atulbamne on 2009-03-17
Before using Ubuntu, I was using WinXP. There u can delete the temporary files and recover some HD space. Whether there is any such facility in Ubuntu? Pls help.

---

### Post by iaculallad on 2009-03-17
You could use the deporphan utility:

```
deborphan | xargs apt-get -y remove --purge
```

Others would also use:

```
sudo apt-get autoclean
```

to remove application/update cache files.

---

### Post by atulbamne on 2009-03-17
Thanks.

---

### Post by atulbamne on 2009-03-17
I will also like to receive view from other friends from the community.

---

### Post by binbash on 2009-03-17
I suggest reading those two : 

[http://www.ubuntu-inside.me/2009/03/clean-your-ubuntu-with-bleachbit.html](http://www.ubuntu-inside.me/2009/03/clean-your-ubuntu-with-bleachbit.html)
[http://www.ubuntu-inside.me/2009/03/how-to-clean-your-orphan-packages-with.html](http://www.ubuntu-inside.me/2009/03/how-to-clean-your-orphan-packages-with.html)

---

### Post by nelskurian on 2009-03-17
The ubuntu advantage==>

A) Linux has no registry or equivalent, nothing to do there.
B) The /tmp folder gets cleared on every boot
C) Linux filesystems are genreally very resilient to fragmentation because of the way it determines where to write files stuff.

As for clearing apt's cached .debs, you don't need to unless you need the harddrive space. In my experience (much to my irritation, in fact), apt clears this on occaision when it decides that its getting too big (I think it was in the region of 600MB when it was clearing mine). As I say, no need to "sudo apt-get clean" because of point (C) above, unless you need the disk space.

Its a zero waste-of-time-maintenance OS

A good tool to keep your file system clean is to use the "fslint" program:
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

and installed with alien:
Code:

```
sudo alien -i fslint-2.12-1.noarch.rpm
```

---

### Post by Kevbert on 2009-03-17
Nice program (Fslint) nelskurian, thanks.
You can actually install Fslint from the repos now with
```
sudo apt-get install fslint
```
so you don't need to use Alien.

---

### Post by nelskurian on 2009-03-17
> Nice program (Fslint) nelskurian, thanks.
You can actually install Fslint from the repos now with
Thanks dude.I check this before months.:popcorn:

---

### Post by atulbamne on 2009-03-19
Thanks to all those who came up with views/solutions.

Good luck to all,

Thanks again.

---

### Post by artvds2708 on 2009-04-28
Use BleachBit !
it is in synaptic

---

