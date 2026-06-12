---
title: "Installing error: permission denied"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Zooropa on 2005-12-06
Hi there,

I'm trying to install drivel, which I would like to use for blogging.
After MUCH installing of new applications and a heavy use of google, I got past the ./configure.

Now I get this:
zooropa@cpc2-kirk1-5-0-cust112:~/Desktop/drivel$ make install
Making install in data
make[1]: Entering directory `/home/zooropa/Desktop/drivel/data'
Making install in mime
make[2]: Entering directory `/home/zooropa/Desktop/drivel/data/mime'
make[3]: Entering directory `/home/zooropa/Desktop/drivel/data/mime'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/application-registry
mkdir -p -- /usr/local/share/application-registry
mkdir: cannot create directory `/usr/local/share/application-registry': Permission denied
make[3]: *** [install-applicationsDATA] Error 1
make[3]: Leaving directory `/home/zooropa/Desktop/drivel/data/mime'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/zooropa/Desktop/drivel/data/mime'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/zooropa/Desktop/drivel/data'
make: *** [install-recursive] Error 1
zooropa@cpc2-kirk1-5-0-cust112:~/Desktop/drivel$


This is my first time installing from source, and I'm new to Linux.

---

### Post by Joe_CoT on 2005-12-06
you need to use sudo to run it as root; the normal user has no write access to the /usr folder

sudo make install

---

### Post by teaker1s on 2005-12-06
may want 'checkinstall' from repositories it will allow you to create a .deb package and install plus it makes source uninstall easy with synaptic

---

### Post by Zooropa on 2005-12-06
[QUOTE=bobfnordman]you need to use sudo to run it as root; the normal user has no write access to the /usr folder

sudo make install[/QUOTE]

This is the kind of really basic thing I totally missed.

Thanks x 1,000,000 people, I got it working, and have it on my applications menu now.

---

### Post by Zooropa on 2005-12-06
[QUOTE=teaker1s]may want 'checkinstall' from repositories it will allow you to create a .deb package and install plus it makes source uninstall easy with synaptic[/QUOTE]
You mean...I didn't have to go through all that?

Eeeesk!

Still, I think it was a good learning experience!
My first source install!

---

### Post by teaker1s on 2005-12-06
you still need 
./configure
make
sudo checkinstall

it just helps and allows you to name describe and change version number and if something fails it creates a log. I had that with a logitech-applet which it didn't like the name

---

