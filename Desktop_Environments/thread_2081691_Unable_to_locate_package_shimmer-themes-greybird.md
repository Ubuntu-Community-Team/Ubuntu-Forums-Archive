---
title: "Unable to locate package shimmer-themes-greybird"
date: 2012-11-07
forum: Desktop Environments
---

### Post by slickymaster on 2012-11-07
Good afternoon.

I did the installation of the Greybird_Mac package in Xubuntu 12.10, using the PPA SHIMMER:
sudo add-apt-repository ppa: shimmerproject / ppa
sudo apt-get update

So far no problems, the imbroglio comes when I gave the command sudo apt-get update.

The output is this:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
E: Unable to locate package shimmer-themes-greybird

And as it is not installed I can not select the "greybird-git" from the settings of XFCE to apply the theme. Can anyone give me a light to solve this?

---

### Post by vasa1 on 2012-11-07
> **slickymaster said:**
> Good afternoon.

I did the installation of the Greybird_Mac package in Xubuntu 12.10, using the PPA SHIMMER:
[B]sudo add-apt-repository ppa: shimmerproject / ppa
[/B]...
What did you see in the terminal when you entered the stuff in bold (from your post)?
I think you have extra spaces in there after **ppa:**. Try without any spaces. You should then see, among other things, a prompt asking you to press enter if you want to continue.

See: [https://launchpad.net/~shimmerproject/+archive/ppa](https://launchpad.net/~shimmerproject/+archive/ppa)

---

### Post by slickymaster on 2012-11-07
I've been trying to work around it and I think I've manage sonething.

I'll paste my Terminal so you'll have a better understanding of what is happening.

slickymaster@PaPir:~$ sudo add-apt-repository ppa:shimmerproject/ppa
[sudo] password for slickymaster: 
You are about to add the following PPA to your system:
 This PPA contains gtk-themes (incl. the murrine-engine, which is a dependency for the themes in order to work properly) and a modified version of gmusicbrowser.

The gmusicbrowser package is built from our Git branch source ([https://github.com/shimmerproject/gmusicbrowser](https://github.com/shimmerproject/gmusicbrowser)). It is based on gmusicbrowser-upstream-git, but includes our own SongTree layout as well as many other improvements to the overall looks.
 More info: [https://launchpad.net/~shimmerproject/+archive/ppa](https://launchpad.net/~shimmerproject/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpi340rh/secring.gpg' created
gpg: keyring `/tmp/tmpi340rh/pubring.gpg' created
gpg: requesting key 685D1580 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpi340rh/trustdb.gpg: trustdb created
gpg: key 685D1580: public key "Launchpad PPA for the Shimmer Project" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
slickymaster@PaPir:~$ sudo apt-get update
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal InRelease
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports InRelease         
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal Release                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en             
Get:4 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates Release [49.6 kB] 
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports Release               
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/main Sources                  
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/restricted Sources            
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/universe Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/main i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/main Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal/universe Translation-en
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [7679 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]
Get:8 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/main Sources [22.0 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [2661 B]
Get:10 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/restricted Sources [14 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [695 B]
Get:12 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/universe Sources [7571 B]
Get:13 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/multiverse Sources [695 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [31.0 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [6888 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1394 B]
Get:18 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/main i386 Packages [59.5 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Get:19 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/restricted i386 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Get:20 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/universe i386 Packages [25.7 kB]
Get:21 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [1394 B]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/main Translation-en
Get:22 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/multiverse Translation-en [587 B]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/main Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/universe Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) quantal-backports/universe Translation-en
Fetched 269 kB in 4s (59.5 kB/s)
Reading package lists... Done
slickymaster@PaPir:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
slickymaster@PaPir:~$ 

Now, so far as I can guest it's already installed, right? But I'm still not able to select the "greybird-git" from the settings of XFCE to apply the theme.

Thanks a lot for you help so far, but can you still help me a little more?

---

### Post by badhorse on 2012-11-07
I have greybird-git in 12.04 and it's the same that default in 12.10. What do you really want to install? Simply select greybird theme in  preferences.

---

### Post by vasa1 on 2012-11-07
Could you put up a list of folders in /usr/share/themes?
And, for readability, you can place the contents between code tags (click the # thingy).

---

### Post by slickymaster on 2012-11-07
Sorry, I'm new to Linux, just been using it for a day, yet.

Anyway, where it goes:

```
file:///usr/share/themes/ZOMG-PONIES!
file:///usr/share/themes/ThinIce
file:///usr/share/themes/Smoke
file:///usr/share/themes/Redmond
file:///usr/share/themes/Raleigh
file:///usr/share/themes/Moheli
file:///usr/share/themes/Mist
file:///usr/share/themes/LowContrast
file:///usr/share/themes/Kokodi
file:///usr/share/themes/Industrial
file:///usr/share/themes/HighContrastInverse
file:///usr/share/themes/HighContrast
file:///usr/share/themes/Greybird-compact
file:///usr/share/themes/Greybird
file:///usr/share/themes/Emacs
file:///usr/share/themes/Default
file:///usr/share/themes/Daloa
file:///usr/share/themes/Crux
file:///usr/share/themes/Clearlooks
file:///usr/share/themes/Bluebird
file:///usr/share/themes/Blackbird
file:///usr/share/themes/Albatross

```

So far as I can tell, I think it's there, but how do I make use of it in the settings of XFCE to apply the theme?

---

### Post by vasa1 on 2012-11-07
> **slickymaster said:**
> Sorry, I'm new to Linux, just been using it for a day, yet.

...
So far as I can tell, I think it's there, but how do I make use of it in the settings of XFCE to apply the theme?

Check out this page and the links there. It will be very helpful to you.
[http://docs.xfce.org/xfce/xfce4-settings/appearance](http://docs.xfce.org/xfce/xfce4-settings/appearance)

---

### Post by badhorse on 2012-11-07
Sorry but i don't understand your problem. Greybird is the default theme for xubuntu 12.10. Select the theme you want in settings manager > appearance.

---

### Post by slickymaster on 2012-11-07
Yes, I know that, but what I want is to use Greybird-Mac. This one

[IMG]http://xfce-look.org/CONTENT/content-pre1/149800-1.png[/IMG]

How can I get to set it in the XFCE settings. I went to settings manager > appearance but I don't have it there.

---

### Post by slickymaster on 2012-11-07
Solved. Just downloaded the tarball from [http://xfce-look.org/](http://xfce-look.org/) and drag it into the list of styles in settings manager > appearance.

Thank you vasa1 and badhorse for all your help.

---

