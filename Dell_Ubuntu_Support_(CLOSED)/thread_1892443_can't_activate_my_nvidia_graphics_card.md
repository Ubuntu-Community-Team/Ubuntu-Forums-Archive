---
title: "can't activate my nvidia graphics card"
date: 2011-12-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 450rOOST on 2011-12-08
DISCLAIMER:  NOOB IN THE HOUSE!!

I installed 11.10, I am having trouble with my video card.  

I have tried both these options, (recommended) and (post-release) to no avail.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/Screenshotat2011-12-06210422.png[/IMG]

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/Screenshotat2011-12-06221554.png[/IMG]

When I run nvidia-xconfig, it tells me to reboot, then I can't boot into ubuntu.  It starts loading and stops here:

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/IMAG0005.jpg[/IMG]

on the right where it says [ok] or [fail], I get a [fail] on the line that says 'generate automatic crash reports'

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/IMAG0006.jpg[/IMG]

Thanks in advance to anyone taking the time to view this post.

---

### Post by 450rOOST on 2011-12-08
I resized and cropped those photos, thats not what they look like in my photobucket account???  Sorry for the huge images.

---

### Post by zeljkojagust on 2011-12-08
Download Nvidia Linux drivers for your card from Nvidia website. Start your computer, after you log in open terminal console. If you have a normal user account by using **sudo** and **su** set the password for root user. Still in terminal console execute **init 1**. It will switch you in single user mode and it will kill X windows service. Enter your root password and position yourself in folder where you downloaded Nvidia drivers. Install drivers by executing **sh drivers-file-name**. On the first screen you will select **NO** to continue installation, and on every other screen you will confirm with **YES**. Afret that you should be able to use you Nvidia GPU.

---

### Post by zeljkojagust on 2011-12-08
And something I forget to mention. After every upgrade of kernel, you will have to repeat the process of driver installation. Hope it won't be hard for you.

---

### Post by BC59 on 2011-12-08
To get you out of this, restart your computer and try to get to the command line, from the recovery mode.

If not try to use CTRL+ALT+F1

Then logon and run:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by BC59 on 2011-12-08
You should run

```
sudo nvidia-xconfig
``` and reboot

---

### Post by 450rOOST on 2011-12-08
Awesome folks, I really appreciate the help, I am going to give this a whirl when I get home. 


BC59, when you say run nvidia-xconfig, I assume you mean after I run:
> sudo dpkg --configure -a
sudo apt-get -f install

otherwise I will be in the same spot I am in now.  Thanks!

---

### Post by BC59 on 2011-12-08
> **450rOOST said:**
> Awesome folks, I really appreciate the help, I am going to give this a whirl when I get home. 


BC59, when you say run nvidia-xconfig, I assume you mean after I run:


otherwise I will be in the same spot I am in now.  Thanks!

Well as I understand your computer is blocked now. To unblock it there are some ways. One way is to run sudo dpkg --configure -a and then sudo apt-get -f install. Then we see what we can do.

---

### Post by 450rOOST on 2011-12-09
> **BC59 said:**
> Well as I understand your computer is blocked now. To unblock it there are some ways. One way is to run sudo dpkg --configure -a and then sudo apt-get -f install. Then we see what we can do.

ohh boy, whoops.  Sorry to lead folks astray, I have since re-installed ubuntu, the top two images is where I am at now, card isn't activated, or says it is, but it really isnt.

This is the 3rd time I've started a thread with the same problem, I had started two over in 'absolute beginner'.  

darn, I feel like an idiot.  So, I am in ubuntu, if I run nvidia-xconfig, I will be where I was when I was locked out, unable to boot into ubuntu.

any suggestions?

---

### Post by josephmills on 2011-12-09
hello there please open your terminal and type in 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```
I hope that this helps 
joseph

---

### Post by 450rOOST on 2011-12-09
> **zeljkojagust said:**
> Download Nvidia Linux drivers for your card from Nvidia website. Start your computer, after you log in open terminal console. If you have a normal user account by using **sudo** and **su** set the password for root user. Still in terminal console execute **init 1**. It will switch you in single user mode and it will kill X windows service. Enter your root password and position yourself in folder where you downloaded Nvidia drivers. Install drivers by executing **sh drivers-file-name**. On the first screen you will select **NO** to continue installation, and on every other screen you will confirm with **YES**. Afret that you should be able to use you Nvidia GPU.

ok, I just downloaded the driver from the nvidia site.  I don't know how to 'position myself in the folder' when I'm in a terminal.  The terminal is almost foreign land to me.  

so, I'll open the terminal, and type 'su', enter my password, then type 'init 1', type password, then how do I 'position myself' in the correct folder?  

I use chromium, on my home screen I can get to the folder where the file I downloaded is, can I not just click on it and install from there?

---

### Post by 450rOOST on 2011-12-09
> **josephmills said:**
> hello there please open your terminal and type in 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```
I hope that this helps 
joseph

sorry, just saw this, doing this first...

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> ok, I just downloaded the driver from the nvidia site.  I don't know how to 'position myself in the folder' when I'm in a terminal.  The terminal is almost foreign land to me.  

so, I'll open the terminal, and type 'su', enter my password, then type 'init 1', type password, then how do I 'position myself' in the correct folder?  

I use chromium, on my home screen I can get to the folder where the file I downloaded is, can I not just click on it and install from there?

you do not need the driver from the site as that repository  in the last post does everything and then some that that driver will do that you get from the site. coulde you please open your terminal and type in 
```
lspci -nn | grep VGA 
``` and paste here thanks

---

### Post by 450rOOST on 2011-12-09
...

> smoker@smoker:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for smoker: 
You are about to add the following PPA to your system:
 X Updates
 Updated versions of X.org drivers, libraries, etc. for Ubuntu.

This PPA is for stable upstream releases of X.org components.  If you're looking for something even more bleeding-edge, please see the xorg-edgers PPA.  Or, if you're actually wanting backports of the current stable X stack to an older Ubuntu release, see the x-backports PPA.

While Ubuntu-X does not officially support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad.  However, please make sure to clearly state that you are running packages from this PPA so we know the fixes need to come here.

If you are uprading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.
 More info: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.oXAurrw6in --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


---

### Post by 450rOOST on 2011-12-09
...
> smoker@smoker:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df5] (rev a1)


---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> sorry, just saw this, doing this first...

NP I am often editing posts and then I look back and I am like o yah but at any rate hope you enjoy

also as you can see you could add the xorg-edgers PPA[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) also to make it even more up-to-date but this can cause troubles sometime. best to stick with stable

---

### Post by 450rOOST on 2011-12-09
> **450rOOST said:**
> sorry, just saw this, doing this first...

ok, just ran the three commands you instructed, how do I check if it worked?

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> ok, just ran the three commands you instructed, how do I check if it worked?

reboot the computer and go to nvidia settings or watch for the nvidia splash logo on reboot, or open terminal and do a ```
lsmod
``` see if nvidia is listed Also like I said above I would look at 
 xorg-edgers PPA  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
if you need help with that just ask.

---

### Post by 450rOOST on 2011-12-09
well Joe, I see no nvidia, I am going to check out the other link you posted.  I was just a little scared since you said it can cause problems, and I've had my share of those and I'm not to keen at fixing the problems yet...

> smoker@smoker:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
bnep                   18436  2 
rfcomm                 47946  8 
binfmt_misc            17540  1 
nvidia              12128043  0 
arc4                   12529  2 
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iwlagn                314213  0 
btusb                  18600  2 
mac80211              462092  1 iwlagn
bluetooth             166112  23 bnep,rfcomm,btusb
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
psmouse                73882  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566711  2 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41480  0 
wmi                    19256  1 dell_wmi
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
xhci_hcd               82772  0 
smoker@smoker:~$ 


---

### Post by 450rOOST on 2011-12-09
once again, I'm a dummy.

> nvidia              12128043  0

---

### Post by 450rOOST on 2011-12-09
I just got 'linux for dummies'  

I think I am going to give that a good read before I bother you helpful folks around here too much more.  I would just rather play with the os then read, but, I need some more info before I play too much more.

Thanks again for your help!

I showed my support for you gaining membership, good luck!

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> well Joe, I see no nvidia, I am going to check out the other link you posted.  I was just a little scared since you said it can cause problems, and I've had my share of those and I'm not to keen at fixing the problems yet...

ok could We please see a 
```
lsb_release -a
```
thanks

---

### Post by 450rOOST on 2011-12-09
...
> smoker@smoker:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
smoker@smoker:~$ 


---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> ...

sweet open terminal 
```
sudo echo deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get -y install nvidia-current && sudo reboot 

 
```
let us know if you get the nvidia logo on reboot

---

### Post by 450rOOST on 2011-12-09
> **josephmills said:**
> sweet open terminal 
```
sudo echo deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get -y install nvidia-current && sudo reboot 

 
```
let us know if you get the nvidia logo on reboot

sorry if I'm dumb, but is that supposed to be one command?

> smoker@smoker:~$ sudo echo deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get -y install nvidia-current && sudo reboot
bash: /etc/apt/sources.list: Permission denied
smoker@smoker:~$ 



---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> sorry if I'm dumb, but is that supposed to be one command?

no you are not dumb and yes that is supposed a bunch of commands tied togeather with the && try it again make sure you enter correct password

my bad  DUH here you go 
```
sudo echo "deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main" >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get -y install nvidia-current && sudo reboot
```

---

### Post by 450rOOST on 2011-12-09
I figured that's what the && was doing.

it's not asking me for a password, I get the same return 'permission denied'  

> smoker@smoker:~$ sudo echo "deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main" >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get -y install nvidia-current && sudo reboot
bash: /etc/apt/sources.list: Permission denied
smoker@smoker:~$ 



---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> I figured that's what the && was doing.

it's not asking me for a password, I get the same return 'permission denied'
```
sudo -i 
```
```

echo "deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main" >> /etc/apt/sources.list && apt-get update && apt-get -y install nvidia-current &&  reboot

```

---

### Post by 450rOOST on 2011-12-09
is this too much too much to post back to you?  I'm gonna reboot now.

> smoker@smoker:~$ sudo -i
[sudo] password for smoker: 
root@smoker:~# echo "deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main" >> /etc/apt/sources.list && apt-get update && apt-get -y install nvidia-current &&  reboot
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,751 B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages [36.2 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [36.4 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 82.7 kB in 4s (20.1 kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xserver-common xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
Suggested packages:
  xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze
  firmware-linux
The following packages will be upgraded:
  nvidia-current xserver-common xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
29 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
Need to get 64.0 MB of archives.
After this operation, 69.6 kB disk space will be freed.
WARNING: The following packages cannot be authenticated!
  xserver-xorg-video-intel xserver-xorg-video-vmware xserver-xorg-video-vesa
  xserver-xorg-video-trident xserver-xorg-video-tdfx xserver-xorg-video-sisusb
  xserver-xorg-video-sis xserver-xorg-video-siliconmotion
  xserver-xorg-video-savage xserver-xorg-video-s3 xserver-xorg-video-radeon
  xserver-xorg-video-r128 xserver-xorg-video-qxl xserver-xorg-video-openchrome
  xserver-xorg-video-nouveau xserver-xorg-video-neomagic
  xserver-xorg-video-mga xserver-xorg-video-mach64 xserver-xorg-video-fbdev
  xserver-xorg-video-cirrus xserver-xorg-video-ati nvidia-current
  xserver-xorg-input-vmmouse xserver-xorg-input-synaptics
  xserver-xorg-input-mouse xserver-xorg-input-evdev xserver-xorg-core
  xserver-xorg-input-wacom xserver-common
E: There are problems and -y was used without --force-yes
root@smoker:~# 


---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> is this too much too much to post back to you?  I'm gonna reboot now.
```

sudo apt-get install nvidia-current 

```
then press y or Y when it asks if you want to install

---

### Post by 450rOOST on 2011-12-09
I didn't catch any nvidia logo on reboot.

---

### Post by 450rOOST on 2011-12-09
> **josephmills said:**
> ```

sudo apt-get install nvidia-current 

```
then press y or Y when it asks if you want to install

doing this now...

---

### Post by 450rOOST on 2011-12-09
> **450rOOST said:**
> doing this now...

did that, reboot now?

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> did that, reboot now?

```
sudo apt-get upgrade 
```
then reboot

---

### Post by 450rOOST on 2011-12-09
this was the last few lines, I see it says fails, and also says amd in there, I have intel i7, does that matter, I can see why it would fail, is that just routine there?

rebooting now...

> Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/libv/libva/libva1_1.0.15-1~xup1_amd64.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/libv/libva/libva1_1.0.15-1~xup1_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
smoker@smoker:~$ 

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> this was the last few lines, I see it says fails, and also says amd in there, I have intel i7, does that matter, I can see why it would fail, is that just routine there?

rebooting now...

```
sudo apt-get --fix-missing update && sudo apt-get upgrade

```

---

### Post by 450rOOST on 2011-12-09
...
> smoker@smoker:~$ sudo apt-get --fix-missing update && sudo apt-get upgrade
[sudo] password for smoker: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 316 B in 3s (79 B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libcairo2 libcairo2:i386
The following packages will be upgraded:
  acpid intel-gpu-tools libcairo-gobject2 libdrm-intel1 libdrm-nouveau1a
  libdrm-radeon1 libdrm2 libffi6 libffi6:i386 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libglu1-mesa libpciaccess0 libpixman-1-0 libpixman-1-0:i386
  libunity-core-4.0-4 libva1 linux-libc-dev unity unity-common unity-services
  x11-common xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
27 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 38.6 kB/7,320 kB of archives.
After this operation, 176 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libcairo-gobject2 libdrm2 libpciaccess0 libdrm-intel1 libdrm-nouveau1a
  libdrm-radeon1 libffi6 libffi6 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglu1-mesa libpixman-1-0 libpixman-1-0 intel-gpu-tools libunity-core-4.0-4
  unity-services linux-libc-dev unity unity-common x11-common
  xserver-xorg-video-all xserver-xorg-input-all xserver-xorg xorg
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) oneiric/main libva1 amd64 1.0.15-1~xup1 [38.6 kB]
Fetched 1 B in 0s (2 B/s)          
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/libv/libva/libva1_1.0.15-1~xup1_amd64.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/libv/libva/libva1_1.0.15-1~xup1_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
smoker@smoker:~$ 


---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> ...
```

gksudo gedit  /etc/apt/sources.list

```


then go all the way down to the bottom and add a # in front of the last line so it looks like this 
```
##deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
```
save the file and close gedit 
then 
```
sudo apt-get update && sudo apt-get upgrade 
```
then reboot

---

### Post by 450rOOST on 2011-12-09
rebooting now...

---

### Post by 450rOOST on 2011-12-09
I didn't see any error or fail messages, but not nvidia logo on reboot.

the nvidia control panel folder was in the system settings folder, I think, but it's not there now, hasn't been for a little bit since we started trying things.

but when I go to system settings>system info>graphics:
Driver: unkown
Experience: Standard

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> rebooting now...

ok after reboot Un comment that  that last line in gedit so it looks like this 
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main
```
Now save and exit 
open terminal and 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1024R/8844C542


```

then 
```
sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by 450rOOST on 2011-12-09
> smoker@smoker:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1024R/8844C542
[sudo] password for smoker: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.pKXzvmWB2y --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1024R/8844C542
gpg: "1024R/8844C542" not a key ID: skipping
smoker@smoker:~$ 


I also ran the next command, rebooting...

---

### Post by 450rOOST on 2011-12-09
no nvidia logo.  Hey man, I'm sure there are some other folks that would appreciate your help if your still up to it, we can revisit this another day.  I'm not giving up, I just don't want to consume much more of your time.  

I really like this forum, it's the reason I went with ubuntu over fedora, cause the help here is awesome.

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> no nvidia logo.  Hey man, I'm sure there are some other folks that would appreciate your help if your still up to it, we can revisit this another day.  I'm not giving up, I just don't want to consume much more of your time.  

I really like this forum, it's the reason I went with ubuntu over fedora, cause the help here is awesome.

I told you the wrong key sorry 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 450rOOST on 2011-12-09
> [sudo] password for smoker: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.ZMcdrTcJNk --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
smoker@smoker:~$ 


running the next command then rebooting...

---

### Post by 450rOOST on 2011-12-09
> smoker@smoker:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 388 B in 3s (101 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libcairo2 libcairo2:i386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
smoker@smoker:~$ 


rebooting...

---

### Post by 450rOOST on 2011-12-09
to no avail, I think?

---

### Post by jespdj on 2011-12-09
Wait a minute.

Why are you thinking that it wasn't working when you started? Look at that very first picture you posted. Note that at the bottom of the window it says:

**This driver is activated and currently in use.**

So, it was already using the NVIDIA driver that was installed from the start. It isn't necessary to download it from the NVIDIA website and do all those complicated things...

Maybe you should just have tried rebooting and restarting the nvidia settings tool.

---

### Post by 450rOOST on 2011-12-10
> **jespdj said:**
> Wait a minute.

Why are you thinking that it wasn't working when you started? Look at that very first picture you posted. Note that at the bottom of the window it says:

**This driver is activated and currently in use.**

So, it was already using the NVIDIA driver that was installed from the start. It isn't necessary to download it from the NVIDIA website and do all those complicated things...

Maybe you should just have tried rebooting and restarting the nvidia settings tool.

Hi jespdj,  well, check out the second image where it says 'You do not appear to be using the nvidia x driver...'

Also, someone else was helping me in another thread and they said this is known problem, where it says it is installed and in use, but it is not.  
But to answer your question, I truly do not know what is going on inside this machine.  This is all new to me.  I am an 'absolute beginner', but I wasn't getting many tips or info in that forum.

I know that my conky says I'm running unity-2d.  Joe said I should see a nvidia logo on boot.  I want to get the cube and some 3d going on.  

I will post some screenshots here in a moment...

---

### Post by 450rOOST on 2011-12-10
I don't know what this means.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/DriverUnknown.jpg[/IMG]

---

### Post by RomeReactor on 2011-12-10
Hi. I have an Inspiron 15R N5110, which is very similar to your XPS 15. [Your L502X]("http://www.dell.com/us/dfh/p/xps-l502x/pd") uses both an integrated Intel GPU and a discreet 525M; it switches between the two on the fly with Optimus, a method developed by nVidia that routes the video information from the 525M *through the integrated GPU*, meaning that while you can just use the Intel GPU, you can't just use 525M alone. It also means that you can't use the nVidia driver since they don't offer support for Optimus on Linux (more on Optimus [here]("http://ubuntuforums.org/showthread.php?t=1657660")).

There is a way to use the nVidia GPU, installing either [Bumblebee]("https://launchpad.net/~bumblebee") or [Ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/") (both projects created by the [same guy]("http://www.martin-juhl.dk/"), although he seems to be concentrating on Ironhide). [This guide]("http://community.linuxmint.com/tutorial/view/610") gives fairly straightforward instructions on installing Ironhide.

Hope this helps.

---

### Post by 450rOOST on 2011-12-12
> **RomeReactor said:**
> Hi. I have an Inspiron 15R N5110, which is very similar to your XPS 15. [Your L502X]("http://www.dell.com/us/dfh/p/xps-l502x/pd") uses both an integrated Intel GPU and a discreet 525M; it switches between the two on the fly with Optimus, a method developed by nVidia that routes the video information from the 525M *through the integrated GPU*, meaning that while you can just use the Intel GPU, you can't just use 525M alone. It also means that you can't use the nVidia driver since they don't offer support for Optimus on Linux (more on Optimus [here]("http://ubuntuforums.org/showthread.php?t=1657660")).

There is a way to use the nVidia GPU, installing either [Bumblebee]("https://launchpad.net/~bumblebee") or [Ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/") (both projects created by the [same guy]("http://www.martin-juhl.dk/"), although he seems to be concentrating on Ironhide). [This guide]("http://community.linuxmint.com/tutorial/view/610") gives fairly straightforward instructions on installing Ironhide.

Hope this helps.

great information Rome.  Does that mean that my 3d capabilities are limited?  Last time I was trying to get the cube up and running, I was reading that I need accelerated 3d graphics??  I am not going to be able to do that?  Same deal with SuperTuxKart, I thought I read that I needed 3d graphics.  I want to get unity-3d going, if that is such a thing.  

Thanks for the info.

---

### Post by RomeReactor on 2011-12-12
> **450rOOST said:**
> Last time I was trying to get the cube up and running, I was reading that I need accelerated 3d graphics??  I am not going to be able to do that?  Same deal with SuperTuxKart, I thought I read that I needed 3d graphics.

The integrated GPU on the 2630QM is an Intel HD Graphics 3000, and the open source driver provides 3D acceleration for it, so you can play **some** 3D games, but not all. Also, Unity 3D runs well under this Intel GPU. The things is, with Optimus-enabled laptops it's recommended that you don't install the nVidia driver *at all* either during Ubuntu's installation or afterwards, regardless of whether you want to use the nVidia card through Bumblebee or Ironhide, or just want to use the integrated Intel GPU; if you **do** want to install Bumblebee or Ironhide, either of those will handle the installation of the binary nVidia driver on their own.

Not sure if SuperTux Kart will run correctly on the integrated GPU, though.

---

### Post by marty331 on 2011-12-23
> **RomeReactor said:**
> Hi. I have an Inspiron 15R N5110, which is very similar to your XPS 15. [Your L502X]("http://www.dell.com/us/dfh/p/xps-l502x/pd") uses both an integrated Intel GPU and a discreet 525M; it switches between the two on the fly with Optimus, a method developed by nVidia that routes the video information from the 525M *through the integrated GPU*, meaning that while you can just use the Intel GPU, you can't just use 525M alone. It also means that you can't use the nVidia driver since they don't offer support for Optimus on Linux (more on Optimus [here]("http://ubuntuforums.org/showthread.php?t=1657660")).

There is a way to use the nVidia GPU, installing either [Bumblebee]("https://launchpad.net/~bumblebee") or [Ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/") (both projects created by the [same guy]("http://www.martin-juhl.dk/"), although he seems to be concentrating on Ironhide). [This guide]("http://community.linuxmint.com/tutorial/view/610") gives fairly straightforward instructions on installing Ironhide.

Hope this helps.

I have literally read every word of this post, this is EXACTLY the same scenario I had going on.  Well Ironhide fixed the problem!  I worked on trying to solve not being able to run Compiz or my Nvidia graphics card for the past two days (relentlessly) and this solved everything!  Thanks so much for posting this info.

---

