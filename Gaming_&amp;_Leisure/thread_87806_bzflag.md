---
title: "bzflag"
date: 2005-11-08
forum: Gaming &amp; Leisure
---

### Post by eyebrowman92 on 2005-11-08
does anyone here play bzflag?

---

### Post by DDM on 2005-11-09
Yup. My handle is "Dooper" 

(I'm a goon as well)

---

### Post by eyebrowman92 on 2005-11-10
i like the game but my lag is etremely high and i get kicked constantly. does anyone know hot to solve this?

---

### Post by Neeko on 2005-11-10
Lag is dependant on the speed and quality of your internet connection. The exception is the Debian version of BZflag with the lag bug, this was also in the Ubuntu repositories.

Check to see if it is lag or jitter. Lag is the time in ms, and usually if you are under 250ms you will not be kicked. Jitter is the +- value after lag, this should be very low or zero or else you will get complaints. If its extremely high then you are using the buggy version.

Usually best to download source from bzflag.org and compile it yourself. When playing close all other applications that may be using your internet connection including mail and web.

---

### Post by etc on 2005-11-10
Download the latest bzflag here, and save it to your desktop: [http://internap.dl.sourceforge.net/sourceforge/bzflag/bzflag-2.0.4.20050930.tar.gz](http://internap.dl.sourceforge.net/sourceforge/bzflag/bzflag-2.0.4.20050930.tar.gz)

Then install checkinstall, which will make a deb package from the source
```
sudo apt-get install checkinstall
```

Let's remove the old bzflag just in case it causes any trouble
```
sudo apt-get remove bzflag bzflag-server
```

Now cd to desktop, and untar it
```
cd ~/Desktop
tar xvfz bzflag-2.0.4*.tar.gz
cd bzflag-2.0.4*

```

And grab the bzflag dependencies
```
sudo apt-get install libcurl3-dev gawk g77 gcc g++ libsdl1.2-dev 
```

Now run the configure script
```
./configure
```

And if it says you do not have a package that is needed (for example libcurl) open up synaptic search for the package, and download the one that ends with -dev
Then go back and run the configure script again

If the configure script finshes with no WARNINGS or errors, then lets compile the package
```
make
```

If there are no errors continue on by using checkinstall to make a deb
```
sudo checkinstall
```

Follow the little wizard, and when you're done it should install the deb it just made, if it didn't then install it yourself
```
sudo dpkg -i bzflag*.deb
```

Test out bzflag in a terminal and you should be good to go

---

### Post by eyebrowman92 on 2005-11-10
alright ill try but i have problems with downloading things not from the terminal or synaptic.

---

### Post by NutrOn on 2006-03-22
I tried the steps by etc. for making a deb. package but it installed in user/local and is "empty" so nothing runs, no bzflag found though I found and removed the package with synaptic. Seems like ny Ubuntu install only installed a user and no root account.
user=root but no root set kind of like mac. Is this the problem or is their another?
How can I set/create root, if needed?
Thanks,](*,) 
NutrOn

---

### Post by bradlis7 on 2006-03-25
I doubt if the root account was not created. Try using the original password created upon installation from your main account as the root password. I think that's what mine was.

---

### Post by sudomania4 on 2006-03-25
i cant use the ```
make
``` command. The terminal displays ```
bash: make: command not found
``` 

edit: ok, you have to install```
 sudo apt-get build-essential
``` to use the make command.

---

### Post by j2fraser on 2008-03-29
Just for clarity, that would be...

```
sudo apt-get install build-essential
```

---

