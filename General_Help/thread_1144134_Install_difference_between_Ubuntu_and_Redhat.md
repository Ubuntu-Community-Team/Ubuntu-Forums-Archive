---
title: "Install difference between Ubuntu and Redhat"
date: 2009-04-30
forum: General Help
---

### Post by jingpro on 2009-04-30
Hi,

I am going to install ABAQUS, a CAE software under Ubuntu. The installation guide provide by our campus IT group is for RedHat. Since I am a newbie for Linux and I like the nice Ubuntu user community, I give up Red Hat (even though it is provided by my department for free.)

The installation guide for RedHat is as below:
> [COLOR="Red"]Some Linux applications require a specific C++ library to run/install.   So before you do anything else, as *root*, run the following to install this specific compatibility library:

yum install compat-libstdc++-33

yum install openmotif
[/COLOR]
1)  Copy the "abaqus68.iso" and "abaqus68doc.iso" files to your desktop

2)  In terminal, issue the following command *as root*:

mkdir /usr/caen    (this may already exist)
mkdir /usr/caen/abaqus68

[COLOR="Red"]echo 0 >/selinux/enforce

NOTE:  This temporarily turns off SELINUX so you can install Abaqus without jumping through a lot of hoops.   BE SURE TO TURN IT BACK ON AT THE END OF THE INSTRUCTIONS![/COLOR]

Next:  Install the Abaqus documentation (otherwise the application installation complains...)

3)  In Terminal, issue the following commands to mount the .iso:

mkdir /tmp/abaqusdocs

mount -o loop /path/to/abaquas68doc.iso /tmp/abaqusdocs

NOTE:  this "/path/to" will be whereever your desktop is.  For example, on my computer it is:

mount -o loop '/home/maser/Desktop/abaqus68doc.iso' /tmp/abaqusdocs


4)  Issue the following command to start the documentation installer:

/tmp/abaqusdocs/setup

When prompted for the scratch directory, enter:  /tmp

Follow the steps in the GUI to install the documentation.  

WHEN YOU GET TO THE "WEB SERVER SELECTION" step, click the "No web server (search not available)" button.

When you get to the documentation "Installation Directory" screen, set the parent directory to be:

/usr/caen/abaqus68

and continue on.   NOTE:  The documentation installation will take a long time.

5)  When finished, run the following commands:

umount /tmp/abaqusdocs

rmdir /tmp/abaqusdocs


NEXT:  Install the Abaqus program

6)  Issue the following commands in Terminal to mount the program .iso:

mkdir /tmp/abaqus

mount -o loop /path/to/linux.iso /tmp/abaqus

NOTE:  this "/path/to" will be whereever your desktop is.  For example, on my computer it is:

mount -o loop '/home/maser/Desktop/abaqus68.iso' /tmp/abaqus


Now, issue the following commands to run the app installation:

7)  /tmp/abaqus/setup

8)  When prompted for the scratch directory, enter:  /tmp

And continue on with the installation

At the "Installation Type" screen, click the "Product" button.

At the "License Server" screen, in the "(REQUIRED)" box, enter:

********@license-abaqus.******.edu

At the "Documentation" screen, enter the following location:

file:///usr/caen/abaqus68/Documentation/docs/v6.8/index.html

At the "Installation directory" screen, enter:

/usr/caen/abaqus68

and "continue" if prompted.

9)  When finished, run the following commands:

umount /tmp/abaqus

rmdir /tmp/abaqus


[COLOR="Red"]IMPORTANT STEP:  REENABLE SELINUX:

10)  Issue this very important step when the installation is done...

echo 1 >/selinux/enforce

[/COLOR]
ALMOST DONE:   Make some SELINUX changes so you can run the program!

[COLOR="Red"]11)  After that, issue the following commands to have SELinux allow some libraries to be loaded:

chcon -t textrel_shlib_t /usr/caen/abaqus68/6.8-1/exec/lbr/lib*

chcon -t textrel_shlib_t /usr/caen/abaqus68/6.8-1/External/lib*

chcon -t textrel_shlib_t /usr/caen/abaqus68/6.8-1/Python/Obj/lbr/lib*

chcon -t textrel_shlib_t /usr/caen/abaqus68/6.8-1/Python/Obj/*

chcon -t textrel_shlib_t /usr/caen/abaqus68/6.8-1/exec/*

/usr/sbin/setsebool  -P allow_execheap=1
[/COLOR]


Then, the command:

'/usr/caen/abaqus68/Commands/abaqus' cae

should work from any other account.
My questions are related with above red-highlighted areas: 

(1) how to check whether my ubuntu meet the c++ lib requirements? I just have gcc installed when install Ubuntu.

(2) Is there a 'SELINUX' setting under Ubuntu? If so, how shall I do? Thanks a lot.

---

### Post by cmnorton on 2009-05-01
When you're done the Ubuntu install, install build-essential, and then use Synaptic -- search for C++ -- to install whatever else you need.

---

### Post by sisco311 on 2009-05-01
> **jingpro said:**
> 
(1) how to check whether my ubuntu meet the c++ lib requirements? I just have gcc installed when install Ubuntu.
> yum install compat-libstdc++-33
yum install openmotif


```
sudo apt-get install build-essential 
sudo apt-get install libmotif3 libmotif-dev
```


> (2) Is there a 'SELINUX' setting under Ubuntu? If so, how shall I do? Thanks a lot.

By default SELinux is not installed in Ubuntu. Ubuntu uses AppArmor.

[uhelp]community/AppArmor[/uhelp]

You should be able to install and use the application without changing the default AppArmor profiles.

---

### Post by jingpro on 2009-05-01
Thanks a lot for your very helpful replies.

Unfortunately I still met a problem during installation.

I implemented following commands according to the instruction:

(1) mkdir /tmp/abaqusdocs
(2) mount -o loop /path/to/abaquas68doc.iso /tmp/abaqusdocs
(3) /tmp/abaqusdocs/setup

It wents well in steps (1) and (2), and when I executed step (3), I got following error:
> root@ubuntu:/home/myname# /tmp/abaqusdocs/setup
bash: /tmp/abaqusdocs/setup: /bin/csh: bad interpreter: No such file or directory

Looks like '/bin/csh' is missing. Is this folder available in Redhat by default? Do I need to do something in Ubuntu?

Thanks a lot for your helps!

---

### Post by jingpro on 2009-05-01
I installed CSH using synaptic package manager, above problem solved. .....The installation proceeded, then comes following warning:
> 
***WARNING:  We were unable to find the system termcap library (libtermcap.so). This library is required to serve and search the Abaqus HTML Documentation. Please install the termcap package for your Linux distribution. 

I search this forum and tried following command according to some posts
> $ sudo apt-get install libncurses5-dev
Unfortunately it does not work.
Any suggestions about this 'libtermcap.so' problem? I searched 'libtermcap.so ubunutu' on google and this forum, there are some discussions, but all almost not helpful.

---

### Post by jingpro on 2009-05-01
Damn, have to give up, since one step of installation says:
> System requirement status is:

Requirement:          SuSE 9.3, 10.0, 10.1 or 10.2, SuSE Enterprise Linux 9.0
                      or 10.0, SuSE Enterprise Desktop 10, Red Hat Enterprise
                      3.0, 4.0 or 5.0, or Fedora Core 6.0
Products:             All Abaqus Products
Status:               Fail - Unable to determine Linux Distribution.

Requirement:          GNU Lib C 2.3.2 or greater
Products:             All Abaqus Products
Status:               Pass - Found GNU Lib C 2.9.

 
Ubuntu is not included! Does this mean Ubuntu is not qualified for serious users?  In order to install this software (required for my work), I have to turn to Redhat.

---

