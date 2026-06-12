---
title: "Unable to resolve function glXQueryExtension in HyperView"
date: 2010-07-13
forum: Desktop Environments
---

### Post by andylinux on 2010-07-13
When using the HyperWorks FEA software HyperView with Ubuntu Lucid the following error is displayed,
ChoosePixelFormat Failed. Cannot find a suitable pixel format
Also in the terminal this error appears,
Unable to resolve function glXQueryExtension is displayed.

This issue can be fixed by doing the following for nvidia cards,
sudo ln -s /usr/lib/nvidia-current/libGL.so.1 /usr/lib/libGL.so.1

or for ATI cards,
sudo ln -s /usr/lib/fglrx/libGL.so.1 /usr/lib/libGL.so.1

Note you must install the Nvidia or ATI proprietary drivers for opengl graphics support to be able to use HyperWorks.

---

### Post by afrodocter on 2010-08-11
i have a similar problem with a different program. the program is HFSS, and uses mainwin to provide the windows interface.

either way, the program runs but i get an error which indicates that i dont have opengl installed.  the error on the command line is

Unable to resolve function glXQueryExtension

i have made the following links which are slightly different on my system, i am running 10.04.
```

> ls -al /usr/lib/libGL*
lrwxrwxrwx 1 root root     38 2010-08-11 11:42 /usr/lib/libGLcore.so.1 -> /usr/lib/nvidia-current/libGLcore.so.1
lrwxrwxrwx 1 root root     34 2010-08-11 11:39 /usr/lib/libGL.so.1 -> /usr/lib/nvidia-current/libGL.so.1

```

i get the same error. any ideas?

---

### Post by andylinux on 2010-08-12
Do you have the nvidia proprietary drivers installed?
Look under, System, Administration, Hardware Drivers

I don't have the libGLcore.so.1 file you show below.  Did you install the nvidia drivers from Ubuntu or some alternative way such as downloading from the nvidia website.

What is the output of this command,  
glxinfo |grep -i open
you might have to install this package to get the glxinfo command,
sudo apt-get install mesa-utils

Do other opengl programs work?

I figured this issue out from this bug.
[https://bugs.launchpad.net/bugs/589250](https://bugs.launchpad.net/bugs/589250)

---

### Post by afrodocter on 2010-08-12
i am actually trying to get this to work on two machines one has a nvidia driver and the other the mesa driver. i used teh ubuntu driver installer for the nvdia i believe, 

note,  this glx problem arose when i upgrade both machines from  9.10, to 10.04

the other machine i am trying to get this to work on which has intel graphics has 
```

> lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
> 

```

i have whatever the supported kernel driver is for that chip, here is the output of what you suggested
```
> glxinfo | grep -i open
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

and glx programs, like glxgears, work. 

on this laptop the libGL links i made are slightly different than the other machine i listed, but neither are working. 
```

> ls -al /usr/lib/libGL*
lrwxrwxrwx 1 root root     22 2010-08-11 12:53 /usr/lib/libGL.so -> /usr/lib/mesa/libGL.so
lrwxrwxrwx 1 root root     24 2010-08-11 12:53 /usr/lib/libGL.so.1 -> /usr/lib/mesa/libGL.so.1
lrwxrwxrwx 1 root root     20 2010-06-22 08:56 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070701
-rw-r--r-- 1 root root 461488 2010-04-29 01:54 /usr/lib/libGLU.so.1.3.070701

```

---

### Post by andylinux on 2010-08-12
I only tested this issue with HyperView and Nvidia and ATI cards.  I don't know if it will work with Intel graphics as HyperView isn't supported with Intel Graphics.

Did HFSS work with Intel graphics with Ubuntu 9.1? 

Maybe you can use the ldd command to see what libraries the HFSS program is looking for?  

You do need to find the actual executable file for the program.  For example /usr/bin/thunderbird is a script.  I look into the script to find the actual program file.  If you do this you might get a message saying something like libmozjs.so => not found.  Then you need to locate that file and see if you can figure out where HFSS is looking for the file.

ldd /usr/lib/thunderbird-3.0.6/thunderbird-bin 
	linux-gate.so.1 =>  (0x006df000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00fb0000)
	libmozjs.so => not found
	libxpcom.so => not found
	libxpcom_core.so => not found
	libplds4.so => /usr/lib/libplds4.so (0x004dc000)
	libplc4.so => /usr/lib/libplc4.so (0x00287000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00110000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x0071000

Another thought is to compare the ldd command HFSS results on Ubuntu 9.1 to Ubuntu 10.04.
Last HyperView also uses mainwin so maybe this has something to do with mainwin.

---

### Post by afrodocter on 2010-08-13
thanks, that advice is very helpful. from the output show at the bottom,  it seems like the hfss doesnt work with ubuntu's new linking system. because the main executable is  missing a bunch of stuff. 

but. . . 

i noticed another thing which may be my problem. i tried to re-install the mainwin libraries (the existing ones where left over from my 9.1 install). and i got an error about start up scripts. the install claimed it needed chkconfig, so i installed that, but it doesnt seem to work. 
if the mainwin is not working correctly because its left over from the old install then maybe this is a[nother] problem?

```

> insserv:  loop involving service apache2 at depth 3
> insserv:  loop involving service rsyslog at depth 2
> insserv:  loop involving service udev at depth 1
> insserv: There is a loop between service apache2 and rsyslog if stopped
> insserv: exiting now without changing boot order!
> /sbin/insserv failed, exit code 1
> mwcore_services           0:off  1:off  2:off  3:off  4:off  5:off  6:off
> Error: Attempt to add service via chkconfig failed.
> Failed.

```

and here is the output from ldd of the main exe. 

```

/opt/ansoft/hfss11# ldd hfss.exe 
        linux-gate.so.1 =>  (0xf7713000)
        libngcore.so => not found
        libdesktop.so => not found
        libolepro32.so => not found
        libot803as.so => not found
        libuiresources.so => not found
        libuicore.so => not found
        libsfl203as.so => not found
        libcomdlg32.so => not found
        libshell32.so => not found
        libcomctl32.so => not found
        libshlwapi.so => not found
        liboleaut32.so => not found
        libole32.so => not found
        librpcrt4.so => not found
        libmfc400s.so => not found
        libgdiuser32.so => not found
        libmsvcrt.so => not found
        libadvapi32.so => not found
        libuuid.so => /lib32/libuuid.so (0xf76e8000)
        libkernel32.so => not found
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf75cb000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf75bb000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf75a1000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf74ab000)
        libm.so.6 => /lib32/libm.so.6 (0xf7485000)
        libc.so.6 => /lib32/libc.so.6 (0xf732b000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf730c000)
        /lib/ld-linux.so.2 (0xf7714000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf72f1000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf72ed000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf72e9000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf72e3000)

```

---

### Post by afrodocter on 2010-08-13
i used this bash command to determine which executables where using libGL and whether the link was good or not. the funny thing is, they all look good. 
could this be a 32/64 bit issue?

[CODE]
/opt/ansoft/hfss11# for i in *; do if [ -f $i ]; then ldd $i | grep libGL && echo $i ;fi;done
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7151000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6caf000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5681000)
libem_moduledll.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7341000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6e9f000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5871000)
libempostdll.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf716d000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6ccb000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf569d000)
libfieldspostprocessor.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf61b5000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf60f0000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf4703000)
libgeometry3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf6ccd000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf682b000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf51fd000)
liblayouttranslator.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf765d000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf71bc000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b8d000)
libmodulebase.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf764c000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf71aa000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b7c000)
libplot3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7601000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf7160000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b31000)
libreport3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7631000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf756c000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b80000)
libview3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7322000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf712f000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5852000)
libvkitools_ported_optimized.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7676000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf75b1000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b4a000)
mesh3d_ng
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7648000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf7583000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b1c000)
modeler3
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf76c7000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf7602000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b9b000)
stepiges2sm3
[\CODE]

---

### Post by andylinux on 2010-08-15
Interesting bash command.  I will have to try that command with HyperView.

I never thought about the 64bit / 32 bit aspect.  All of my testing with HyperView was using a 64 bit version of Ubuntu running a 64 bit version of HyperView.  I haven't tried 32 bit.

I assume you are using 64 bit Ubuntu?

The only thing I could think of would be to reinstall the nvidia driver?  
Probably won't help but you could try it.

Do the 3d compiz-fusion visual effects work?  If they do then that would mean the opengl drivers are installed and working.

Last maybe Ansoft would help you with the issue.  

And one more thought would be to install 9.10 on a machine (or dual boot 9.10 & 10.04) and run your bash script on 9.10 (assuming hfss worked on 9.10) and compare your results to see if you can figure it out.

---

### Post by andylinux on 2010-08-16
I was trying to use your command on HyperView and could not get it to work.  Did you come up with this command yourself or did you find this somewhere else?  If somewhere else can you send a link so I can understand how it is supposed to work. 

I'm confused by the "#" as I thought was a comment in bash.  

/opt/ansoft/hfss11# for i in *; do if [ -f $i ]; then ldd $i | grep libGL && echo $i ;fi;done

---

### Post by ShouriChatterjee on 2010-08-19
I was trying to get allegro (32-bit) to work on my 64-bit ubuntu machine. No graphics card (intel graphics.) I was facing the same (and more) errors.

Inserting /usr/lib32/mesa in front of the LD_LIBRARY_PATH variable did the trick.

Hope that helps.

---

### Post by cioma on 2010-08-29
This also solved the problem with Mentor Graphics HyperLynx 8.1 under Lucid 10.04 amd64
Thanks a lot!

---

### Post by cioma on 2010-11-21
But Mentor Expedition 7.9.1 on Ubuntu 10.10 with NVIDIA driver 260.19.21 tells there is no OpenGL support on my system which is incorrect.
Perhaps the problem is in libGLU.so.1 that reports wrong information to the Expedition?

---

