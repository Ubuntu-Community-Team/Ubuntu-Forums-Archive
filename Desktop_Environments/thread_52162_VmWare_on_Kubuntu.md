---
title: "VmWare on Kubuntu"
date: 2005-07-26
forum: Desktop Environments
---

### Post by vedro on 2005-07-26
ellow...

Since I am a carefull person and I read the documentation,   :smile:   I have a question: [Here](http://www.vmware.com/support/ws5/doc/intro_hostreq_ws.html#wp1000805)  it states that on those Linux distributions is vmWare working --> Supported distributions and kernels are listed below. VMware Workstation may not run on systems that do not meet these requirements.
So I`m asking you: Can I install the latest vmware on my Kubuntu dist and that it will work?

have a nice day, 
vedro

---

### Post by freelsjd on 2005-07-26
Yes.  Vmware will work fine on kunbuntu and debian systems.  I just compile the vmware modules as part of the normal vmware install procedure.  It is tied more to the kernel than the distribution.  I think vmwware works best if you compile your own kernel also.

---

### Post by vedro on 2005-07-26
ok... I`ll try  :) 

tnx for the info,
vedro

---

### Post by coaxx on 2005-07-26
vmware works here, too. But be aware it does not support Bridged Connections for WLAN Connections

---

### Post by vedro on 2005-07-27
ellow..

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What am I missing here?

vedro

---

### Post by vedro on 2005-07-27
ellow...

Solved the mystery  :)  sudo apt-get install linux-headers-`uname -r` did the job and VMware is working like a charm... Afcourse this solution was on the Forum  :) 

tnx, 
vedro

---

### Post by vedro on 2005-07-27
hmmm....

When starting the virtual OS I get the foloving message: Failed to open sound device /dev/dsp: Device or resourse busy 
Virtual device sound will start disconnect

Using Win XP Pro as the virtual OS

What to do?

have a nice day, 
vedro

---

### Post by freelsjd on 2005-07-27
In general, vmware has a problem sharing devices that are simultaneously being used by the Linux system.  For example, if you want to use a usb pen drive under vmware, you have to make sure the usb mass storage module is not loaded under linux; i.e., make sure that you cannot mount the pen drive under linux while you mount it under the virtual machine.  The KDE system has arts which allows multiple instances of sound to be played and I think that the alsa drivers now allow multiple instances to a certain extent.  My suggestion would be to make sure no sound application is enabled under linux, then try it under the virtual machine.

---

### Post by elgaelo on 2005-08-25
After installing VMWare Workstation in Ubuntu+KDE, suddenly the Kaffeine player was inaudible. I have also a "Error opening sound device /dev/dsp: resource busy or..." but once the session is started, no way to recover sound properties!!

Please...help me!...is only a software trouble isn't it??

thanks a lot

---

### Post by t2kburl on 2005-08-25
virtual machine's sound isn't worth having. I just Edit the settings for the virtual machine (XP, in your case) select the sound and uncheck "Connect at power on"

---

### Post by elgaelo on 2005-08-25
Hello kubuntu-guyss!!

Now, I lanched Kontrol Centrel withc 'sudo kontrol' and try the sound. The message in the console is sooo clear:

ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
handle==0
okay
unable to connect to sound server
unable to connect to sound server
unable to connect to sound server
unable to connect to sound server

What happens? I couln't believe that vmware and kubuntu are incompatible!!

Thanks... I'm going to try with Ubuntu Live CD!! Only to check that is a software problem!!

---

### Post by incinerator on 2005-08-25
Check the wiki: [https://wiki.ubuntu.com/VmWare](https://wiki.ubuntu.com/VmWare)

It won't hurt to install the vmware updates as listed in the "UBUNTU as a VMware guest", even if you are using it as a host. You will notice that the ftp server mentioned in the wiki page has a newer version of that aforementioned update available.

As for sound output, there is a simple solution: Go to that ftp server again and download the file named **vmwaredsp-1.3.tar.gz**
For installation instructions search the knowledge base at [http://www.vmware.com/](http://www.vmware.com/) . After installing that add-on you can use the command **vmwarearts** to get working sound output with vmware. Alternatively, edit the vmware menu entry in the kde menu to call **vmwarearts** instead of **vmware**.

---

### Post by patricia on 2005-08-28
[QUOTE=freelsjd]Yes.  Vmware will work fine on kunbuntu and debian systems.  I just compile the vmware modules as part of the normal vmware install procedure.  It is tied more to the kernel than the distribution.  I think vmwware works best if you compile your own kernel also.[/QUOTE]


Hi Guys!

I tried to install vmware on Unbuntu, but I got problem while running the configure script.

-----
What is the location of the directory of C header files that match your running
kernel? [/usr/src/kernel-headers-2.6.12-amd64-k8/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entrando no diretório `/tmp/vmware-config0/vmmon-only'
make -C /usr/src/kernel-headers-2.6.12-amd64-k8/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entrando no diretório `/usr/src/kernel-headers-2.6.12-amd64-k8'

  WARNING: Symbol version dump /usr/src/kernel-headers-2.6.12-amd64-k8/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[2]: scripts/Makefile.build: Arquivo ou diretório não encontrado
make[2]: *** Sem regra para processar o alvo `scripts/Makefile.build'.  Pare.
make[1]: ** [_module_/tmp/vmware-config0/vmmon-only] Erro 2
make[1]: Saindo do diretório `/usr/src/kernel-headers-2.6.12-amd64-k8'
make: ** [vmmon.ko] Erro 2
make: Saindo do diretório `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---


Could you hep me?  I have a compaq presario R3000 with a AMD 64 and the kernel is: 2.6.12-amd64-k8.


Thanks

---

### Post by incinerator on 2005-08-28
The error messages are telling you that the directory /usr/src/kernel-headers-2.6.12-amd64-k8 could not be found. You should not be surprised, it is linux-headers, not kernel-headers. You can easily verfy this by having a look at /usr/src/.

Also, with 2.6.12 kernel you will probably need to install [this vmware update](http://ftp.cvut.cz/vmware/vmware-any-any-update93.tar.gz)

---

### Post by flosoft on 2005-10-29
Here it starts compiling. But it crashes with the message:
gcc-3.4: installation problem, cannot exec 'ccplus': File or Directory not found.

---

### Post by Mark Rose on 2006-04-30
[QUOTE=flosoft]Here it starts compiling. But it crashes with the message:
gcc-3.4: installation problem, cannot exec 'ccplus': File or Directory not found.[/QUOTE]

apt-get install g++-3.4

---

### Post by flosoft on 2006-04-30
I have to say, the problem solved itself ;)

---

