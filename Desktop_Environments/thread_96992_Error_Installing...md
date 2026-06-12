---
title: "Error Installing.."
date: 2005-11-30
forum: Desktop Environments
---

### Post by windowsXuser on 2005-11-30
Hey,

For some reason when i download the kxdocker from repositories it worked fine, when i rebooted back into linux it wouldn't open.  Anyways, i wanted to get the lastest version so i downloded version 0.39.

I get an error when i compile it,

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

i used this prefix as root:  ./configure --prefix=/usr

do i need to install some headers?

ps. i am using kubuntu 5.10 w/ kde 3.5

thanks,

blair..

---

### Post by windowsXuser on 2005-11-30
Alright, i was able to successfully compile kxdocker.

Then i ran make, then checkinstall -D make install

Everything installed successfully, but am not sure how to run the program. 

blair..

---

### Post by windowsXuser on 2005-11-30
So, i think i found the application to run kxdocker, but now i get this error.

"You may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
loading xml...
May be you have load a wrong kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed"

i already have the resources from the site they mention above.
Any suggestions?

blair..

---

### Post by windowsXuser on 2005-12-01
I am getting fustrated with kxdocker.  I still get the same error message from ubove.

If anyone can help me i'd appreciate it.

blair..

---

### Post by deNoobius on 2005-12-23
I just managed to install kxdocker and I was looking for more info when I ran across your post.

I don't know if this helps or if you still need help, but, the only way I could get proper results from the kxdocker install was to reinstall using the deb package created after checkinstall:  sudo dpkg -i kxdocker-0.39.deb (or whatever the name was, I'm not at my ubuntu box).  Otherwise it was kind of a mess.  Also, there are several depencies you need--these qt-3 development libraries and kde headers.   Did you get all that (available using apt-get or synaptic)?

---

