---
title: "Rar archives and Linux"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ace2005 on 2005-12-01
Is it just me or do these two never mix, if an rar archive has a password i can never get it to extract in Linux, i've installed rar and unrar-free and when ark opens it i can see the contents but i can't extract them, they just give errors. I've tried copying and pasteing the password and also typeing it in but it never works.

In Linux : Ark + Password = Password Error
However: Wine + TUGZip + Password (same as before)= Extracted files

[http://www.tugzip.com/](http://www.tugzip.com/) :D

Anyone with a similar problem?

---

### Post by Bou on 2005-12-01
[QUOTE=ace2005]Is it just me or do these two never mix, if an rar archive has a password i can never get it to extract in Linux, i've installed rar and unrar-free and when ark opens it i can see the contents but i can't extract them, they just give errors. I've tried copying and pasteing the password and also typeing it in but it never works.

In Linux : Ark + Password = Password Error
However: Wine + TUGZip + Password (same as before)= Extracted files

[http://www.tugzip.com/](http://www.tugzip.com/) :D

Anyone with a similar problem?[/QUOTE]


You should install unrar-nonfree, it's in the multiverse repos ;)

---

### Post by ace2005 on 2005-12-01
How could have i missed that :o

---

### Post by Pauleberber on 2005-12-11
**[ English Only ! ]**

---

### Post by Bou on 2005-12-12
**[ English Only ! ]**

---

### Post by lindejos on 2006-01-13
thanks after getting rar, unrar-free, and unrar-nonfree I was able to unpack rar archives.

I love it when a plan comes together.

---

### Post by hyg53 on 2006-01-14
still doesn't work for me. I'll try with tugzip

---

### Post by Rikoto on 2006-02-14
[QUOTE=Bou]You should install unrar-nonfree, it's in the multiverse repos ;)[/QUOTE]

...Where do I get that, and how do I install it?

---

### Post by kaamos on 2006-02-14
First: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Second: Use synaptic to install the package. [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by donaldd on 2006-02-14
Add the Multiverse repository using synaptic

[http://easylinux.info/wiki/Ubuntu#How_to_apt-get_the_easy_way_.28Synaptic.29](http://easylinux.info/wiki/Ubuntu#How_to_apt-get_the_easy_way_.28Synaptic.29)


or  edit /etc/apt/sources.list

use terminal
sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar
Applications -> Accessories -> Archive Manager 

or synaptic search rar install

---

### Post by Gustav on 2006-02-14
For me extracting rar archives with passwords isn't possible with file-roller but if I extract the command line way it works.

---

### Post by void_false on 2006-02-14
```
unrar e <filename.rar>

```
Then it will ask you for a passwd. Enter it and your files will be extracted.

---

