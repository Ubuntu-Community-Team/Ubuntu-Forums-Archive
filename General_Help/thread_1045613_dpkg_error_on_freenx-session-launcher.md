---
title: "dpkg error on freenx-session-launcher"
date: 2009-01-20
forum: General Help
---

### Post by nowhere@cox.net on 2009-01-20
Hi,
I installed the three free packages from NoMachine (nxclient, nxnode, and nxserver). It runs fine but for some reason I am getting the following error any time I run apt-get:
> mythserver:/usr/bin$ sudo apt-get purge freenx-session-launcher
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  freenx-session-launcher*
0 upgraded, 0 newly installed, 1 to remove and 122 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 105509 files and directories currently installed.)
Removing freenx-session-launcher ...
chmod: cannot access `/usr/bin/nx-session-launcher-suid': No such file or directory
dpkg: error processing freenx-session-launcher (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 freenx-session-launcher
E: Sub-process /usr/bin/dpkg returned an error code (1)
As far as I know I didn't install freenx from the repos so I don't know why this error is happing. Also as you can see, I cannot uninstall the package either. 

How do I fix this?

Thanks!

Edit: Oops, it looks like I was trying to uninstall freenx-session-launcher but that is not what the system is complaining about. I still get that error about nx-session-launcher-suid tho... Any help?

Edit 2: output of sudo aptitude search freenx shows a partial configuration so the real question is about apt-get or dpkg and how to remove this partially installed package:
> p   freenx                                                         - The FreeNX application/thin-client server based on NX technology        
p   freenx-media                                                   - The FreeNX application/thin-client server based on NX technology        
p   freenx-rdp                                                     - The FreeNX application/thin-client server based on NX technology        
p   freenx-server                                                  - The FreeNX application/thin-client server based on NX technology        
Cp  freenx-session-launcher                                        - The FreeNX application/thin-client server based on NX technology        
p   freenx-vnc                                                     - The FreeNX application/thin-client server based on NX technology        


---

### Post by Ub1476 on 2009-01-20
Hm, what are you trying to do in the first place? Install, remove, launch?

In any case, updating and cleaning the system is a good start:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get clean
```

---

### Post by nowhere@cox.net on 2009-01-20
Thanks! I had tried all that but it didn't clear the error. I wasn't really trying to do anything. I really have no idea how freenx got involved at all. However, I just came across this:

[http://ubuntuforums.org/showthread.php?t=346164]("http://ubuntuforums.org/showthread.php?t=346164") 

and it worked. Seems that it was just a matter of the status file had an entry in it. 

Thanks for the quick reply tho!

---

