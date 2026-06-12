---
title: "Mudmagic Mud client MSD sound help needed."
date: 2006-04-15
forum: Gaming &amp; Leisure
---

### Post by Omnios on 2006-04-15
Hi I found a fully fuction mud client called Mudmagic which has MSD sound protocall and commpression protacalls. It features are. 

```

Interface
        1. ANSI color
        2. Input
           a. Multi-line input
           b. string argument seperator
           c. command history
           d. auto completion
           e. keep sent text
        3. Multi-Game Tabs
           a. Tab moving
           b. Tab detachment
           c. Tab alert on change
           d. Tab reconnection, disconnect, close
        4. Game Wizard List
        5. Logging
        6. Themes

II. Protocols
        1 MSP (sound protocol)
        2 MCCP v1/v2 (compression protocol)
        3 ZMP (Zenith Mud Protocol)
        4 MXP (Mud Xtension Protocol)

III. Alias, Triggers, Macros
        1. Alias
        2. Triggers
        3. Macros


IV. Modules
        1. Database Module
        2. Notes Module
        3. Recorder Module
        4. Automapper Module

V. Scripting
        1. MudMagic BASIC
        2. Python

```

 A deb is downloadable at. [http://www.mudmagic.com/mud-client/linux_download.php]("http://www.mudmagic.com/mud-client/linux_download.php")

 Anyways this is a quote from the help file which is not very helpfull. 

```
1. MSP (mud sound protocol)
---------------------------
This protocol allow different sounds effect or music to be played in certain situations. The protocol must be also 
supported by server. 

To activate MSP for a session enable:
Settings -> Global Settings -> Sounds

In case the file specified it's not available on local disk, and a URL is specified by mud server ( this is 
transparent for user ) the file may be downloaded. This can have a significant impact on MUD playing performance. To 
activate download enable: 
Settings-> Global Settings -> Sounds -> (click) Allow Download

The command should be in $PATH or a full filename must be specified.

Example:
.wav 
play %s -v %d
.mid
/usr/local/bin/playmidi -V %d %s

Notes:
	- %s will be replaced by mud client with filename
	- %d will be replaced by mud client with volume 


```

 Anyways I downloaded the Materimagica sound files both the mp3 and the wave files and tryed to set up the sound path.
[CODE][/home/MyName/play %s -V %d/CODE]
Play is the file name I am pointing to. I also tryed adding play on to the end of it in case it was a command and still nota. It also has the ability to download sounds and it has downloaded and played a few sounds.

 Any help sould be apreciated.

---

