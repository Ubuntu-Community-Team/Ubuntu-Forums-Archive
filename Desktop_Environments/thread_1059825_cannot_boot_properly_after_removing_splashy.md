---
title: "cannot boot properly after removing splashy"
date: 2009-02-04
forum: Desktop Environments
---

### Post by mic26 on 2009-02-04
Hi, i tried changing my splash screen following the guide in this link >> [http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/](http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/) but now when i removed splashy i cannot boot properly to the log in window. Any help would be much appreciated, thanks

---

### Post by binbash on 2009-02-04
I got same problem.install the splashy and then purge it instead of remove.sudo apt-get purge packagename.Then install usplash

---

### Post by mic26 on 2009-02-04
i cannot install splashy again because when it fails to the command line screen i try to install splashy from there but it does not work. This is what i done

su root

dpkg -i /home/username/Desktop/splashy_0.3.13-3ubuntu1_amd64.deb

then i get this- dpkg: unable to access dpkg status area: Read-only file system

any ideas??

---

### Post by Lukasz Tarkowski on 2009-02-05
Do this ```
sudo apt-get install splashy
```
then ```
sudo apt-get install libsplashy1
```

---

### Post by Lukasz Tarkowski on 2009-02-05
To install Usplash
You will need to remove Splashy first
```
sudo apt-get --purge remove splashy
```
then

```
sudo apt-get install usplash
```

If it doesn't work do search ```
apt-cache search usplash
``` and install stuff it found,  not all of it just the usplash, and the dev and themes
Look at the top of this reply I posted if you want to use Splashy

---

### Post by rvjr on 2009-02-18
It seems that I have the same problem here after doing
```
sudo apt-get remove splashy splashy-themes
```

Somehow 'mount' shows me that my root-fs has been mounted as read-only (errors:remount-ro)

Anything that I could do here?

---

### Post by rvjr on 2009-02-18
Oh, and I always see a lot of messages still containing 'splashy'. It seems that the uninstall did not remove the modified scripts and all that stuff... Maybe that's why the root fs mount fails?

---

### Post by Lukasz Tarkowski on 2009-02-20
you forgot to ```
--purge
``` when uninstalling it it :D
Well dunno what now :D
--purge it purges the configuration for splashy :D or any app

---

