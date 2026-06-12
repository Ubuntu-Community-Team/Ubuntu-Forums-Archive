---
title: "ATI Radeon XPress 200 works for Beryl?"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by paladin_knight on 2007-06-19
Hey guyz, I would like to know if I could using beryl in my ubuntu with ATI RadeonXpress 200 as my video card ( integrated):p

---

### Post by divague on 2007-06-19
Yes, you can. My laptop has that card i'm using it with 32 MB and beryl is working fine.

---

### Post by meindian523 on 2007-06-20
Not here,the window manager keeps crashing......and falls back to metacity window manager.
There's a rearrangement of windows that takes place for a few seconds and then evrything is back in it's place and the window manager is metacity.......

My Hardware:
Pentium D 2.80 GHz Dual Core
Intel D101GGC mobo
(Integrated ATi Radeon XPress 200 Series graphic card)
IDE 80 GB HDD
IDE TSSTCorp CDRW/DVD-R combo drive SH-M522C
:(

---

### Post by paladin_knight on 2007-06-20
[COLOR="Green"]I have tried to use desktop effects but what I got was blank screen. 
So , I am still afraid to go on.:(

NB: I haven't installed beryl[/COLOR]

---

### Post by meindian523 on 2007-06-20
It works,it works!:D

Don't try the Desktop effects,I tried too,my box hanged and I had to put it off from the plug point.......

A very good guide to Beryl on Ubuntu is here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29")

I did the restricted drivers method since I had already installed the fglrx driver from ATi....ahead it's your choice whether to go for the open-source method........

---

### Post by paladin_knight on 2007-06-20
[COLOR="Magenta"] I tried method no 1 but there was an error with the gpg key
[/COLOR]

```
root@paladin-desktop:/etc/apt# apt-get updateGet:1 http://sg.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://sg.archive.ubuntu.com feisty/main Translation-en_SG                 
Ign http://sg.archive.ubuntu.com feisty/restricted Translation-en_SG           
Ign http://sg.archive.ubuntu.com feisty/universe Translation-en_SG             
Ign http://sg.archive.ubuntu.com feisty/multiverse Translation-en_SG           
Get:2 http://sg.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://sg.archive.ubuntu.com feisty-updates/main Translation-en_SG         
Ign http://sg.archive.ubuntu.com feisty-updates/restricted Translation-en_SG   
Hit http://sg.archive.ubuntu.com feisty Release                                
Hit http://sg.archive.ubuntu.com feisty-updates Release                        
Hit http://sg.archive.ubuntu.com feisty/main Packages                          
Hit http://sg.archive.ubuntu.com feisty/restricted Packages                    
Hit http://sg.archive.ubuntu.com feisty/main Sources                           
Hit http://sg.archive.ubuntu.com feisty/restricted Sources                     
Hit http://sg.archive.ubuntu.com feisty/universe Packages                      
Hit http://sg.archive.ubuntu.com feisty/universe Sources                       
Hit http://sg.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://sg.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://sg.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://sg.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Sources             
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_SG        
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_SG
Get:4 http://ubuntu.beryl-project.org feisty Release.gpg [191B]      
Get:5 http://medibuntu.sos-sts.com feisty Release.gpg [189B]         
Ign http://security.ubuntu.com feisty-security/universe Translation-en_SG    
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_SG
Hit http://security.ubuntu.com feisty-security Release               
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_SG    
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_SG
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://ubuntu.beryl-project.org feisty Release
Err http://ubuntu.beryl-project.org feisty Release                 
  
Hit http://security.ubuntu.com feisty-security/restricted Packages 
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Get:6 http://ubuntu.beryl-project.org feisty Release [2965B]         
Ign http://ubuntu.beryl-project.org feisty Release                   
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_SG   
Hit http://medibuntu.sos-sts.com feisty Release
Hit http://ubuntu.beryl-project.org feisty/main Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources                       
Fetched 3728B in 6s (599B/s)                                                   
Reading package lists... Done
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems

```

How can I fix this ?? :KS

---

### Post by divague on 2007-06-20
run this in a terminal

$wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
$sudo apt-get update

that should fix it

---

### Post by edwin.e.johnson on 2007-06-20
hey i have the ATI xpress 200m running and it works perfect i wrote a little post about how to and that is in it

[http://ubuntuforums.org/showthread.php?t=479524](http://ubuntuforums.org/showthread.php?t=479524)


it worked on my system and if you seen that youtube beryl video this card will handle all the same effects my system is running them now.. have fun

---

### Post by paladin_knight on 2007-06-21
> **meindian523 said:**
> It works,it works!:D

Don't try the Desktop effects,I tried too,my box hanged and I had to put it off from the plug point.......

A very good guide to Beryl on Ubuntu is here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29")

I did the restricted drivers method since I had already installed the fglrx driver from ATi....ahead it's your choice whether to go for the open-source method........

I tried method no 1. It works but in very poor performance. The cube movement was not working smoothly. So , I disabled the beryl. And if I run 
```
glxinfo | grep rendering

```
It says ```

direct rendering : no

```

Is my ATI already installed? I could change my screen resolution however. Please tell me.

---

### Post by meindian523 on 2007-06-21
I actually did a hybrid type of install...If i remember right,in this forum,there's a sticky thread which gives a link to a official(kind-of) Ubuntu how-to to install beryl....there we are supposed to check whether direct rendering is enabled......
the command was:
$glxinfo|grep direct

We were supposed to proceed only if direct rendering=yes

---

### Post by meindian523 on 2007-06-21
[https://help.ubuntu.com/community/BerylOnFeisty]("https://help.ubuntu.com/community/BerylOnFeisty")
...that's the link

---

