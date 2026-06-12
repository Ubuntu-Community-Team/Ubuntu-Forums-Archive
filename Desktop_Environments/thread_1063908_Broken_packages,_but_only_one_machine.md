---
title: "Broken packages, but only one machine"
date: 2009-02-08
forum: Desktop Environments
---

### Post by pwaldo on 2009-02-08
Hi all,

I'm having a weird problem.  I have two machines (destop and laptop), both running Intrepid 64 bit.  I have successfully installed kde-extras on the desktop, but when I try it on my laptop, I get complaints about broken packages (below).  Of grave concern is network-manager for the laptop.  Any ideas?  Thanks!

```
paul@paul-laptop:~$ sudo aptitude upgrade
[sudo] password for paul:                
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done                                      
Building dependency tree                                           
Reading state information... Done                                  
Reading extended state information                                 
Initializing package states... Done                                
No packages will be installed, upgraded, or removed.               
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.           
Reading package lists... Done                                          
Building dependency tree                                               
Reading state information... Done                                      
Reading extended state information                                     
Initializing package states... Done                                    

paul@paul-laptop:~$ sudo aptitude install kde-extras
Reading package lists... Done                       
Building dependency tree                            
Reading state information... Done                   
Reading extended state information                  
Initializing package states... Done                 
The following packages are BROKEN:                  
  knights network-manager-gnome network-manager-kde 
The following NEW packages will be installed:       
  abakus{a} apollon{a} aqbanking-tools{a} barcode{a} basket{a} cddb{a} 
  creox{a} cscope{a} dialog{a} dvipdfmx{a} dvipng{a} exuberant-ctags{a} 

```

---

### Post by gettinoriginal on 2009-02-08
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by pwaldo on 2009-02-09
> **gettinoriginal said:**
> Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

Thanks for the reply, gettinoriginal.  I assume that what you are suggesting does the same thing as dpkg's reconfigure to fix a broken package (dpkg --configure -a).  I'm confused, because dpkg does not indicate that the package is broken:
```
paul@paul-laptop:~$ dpkg -l network-manager-gnome
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  network-manager-gnome     0.7~~svn20081020t000444-0 network management framework (GNOME frontend)


paul@paul-laptop:~$ dpkg -s network-manager-gnome|head -5
Package: network-manager-gnome
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 2744


```

---

