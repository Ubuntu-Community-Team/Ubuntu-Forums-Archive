---
title: "Salome Installation 3.2.6 in Feisty 7.0.4"
date: 2007-05-28
forum: Education &amp; Science
---

### Post by in_flu_ence on 2007-05-28
Hi,

     Has anyone successfully installed Salome 3.2.6 in Feisty? I have encountered the following error when installing.

Traceback (most recent call last):
  File "/home/myname/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 23, in ?
    import orbmodule
  File "/home/myname/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 21, in ?
    from omniORB import CORBA
ImportError: No module named omniORB

I can't remember how I should solve this? Any one?

Thanks

---

### Post by kleeman on 2007-05-28
Your error is in this thread:

[http://www.salome-platform.org/forum/?groupid=10&forumid=9&thread=449](http://www.salome-platform.org/forum/?groupid=10&forumid=9&thread=449)

---

### Post by in_flu_ence on 2007-05-28
Doesn't seem to work

Still same problem.

---

### Post by in_flu_ence on 2007-05-28
I found something about the incompatibility of omniORB with python 2.5 somewhere. Will it be the cause?

After i find that, i have reinstall the salome without installing python.

Here is the error
```

Searching for a free port for naming service: 2810 2811 2812 2813 - OK
Lancement du Naming Service runNS.sh > /tmp/logs/usrname/salomeNS.log 2>&1
Searching Naming Service   found in 0.0 seconds 
SALOME_ContainerManagerServer: error while loading shared libraries: libSalomeContainer.so.0: cannot open shared object file: No such file or directory
omniORB: Assertion failed.  This indicates a bug in the application using
omniORB, or maybe in omniORB itself.
 file: ../../modules/pyExceptions.cc
 line: 421
 info: PyClass_Check(excclass)
omniORB: To endpoint: giop:tcp:192.168.1.2:2813. Send GIOP 1.0 MessageError because a protocol error has been detected. Connection is closed.
Searching /Containers/usrname/FactoryServerPy in Naming Service +SALOME_Session_Server: error while loading shared libraries: libSalomeSession.so.0: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/home/usrname/salome_3.2.6/KERNEL_3.2.6/bin/salome/SALOME_ContainerPy.py", line 34, in <module>
    import omnipatch                     # PAL10310
ImportError: No module named omnipatch
omniORB: Assertion failed.  This indicates a bug in the application using
omniORB, or maybe in omniORB itself.
 file: ../../modules/pyExceptions.cc
 line: 421
 info: PyClass_Check(excclass)
omniORB: To endpoint: giop:tcp:192.168.1.2:2813. Send GIOP 1.0 MessageError because a protocol error has been detected. Connection is closed.
+/home/usrname/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py:173: DeprecationWarning: raising a string exception is deprecated
  raise "Impossible de trouver %s" % theName
Traceback (most recent call last):
  File "runSalome.py", line 802, in useSalome
    clt = startSalome(args, modules_list, modules_root_dir)
  File "runSalome.py", line 729, in startSalome
    clt.waitNSPID("/Containers/" + theComputer + "/FactoryServerPy",myServer.PID)
  File "/home/usrname/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 173, in waitNSPID
    raise "Impossible de trouver %s" % theName
Impossible de trouver /Containers/usrname/FactoryServerPy


--- erreur au lancement Salome ---

```

---

### Post by in_flu_ence on 2007-06-04
I fixed my own problem once again.

All I did is to copy the omniORB BINARY folder/zip file from 3.2.2 and place it back to the BINARY in 3.2.6

Next: Make sure you update the config.xml file to install the binary of omniORB4.0.5 (same thing: copy the relevant lines from the xml file in 3.2.2.)

This will solve all the issues above. I can make it run but I have yet to test if there is any issue during operation.

Give feedback for those who try it.

---

### Post by jmb365 on 2007-06-06
Hello,

I am trying to install Salome 3.2.6 in Feisty 7.04 but encountering problems running it.  Here is what I did:

# Attempt at installing Salome 3.2.6 on ubuntu Feisty (7.04)
cd /tmp
gunzip -cd /tmp/Salome-InstallWizard_3.2.6_DebianSarge.tar.gz | tar -xvf -
cd /tmp/InstallWizard_3.2.6_DebianSarge

# Copy the omniORB version fron from Salome 3.2.2
cp /tmp/InstallWizard_3.2.2_DS/Products/BINARIES/DebianSarge/omniORB-4.0.5.tar.gz  \
     /tmp/InstallWizard_3.2.6_DebianSarge/Products/BINARIES/DebianSarge

# Edit the XML file suitably to allow usage of the older version of omniORB
cp config.xml config.xml.orig
gedit config.xml &
# Change all references of omniOrb 4.0.7 to 4.0.5

./runInstall
# Install everything as binary except gcc being native (4.1)
# Because of incompatibility between Salome packaged python (2.3) and native python (2.5.1) do not install python.

# Check the version of python that is installed
which python
# /usr/bin/python
/usr/bin/python --version
# Python 2.5.1

cd ~/salome_3.2.6/KERNEL_3.2.6
source salome.sh

cd bin/salome
./runSalome

And the error I get is:

Configure parser: Warning : could not find user configuration file
Searching for a free port for naming service: 2810 2811 2812 2813 2814 2815 2816 - OK
Lancement du Naming Service runNS.sh > /tmp/logs/ks/salomeNS.log 2>&1
Searching Naming Service ++++++++++Failed to narrow the root naming context
Traceback (most recent call last):
  File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 802, in useSalome
    clt = startSalome(args, modules_list, modules_root_dir)
  File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 629, in startSalome
    clt=orbmodule.client()
  File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 60, in __init__
    self.initNS()
  File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 93, in initNS
    sys.exit(1)
SystemExit: 1

--- erreur au lancement Salome ---

Could somebody please assist?

Thank you
JMB

---

### Post by in_flu_ence on 2007-06-06
I read somewhere that the omniORB thingy might sometimes conflict with network drivers. Dunno how true that is but will check that out along the way.

It works for me for my desktop but it seems to not work for me in my lappy. I shall investigate that further since I have the same error as yours.

---

### Post by in_flu_ence on 2007-06-06
For those who have problem even after doing what I have said in previous post. 

The problem seems to be somehow similar to OpenFOAM about COBRA.

What you need to do is to edit the /etc/hosts file.

First. Go to terminal and type hostname.
and use gedit /etc/hosts and add a line say
127.0.0.1 yourhostname

It might vary depending on how you might eventually use network to assign your job.

I find it working ok since I always use single machine for single job.

Again. feedback will be great.

---

### Post by jmb365 on 2007-06-07
Hello,

For those of you trying to install Salome 3.2.6 on Ubuntu Feisty Fawn (7.04), I have successfully done so with the help and assistance of others on the Salome forum who I am very grateful to.  Here are the detailed steps that worked for them (& me).  Hopefully this will assist others as well.

# Download the package to /tmp
cd /tmp
gunzip -cd /home/mshome/Salome-InstallWizard_3.2.6_DebianSarge.tar.gz | tar -xvf -
cd /tmp/InstallWizard_3.2.6_DebianSarge

# Download the Debian Salome version 3.2.2 as well to /tmp
# Follow similar steps as above to unpackage it, then
# Copy the omniORB version fron from Salome 3.2.2 to Salome 3.2.6
cp /tmp/InstallWizard_3.2.2_DS/Products/BINARIES/DebianSarge/omniORB-4.0.5.tar.gz /tmp/InstallWizard_3.2.6_DebianSarge/Products/BINARIES/DebianSarge

# Edit the XML file suitably to allow usage of the older version of omniORB
cp config.xml config.xml.orig
gedit config.xml &
# Change all references of omniOrb 4.0.7 to 4.0.5

./runInstall
# Install everything as binary except gcc being native (mine is version 4.1)

cd ~/salome_3.2.6/KERNEL_3.2.6
source salome.sh

cd bin/salome
./runSalome

# If you get an error...
# Configure parser: Warning : could not find user configuration file
# Searching for a free port for naming service: 2810 2811 2812 - OK
# Lancement du Naming Service runNS.sh > /tmp/logs/ks/salomeNS.log 2>&1
# Searching Naming Service ++++++++++Failed to narrow the root naming context
# Traceback (most recent call last):
#   File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 802, in useSalome
#     clt = startSalome(args, modules_list, modules_root_dir)
#   File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 629, in startSalome
#     clt=orbmodule.client()
#   File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 60, in __init__
#     self.initNS()
#   File "/home/ks/salome_3.2.6/KERNEL_3.2.6/bin/salome/orbmodule.py", line 93, in initNS
#     sys.exit(1)
# SystemExit: 1
# 
# 
# --- erreur au lancement Salome ---
#
# The fix is:

# Edit the /etc/hosts file from:
# 
# "127.0.0.1 name.domain" to "127.0.0.1 name.domain name"

# It seems that omniORB (or something else) perhaps does not recognize a "name" followed by a ".domain"
#  and expects to find just the "name" of the computer in the /etc/hosts file. 
# Putting it on the same line works.  So my /etc/hosts file looks like this:

# #----------------------------------------------
# 127.0.0.1       localhost
# 127.0.1.1       name.domain        name
# 
# 192.168.1.1   name.domain  name
# 
# etc, etc.
# #----------------------------------------------

./runSalome				# Now it works!

# Salome 3.2.6 now works on Ubuntu Feisty Fawn (7.04)!

---

### Post by braddcadd on 2007-07-10
Well, I'd like to install salome but i can't even download it.  The download page says you have to be logged in to download.  [http://www.salome-platform.org/download/dl326/](http://www.salome-platform.org/download/dl326/)  

But they don;t have a pace to register.  How stupid!

Anyone have any tricks?  Or other download locations?

---

### Post by kleeman on 2007-07-11
Errr I think you need some more coffee ;-) There is a register button on your linkpage: Top righthand corner

---

### Post by braddcadd on 2007-07-11
haha, lol

I need something.  (had to scroll the browser over to the right).

---

### Post by Hayesio on 2007-09-29
Hi 
I'm getting this error
```
jack@Star-Ship-Omega:~/Salome/KERNEL_3.2.6/bin/salome$ ./runSalome
Configure parser: Warning : could not find user configuration file
Searching for a free port for naming service: 2810 - OK
Traceback (most recent call last):
  File "/home/jack/Salome/KERNEL_3.2.6/bin/salome/runSalome.py", line 984, in ?
    clt,args = main()
  File "/home/jack/Salome/KERNEL_3.2.6/bin/salome/runSalome.py", line 975, in main
    searchFreePort(args, save_config)
  File "/home/jack/Salome/KERNEL_3.2.6/bin/salome/runSalome.py", line 926, in searchFreePort
    f = open(os.environ['OMNIORB_CONFIG'], "w")
IOError: [Errno 13] Permission denied: '/home/jack/.omniORB_Star-Ship-Omega_2810.cfg'

```

My /etc/hosts file looks like this (I havent touched it): 
127.0.0.1	localhost
127.0.1.1	Star-Ship-Omega

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Any ideas?

---

### Post by keeswouters on 2008-04-21
> **braddcadd said:**
> Well, I'd like to install salome but i can't even download it.  The download page says you have to be logged in to download.  [http://www.salome-platform.org/download/dl326/](http://www.salome-platform.org/download/dl326/)  

But they don;t have a pace to register.  How stupid!

Anyone have any tricks?  Or other download locations?

Top right? Register (I think it is called) and you can ... register!

---

