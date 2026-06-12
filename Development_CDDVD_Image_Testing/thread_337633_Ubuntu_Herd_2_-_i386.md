---
title: "Ubuntu Herd 2 - i386"
date: 2007-01-13
forum: Development CD/DVD Image Testing
---

### Post by henrikwidth on 2007-01-13
Test case type: Ubuntu daily build 20070113, Desktop CD i386, auto-resize
Date of testing: 13.01.2007
md5sum confirmed: yes
Pass/Fail: Fail
Bugs identified: #78810
Other comments: got black screen after selecting keyboard layout
testmachine: Dell inspiron8500, 2Ghz, 2GB ram, 80GB HDD, Nvidia GeForce 4200 Go, wireless intel 2200,

---

### Post by rai4shu2 on 2007-01-13
Did you try ctrl+alt+f1 then ctrl+alt+f7? That's how I got past that.

---

### Post by moma on 2007-01-13
Many people has got the same error.
Check this: [https://launchpad.net/ubuntu/+bug/78810](https://launchpad.net/ubuntu/+bug/78810)

I have tried to debug the installer's (Ubiquity's) code, but it's pretty complicated affair because it uses debconf library and several bash-scripts to deliver data.

---

### Post by henrikwidth on 2007-01-13
The poster of bug #78810 states that he is using the Norwegian layout, this is the same as me.. does anyone using different layouts get the same error?

---

### Post by rai4shu2 on 2007-01-13
I'm using the default US layout here.

---

### Post by henrikwidth on 2007-01-13
> **rai4shu2 said:**
> Did you try ctrl+alt+f1 then ctrl+alt+f7? That's how I got past that.

Thanks rai4shu2!

This works.

ehm.. got a little exited too soon i think :p

> 
We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 185, in ?
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 180, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 56, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 310, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 867, in process_step
    self.process_autopartitioning()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 922, in process_autopartitioning
    choice = self.get_autopartition_choice()[0]
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 1620, in get_autopartition_choice
    raise AssertionError, "no active autopartitioning choice"
AssertionError: no active autopartitioning choice


reported as bug 79091 [https://launchpad.net/ubuntu/+source/ubiquity/+bug/79091](https://launchpad.net/ubuntu/+source/ubiquity/+bug/79091)

---

### Post by clinteas on 2007-01-13
I have been unable to boot into any of the isos so far,be it Ubuntu or Kubuntu,Desktop or alternate,Herd 1 or 2,last tried 070113,I cant even get past the first boot screen.
My system is a C2D 6600 on AsUS P5B MoBo,pretty standard these days youd think.
Maybe Mr Shuttleworth should have a good long look at who is spending his money at Ubuntu,how can you publish such rubbish that wont even boot??
Its gotten worse and worse since Dapper,very disappointing.

---

### Post by _Pierre_ on 2007-01-13
Test case type: Ubuntu daily build 20070113, Desktop CD i386
Date of testing: 13.01.2007
md5sum confirmed: yes
Pass/Fail: Fail
Bugs identified:
Other comments: 
Testmachine: Acer TravelMate 803 LMi (Ati Mobility Radeon 9000)

Didn't boot into gnome 
Usplash loader stops at 1/4 

I'm also using an updated Herd1 wich also cannot any of the 2.6.20-*-generic kernels
only 2.6.19-7-generic works fine
So I think it's the same problem I have with the daily live cd
Also 2.6.20-4-generic booted once and next boot it became also unbootable

More info on not booting (2.6.20-*) when I switch to VT's on boot the last things on the screen are

udevd[2290]:lookup-group: specified group 'nvram' unknown
udevd-event[2340]: udev_db_add_device: unable to create db file '/dev/.udev/db/class@input@mice :' No such file or directory
udevd-event[2622]: udev_db_add_device: unable to create db file '/dev/.udev/db/class@inupt@inupt1@mouse0' : No such file or directory
udevd-event[3134]:run_program: '/sbin/modprobe' abnormal exit

Hope you guys can do anything with this :) 
Keep up the great work

---

### Post by pochu on 2007-01-13
> **clinteas said:**
> I have been unable to boot into any of the isos so far,be it Ubuntu or Kubuntu,Desktop or alternate,Herd 1 or 2,last tried 070113,I cant even get past the first boot screen.
My system is a C2D 6600 on AsUS P5B MoBo,pretty standard these days youd think.
Maybe Mr Shuttleworth should have a good long look at who is spending his money at Ubuntu,how can you publish such rubbish that wont even boot??
Its gotten worse and worse since Dapper,very disappointing.
You are using a very very early alpha software, so things are supposed to break.

If you don't want this to happen, please, don't test them. Go and install Dapper Drake, and wait for the next LTS to upgrade your system. Or if you want, install the stable versions, but don't complain if an alpha software doesn't boot, because things are been developed and in some moments (maybe always) the system can get broken.

I think things are very clear, so don't complain again.

Regards
Pochu

---

### Post by clinteas on 2007-01-14
Im writing this from a working Kubuntu Edgy,and i realize its an alpha release mate !
Btw,im having the exact error messages as _Pierre_above,in case anyone would like to actually check what the problem is.Boot breaks up at "configuring network interfaces" every time,whether from the livecd ur an updated edgy install.
All im saying is for ppl to test a new distro,publish it when it can actually be booted !

---

### Post by Henrik on 2007-01-14
Thanks for your testing. As pochu says, Alpha software will very often break. It's inevitable when introducing brand new code. 

There are many great sections in the forum for debates about this such as the [Feisty dev section]("http://www.ubuntuforums.org/forumdisplay.php?f=179"). But this is not one of them. These threads are meant for test results and questions about testing only. Closing thread.

---

