---
title: "Dell XPS15 L502X - Noob's way for Optimus issue"
date: 2011-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by asn_knight on 2011-05-20
Hey! 
I have a Dell XPS15 L502X with Nvidia GeForce GT 525M switchable with Intel HD Graphics accelerator. I have Ubuntu 11.04 but I am aware there is some issue with Optimus and it.
I found many threads and posts for the solution for the above but couldn't make all of it. 

I am all new to 'acpi', 'bumblebee' etc.

Can someone post step-by-step procedure for the solution?

There is a thread which is regularly updated [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1713308").
though I can't make much from it. 

I just dont want to use my Nvidia card as I use Ubuntu for only light tasks! :)

Thanks a lot and appreciate it!

---

### Post by pszafer on 2011-05-24
Hello,

I don't know what You did, so I'll try to write every step You need.

First of all, please make backup in case something go wrong.

Steps to do in terminal:
0. Don't even try to install nvidia drivers (if you really don't need nvidia graphic card).
1. Add xorg edgers and install newest xorg
```
sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update
```
2. Install XORG
```
sudo apt-get install xorg
```
3. For a second go away for terminal, and check updates (if you want you can of course check updates via apt-get):
- ALT-F2 -> update-manager -> check -> install updates if available
4. Reboot
5. Open terminal
6. If You have git already installed that's cool, otherwise install git-core
7.```
cd ~
```
8. ```
git clone http://github.com/mkottman/acpi_call.git
```
9. ```
cd acpi_call
```
10. ```
make
```
11. ```
sudo insmod acpi_call.ko
```
12. ```
./test_off.sh
```

You probably switched off Your nvidia card!

13. In my case calling all this acpi_methods, which are in test_off.sh, hangs up system sometimes.
So I prefer to leave only this one I need:
If You want this too, just edit test_off.sh and Your methods should look like this:
```
methods="
	\_SB.PCI0.PEG0.PEGP._OFF
	"
```
remember about quotes.

Hope this helps.

Suspend not always working, I've done suspending works on my XPS, but I'm not sure how I did this :D.

---

### Post by asn_knight on 2011-05-25
Wow..cool! Thanks for that reply!!! Will try it out soon and let you know!

But, do I have to run that script everytime I restart (read sumwer like that!) or just once is enough? :)

---

### Post by pszafer on 2011-05-25
You need to run this every restart if You don't add it to autostart:
```
cd ~/acpi_call
sudo insmod acpi_call.ko
./test_off.sh
```

One more thing. 
If You had kernel updates You will need to recompile this, so like this:
```
make clean
make
```

and normal procedure then.

---

### Post by asn_knight on 2011-05-25
Amazing!! Thanks a ton!!! 

Again,a doubt! :) 
The procedure is independent of x32 or x64 bit Ubuntu right?

---

### Post by pszafer on 2011-05-26
Yes, it doesn't matter if You installing that on x32 or x64 architecture.

---

### Post by Ranko Kohime on 2011-05-26
Hi, I used this to switch of the independent card in my Clevo W150HNQ, but after rebooting, it no longer works.

The module still inserts into the kernel just fine, but running the test_off.sh files shows it failing on every attempt.

Any suggestions?

ETA: The Nvidia card no longer shows up in "lspci"

EATAM: Running Xubuntu Natty.

---

### Post by asn_knight on 2011-05-27
@pszafer : Thanks a lot!!! All's working fine...I just didnt understand how to put that script to turn off the card during start-up!..Can u pls explain that as well.. :) Thanks anyway!!!

---

### Post by bro on 2011-05-28
I can run test_off.sh but though one of them says 'works', it doesn't safe me any battery life. So that should mean it isn't shut down is it? 

Also, I'm not sure how to correctly configure the bumblebee-disablecard and bumblebee-enablecard files.

---

### Post by pszafer on 2011-05-28
@Ranko Kohime
give me output of:
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

and do You have windows installed on Your laptop?

----------
@asn_knight
Here is one of at least three ways to add it to startup:
1. Open terminal
2. Go to folder where You have your acpi_call.ko module, probably:
```
cd ~/acpi_call/
```
3. Next we will copy this module to kernel modules
```
sudo cp acpi_call.ko /lib/modules/$(uname -r)/kernel/drivers/acpi/acpi_call.ko
```
4. Now we need to add this to modules.
Just in case we will make backup:
```
sudo cp /etc/modules /etc/modules.old
```
5. Add module acpi_call to /etc/modules
```
echo acpi_call | sudo tee -a /etc/modules
```
6. Restart and it should working now.

@bro
About battery life I cannot save as much as You need, but I got 9-cell battery and XPS15 is working about 5 hours on Ubuntu.
On Windows I've almost not working but battery indicator shows 7 hours.
In my case main problem and probably main place to find most power consumption is hard drive.
It got 46 degrees (Celcius), but case is really hot in left hand area.

About bumblebee last version (from Wednesday) stopped working on my laptop and I'm waiting at least one week to check functionality of it again ;)

Hope I helped You guys

---

### Post by bro on 2011-05-28
> **pszafer said:**
> 
@bro
About battery life I cannot save as much as You need, but I got 9-cell battery and XPS15 is working about 5 hours on Ubuntu.
On Windows I've almost not working but battery indicator shows 7 hours.
In my case main problem and probably main place to find most power consumption is hard drive.
It got 46 degrees (Celcius), but case is really hot in left hand area.


If I have only integrated graphics enabled it estimates my battery time serveral hours longer then with optimus/bumblebee. This made me believe that it is not properly shutting down the nvidia card. Ideally the battery time should be the same (unless I start an application as optirun64)

I'm a bit disappointed/curious about the fact that nobody seems able to explain the workings and configurations of the bumblebee-disablecard file. Also it seems impossible to just 'check' if the card is shutdown. Or, for example, to give command to shut it down.

---

### Post by pszafer on 2011-05-28
> **bro said:**
> If I have only integrated graphics enabled it estimates my battery time serveral hours longer then with optimus/bumblebee. This made me believe that it is not properly shutting down the nvidia card. Ideally the battery time should be the same (unless I start an application as optirun64)

I'm a bit disappointed/curious about the fact that nobody seems able to explain the workings and configurations of the bumblebee-disablecard file. Also it seems impossible to just 'check' if the card is shutdown. Or, for example, to give command to shut it down.

You talking about bumblebee only, not acpi_call, am I right?

If yes tomorrow I will install bumblebee again and write enablecard/disablecard scripts here and whole instruction to got it working. Of course if everything will be working ;)

---

### Post by bro on 2011-05-28
That would be grand ;)

I got acpi_call installed. This seemed needed to configure the enable/disable stuff.

---

### Post by asn_knight on 2011-05-28
@pszafer : You are an angel!!!!!!! Thanks a million, bro! :) :D 

Meanwhile, I'll mark this thread solved. Do post(or link to) updates...Thanks again! :)

PS : @bro Pls do continue the discussion. I too am checking workarounds. :)

---

### Post by Ranko Kohime on 2011-05-28
> **pszafer said:**
> @Ranko Kohime
give me output of:
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

and do You have windows installed on Your laptop?

Following is the output of the command, though I should mention that several reboots later, the Nvidia card is now back in "lspci", and so I'm good again.  It seems like, if I enable the acpi_call bit, after a reboot the card disappears from "lscpi", but going by the lights on the laptop, the card turns back on at reboot time.  After the second, or perhaps third reboot, the card reappears.

It doesn't seem to disappear after running the test_off.sh script, only after rebooting.  My next test will involve switching the OFF to ON in a new script, and running that prior to reboot.

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 07) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev ff) (prog-if ff)

```

As for Windows, no.  I bought it as a barebones, and assembled myself, if it could called assembly.  (Just hard drives, processor and RAM, really).

---

### Post by pszafer on 2011-05-29
@asn_knight
Sorry, I forgot to call switching off acpi:
So You got this test_off.sh in acpi_call dir.
Add it to startup programs:
Go to:
```
System -> Preferences -> Startup/Autostart programs (I don't use English language in Ubuntu so it translations, could be little different).
```

Click Add:
```
Name - ACPI OFF
Command - ~/acpi_call/test_off.sh
Add and now everything is ok.
```


@bro

Do everything from my last instruction:
[http://ubuntuforums.org/showpost.php?p=10873342&postcount=10]("http://ubuntuforums.org/showpost.php?p=10873342&postcount=10")

Don't add this to startup programs.

Do this (in terminal):
0. We had to have Intel graphic card working (my first post in this thread)
1. We need root right so: 
```
sudo -s, enter password
```
2. To be sure copy xorg.conf:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
3. Download bumblebee:
```
cd ~
git clone https://github.com/MrMEEE/bumblebee.git
```
4. Install it
```
cd bumblebee
./install.sh
```
5. Go to /usr/local/bin/
```
cd /usr/local/bin/
```
6. Edit bumblebee-enablecard and disablecard (based on [http://ubuntuforums.org/showpost.php?p=10840004&postcount=66]("http://ubuntuforums.org/showpost.php?p=10840004&postcount=66"))
```
nano bumblebee-enablecard
```


> #!/bin/bash
modprobe acpi_call

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "\_SB.PCI0.PEG0.PEGP._ON" > /proc/acpi/call
    result=$(cat /proc/acpi/call)
    case "$result" in
     Error*)
      echo "Enabling nVidia Card failed ($result)."
      ;;
     *)
      echo "Enabling nVidia Card Succeded."
     ;;
    esac
}

acpi_call
modprobe nvidia-current


7. Time for bumblebee-disablecard:
```
nano bumblebee-disablecard
```


> modprobe acpi_call
rmmod nvidia
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call

    result=$(cat /proc/acpi/call)
    case "$result" in
     Error*)
      echo "Disabling nVidia Card failed ($result)."
      ;;
     *)
      echo "Disabling nVidia Card Succeded."                                                                                
     ;;
    esac
}

acpi_call

Hope everything will be great.
Now add bumblebee-disablecard to startup programs (similar as test_off.sh)

And now if You run command with optirun/optirun64 application it would enable nvidia, after proper close application it should disable nvidia card.
Everything for now!

---

### Post by bro on 2011-05-29
Thanks, 

My bumblebee-disablecard file now looks like this: 

```

#!/bin/bash
rmmod nvidia
modprobe acpi_call

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    cat /proc/acpi/call
}

echo NVOP $(acpi_call "\_SB.PCI0.LPC.EC.PUBS._OFF 0 0x100 0x1A {255,255,255,255}")
echo _PS3 $(acpi_call "\_SB.PCI0.LPC.EC.PUBS._OFF") 

```

I could change it to your version, but I doubt that makes a difference, unless you mean for me not to use \_SB.PCI0.LPC.EC.PUBS._OFF but your code instead. 

Right now it seems to work, but safes nothing on the battery.

---

### Post by pszafer on 2011-05-29
Yes, of course You call wrong acpi method

For L502X You have to call \_SB.PCI0.PEG0.PEGP ON/OFF method.

---

### Post by bro on 2011-05-29
Did I mention I have a --lenovo w520 2720QM 8Gb Nvidia Quadro 1000 
;)

---

### Post by pszafer on 2011-05-29
not at all :p,

If You don't know if this command is working with Your laptop:
1. I assume You have loaded acpi_call module (sudo insmod acpi_call).
2. Now do it from terminal:
```
echo "\_SB.PCI0.LPC.EC.PUBS._OFF" > /proc/acpi/call
cat /proc/acpi/call
```

And result of cat is answer if this method is working for your model.

---

### Post by bro on 2011-05-29
the answer is 0x0

---

### Post by pszafer on 2011-05-29
It's good answer and it should work.

---

### Post by Ranko Kohime on 2011-05-30
pszafer: I got around to installing bumblebee, and I've run into a slight issue:

```
ranko@yggdrasil:~$ optirun64 vlc
 * Starting Bumblebee X server bumblebee                                        Enabling nVidia Card Succeded.
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-8-generic/updates/dkms/nvidia-current.ko): No such device
                                                                         [ OK ]
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x256a5e0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[VGL] ERROR: Could not open display :1.
 * Stopping Bumblebee X server bumblebee                                        ERROR: Module nvidia does not exist in /proc/modules
Disabling nVidia Card Succeded.
                                                                         [ OK ]

```

Nvidia current drivers are installed per Synaptic, any suggestions?

---

### Post by pszafer on 2011-05-30
Delete nvidia drivers

Do it in terminal:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get -y install nvidia-current

after install do manually:
modprobe nvidia-current

if everything is fine, it shouldn't show any errors and bumblebee would work too.

---

### Post by Ranko Kohime on 2011-05-30
> **pszafer said:**
> Delete nvidia drivers

Do it in terminal:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get -y install nvidia-current

after install do manually:
modprobe nvidia-current

if everything is fine, it shouldn't show any errors and bumblebee would work too.
No errors except on modprobe, at least that I could see.

```
ranko@yggdrasil:~$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ranko@yggdrasil:~$ sudo apt-get update
Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease                        
Ign http://ppa.launchpad.net natty InRelease                         
Ign http://security.ubuntu.com natty-security InRelease              
Ign http://us.archive.ubuntu.com natty InRelease                     
Ign http://us.archive.ubuntu.com natty-updates InRelease             
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://extras.ubuntu.com natty InRelease                                   
Get:1 http://security.ubuntu.com natty-security Release.gpg [198 B]  
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Get:2 http://ppa.launchpad.net natty Release.gpg [316 B]             
Get:3 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Get:4 http://security.ubuntu.com natty-security Release [27.2 kB]              
Get:5 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Get:6 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://extras.ubuntu.com natty Release                                     
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty/main Sources                                
Get:7 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]             
Get:8 http://security.ubuntu.com natty-security/main Sources [9,212 B]         
Get:9 http://ppa.launchpad.net natty Release [9,741 B]                         
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:10 http://ppa.launchpad.net natty Release [9,745 B]                        
Get:11 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:12 http://security.ubuntu.com natty-security/universe Sources [3,152 B]    
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                     
Get:13 http://security.ubuntu.com natty-security/multiverse Sources [647 B]    
Get:14 http://security.ubuntu.com natty-security/main amd64 Packages [28.8 kB] 
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:15 http://us.archive.ubuntu.com natty-updates/main Sources [34.9 kB]       
Get:16 http://security.ubuntu.com natty-security/restricted amd64 Packages [14 B]
Get:17 http://security.ubuntu.com natty-security/universe amd64 Packages [11.6 kB]
Get:18 http://security.ubuntu.com natty-security/multiverse amd64 Packages [1,930 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Get:19 http://ppa.launchpad.net natty/main Sources [2,307 B]                   
Get:20 http://ppa.launchpad.net natty/main amd64 Packages [6,578 B]            
Get:21 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:22 http://us.archive.ubuntu.com natty-updates/universe Sources [8,827 B]   
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:23 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,362 B] 
Get:24 http://ppa.launchpad.net natty/main Sources [20.4 kB]                   
Get:25 http://us.archive.ubuntu.com natty-updates/main amd64 Packages [114 kB] 
Get:26 http://ppa.launchpad.net natty/main amd64 Packages [32.1 kB]            
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Get:27 http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages [14 B]
Get:28 http://us.archive.ubuntu.com natty-updates/universe amd64 Packages [43.7 kB]
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:29 http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages [3,661 B]
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 399 kB in 11s (34.1 kB/s)                                              
Reading package lists... Done
ranko@yggdrasil:~$ sudo apt-get -y install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 0 B/51.7 MB of archives.
After this operation, 159 MB of additional disk space will be used.
Selecting previously deselected package nvidia-current.
(Reading database ... 154649 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_275.09-0ubuntu1~edgers~natty_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (275.09-0ubuntu1~edgers~natty) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-275.09 DKMS files...
Building only for 2.6.38-8-generic
Building for architecture x86_64
Building initial module for 2.6.38-8-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Processing triggers for python-support ...
ranko@yggdrasil:~$ sudo modprobe nvidia-current 
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-8-generic/updates/dkms/nvidia-current.ko): No such device
```
I tried turning the card on by "nv on" and re-running modprobe again, same result.  The light changed, so bumblebee is switching the card on and off, it's just not loading the module.

As for the file it wants, it's there:
```
ranko@yggdrasil:~$ ll /lib/modules/2.6.38-8-generic/updates/dkms/nvidia-current.ko 
-rw-r--r-- 1 root 16M 2011-05-30 21:47 /lib/modules/2.6.38-8-generic/updates/dkms/nvidia-current.ko

```
The Nvidia card is still showing in lspci.

---

### Post by pszafer on 2011-05-31
It seems You're using the nvidia card with the nouveau driver already, so try:
```
rmmod nouveau
```
and then:
```
modprobe nvidia-current
```

if that doesn't help show me Your:
```
lspci
lsmod
dmesg | grep nvidia
```

---

### Post by Ranko Kohime on 2011-05-31
> **pszafer said:**
> It seems You're using the nvidia card with the nouveau driver already, so try:
```
rmmod nouveau
```
and then:
```
modprobe nvidia-current
```

if that doesn't help show me Your:
```
lspci
lsmod
dmesg | grep nvidia
```

```
ranko@yggdrasil:~$ rmmod nouveau
ERROR: Module nouveau does not exist in /proc/modules
```

lspci:
```
ranko@yggdrasil:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 07)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 07)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev ff)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
08:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
```
lsmod:
```
ranko@yggdrasil:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   21708  0 
fat                    61374  1 vfat
nls_utf8               12557  0 
isofs                  40283  0 
usb_storage            53538  0 
uas                    17996  0 
snd_seq_dummy          12798  0 
acpi_call              12623  0 
aesni_intel            55161  4839 
cryptd                 20510  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            38279  2 aesni_intel,aes_x86_64
parport_pc             36959  0 
dm_crypt               22993  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_usb_audio         112426  0 
snd_usbmidi_lib        25139  1 snd_usb_audio
binfmt_misc            17565  1 
snd_hda_intel          33211  5 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96625  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  4 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
jmb38x_ms              17596  0 
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
memstick               16520  1 jmb38x_ms
xhci_hcd               77643  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
vhba                   17398  2 
coretemp               13490  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
i915                  514985  2 
drm_kms_helper         42136  1 i915
ahci                   25951  2 
drm                   227495  3 i915,drm_kms_helper
sdhci_pci              13989  0 
jme                    40728  0 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
usbhid                 46956  0 
hid                    91020  1 usbhid
```
dmesg:
```
ranko@yggdrasil:~$ dmesg | grep nvidia
[    9.400021] nvidia: module license 'NVIDIA' taints kernel.
[    9.745727] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.745730] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.745733] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[    9.745738] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.745744] nvidia 0000:01:00.0: setting latency timer to 64
[  832.673451] nvidia 0000:01:00.0: PCI INT A disabled
[  840.413406] nvidia 0000:01:00.0: power state changed by ACPI to D0
[  840.413409] nvidia 0000:01:00.0: power state changed by ACPI to D0
[  840.413413] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[  840.413417] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  840.413422] nvidia 0000:01:00.0: setting latency timer to 64
[  848.783253] nvidia 0000:01:00.0: PCI INT A disabled
[ 1634.506548] nvidia 0000:01:00.0: power state changed by ACPI to D0
[ 1634.506552] nvidia 0000:01:00.0: power state changed by ACPI to D0
[ 1634.506555] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[ 1634.506560] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1634.506566] nvidia 0000:01:00.0: setting latency timer to 64
[ 1662.308861] nvidia 0000:01:00.0: PCI INT A disabled
[82956.941249] nvidia 0000:01:00.0: power state changed by ACPI to D0
[82956.956107] nvidia 0000:01:00.0: power state changed by ACPI to D0
[82956.956112] nvidia 0000:01:00.0: enabling device (0506 -> 0507)
[82956.956118] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[82956.956126] nvidia 0000:01:00.0: setting latency timer to 64
[82956.956192] NVRM: www.nvidia.com.
[82956.956198] nvidia 0000:01:00.0: PCI INT A disabled
[82956.956205] nvidia: probe of 0000:01:00.0 failed with error -1
[82973.672321] nvidia 0000:01:00.0: power state changed by ACPI to D0
[82973.687837] nvidia 0000:01:00.0: power state changed by ACPI to D0
[82973.687852] nvidia 0000:01:00.0: enabling device (0506 -> 0507)
[82973.687868] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[82973.687887] nvidia 0000:01:00.0: setting latency timer to 64
[82973.688027] NVRM: www.nvidia.com.
[82973.688032] nvidia 0000:01:00.0: PCI INT A disabled
[82973.688043] nvidia: probe of 0000:01:00.0 failed with error -1
[83152.999614] nvidia 0000:01:00.0: power state changed by ACPI to D0
[83153.010705] nvidia 0000:01:00.0: power state changed by ACPI to D0
[83153.010709] nvidia 0000:01:00.0: enabling device (0506 -> 0507)
[83153.010723] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[83153.010729] nvidia 0000:01:00.0: setting latency timer to 64
[83153.010784] NVRM: www.nvidia.com.
[83153.010789] nvidia 0000:01:00.0: PCI INT A disabled
[83153.010800] nvidia: probe of 0000:01:00.0 failed with error -1
[104900.233161] nvidia 0000:01:00.0: power state changed by ACPI to D0
[104900.244757] nvidia 0000:01:00.0: Refused to change power state, currently in D3
[104900.244774] nvidia 0000:01:00.0: power state changed by ACPI to D0
[104900.244790] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[104900.244936] NVRM: www.nvidia.com.
[104900.244949] nvidia 0000:01:00.0: PCI INT A disabled
[104900.244967] nvidia: probe of 0000:01:00.0 failed with error -1
[105060.740321] nvidia 0000:01:00.0: power state changed by ACPI to D0
[105060.740324] nvidia 0000:01:00.0: power state changed by ACPI to D0
[105060.740328] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[105060.740333] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[105060.740338] nvidia 0000:01:00.0: setting latency timer to 64
[105060.740373] NVRM: www.nvidia.com.
[105060.740378] nvidia 0000:01:00.0: PCI INT A disabled
[105060.740382] nvidia: probe of 0000:01:00.0 failed with error -1
[105079.302904] nvidia 0000:01:00.0: power state changed by ACPI to D0
[105079.302907] nvidia 0000:01:00.0: power state changed by ACPI to D0
[105079.302913] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[105079.302920] nvidia 0000:01:00.0: setting latency timer to 64
[105079.302952] NVRM: www.nvidia.com.
[105079.302957] nvidia 0000:01:00.0: PCI INT A disabled
[105079.302962] nvidia: probe of 0000:01:00.0 failed with error -1
[168943.251571] nvidia 0000:01:00.0: power state changed by ACPI to D0
[168943.263076] nvidia 0000:01:00.0: Refused to change power state, currently in D3
[168943.263091] nvidia 0000:01:00.0: power state changed by ACPI to D0
[168943.263107] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[168943.263246] NVRM: www.nvidia.com.
[168943.263258] nvidia 0000:01:00.0: PCI INT A disabled
[168943.263275] nvidia: probe of 0000:01:00.0 failed with error -1
```

---

### Post by pszafer on 2011-06-01
First what I need (sometimes just answer question)
1. Do You have Windows on this laptop and are You using hibernate?
2. Give me output of 
```
cat /etc/X11/xorg.conf
cat /etc/X11/xorg.conf.nvidia
cat /etc/X11/xorg.conf.optiorig
```

3. Give me output of:
```
dpkg -l | grep xorg
```

4. Give me output of
```
sudo lshw
```

It could take some space, so consider adding outputs as attachment.

---

### Post by Ranko Kohime on 2011-06-01
> **pszafer said:**
> First what I need (sometimes just answer question)
1. Do You have Windows on this laptop and are You using hibernate?
No Windows, and no hibernate.  (not running swap.)

> **pszafer said:**
> 2. Give me output of 
```
cat /etc/X11/xorg.conf
cat /etc/X11/xorg.conf.nvidia
cat /etc/X11/xorg.conf.optiorig
```

3. Give me output of:
```
dpkg -l | grep xorg
```

4. Give me output of
```
sudo lshw
```

It could take some space, so consider adding outputs as attachment.
Check attachments to this post.

---

### Post by pszafer on 2011-06-01
I see, this happens in this laptop a lot times.

Try:
nvidia-xconfig, and if
```
dmesg | grep nvidia
```
doesn't show:
```
nvidia: probe of 0000:01:00.0 failed with error -1
```

then give this output here.

show also:
```
cat /var/log/Xorg.0.log
```

---

### Post by Ranko Kohime on 2011-06-02
> **pszafer said:**
> I see, this happens in this laptop a lot times.

Try:
nvidia-xconfig, and if
```
dmesg | grep nvidia
```
doesn't show:
```
nvidia: probe of 0000:01:00.0 failed with error -1
```

then give this output here.

show also:
```
cat /var/log/Xorg.0.log
```

dmesg IS showing the line you posted, but here's the whole output of the command:
```
ranko@yggdrasil:~$ dmesg | grep nvidia
[    9.393340] nvidia: module license 'NVIDIA' taints kernel.
[    9.739038] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.739041] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.739044] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[    9.739049] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.739054] nvidia 0000:01:00.0: setting latency timer to 64
[   12.150221] nvidia 0000:01:00.0: PCI INT A disabled
[46855.355322] nvidia 0000:01:00.0: power state changed by ACPI to D0
[46855.367777] nvidia 0000:01:00.0: power state changed by ACPI to D0
[46855.367792] nvidia 0000:01:00.0: enabling device (0506 -> 0507)
[46855.367808] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[46855.367829] nvidia 0000:01:00.0: setting latency timer to 64
[46855.367962] NVRM: www.nvidia.com.
[46855.367967] nvidia 0000:01:00.0: PCI INT A disabled
[46855.367986] nvidia: probe of 0000:01:00.0 failed with error -1

```
And in case it might be useful anyway, I'm attaching Xorg.0.log

---

### Post by pszafer on 2011-06-02
What kernel version do You have? (uname -a)
I think You should install 2.6.40 kernel (there are repositories with this kernel).
Also check if You have latest BIOS version for your laptop.


Also another idea is to uninstall Nvidia driver, install Nouveau.
Why?
Maybe we got more information about this error, because this logs says only that on BusID, which is entered nvidia doesn't exists.
But xorg.log.0 denies it.

---

### Post by Ranko Kohime on 2011-06-04
> **pszafer said:**
> What kernel version do You have? (uname -a)
I think You should install 2.6.40 kernel (there are repositories with this kernel).
Also check if You have latest BIOS version for your laptop.


Also another idea is to uninstall Nvidia driver, install Nouveau.
Why?
Maybe we got more information about this error, because this logs says only that on BusID, which is entered nvidia doesn't exists.
But xorg.log.0 denies it.

I'm running 2.6.38-8 generic, what came with Natty.

Before following any of the instructions in your most recent post, I rebooted, and was met with an Xserver that would not start up.  It also won't take pipes for some reason, so I can't get the error messages printed to screen.

I've tried switching around my various copies of Xorg.conf, switching nv on, (where it previously did not switch until I had logged in, where I had set the script to be called upon login, it's now switching at the point that boot halts), both to no avail.

I'm attaching the Xorg.0.log file again, in case it might be something elementary I may have missed.

---

### Post by pszafer on 2011-06-04
So let's just do how they say:
Fatal server error:
[  6815.935] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  6815.937] (EE) NVIDIA:     system's kernel log for additional error messages.

```
/var/log/kern.log
/var/log/syslog
/var/log/syslog.1
```

I don't need information about Your networks so for security reasons just delete all lines with NetworkManager in it ;)

If we got failed, I'll have time after 13th June, so I could try help You via ssh.
Of course if it will give anything we will post it here for other users ;)

---

### Post by aciidb0mb3r on 2011-06-05
Is it possible to get output from HDMI?

---

### Post by Ranko Kohime on 2011-06-05
> **pszafer said:**
> So let's just do how they say:
Fatal server error:
[  6815.935] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  6815.937] (EE) NVIDIA:     system's kernel log for additional error messages.

```
/var/log/kern.log
/var/log/syslog
/var/log/syslog.1
```

I don't need information about Your networks so for security reasons just delete all lines with NetworkManager in it ;)

If we got failed, I'll have time after 13th June, so I could try help You via ssh.
Of course if it will give anything we will post it here for other users ;)
After playing around with it for a while, I finally just got rid of Xorg.conf altogether, and that fixed the more immediate issue of not being able to start X.  Would you still need the above files for the issue of not loading the Nvidia driver, or was that specifically for the not starting X issue?

---

### Post by Ranko Kohime on 2011-06-05
> **aciidb0mb3r said:**
> Is it possible to get output from HDMI?
Referring to my problem, or to the platform in general?  I can't comment on either, as I have no HDMI devices to plug into.

I'm interested in an answer myself if you meant the latter sense, as while I don't own any HDMI devices, it would be handy if I could plug into them when at friends house's.

---

### Post by pszafer on 2011-06-06
@Ranko Kohime
Yes I need this file to know more why nvidia driver seems to not see your nvidia graphic card.

@aciidb0mb3r
hdmi output is impossible to get yet because, 
your standard monitor is connected to intel graphic card, 
hdmi is connected to nvidia graphic card.

And display manager cannot (for today) use two xorg.conf simultaneously.

You can get 3d and output monitor/tv with mini display-port, because it is connected to intel graphic card.

---

### Post by Ranko Kohime on 2011-06-06
> **pszafer said:**
> @Ranko Kohime
Yes I need this file to know more why nvidia driver seems to not see your nvidia graphic card.

@aciidb0mb3r
hdmi output is impossible to get yet because, 
your standard monitor is connected to intel graphic card, 
hdmi is connected to nvidia graphic card.

And display manager cannot (for today) use two xorg.conf simultaneously.

You can get 3d and output monitor/tv with mini display-port, because it is connected to intel graphic card.
Ok, here's both in a tarball.  In the work to get X working again I uninstalled both the Nvidia and Nouveau drivers, sometime around 15:30 on the 4th by the logs.  I'm only including syslog.1, as it was rotated in the morning of the 5th, when there was no driver present to be used.

---

### Post by Ranko Kohime on 2011-06-20
Update: I built kernel 3.0rc2, but it panicked on start-up.

I'm going to try another build with 3.0rc3, but is there anything I should specifically include in the build?

---

### Post by clipmaster3 on 2011-06-25
I attempted the method described at the beginning on this thread on a fresh install, except on an XPS17 L702X, and upon running test_off.sh everything fails (which I suppose means the driver wasn't successfully turned off...)
Help?  I'm only getting 2.5 hours of battery life on here as opposed to 7 with windows 7 :/

---

### Post by Ranko Kohime on 2011-07-03
> **clipmaster3 said:**
> I attempted the method described at the beginning on this thread on a fresh install, except on an XPS17 L702X, and upon running test_off.sh everything fails (which I suppose means the driver wasn't successfully turned off...)
Help?  I'm only getting 2.5 hours of battery life on here as opposed to 7 with windows 7 :/
Run this:

```
lspci | grep -i vga
```

If you see nothing about Nvidia, power the laptop off, then restart.  The card seems to disappear under certain conditions on reboot (typically with the acpi_call module loaded at reboot time, in my experience).

Alternatively, the XPS might have a different BIOS than mine, check in the BIOS if you can disable the discreet card there, which would save battery life as well.

---

### Post by pszafer on 2011-07-03
sorry, for such long time no responses from me, but I had really busy lat 2 weeks.

@clipmaster3
here somebody got L702x graphic card successfully turned off - [https://lists.launchpad.net/hybrid-graphics-linux/msg00663.html]("https://lists.launchpad.net/hybrid-graphics-linux/msg00663.html")

@Ranko Kohime
waht's Your status about nvidia turning off?

I should warn You and many others that newest updates of Ubuntu 11.04 in my case destroyed all X'es, all bumbleebee and other configs - horrible.
Probably I will coming back to latest configuration a few hours :(

---

### Post by Ranko Kohime on 2011-07-14
> **pszafer said:**
> @Ranko Kohime
waht's Your status about nvidia turning off?

I should warn You and many others that newest updates of Ubuntu 11.04 in my case destroyed all X'es, all bumbleebee and other configs - horrible.
Probably I will coming back to latest configuration a few hours :(
I haven't experienced any updates causing major breakages, just a few annoyances.  I've got the edgers and bumblebee PPA's, and I've upgraded to 2.6.38-10 kernel.  I still haven't successfully built a 3.0-anything kernel, as the ones I do kernel panic, and I'm not sure what options I'm missing in the compile stage.  I'd be interested to know what broke your setup, so I can avoid it, if I haven't already experienced it.

I am experiencing the occasional total lockup, but it's unrepeatable, and I haven't experienced it for more than a week now, and I honestly have no idea if it's even related to the video card mess, or my processor (engineering sample)

I've had the ability to disable the Nvidia card for a while, I think since I saw this thread, and still do.  Temperatures are down noticeably, and battery life appears to be over 3 hours, whenever the card is disabled.

I upgraded to the bumblebee PPA version, and now it re-enables the card on shutdown, so I can reboot instead of shutting down and powering back on.  (Previously, the driver would leave the card disabled, or force it disabled if I had purposely enabled it on rebooting, causing the card to disappear from lspci for as long as the laptop remained powered on, and upon reboot the card automatically becomes enabled, and since it can't be seen, can't be disabled.)

Only real issue I'm still having is getting the Performance mode working.  The display updates around 20-22 FPS, which is just a little annoying watching videos at 30 FPS.  When I do
```
optirun64 vlc
```
I get the following:
```
ranko@yggdrasil:~$ optirun64 vlc
 * Starting Bumblebee X server bumblebee                                                                                                                         Enabling nVidia Card Succeded.
                                                                                                                                                          [ OK ]
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xafebf0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-ranko", 1)
Warning: call to srand(1310373608)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:21611): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

```
Upon playing the video, it's obviously still running on the integrated graphics only, even though the card light is showing active.

Also, although I haven't tested it yet to confirm that my hardware is laid out the same, if the HDMI port is connected to the Nvidia card as opposed to the combined output stage, I'd like to get that working, as I can see a future use for the HDMI port.

---

