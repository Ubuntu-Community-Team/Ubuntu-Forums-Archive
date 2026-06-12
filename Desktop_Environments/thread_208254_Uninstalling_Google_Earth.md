---
title: "Uninstalling Google Earth"
date: 2006-07-03
forum: Desktop Environments
---

### Post by rskovacs on 2006-07-03
I already posted this in a different thread, but this is probably a better place for it...

To uninstall Google Earth, assuming it is installed in /usr/local/google-earth, this is the code I should type in the terminal, right?

```
cd /usr/local/google-earth
sudo sh uninstall
```

But when I try this, I get the error: "Could not find a usable uninstall program. Aborting."  What is going wrong?

---

### Post by mannheim on 2006-07-03
That uninstall script appears to look for a program called "loki-uninstall" to actually do the work. Google turns up [http://www.lokigames.com]("http://www.lokigames.com") as a source for that program.

But probably it's simple to do it by hand. I would just wipe out the directory /usr/local/google-earth and remove the symlink to the binary, /usr/local/bin/googleearth:
```
sudo rm -r /usr/local/google-earth
sudo rm /usr/local/bin/googleearth
```

---

### Post by rskovacs on 2006-07-03
That worked!  I am still kinda new to Linux, so I knew you could just basically delete the directory, but for some reason I was afraid of really messing something up somehow.  In my case, for anyone who may happen to also take this advice, the symlink was in /usr/local/sbin/googleearth, so keep that in mind.   Thank you!

---

### Post by mannheim on 2006-07-03
It is probably worth deleting the directory ~/.googleearth in your home directory too, if you haven't alraedy. Google-Earth caches a lot of data there.

---

### Post by cvmostert on 2006-08-31
```
cd /usr/local/google-earth
sudo sh uninstall
```

Thank you, this worked for me... it was because i did not install GE from synaptic, and not in the propper dir... i had to do the sudo sh uninstall...

in my_home_dir/google-earth/

take care

---

### Post by Don Keeton on 2008-01-06
Hey if you google uninstall google-earth you will find this is a huge hassle for many. 

don@Odin:~/google-earth$ ./uninstall
Could not find a usable uninstall program. Aborting.
don@Odin:~/google-earth$ sudo su -
root@Odin:cd /home/don/google-earth
root@Odin:/home/don/google-earth# ./uninstall
Product: Google Earth
Installed in /home/don/google-earth
Uninstalling desktop menu entries...
Uninstalling mimetypes...
# Installed by xdg-mime from googleearth-mimetypes.xml
grep: /usr/share/mimelnk//application/earthviewer.desktop: No such file or directory
# Installed by xdg-mime from googleearth-mimetypes.xml
# Installed by xdg-mime from googleearth-mimetypes.xml
/usr/local/bin/googleearth : No such file or directory
Google Earth has been successfully uninstalled.


Hope this helps someone

---

