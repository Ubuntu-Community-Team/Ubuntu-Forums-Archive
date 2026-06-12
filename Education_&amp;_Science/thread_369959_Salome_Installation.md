---
title: "Salome Installation"
date: 2007-02-25
forum: Education &amp; Science
---

### Post by in_flu_ence on 2007-02-25
Hi,

   Anyone having success in installing Salome in Ubuntu? I keep on getting an error of

Not supported Linux platform!

error while loading shared libraries: libmng.so.1: cannot open shared object file: No such file or directory

    when i try to run python runInstall.

   Any help?

Thanks

---

### Post by in_flu_ence on 2007-03-08
The above mentioned problem seems only exist for 64bit ubuntu/kubuntu.

I had tried running python runInstall in a 32bit environment. It works. Basically, it will ask you to make some decision on gcc and stuff and I just not install gcc and use the default for the remaining.

There seems to be an error in the KERNEL_3.2.2/salome.sh at the end.

so change the 2nd line using a text editor to the following

```
output=`echo $1 $2 | awk **-W sprintf=5060** -v dir=$3 '{        \
```

Do not do a copy and paste because the ` sign seems always give people problem. just add the bold part to the default .sh file.

I have created another .sh file to auto run both the source salome.sh function and ./runSalome function since that is not activated once the terminal is closed.

Hope this helps.

---

### Post by in_flu_ence on 2007-03-18
To resolve the 64bit libmng.so issue, I have downloaded the debian package from the official site.
Then place the zipped files into /usr/lib32

After which, the installation should run smoothly according to the Readme provided in the official package.

Remember to add the lib32g2c0 package from adept or synaptic.

Hope this helps for those who use the software.

---

### Post by in_flu_ence on 2007-03-22
For those using Salome to export mesh to OpenFOAM in unv format, there is a unv convertor available as attached. While it is not officially within the OpenFOAM package, it has been reported to work. So it should work but with no guarantee/warranty.

1)To make it work, simply unzip it into the ~/OpenFOAM/OpenFOAM-1.3/applications/utilities/mesh/conversions/

2) Type in: cd unvToFoam

3) Type in: wmake

Once compiled, it should work.

**Common issue**
During compilation, I notice that there is an error message of the following
/usr/bin/ld: cannot find -liberty

To resolve this, install the binutils-dev package via synaptic, adept or apt-get.

Recompile the convertor by using wmake at the unvToFoam folder.

**Support**
I do not provide support for this convertor since it is not made by me. You can get support from the official OpenFOAM forum.

Good Luck

---

### Post by lc_2007 on 2007-05-15
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2209380](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2209380)

Hi, I am having trouble installing Salome on Ubuntu 7.04 32bit machine.  Have you installed it on 7.04?  Thanks.

---

### Post by skidzo on 2008-08-27
I am experiencing some troubles after installing Salome Platform 3.2.6 (the sarge binary Install wizard) on Ubuntu Hardy Heron 64 bit...

did all the steps that where mentioned so far and could install whithout errors showing up during the install process.

afterwards, when doing

 $~/salome_3.2.6/KERNEL_3.2.6/bin/salome$ ./runSalome

I get:

```
Traceback (most recent call last):
  File "/home/digital/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 23, in ?
    import orbmodule
  File "/home/digital/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 21, in ?
    from omniORB import CORBA
ImportError: No module named omniORB
```

I placed the libmng.so.1 in /usr/lib32 and also added the lib32g2c0 package, and made the change to salome.sh.

Any more suggestions?

[http://salome-platform.org/forum/?groupid=10&forumid=9&thread=1990](http://salome-platform.org/forum/?groupid=10&forumid=9&thread=1990) could help... I'm trying this now

---

### Post by Jagermeister on 2008-11-12
I wrote installation instructions for Salome-Meca 2008.1 (Salome with Code_Aster integrated) here:

[http://www.caelinux.org/wiki/index.php/Doc:Installing_Salome-Meca-2008.1](http://www.caelinux.org/wiki/index.php/Doc:Installing_Salome-Meca-2008.1)

Also, I read in the CAELinux forums that the next version of CAELinux will most probably be based on Ubuntu 8.04 LTS 64-bit, around March next year.

---

### Post by benjas83 on 2008-12-26
Thanks for your information.

---

### Post by AMAMH on 2009-05-25
> **in_flu_ence said:**
> To resolve the 64bit libmng.so issue, I have downloaded the debian package from the official site.
Then place the zipped files into /usr/lib32

After which, the installation should run smoothly according to the Readme provided in the official package.

Remember to add the lib32g2c0 package from adept or synaptic.

Hope this helps for those who use the software.

thanks man, that saved my ******* day ;)

---

