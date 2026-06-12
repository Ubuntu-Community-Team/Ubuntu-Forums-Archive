---
title: "Ubuntu and Linux-GPIB"
date: 2011-01-11
forum: Education &amp; Science
---

### Post by wannabegeek on 2011-01-11
Hi all,

Has anyone had success using linux-gpib in their lab to control bench equipment ?

I plan to use MATLAB to send commands to a network analyser and a microwave
source. I'd like to avoid using a windoze machine with samba just to do data aquisition.

I have read the many NI web site posts about Ubuntu 8.10 and such but just wanted to check if anyone has just a basic GPIB setup working.

thanks in advance,
wbg

---

### Post by crasic on 2011-02-03
Hopefully you will get to read this reply though the question is three weeks old. 

It is actually quite doable to get GPIB-linux to work with Ubuntu. I've been using Debian as my instrumentation controller for a little over a year and just switched over to ubuntu 10.10, ubuntu would have been my first choice, but the old version of linux-gpib was incompatible with the 2.6.x x>24 kernels so I had to go with debian. Now that gpib-linux has been successfully patched for the new kernels i'm migrating over to ubuntu (its a lab computer so ubuntu is much friendlier as a general desktop OS)

The packages that you need to install are gpib-modules-source (module sources) and libgpib-bin (binary utilities). gpib-modules-source will also install all the build utilities and dependencies if you don't have them already (and the kernel headers). 

You can try to use the module-assistant to build the kernel modules, but this failed for me for whatever reason, instead I just downloaded the gpib-modules-source tarball from sourceforge.

What follows is the standard unpack-configure-build-install procedure that you must go through when installing from source (if you need me to elaborate on this please ask). The install script should place everything in the right locations and setup up the new gpib group - I'm running a vanilla x86 10.10 install and the build completed without any issues.

First step after installing the kernel modules is to test that everything installed as planned. You can either reboot, or load the proper kernel module by hand (board model -> driver module name chart is located [_here_]("http://linux-gpib.sourceforge.net/doc_html/x259.html#HARDWARE-MATRIX") ). Run ```
sudo gpib_config
``` followed by ```
 sudo ibtest
``` (we are using sudo because we haven't set permissions for the gpib device node yet). ibtest should give you a prompt asking you for wheather you want to open a device or a board (device), then it will ask you for the GPIB address of the device. Write a string (w) to the device - *IDN?  is a good one because its universal and spits back the name of the device, get the response to the query by asking ibtest to read (r) 100 characters or so. 

If the above test worked then you are ready to setup permissions. Create a new file in /etc/udev/rules.d named 70-gpib.rules or something similiar (the number in front doesnt really matter, it only determines which rules will be set first) and add the following line 

```
KERNEL="gpib[0-9]*",    MODE="0660", GROUP="gpib"
```then proceed to add yourself and any other users to the gpib group.

Once this is done you can install python-gpib (python bindings for the library), you can also edit /etc/gpib.conf to address your devices by name (rather than looking up their id's every time) - this is necessary for python-gpib (when you instantiate a device it wants a name and not a address). You should read in the documentation on how to do this properly. (Look at the examples in the conf).

You should reboot after setting the udev rules (or change the permissions by hand for this session if you don't want to restart yet), restarting udev didn't seem to do the trick.

---

### Post by wannabegeek on 2011-02-03
thank you very much....super helpful...

I'll post back when I get the NI card installed....

cheers,
wbg

---

### Post by crasic on 2011-02-03
I forgot to add, the driver package that corresponds to gpib-modules-source (and where you should look for the source tarball) is [linux-gpib]("http://linux-gpib.sourceforge.net/"). It works just as well for writing your own control software (in python,c, etc.) , unfortunately I've never tested it with labview or any official NI software.

I haven't had any luck with the official NI visa drivers (they won't compile, new kernels aren't supported etc. etc.) which is why I'm sticking to the open source driver.

I forgot to add, I'm using the NI, gpib-pci card, if you need to use a usb adapter it requires some intermediate steps (something about loading the firmware - I've never done it myself)

---

### Post by crasic on 2011-02-10
Because you indicated in your pm that you had some hesitations with compiling the drivers from source I decided to write up a short thing to walk you through the process and for the benefit of anyone else that stumbles upon this thread.

First, make sure all the dependencies are satisfied, luckily for us there is an abortive Ubuntu package in the repository (gpib-modules-source) that while failing to install the drivers,  installs all the dependencies it requires (which are the same as for the sourceforge version).

Second, get the tarball from sourceforge (link in my first post), extract using 
```
tar -xzf sourcetarball.tar.gz
```change into the directory and run the configure script 
```
./configure
```Assuming the config went fine run make to build the module
```
make
```You can take a 10 minute break here, building the module will not require root privileges in most cases. After the build is complete install the module using the provided install script
```
 make install
```Luckily for us, the library maintainers wrote a competent install script that places the modules in the correct location and sets up a gpib user group for you.

At this point you can proceed to do as I explained in my first post (test the installation and setup privileges).

P.S. in order to use modprobe to load the driver module (without restarting) look up the name of the driver for the specific board from the link in my first post and do (example is for the NI pci-gpib board)
```
sudo modprobe tnt4882
```

---

### Post by wannabegeek on 2011-02-10
hi again....

I downloaded from the repo and installed the gpib-modules-source  and libgpib-bin.

went to sourceforge and  got linux-gpib tar ball and I think everything compiled correctly...I don't have the PCI card yet
so cannot test.

I was worried when I first looked at the supported hardware page since I didn't see our HP 8510C, then realized that
I should be looking for the gpib card....looks like newer equipment doesn't need an interface card...

wbg

---

### Post by crasic on 2011-02-11
> **wannabegeek said:**
> 
I should be looking for the gpib card....looks like newer equipment doesn't need an interface card...

wbg


Newer equipment typically has more interface options (usb, ethernet) so GPIB has been phased out slowly, but I've seen even brand new equipment with GPIB options (albeit an expensive option). Like a lot of other legacy systems (in science and otherwise), there is just SO much old equipment out there still in full use that exclusively use GPIB that it's unlikely the standard will completely die out anytime soon. 

Plus an interface card is sure cheaper than a new network analyser.

---

### Post by wannabegeek on 2011-02-16
HI crasic...hope you're still checking this thread ...:)

I installed everything per your instructions, got my card in the mail and tried to test test tonight.
I connected the cable to the display portion of the network analyzer....there's already two cables in parallel so this makes the 3rd...


here's what I did:
```

Choose Device, gpib address 0  (guessed since I saw /dev/gpib0-15)

: w
enter a string to send to your device: *IDN?   
sending string: *IDN?

gpib status is: 
ibsta = 0xc100  < ERR TIMO CMPL >
iberr= 6
EABO 6: Operation aborted

ibcnt = 0

```


I did some poking around:
```

daniel@debye-desktop:/etc$ dmesg | tail
[  571.959680] gpib: (debug) request module returned 256
[  584.648672] gpib: (debug) request module returned 256
[  584.648691] gpib0: exiting autospoll thread
[  584.648758] pci 0000:04:00.0: PCI INT A disabled
[  584.648792] pci 0000:04:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  584.648959] mite: 0xfb104000 mapped to ffffc90000c70000
[  584.648970] mite: daq: 0xfb100000 mapped to ffffc90000c78000
[  584.648986] tnt4882: irq 21
[  590.433937] gpib: (debug) request module returned 256
[  596.163263] tnt4882: write timed out

```

---

### Post by kerrykuta12 on 2011-02-17
Hi! Very glad to be able to see your post, you said well, I agree, thank you, hope to see more of your articles, continue!

---

### Post by tkbaldwin on 2011-02-24
Crasic, I wonder if you could on elaborate on how the gpib-modules-source package failed for you. I'm following along on xubuntu 10.10 with a NI-branded GPIB PCI card, and I'm curious if mine would fail in the same way.

According to the package information, it only includes the source for the GPIB kernel modules. It doesn't claim to configure, build or install them for you, nor does it tell you where it put the source after downloading. I'm having a hard time figuring out what the point of this package is supposed to be.

(I know it serves the purpose of grabbing all dependencies for a tarball install, but that can't be what the maintainer had in mind.)

---

### Post by tkbaldwin on 2011-02-24
Anyway, I did some homework and tried the module-assistant process which Crasic hinted at, and it failed for me too. Here's the lowdown in case anybody else wants to try it.

After grabbing gpib-modules-source and libgpib-bin from the ubuntu software center, drop to a command line and use module-assistant, like:

```
sudo m-a prepare
sudo m-a update
sudo m-a list
```On this list was an entry showing that it picked up the souce distribution I just downloaded.

```
gpib-modules-source (source) installed (V: 3.2.11-0.2ubuntu4):
  -- Binary package(s) for kernel(s):
   + (2.6.35-24-generic): not found
```So far so good. I tell it to auto-install:

```
sudo m-a a-i gpib-modules
```It seemed to work for a bit and then failed without being specific about how, with a pretty unhelpful log file:

```
/usr/src/modules/gpib/agilent_82357a/agilent_82357a.c:1543: error:         
implicit declaration of function &#8216;info&#8217;                                    
make[4]: *** [/usr/src/modules/gpib/agilent_82357a/agilent_82357a.o] Error 1
make[3]: *** [/usr/src/modules/gpib/agilent_82357a] Error 2                
make[2]: *** [_module_/usr/src/modules/gpib] Error 2                       
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'      
make[1]: *** [binary-modules] Error 2                                      
make[1]: Leaving directory `/usr/src/modules/gpib'                         
make: *** [kdist_build] Error 2 
```Sound familiar? Whatever, I don't even have an agilent branded card. I'll try compiling the generic sourceforge distribution next, like you said.

---

### Post by tkbaldwin on 2011-02-24
Ok, crasic's instructions on installing from the source tarball worked for me. However, I was a little disappointed by the python bindings provided in the ubuntu package python-gpib - as mentioned previously, it only supports referring to an instrument by name, not by address. This seems a little backwards, and I don't want to have to tweak /etc/gpib.conf every time I change the gpib address of an instrument.

The sourceforge package contains some improved python bindings, but it won't install them if it can't find the Python.h header file. The solution to this, I think, is to add the python-dev package before building linux-gpib from the source tarball.

To tack the improved bindings on afterward (as I did), first remove the ubuntu python-gpib package if you installed it. Then, in your linux-gpib source tree, cd into language/python and do

```
python setup.py build
sudo python setup.py install
```

This should compile the bindings. To reiterate, these steps should only be necessary if python-dev was installed *after* linux-gpib.

cd to some other directory, open python and try it out:

```
>>> import Gpib
>>> inst = Gpib.Gpib(0,12) # zeroth board, address 12
>>> inst.write("*IDN?")
>>> inst.read(100) # read 100 bytes
'My instrument name\r\n'
```

Ok, it works. The documentation is nearly non-existent but we have the basics. 

PS: There is an "ask" method on the instrument, which appears to be different from "write then read". Anyone know what this is for?

---

### Post by crasic on 2011-02-26
I thought I subscribed to this thread so sorry for the late reply.

My module-assistant build failed in the same way that yours did, I just ended up installing from source as explained and everything works fine for me.

python-gpib is a bit disappointing, AFAIR pyvisa provides a much more useful interface and is compatible with linux-gpib, the only reason I suggested python-gpib is because its simple and a direct binding for the library.

>  PS: There is an "ask" method on the instrument, which appears to be  different from "write then read". Anyone know what this is for?

if I remember correctly ask is just write then read, maybe with a delay or something.

---

### Post by tkbaldwin on 2011-03-17
Crasic - I used PyVISA when I was on windows and I agree, it's great. But it also depends on NI-VISA, a proprietary layer between the GPIB interface (aka 488.2) and whatever python code you are writing. Installing NI-VISA on non-Red Hat systems sounds like a nightmare scenario (converting .rpm files to .deb files, general apathy from NI, etc.) - I'd rather convert all my scripts to use the crappy open-source python bindings that at least work. Correct me if I'm wrong.

wbg - you PM'd me about a week ago looking for help, did you get it sorted out? If you're still having problems it would be best to address them here, in this thread.

---

### Post by Sara on 2011-03-23
I have just been through the saga of setting up NI-VISA on Lucid. This is the second time. I did it on Hardy a couple of years ago. It does not get any easier.
 
It all works fine for RS232 connected instruments. 

I have considerable Python instrument control and system applications that run fine on Windows and the serial parts run better on Linux, mainly because they do not fight with the essential virus scanners in M$. One system needs to operate near real time, hence the use of Linux and a low latency kernel if necessary. 

I have installed linux-gpib, and can talk to instruments using ibtest without a problem.

I cannot however get the NI-VISA installation to recognise a 488 PCI card with linux-gpib drivers.

I have run gpib_config for the linux-gpib and updateNIDrivers for the NI-VISA but the card will not come up in the VISA-Configuration, even if I try to manually add it static. 
VISA cannot find the library component to talk to the card.

Any ideas?

By the way, the NI-VISA package includes NI-SPY which none of the installation instructions mention. This is a very useful too for debugging instrument communication but beware, if time is critical it will slow things down.

---

### Post by Takala on 2011-05-23
> **crasic said:**
> Hopefully you will get to read this reply though the question is three weeks old. 

It is actually quite doable to get GPIB-linux to work with Ubuntu. I've been using Debian as my instrumentation controller for a little over a year and just switched over to ubuntu 10.10, ubuntu would have been my first choice, but the old version of linux-gpib was incompatible with the 2.6.x x>24 kernels so I had to go with debian. Now that gpib-linux has been successfully patched for the new kernels i'm migrating over to ubuntu (its a lab computer so ubuntu is much friendlier as a general desktop OS)

The packages that you need to install are gpib-modules-source (module sources) and libgpib-bin (binary utilities). gpib-modules-source will also install all the build utilities and dependencies if you don't have them already (and the kernel headers). 

You can try to use the module-assistant to build the kernel modules, but this failed for me for whatever reason, instead I just downloaded the gpib-modules-source tarball from sourceforge.

What follows is the standard unpack-configure-build-install procedure that you must go through when installing from source (if you need me to elaborate on this please ask). The install script should place everything in the right locations and setup up the new gpib group - I'm running a vanilla x86 10.10 install and the build completed without any issues.

First step after installing the kernel modules is to test that everything installed as planned. You can either reboot, or load the proper kernel module by hand (board model -> driver module name chart is located [_here_]("http://linux-gpib.sourceforge.net/doc_html/x259.html#HARDWARE-MATRIX") ). Run ```
sudo gpib_config
``` followed by ```
 sudo ibtest
``` (we are using sudo because we haven't set permissions for the gpib device node yet). ibtest should give you a prompt asking you for wheather you want to open a device or a board (device), then it will ask you for the GPIB address of the device. Write a string (w) to the device - *IDN?  is a good one because its universal and spits back the name of the device, get the response to the query by asking ibtest to read (r) 100 characters or so. 

If the above test worked then you are ready to setup permissions. Create a new file in /etc/udev/rules.d named 70-gpib.rules or something similiar (the number in front doesnt really matter, it only determines which rules will be set first) and add the following line 

```
KERNEL="gpib[0-9]*",    MODE="0660", GROUP="gpib"
```then proceed to add yourself and any other users to the gpib group.

Once this is done you can install python-gpib (python bindings for the library), you can also edit /etc/gpib.conf to address your devices by name (rather than looking up their id's every time) - this is necessary for python-gpib (when you instantiate a device it wants a name and not a address). You should read in the documentation on how to do this properly. (Look at the examples in the conf).

You should reboot after setting the udev rules (or change the permissions by hand for this session if you don't want to restart yet), restarting udev didn't seem to do the trick.

Hi, I have a "National Instruments[ GPIB-USB-HS]("http://linux-gpib.sourceforge.net/doc_html/x259.html#NI-USB-HS")" GPIB device and I tried to install it by using this nice how-to. I succeeded, so thank you very much for the information you have shared! However, for me the "board_type" was incorrect in "/etc/gpib.conf" for some reason so I had to change it from "ni_pci" to "ni_usb_b" which is the correct type based on the information that was in the shared link([http://linux-gpib.sourceforge.net/doc_html/x259.html#HARDWARE-MATRIX](http://linux-gpib.sourceforge.net/doc_html/x259.html#HARDWARE-MATRIX)).

Thank you again!

---

### Post by Takala on 2011-05-23
Guys, I have a weird problem.

When I create the group "gpib", and add myself there, I'm still not able to read or write to the gpib device. If I change the udev rule to for example
```
KERNEL=="gpib[0-9]*", MODE="0660", GROUP="dialout"
```
then it works (I'm also in the dialout group)

So if I create the group myself, it is not working. But if I use an existing group it works...
Why this is happening?

---

### Post by wannabegeek on 2011-06-15
Hi everyone,

I have been spending some time understanding the gpib library functions, but still 
unsure of how gpib and Gpib work. I didn't know there was a difference in Gpib and gpib until recently.

I have opened a python prompt and imported gpib, and tried help(gpib). I get a short list of useful commands which seems to mirror some of the c library commands.

Is it possible to call any of the c library functions with gpib ? Such as:
gpib.[ReadStatusByte]("http://linux-gpib.sourceforge.net/doc_html/r2714.html")    ?


I am not at the lab and cannot try  just yet. I am curious what help(Gpib) will show.

I am considering writing my control program in C, since I don't know numpy and need resources like fscanf.

If I do write in C and need to link to the gpib library, can I just put 
#include <gpib/ib.h>

in the header ?  

thanks in advance,
wbg

---

### Post by karik_o on 2012-02-01
I am using NI GPIB-PCI card to control a LeCroy 8901a Camac interface. I have installed the linux-gpib package on ubuntu 10.10. When I run the ibtest I get this

 : w
enter a string to send to your device: *IDN?
sending string: *IDN?

gpib status is: 
ibsta = 0xc100  < ERR TIMO CMPL >
iberr= 6
EABO 6: Operation aborted

ibcnt = 0

and also in my program the ibwrt function does not send any data. Can someone please help me? I know this is an old thread but I really need some help.

Thanks in advace,

karik

---

### Post by wannabegeek on 2012-02-02
Hi Karik,

I haven't worked in the lab where I set up the GPIB interface in a long time...but I recall getting that message often .

It may be true, that your bench device doesn't know the command '*IDN?' not all do. It's a standard command, but the VNA I sent it too never responded.

Try a different command.

Also, did you set up your config file for the GPIB card ?

Consider skipping ibtest and try python.

---

### Post by karik_o on 2012-02-02
I tried different commands but still my LeCroy 8901A doesn't respond. I've set up the gpib.conf file. Here it is 

interface {
    minor = 0
    board_type = "ni_pci" 
    name = "ni"
    master = yes
    pad = 1
    sad = 0
}

I can send commands using the c function in ibtest, but I cannot read nor write.

---

### Post by wannabegeek on 2012-02-03
I would stop using ibtest since you can't really trouble shoot it....start using the python linux-gpib library.


However, you should look at your configuration file and be sure that you are communicating with the right address. I think the default is channel 16.  Check to make sure your device is listening on channel 16. I  vaguely recall that the conf file also uses a named device. Please post the entire conf file here. I don't have access to it anymore.



EDIT:
AS I recall, in gpib, you send by 'writing' and then wait, then read in so many bytes. Using  gpib.find sets the channel and gpib.close resets it.
Did you try a different gpib command, preperably one from the LeCroy manual ?

---

