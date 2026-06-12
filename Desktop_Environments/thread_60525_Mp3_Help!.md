---
title: "Mp3 Help!"
date: 2005-08-28
forum: Desktop Environments
---

### Post by LucidDarkwill on 2005-08-28
Is there a way I can install the  gstreamer0.8-mad package without connecting to the net?  I have downloaded it from debian and transferred it to my ubuntu box via a usb pen - but I cannot work out how to install it!
I would spend time trying to learn these things (im totally new to linux etc) but I need it to be playing mp3s by the end of the week!!  Im going on holiday with some mates and we need it for the hotel room!
Any help would be *hot*
-Lucid

---

### Post by heimo on 2005-08-28
Well. I'm not sure if this will solve your problem, but anyway: To install deb packages without frontend (apt-get / aptitude / synaptic) you use dpkg.

For example:
dpkg -i packagename.deb

---

### Post by nemin on 2005-08-28
[QUOTE=LucidDarkwill]Is there a way I can install the  gstreamer0.8-mad package without connecting to the net?  I have downloaded it from debian and transferred it to my ubuntu box via a usb pen - but I cannot work out how to install it![/QUOTE]Download the right package from:
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad)
Then open a terminal and cd to the directory where you downloaded the file. Next, enter:
```
dpkg -i <package name>
``` 
This should do it, good luck.

---

### Post by izmaelis on 2005-08-28
If you have downloaded .deb [ackage you can install it by doing this:
[code]
dpkg -i package.name.deb

---

### Post by LucidDarkwill on 2005-08-28
It says I need superuser priveliges - I would assume I am the superuser (as I set it up and have no other users) any ideas?

---

### Post by stoffepojken on 2005-08-28
sudo dpkg -i packagename.deb

---

### Post by LucidDarkwill on 2005-08-28
Okay I did the above, and its appeared in the synaptic pck mgr, but its broken.  Any ideas?

---

### Post by stoffepojken on 2005-08-28
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad) <-------- did you get that package?

---

### Post by LucidDarkwill on 2005-08-28
Wheeeeeeeeeeeeeeeeeee!!  I got it!  Thanks! (I had forgotten to install some libraries that the package was dependant on)
What package do I have to download for wma files please?

---

### Post by stoffepojken on 2005-08-28
If you got xmms media player check [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by stoffepojken on 2005-08-28
sudo apt-get install xmms
wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

Thats how I did

---

### Post by LucidDarkwill on 2005-08-30
When I try to install XMMS using that method, it keeps saying:
> Package XMMS is not available, but its referred to by another package.
This may mean that the package is missing, has been obsoleted or is only available from another source.
 

Ergh...help! (please)

---

