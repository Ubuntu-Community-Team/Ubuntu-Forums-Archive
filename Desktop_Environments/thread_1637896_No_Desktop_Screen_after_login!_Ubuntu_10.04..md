---
title: "No Desktop Screen after login! Ubuntu 10.04."
date: 2010-12-05
forum: Desktop Environments
---

### Post by tattushenoi on 2010-12-05
Hi all,

There is a problem with my linux. After I give username and password for logging in, I get an error saying my TCP/IP cannot be detected and cannot load configuration for evolution alarm notification. When I press ok, the ubuntu screen is displayed without anything but mouse icon on it. No menu, no partition  disks, nothing is displayed.

I tried installing ubuntu-desktop. But it says its already installed. I reinstalled after uninstall. I tried to install gnome. It says dependency problems with epiphany and it fails. I installed plasma dekstop and selected KDE while logging in and it goes in. But still I cannot configure network connection. 

How can I log into GNOME? or Install gnome.

Needless to say, I have tried sudo get-update, upgrade.

Also tried dpkg-reconfigure with no avail.

please help me. Thanks in advance.

---

### Post by sikander3786 on 2010-12-05
Hi.

Press Ctrl + Alt + F1 at your login screen to get to the tty. Login using your credentials.

Bring up internet.

```
dhclient eth0
```

Where eth0 is your network interface.

Try fixing missing packages/dependencies.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

If the commands complete successfully, reboot.

```
sudo shutdown -r now
```

If not, please post the error encountered there.

Also, make sure you are not running out of space on any of your partitions.

```
df -h
```

---

### Post by tattushenoi on 2010-12-05
Thanks for the quick response.

I had tried most of your suggestions. But being a 'root' . But still no avail.
When I login to tty using my user-name and password and then try

dhclient. The error is saying that I have no permission. 

Funny thing is I can login to previous version shown in the grub. thats 25 . The one I cant login into is [latest] 26. I tried to install gnome through that version [25] . But it gave following error.

tattushenoi@TATTUS:~$ sudo apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: epiphany-extensions but it is not going to be installed
E: Broken packages


I have 8.5 Gb free space. I guess thats enough for it to load.

---

### Post by tattushenoi on 2010-12-05
This is the error it gives when I try to bring the internet up in TTY login.

tattushenoi@TATTUS:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted


Thanks for the suggestions again! But it seems I need more help :D. Its eating my head!

---

### Post by tattushenoi on 2010-12-05
I logged into the previous version, where I could connect to internet and tried all your options.

This is what I got.

-----------------------------------------------------------

tattushenoi@TATTUS:~$ sudo apt-get install -f
[sudo] password for tattushenoi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tattushenoi@TATTUS:~$ sudo dpkg --configure -a
tattushenoi@TATTUS:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources                     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources             
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed/restricted Packages           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed/main Packages                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,081B]                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-proposed/universe Packages             
Fetched 2,625B in 5s (504B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tattushenoi@TATTUS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G  4.9G  8.5G  37% /
none                  242M  260K  242M   1% /dev
none                  249M  360K  249M   1% /dev/shm
none                  249M  280K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
/home/tattushenoi/.Private
                       15G  4.9G  8.5G  37% /home/tattushenoi
/dev/sda2              18G   15G  2.3G  87% /media/82F09943F0993E7B
/dev/sda3              44G   39G  4.4G  90% /media/DAA4832DA4830AE9
tattushenoi@TATTUS:~$ 



Now what should I do?

---

### Post by tattushenoi on 2010-12-05
ohh...yeah i missed shut down.

I got an error.


tattushenoi@TATTUS:~$ shutdown -r now
shutdown: Need to be root

---

### Post by tattushenoi on 2010-12-05
I forgot to add 'SUDO'. 

After which it shut down and guess what!

It logged in.

But I am not that convinced as I still dont know what was the problem.


Any ways thanks for your quick response, my problem was solved.

---

### Post by sikander3786 on 2010-12-05
> But I am not that convinced as I still dont know what was the problem.

I'm not also convinced as I see from the output in your above post that those commands had no effect what so ever. There were no broken packages, no missing dependencies, no packages to upgrade but that still worked for you.

I hope the issue won't strike back ;-)

Happy Ubuntu-ing!

---

