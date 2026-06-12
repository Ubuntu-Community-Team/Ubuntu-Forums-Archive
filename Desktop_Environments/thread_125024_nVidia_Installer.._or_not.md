---
title: "nVidia Installer.. or not"
date: 2006-02-02
forum: Desktop Environments
---

### Post by finalzero on 2006-02-02
Hi,

Just wanted some info regarding the installation of nVidia drivers.  On Debian Sarge I was able to download and install the official nVidia Installer and found this method to be the best for building and installing the nVidia driver against the kernel however I am not sure what the best approach is on Ubuntu 5.10.

I downloaded the official driver package and made sure I had the latest kernel + the headers and source.  I chmoded the nVidia package so I could execute it from the console (I had to go into a terminal and kill the GDM session first, installer will not work otherwise) and then ran the installer:
```

sudo sh NVIDIA-........run  --kernel-source-path=/usr/src/linux-headers-2.6.12-10-686-smp

```
This fired up the nVidia installer (the option tells the installer where the kernel headers are) and I was able to continue however when the install attempts to test the version of GCC it fails.  I thought it was due to gcc not being present so I ran apt and downloaded the latest version:
```

sudo apt-get install gcc

```
Which pulled down gcc v4.0 and its associated libs.  I added the CC varaible to the environment:
```

sudo env CC=cc

```
Tested this, worked fine so I reran the command to start the nVidia installer however it still failed with the message:

**gcc-version-check failed**

No valid compiler found, please check the CC directive ... ... ...

I am not sure what is going wrong, it appears as if the nVidia installer simply doesn't believe gcc is present, even with the CC directive set explicitly.

I browsed the net and found Ubuntu users were downloading the nvidia-glx driver using apt however I would like to try to the use the official method as I am not sure how much difference there is between the nvidia-glx driver and the official release (version 81.78 ).

Thanks in advance,

Fz

---

### Post by finalzero on 2006-02-02
cool,

I had to do CC=gcc-4.0
export CC

Which resolved the issue with the CC check however the installer now fails when it reaches the end i.e. it seems to compile the driver and then when it tries to load it and finish up it reports an error:

**Unable to install driver**

I gave up using the official nVidia drivers, I tried the nvidia-glx method which worked fine.  If anyone has a solution to the official nVidia installer method please let me know as I would be interested to get that method working.

Cheers,

Fz

---

### Post by RAOF on 2006-02-02
The Breezy kernel is built with gcc-3.4, so you need to apt-get that specific version.  As for an nvidia driver guide, check out my sig.

---

### Post by finalzero on 2006-02-02
Okay I am on a roll today, managed to workout the problem after trawling through dmesg and the nvidia log file.

Looks like the nVidia installer is very picky about the versions of gcc, make and the libc headers so you have to make sure you get the right ones.

For those that want to install the latest nVidia drivers using the official nVidia installer (v81.78 ) follow these steps (I am 99% certain the below method works for Ubuntu 5.10):

1. Assuming you have a clean install of Ubuntu 5.10; if you do not, install Ubuntu (just hit enter to install the desktop version).

2. When you are at the Ubuntu log-in screen (log out if you are already at the desktop), press **Ctrl+Alt+F1** to switch to the console screen

2.1 (missed a step): type the following to kill the desktop:
```

sudo /etc/init.d/gdm stop

```
You should see a message indicating GDM stopped correctly.

3. Log-in with your user account (whatever you created during installation)

4. At the prompt type the following:
```

uname -r

```
This will display the current kernel image installed with the version number.  You can upgrade your kernel if you want however the Ubuntu 5.10 kernel is pretty fresh so you don't really need to touch this.

5. Now you need to search apt and download the matching headers for your linux kernel (I downloaded the source as well as I want to compile my own apps in the future) so if you are using kernel image 2.6.10-9-386 you will want the file labelled linux-headers-2.6.10-9-386:
```

sudo apt-cache search linux-headers-2.6.10

```
*returns a list of file names matching the string linux-headers-2.6.10*

Now download the correct one *(example)*:
```

sudo apt-get install linux-headers-2.6.10-9-386

```
Apt will download two packages, linux-headers-2.6.10 and linux-headers-2.6.10-9-386 and install them in the directory /usr/src

5.1 I will recommend you also install the kernel source as apt will install some necessary kernel build tools which I are useful:
```

sudo apt-get install linux-source-2.6.10

```
6. Now you want to make sure you have the development tools to make the official nVidia driver so do the following:
```

sudo apt-get install gcc-3.4
sudo apt-get install libc6-dev
sudo apt-get install make

```
This will download everything you need to compile the official nVidia driver so we can now build the driver and install it.

6.1 You need to setup the environment variables so the nVidia installer can locate the compiler, make and the libc6 headers (this caught me out) so do the following:
```

gcc-3.4 --version

```
Just to confirm gcc is really there, then do the following:
```

CC=gcc-3.4
export CC

```

7. I am assuming you have downloaded the official nVidia driver, if not go to the following location and grab the latest version (should be 81.78 ):

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

8. You need to chmod the file so its executable, go to the location where you downloaded the driver (I will assume in your home folder e.g. /home/yourname/) and type:
```

chmod 777 <whatever the file is called>.run

```
Now you need to execute the package so do the following:
```

sh <whatever the file is called>.run --kernel-source-path=/usr/src/linux-headers-2.6.10-9-386

```
the --kernel-source-path tells the nVidia installer where to find the kernel include files so it can compile the driver correctly.

When prompted hit Accept to accept the licence agreement.  Choose NO to the option to download precompiled headers, if everything is working you will see a progress bar with some messages telling you the driver is being built.  When complete you will get a prompt asking if the nVidia installer should configure your xorg.conf file, hit YES.

This will simply clean up the conf file and remove any options like dri that are not required.

9. Finally you can start X windows however I prefer to reboot (old Windows habit) so type:
```

sudo reboot

```
To reboot the system.  If everything worked you will see the nVidia logo flash up quickly (white background, green logo, depends on your graphics card) and then the Ubuntu log in screen.  You will also notice the desktop is faster, thats because the official drivers work great and the latest version has a built-in uninstall and repair feature so if you do update the kernel, simply rerun the installer and follow the prompts (you will be asked to uninstall the old driver before installing the new one).

Good luck!

Fz ;)

---

### Post by finalzero on 2006-02-02
I won't go into detail about how to setup the xorg.conf file however if you are using dual screens then go the following link and follow the directions on how to setup TwinView, I would recommend you copy some of the driver option settings even if you are using a single screen so you can benefit from the driver e.g:
```

Option   "NvAGP" "0"

```
This tells the nVidia driver to attempt to use AGPGART method to drive the graphics card (all modern intel based boards) and if that fails to use the drivers built-in method which is also as fast.  This makes a huge difference to the fps performance, you can test this in Gnome by firing up a terminal window and typing:
```

glxgears

```
Then maximize the window and wait a few seconds and close it, you should see some results in the terminal window, I was getting 3700 fps, just to give you an idea of how well my card performed :D

**TwinvView config**: [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

Adios,

Fz

---

### Post by finalzero on 2006-02-02
[QUOTE=RAOF]The Breezy kernel is built with gcc-3.4, so you need to apt-get that specific version.  As for an nvidia driver guide, check out my sig.[/QUOTE]

Cheers RAOF,

I didn't see your post as I was typing out my solution, I had a look at your links, allot of detail that I have not covered so I will go through them and make any changes I need to (I recommend you checkout ROAF's links as well to get all the info you need to know how to install the official nVidia driver).

Thanks,

Fz

---

### Post by finalzero on 2006-02-02
Some more TwinView links for dual monitor setup:

[http://www.simplyrender.com/TwinView.html](http://www.simplyrender.com/TwinView.html)

[http://ubuntuforums.org/archive/index.php/t-75149.html](http://ubuntuforums.org/archive/index.php/t-75149.html)

[http://lists.suse.com/archive/suse-linux-e/2001-Jun/att-0072/01-TWINVIEW_README](http://lists.suse.com/archive/suse-linux-e/2001-Jun/att-0072/01-TWINVIEW_README)

[http://www.gmpf.de/index.php/NVidia:Twin_View](http://www.gmpf.de/index.php/NVidia:Twin_View)

Fz

---

