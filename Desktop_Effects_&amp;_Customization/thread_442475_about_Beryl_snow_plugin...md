---
title: "about Beryl snow plugin.."
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by rocketboys on 2007-05-13
I was trying to  install snow plugin, but I'm keep getting this error

danny@Dan:~/xglsnow-0.2.0$ sudo make install
-e compiling : snow.c -> build/libsnow.loPackage ice was not found in the pkg-config search path.
Perhaps you should add the directory containing `ice.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ice', required by 'beryl', not found
/bin/sh: libtool: not found
make: *** [build/libsnow.lo] Error 127
danny@Dan:~/xglsnow-0.2.0$ add dir ice.pc
bash: add: command not found
danny@Dan:~/xglsnow-0.2.0$ make

can anyone help step by step,,?

thank you!

---

### Post by godd4242 on 2007-05-13
>>Package 'ice', required by 'beryl', not found

Open synaptic and look for ice?

---

### Post by rocketboys on 2007-05-13
> **godd4242 said:**
> >>Package 'ice', required by 'beryl', not found

Open synaptic and look for ice?

Thank you for the response!

I found it. What do I have to do next..?

I see hundreds of files.

---

### Post by the8thstar on 2007-05-13
Install them all, that's the way to go!

No seriously, try and narrow down your search with 'beryl' and 'ice' and see what the query returns.

---

### Post by rocketboys on 2007-05-13
I was trying to install Snowplugin for Beryl, but I got the error.

danny@Dan:~/xglsnow-0.2.0$ sudo make install
-e compiling : snow.c -> build/libsnow.loPackage ice was not found in the pkg-config search path.
Perhaps you should add the directory containing `ice.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ice', required by 'beryl', not found
/bin/sh: libtool: not found
make: *** [build/libsnow.lo] Error 127
danny@Dan:~/xglsnow-0.2.0$ add dir ice.pc
bash: add: command not found
danny@Dan:~/xglsnow-0.2.0$ make


So I used sypnatic and found ice package. There was hundreds of stuff and I installed

all of the stuff that name starts with ice..but I still can't get it. 

does anyone know how I can figure this out..?

---

### Post by Jack33 on 2007-05-21
EDIT: Dont do this, I found out a different way, simply ```
apt-get install beryl-plugins-unsupported
``` In fact when i finished compilin the snow on my own, my beryl got fubared. anyways, once you have apt-getted the unsupported plugins, simply enable snow by beryl settings manager>extras>snow
good luck


Old:
after some poking around I fixed this problem. seems like someone forgot to say it needed some other dependencys
first you will need to 
```
sudo apt-get install libsm6 libsm6-dbg libice6 libice-dev
```
Next grab the rpm [ftp://fr2.rpmfind.net/linux/MandrakeCooker/cooker/i586//media/main/release/libsm6-devel-1.0.3-1mdv2008.0.i586.rpm](ftp://fr2.rpmfind.net/linux/MandrakeCooker/cooker/i586//media/main/release/libsm6-devel-1.0.3-1mdv2008.0.i586.rpm)
and do 
```
cd 'area of rpm download'
alien libsm6-devel-1.0.3-1mdv2008.0.i586.rpm
```
there will probably be lots of errors from alien, but ignore them, it should be fine.
now do
```
sudo dpkg -i libsm6-devel_1.0.3-2_i386.deb
```
finally you should be able to do 
```
make && sudo make install
```

---

