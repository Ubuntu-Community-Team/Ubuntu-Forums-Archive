---
title: "I cant figure out how to install the Murrine engine."
date: 2009-03-10
forum: General Help
---

### Post by fbjoey on 2009-03-10
I want to install the Murrine engine using Binary Packages
The website says "Murrine is in Universe! Check out feisty repository!"

What does this mean?

---

### Post by AndThenWhat on 2009-03-10
Just download this:

[http://www.cimitan.com/murrine/files/murrine-0.53.1.tar.bz2](http://www.cimitan.com/murrine/files/murrine-0.53.1.tar.bz2)

Then extract it.  Open a terminal and if the murrine-0.53.1 folder is on your desktop type:

```
cd ~/Desktop/murrine-0.53.1
sudo ./configure
sudo make
sudo make install
```

And then you should be good to go when it finishes.  You of course have to install Murrine themes from their website after that:

[http://www.cimitan.com/murrine/themes/gallery](http://www.cimitan.com/murrine/themes/gallery)

---

### Post by fbjoey on 2009-03-10
worked like a charm. Brilliant.

Cheers buddy

---

### Post by fbjoey on 2009-03-10
wait no > configure: error: GTK+-2.8 is required to compile murrine
fbjoey@Fred:~/Desktop/murrine-0.53.1$ 


That came up at the end :(

---

### Post by todak on 2009-03-10
Try this: ```
sudo apt-get install gtk2-engines-murrine
```

---

### Post by fbjoey on 2009-03-10
I got > Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-murrine is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by todak on 2009-03-10
It means you have the newest version of murrine that is available from the repositories, however you can install murrine-themes also, assuming you do not have it installed already. The other statement about packages being automatically installed and no longer required means that they are not needed by the system and are removed by using the command **sudo apt-get autoremove**

---

### Post by fbjoey on 2009-03-10
So I should be able to use any murrine themes I download?

---

### Post by todak on 2009-03-10
> **fbjoey said:**
> So I should be able to use any murrine themes I download?

I would assume you would be able to, unless the themes you download from outside the repositories i.e., from a website,require a newer version of murrine engines than are in the repositories.

---

### Post by ESDEEM on 2011-05-06
> **todak said:**
> Try this: ```
sudo apt-get install gtk2-engines-murrine
```
thanks it worked...!

---

