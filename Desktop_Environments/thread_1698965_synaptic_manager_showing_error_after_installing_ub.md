---
title: "synaptic manager showing error after installing ubuntu tweak in 10.10"
date: 2011-03-03
forum: Desktop Environments
---

### Post by dudesks on 2011-03-03
Recently i upgraded to 10.10 from 10.04
after that I installed ubuntu tweak to customize then ubuntu tweak showed errors.
So I removed it.
Now the synaptic manager showing errors
it shows

E: Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Also the update manager,software center are not opening up.
and cant create/place any new folder or files in desktop.
Pls. help

---

### Post by Frogs Hair on 2011-03-03
First I would attempt to reload the synaptic package manager . Next , using custom filters (bottom left) in SPM select broken packages and if there are any showing run repair broken packages from the edit tab. Welcome to the forums.

---

### Post by dudesks on 2011-03-03
But how can I reload synaptic,when it is showing errors and closes after sometime.

---

### Post by Frogs Hair on 2011-03-03
I did not know the SPM was closing . Will it stay open long enough to remove Ubuntu tweak from software sources ? . It appears from the error that you are being asked correct the error in from the source. I would think removing the source would remove the error and then you could reload the SPM or run ```
sudo apt-get update
```
 
which is the same thing. If you are able to clear the error by removing the source It would be up to you weather you want to try again. If you had Ubuntu Tweak on 10.04 that would explain why the source is incorrect or there is a conflict.
 
I am not on Ubuntu at the moment , so I will check back and give more details about removing the source if someone doesn't help before then.

---

### Post by Frogs Hair on 2011-03-03
To remove the Ubuntu Tweak software source open the synaptic package manager > settings tab > repositories > other software . click on the Ubuntu Tweak stable or PPA source and select remove. You should be asked to update repositories at that point . If this works you can attempt to install again.

---

### Post by dudesks on 2011-03-04
But the Synaptic does not responds before it closes.
so cant remove ubuntu tweak by synaptic.
One thing I noticed that now that the .deb files are also not been installed due to the same error

---

### Post by SantaFe on 2011-03-04
A long shot if it isn't already installed, but if you can access your gnome menus, can you find a program entry called Software Sources?  It does the same thing as what Frogs Hair said, but you don't have to be in Synaptic to use it.  IF you do have it, click on it & follow Frogs Hair's instructions above to remove the Ubuntu Tweak software source.

Hopefully it is a stand alone application & will edit the file correctly, it's the only thing I can think of.   Guess I picked the wrong time to switch from Ubuntu to Kubuntu. ;)

---

### Post by Frogs Hair on 2011-03-04
Here are Two solved threads with the same issue.

[http://ubuntuforums.org/archive/index.php/t-1501743.html](http://ubuntuforums.org/archive/index.php/t-1501743.html)



[http://ubuntuforums.org/archive/index.php/t-1688262.html](http://ubuntuforums.org/archive/index.php/t-1688262.html)

---

### Post by dudesks on 2011-03-04
Thank you very much frogs hair for your valuable reply.
Which font you used in window title in upper screenshot and how to get that?

---

### Post by Frogs Hair on 2011-03-04
I hope you have it sorted out or are on the way. Here is a link to the fonts. Font Zero_Threes :[http://www.urbanfonts.com/fonts/Zero_Threes.htm](http://www.urbanfonts.com/fonts/Zero_Threes.htm)

---

