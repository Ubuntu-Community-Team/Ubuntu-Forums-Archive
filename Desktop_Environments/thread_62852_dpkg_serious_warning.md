---
title: "dpkg serious warning?"
date: 2005-09-06
forum: Desktop Environments
---

### Post by spedsta on 2005-09-06
I had a problem with apt-get & synaptic last week where it was complaing about a input/output error on a file(libxmuu1) , someone suggested that i scan my disk for bad blocks. I didn't know how to do that so just left it knowing that ubuntu runs a scan on / after every 30 mounts. Which happened last night. The disk scan , fsck i think, found errors and then fixed them. I restarted and tried apt-get install again.

I installed a previously downloaded package 3dchess, and it gave the following warnings:

[COLOR=Blue]dpkg: serious warning: files list file for package `foomatic-db' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `m4' missing, assuming package has no files currently installed.[/COLOR]

there were many other such warnings of other packages as well. The thing is that it actually installed perfectly fine. 

It seems to me that my packages list is corrupted or non existent.
So does anyone know how to fix this situation ?

---

### Post by tlepes on 2005-09-25
I am getting the same dpkg errors on several packages.  From other threads I hear it is because dpkg is missing some .list files somewhere.  Is there a way for dpkg to rebuild those lists or to re-install them perhaps?  I must admit I am not very familiar with dpkg myself.

Thanks
Tim

---

### Post by mlomker on 2005-09-25
Have you tried **sudo dpkg -A**?

You could also delete the offenders from /var/lib/dpkg/info/

---

### Post by kvidell on 2005-10-16
[QUOTE=mlomker]Have you tried **sudo dpkg -A**?

You could also delete the offenders from /var/lib/dpkg/info/[/QUOTE]
Further guidance, maybe? :-\```
happytop:~# dpkg -A
dpkg: --record-avail needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
``````
happytop:/var/lib/dpkg/info# rm fglrx-kernel-source
rm: cannot remove `fglrx-kernel-source': No such file or directory
```I'm not sure what to do now...

```
dpkg: serious warning: files list file for package `fglrx-kernel-source' missing, assuming package has no files currently installed.
```is my error, btw.

---

### Post by mlomker on 2005-10-16
> Further guidance, maybe? :-\```
happytop:~# dpkg -A
dpkg: --record-avail needs at least one package archive file argument


This one seems to work better:

[code]
sudo apt-get update
sudo apt-get -f upgrade

```

> happytop:/var/lib/dpkg/info# rm fglrx-kernel-source

Try:

```

sudo rm /var/lib/dpkg/info/fglrx-kernel-source*

```

---

### Post by kvidell on 2005-10-16
[QUOTE=mlomker]This one seems to work better:

```

sudo apt-get update
sudo apt-get -f upgrade

```



Try:

```

sudo rm /var/lib/dpkg/info/fglrx-kernel-source*

```[/QUOTE]
Note the #, I was already root(ed).

```
happytop:/var/lib/dpkg/info# fgl
fgl_glxgears  fglrxconfig   fglrxinfo     fglrx_xgamma  
happytop:/var/lib/dpkg/info# fgl
```Also:```
happytop:/# apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

(I sudo -s -H when I do stuff, so I don't have "sudo" in every command).

How now, brown cow? :-\
- Kev

---

### Post by mlomker on 2005-10-16
>  happytop:/var/lib/dpkg/info# rm fglrx-kernel-source

You skipped the asterisk.  The **-f** switch can be used with *install* or *upgrade* to attempt to resolve dependency issues.

The **-c** switch is supposed to fix partially installed packages, which might be the case here.  Of course, deleting the package files also works...when you use the asterisk.  ;)

```

sudo dpkg -C

```

All the switches can be seen with **man dpkg**.

---

### Post by kvidell on 2005-10-16
What I'm trying to show you though is that that doesn't exist. period.
Here's another way to look at it:```
happytop:/var/lib/dpkg/info# ls | grep -i "fgl*"
libelfg0.list
libelfg0.postinst
libelfg0.postrm
libelfg0.prerm
libelfg0.shlibs
libisccfg1.list
libisccfg1.md5sums
libisccfg1.postinst
libisccfg1.shlibs
netcdfg3.list
netcdfg3.postinst
netcdfg3.prerm
netcdfg3.shlibs
xorg-driver-fglrx.list
xorg-driver-fglrx.md5sums
xorg-driver-fglrx.postrm
xorg-driver-fglrx.preinst
happytop:/var/lib/dpkg/info#
``````
happytop:/var/lib/dpkg/info# rm fglrx-kernel-source*
rm: No match.
```I've been doing this long enough that it would be nice if you trusted me to know what's up as far as finding files :-P

Moving on..
dpkg -C (as root :-P) returns no broken or partially installed packages...
But there is also this, does this lend any hints?```
happytop:/var/lib/dpkg/info# dpkg -l |grep -i fgl
ii  fglrx-kernel-source                   8.16.20-0ubuntu16                    ATI binary kernel module source
ii  xorg-driver-fglrx                     6.8.0-8.16.20-0ubuntu16              Video driver for ATI graphics accelerators
```I'm still getting my cute little error, mind you.

I dunno what's up, I'm almost at the point of just ignoring it as it's really not that big a deal.
Nothing's _not_ installing, so it just seems like something I can ignore.
- Kev

---

### Post by mlomker on 2005-10-16
> rm: No match.[/code]I've been doing this long enough that it would be nice if you trusted me to know what's up as far as finding files :-P


You listed not only the incorrect command but its output...

> 
Moving on..


Indeed.

> 
(as root :-P) 


I manage a couple dozen servers and do not even have su access to all of them, myself (sensitive hr and accounting servers).  Sudo is how permissions are delegated in debian and a good habit, I think.

> 
Nothing's _not_ installing, so it just seems like something I can ignore.


That is something that I haven't seen before--an error with out the package list being there.  I assume that you can't apt-get the package and then remove it a second time?  Some people have had success downloading the .deb from [http://packages.ubuntu.org](http://packages.ubuntu.org) and using **dpkg -i** and then removing it...even when apt-get wasn't cooperating.  You could try the **--force** switches if need be.

---

