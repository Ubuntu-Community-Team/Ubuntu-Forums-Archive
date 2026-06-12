---
title: "UVCVideo Driver problems - have driver need to install"
date: 2008-04-13
forum: Dell  Ubuntu Support
---

### Post by DSmyth on 2008-04-13
Hi There,

Newby so please excuse the terminology etc

Running an Inspiron 1520 with Gutsy 7.10 install. Having trouble getting the webcam operational. Have looked through all info here and realised that I needed UVCVideo driver - which I could not find after installation. 

Webcam is seen following lsusb. 

Anytime I attempt to visit driver site I get a timed out connection from firefox and if I try to grab it via terminal i get the following

svn: Can't connect to host 'svn.berlios.de': Connection timed out

SO... The guy who put me on to linux send me a driver which I now have in /lib/modules/2.6.22-14-generic. It is named uvcvideo.ko

He has had the driver in the path  /lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo

Does anyone know what way I should go about loading this driver up to get the camera working>?

Cheers

---

### Post by sdennie on 2008-04-13
You may not be able to load a kernel module that someone else built.  However, the default Gutsy kernel comes with the uvcvideo driver pre-installed.  It should load at boot time (on my XPS m1330 I see a little blue light blink a few times) but, if it doesn't, the following command will load it:

```

sudo modprobe uvcvideo

```

It sounds like you may have clobbered the default uvcvideo driver if you put someone else's module where you did so, that command may not work.  You may have to either rebuild the module from source or reinstall the kernel to get back the original uvcvideo driver.  I don't know why the server is timing out but, I would just keep trying.  I test a lot of kernels and so connect to that server frequently to get updates.

Also, once you get the drivers sorted out, you may not immediately see it working.  I believe that the driver only works with v4l2 so, to test it and set it up right, you may have to fire up gstreamer-properties and switch it to use v4l2 instead of v4l.

---

### Post by DSmyth on 2008-04-14
Hi Vor,

Thanks for the response. 

> ou may not be able to load a kernel module that someone else built. However, the default Gutsy kernel comes with the uvcvideo driver pre-installed. It should load at boot time (on my XPS m1330 I see a little blue light blink a few times) but, if it doesn't, the following command will load it:

Code:

sudo modprobe uvcvideo



I had tried this both before and after getting the driver. Returned FATAL: Module uvcvideo not found.

However... I was able to access the berlios website this evening and have resolved the issue.

Thanks for the help -

All sorted now
Thanks again.

---

### Post by psavva on 2008-05-16
Check if the driver is being loaded. Post it up here
```
dmesg | grep uvc
```

Check the camera is being detected. Post it up here as well.
```
lsusb
```



Please note, you will probably need the build-essential package if you don't have it installed. It's a package that provides you with common compiling tools
```

sudo apt-get install build-essential

```

You can get the uvcdriver from here
```

cd ~/ #go to your home directory
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk # download the uvcdriver from the subversion
sudo make # compile the driver
sudo make install # install the driver

```

I'm no professional, but i hope this works for you :-)

> **DSmyth said:**
> Hi There,

Newby so please excuse the terminology etc

Running an Inspiron 1520 with Gutsy 7.10 install. Having trouble getting the webcam operational. Have looked through all info here and realised that I needed UVCVideo driver - which I could not find after installation. 

Webcam is seen following lsusb. 

Anytime I attempt to visit driver site I get a timed out connection from firefox and if I try to grab it via terminal i get the following

svn: Can't connect to host 'svn.berlios.de': Connection timed out

SO... The guy who put me on to linux send me a driver which I now have in /lib/modules/2.6.22-14-generic. It is named uvcvideo.ko

He has had the driver in the path  /lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo

Does anyone know what way I should go about loading this driver up to get the camera working>?

Cheers

---

