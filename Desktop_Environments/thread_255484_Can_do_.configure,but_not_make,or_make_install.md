---
title: "Can do ./configure,but not make,or make install"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Winball on 2006-09-11
As the topic says.
I can do ./configure when im trying to install apps, but MAKE and MAKE INSTALL doesn't work.
I've installed the build-essentials and make are installed with synaptic

> make: *** No targets specified and no makefile found.  Stop.

Anyone?

---

### Post by Anonii on 2006-09-11
Then, ./configure finished with an error :3
Most probably because of dependancies.
Did you try installing that program with APT?

---

### Post by Winball on 2006-09-11
[http://sonique6784.blogspot.com/2006/05/gset-compiz-tool-to-configure-compiz.html](http://sonique6784.blogspot.com/2006/05/gset-compiz-tool-to-configure-compiz.html)


That's the app I tried to install.
Not with apt


the readme says 
./configure
make
make install

---

### Post by Dinerty on 2006-09-11
did you get any errors while compiling the program?, what program is it?

---

### Post by Winball on 2006-09-11
So, I exctracted the files, cd to the folder.
./configure works fine

But make doesn't work

---

### Post by Winball on 2006-09-11
> **Dinerty said:**
> did you get any errors while compiling the program?, what program is it?


I have the same problem with everything i try to install with ./configure;make;make install process

---

### Post by Winball on 2006-09-11
It's a program called gset-compiz
It's used to configure compiz.
Since csm didn't work either. But XGL and compiz works fine





Sorry for all the posts. Now I found out how to edit posts : >

---

### Post by Dinerty on 2006-09-11
> **Winball said:**
> It's a program called gset-compiz
It's used to configure compiz.
Since csm didn't work either. But XGL and compiz works fine





Sorry for all the posts. Now I found out how to edit posts : >

gset-compiz is pretty much obselete now and I don't recommend you use it, this guide for xgl/compiz is very good indeed:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by ronmarley1 on 2006-09-11
> **Winball said:**
> As the topic says.
I can do ./configure when im trying to install apps, but MAKE and MAKE INSTALL doesn't work.
I've installed the build-essentials and make are installed with synaptic



Anyone?
Go into the Synaptic Package manage and search for "build-essential" without the quotes. When it finishes the search, click the box in front of build-essential and the click Mark for Installation.  Click Apply on the toolbar and wait for it to download and install.  Then you can go back and do a make, and make install.
OR
You can go to a terminal and type:
sudo apt-get install build-essential

---

### Post by Winball on 2006-09-11
> build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Ok, the mainproblem is doing make;make install etc
I've figured out different ways to configure compiz.np


I've allready have the build-essential as you can see

---

### Post by Dinerty on 2006-09-11
Have you read the readme and install notes within the package, it may say different instructions?

---

### Post by ronmarley1 on 2006-09-11
> **Winball said:**
> 

I've allready have the build-essential as you can see
Hmmm.  Not sure what the problem is then.  Sorry I was not helpful.

---

