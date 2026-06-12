---
title: "Autostarting terminals on Gnome Login with debian OS"
date: 2008-05-06
forum: Desktop Environments
---

### Post by Catchy on 2008-05-06
Hi
Im very new to linux and have a linux project to set up a Open IMS core server. Got the server up and running. And I want to start 4 different terminal-applications when im logging in as a spesific user called for example: imsadmin

There are 4 different programs or shell scripts i have to run to start the server. Filenames: icscf.sh, scscf.sh, fhoss.sh and pcscf.sh. Each of these files require one terminal window which have to be up and running at all times.

So far i have done this: 

I have made a script called scripting.sh and it looks like this:

```

##scripting.sh
#!/bin/bash
sleep 1
gnome-terminal -e ./icscf.sh 
sleep 1
gnome-terminal -e ./scscf.sh 
sleep 1
gnome-terminal -e ./pcscf.sh 
sleep 1
gnome-terminal -e ./fhoss.sh 
```

Each of the icscf.sh, scscf.sh, fhoss.sh and pcscf.sh scripts looks like this:

```
#!/bin/bash
cd /opt/OpenIMSCore/
./scscf.sh

```

Where the "./scsf.sh" is either "./fhoss.sh" or "./icscf.sh" or "pcscf.sh".

(The reason i have made a script which is so short to run another script, is because if i run one of the scripts directly which is in the folder /opt/OpenIMSCore/. That part of the server will not function correctly for some reason. It will either crash or just terminate.)

Then I go to Desktop>Preferences>Sessions>Startup Programs

I add the script: "scripting.sh" and then i go to the folder: /home/imsadmin/.config/autostart/ I then edit the file named
"no name" :

```
[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=/home/imsadmin/Desktop/Doku/scripting.sh
X-GNOME-Autostart-enabled=true
StartupNotify=true
Terminal=true
Hidden=false


```

I then try to relogg to imsadmin but i can only see 4 terminals that starts one by one, but closes immediately. Which I was hoping they wouldnt, I want them to stay visible. 

I have also tried starting all the 4 parts separately, with the Gnome startup file looking like this for the icscf.sh script:


```
[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=/home/imsadmin/Desktop/Doku/icscf.sh
X-GNOME-Autostart-enabled=true
StartupNotify=true
Terminal=true
Hidden=false


```

But the terminal just closes.

So i was hoping someone could help me figure out how to make the autostart to not close the terminals or any other method to make these 4 scripts autostart on login.

Sorry for the long post by the way.

---

