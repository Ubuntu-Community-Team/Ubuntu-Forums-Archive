---
title: "Installing NVIDIA Drivers"
date: 2005-07-17
forum: Desktop Environments
---

### Post by matva on 2005-07-17
I just made the switch, and i'm trying to get quake3 up and running on kubuntu. I have got q3 set up, but when i run it i get:
You are using software Mesa (no hardware acceleration)

From what i have read, i need to install my nvidia drivers. Well i have found and downloaded them, but installing them is difficult (for me). 

I followed the instructions which included logging out of x and doing the sh command to run it. Some way through the installation it asks me for my kernel source so it can build something. How do i get my kernel source and create the symbolic links etc??? i tried it once before, but i think i did something wrong because it didn't work. 

After i install the nvidia drivers, what do i need to edit (if anything) in my x config so that i can run quake3?

As i said, i just made the switch, so i am a bit of a newb. 

Thanks for any help.

---

### Post by netrattler on 2005-07-17
Here are instructions for the Nvidia drivers unless you want to compile them yourself.

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Joe

---

### Post by matva on 2005-07-17
Ok.

I tried the commands listed:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Everything seemed to work except 

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

it says: sudo: gedit: command not found

Also, don't i have to install the nvidia drivers specific to my card? I had the idea that the above commands were for something different.

---

### Post by farfargoth on 2005-07-17
first of all it's easier if you just apt-get nvidia-glx and nvidia-settings from a debian repository (or download them from [http://debian.org](http://debian.org) and do "sudo -i nvidia*.deb" in the directory where you downloaded them.

if i remember correctly i used a program called nvidia-config or nvidia-setup or something for the configuration. search for it on your harddrive after you've installed the packages. 
if it's not there, you can read the documantation in /usr/share/doc/nvidia-glx/*..

---

### Post by matva on 2005-07-17
[QUOTE=farfargoth]first of all it's easier if you just apt-get nvidia-glx and nvidia-settings from a debian repository (or download them from [http://debian.org](http://debian.org) and do "sudo -i nvidia*.deb" in the directory where you downloaded them.

if i remember correctly i used a program called nvidia-config or nvidia-setup or something for the configuration. search for it on your harddrive after you've installed the packages. 
if it's not there, you can read the documantation in /usr/share/doc/nvidia-glx/*..[/QUOTE]
 well i already ran the above commands. I restarted and quake3 is still using mesa. Maybe i need to change something in my config? how do i do this?

---

### Post by coolclassic on 2005-07-17
Have a look in the following file:/etc/x11/xorg.conf and see if you can find an entry like this:



Section "Device"
 Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
 Driver  "nvidia"
 BusID  "PCI:1:0:0"

If the entry for Driver reads "nv" thenjust replace this with "nvidia"

---

### Post by matva on 2005-07-17
[QUOTE=coolclassic]Have a look in the following file:/etc/x11/xorg.conf and see if you can find an entry like this:



Section "Device"
 Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
 Driver  "nvidia"
 BusID  "PCI:1:0:0"

If the entry for Driver reads "nv" thenjust replace this with "nvidia"[/QUOTE]
 Mine reads 
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"



Here is more of the message that quake 3 gives:
----- Client Initialization Complete -----
----- R_Init -----
...loading opengl32: QGL_Init: Can't load opengl32 from /etc/ld.so.conf or current dir: /usr/local/games/quake3/opengl32: cannot open shared object file: No such file or directory
failed
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

---

### Post by coolclassic on 2005-07-17
It sounds like your nvidia drivers are correctly installed. Your problem could be q3 when you did the installation it may of asked if you wanted software emilation or hardware accelaration if this is the case you may have to reinstall.

Another issue could be you installed q3 before nvidia if so install q3 again.

---

### Post by matva on 2005-07-17
i think it has something to do with editing a config file that says to use the nvidia acceleration drivers rather than the software mesa drivers. Maybe i need to uninstall mesa? I dont know, hopefully someone does.

Also, the q3 linux readme says:
You can specifically target e.g. the included 3dfx based Mesa driver,
by using the following command line:

	quake3 +set r_gldriver libMesaVoodooGL.so.3.2

So do i want to target my nvidia drivers? How do i do that?

---

### Post by coolclassic on 2005-07-17
What you can do to prove your drivers is install gl-117 this is a flight simulation game:

sudo apt-get install gl-117

Once this is done type gl-117 in a shell and it should run if it doesn't then you have a problem with nvidia.

---

### Post by matva on 2005-07-17
[QUOTE=coolclassic]What you can do to prove your drivers is install gl-117 this is a flight simulation game:

sudo apt-get install gl-117

Once this is done type gl-117 in a shell and it should run if it doesn't then you have a problem with nvidia.[/QUOTE]
 sudo apt-get install gl-117 yields:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gl-117

---

### Post by coolclassic on 2005-07-17
Sorry you need the universe repositorys edit the following file
/etc/apt/sources.list

and cut and paste the following into it
#
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse  
#
Then from the shell

sudo apt-get update

then install gl-117

---

### Post by mohaham on 2005-07-17
run this command in a terminal:
glxgears

the output should be greater than 1000 FPS

If not then the NVIDIA driver is not configured correctly..

try adding this line to "DEVICES" section of  file:/etc/x11/xorg.conf

Option "UseInternalAGPGART" "no"

hope this helps..

---

### Post by matva on 2005-07-17
:D

All it took was a restart after following the steps listed in the first post :P

Thanks guys. I think i will go kill myself now. Actually first i'd like to get rid of that ugly nvidia intro screen:p

---

