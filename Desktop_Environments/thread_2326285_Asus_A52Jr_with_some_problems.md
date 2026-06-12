---
title: "Asus A52Jr with some problems"
date: 2016-05-30
forum: Desktop Environments
---

### Post by sed_faster on 2016-05-30
Hello everyone,

I have this laptop: [https://www.asus.com/Notebooks/A52Jr/specifications/](https://www.asus.com/Notebooks/A52Jr/specifications/) with this CPU: Intel®  Core&#8482; i3  330M/350M/370M  Processor and 4GBram. I am using the Ubuntu Mate 14.04 LTS and I have a bad performance with this system and machine. For example:


[LIST=1]
[*]the Firefox it is slowly when need opened the new tabs; 
[*]the Caja (File manager) sometimes crashed when I browsed inside the folders on the usb or the nfs folders; 
[*]Another thing with **** me off is when I put the window (e.g. window broswer, program, or window pluma editor) on second monitor and when I clicked in the main screen the window jumped the main screen! I need put again the window on the second screen; 
[/LIST]

**Note:** I have plug on this laptop two screen. One of them is 22" and another is 17". Since there isn't drive to this GPU (ATI Mobility Radeon HD 5470 Graphics 1GB) I can't turn on all monitor (22" + 17" + 15.6"(main screen laptop)).

How can I fix all this problem?

**Note:** Sorry about my english, If you wouldn't understand anything please tell me which I will try explain you, thanks

---

### Post by sed_faster on 2016-06-02
Hello everyone,

Anyone can help me?
I decided try the Lubuntu 16.04 LTS, and the pc was very slowly :( It wasn't supposed! For example, the firefox it is a high delay when write or open new tab, almost 25 minutes after turn on pc he crashed and I need reboot all system, when I slided the window he left an drag! 
I think the problem it is on the drive the GPU or CPU, but how can I resolve this?

Please help me, because this pc it is the only I have and I need this machine to work...thanks and sorry for my level English. I hope you can understand!

---

### Post by sed_faster on 2016-06-03
Hello,

I decide the plus more information about this topic, because however I search and  found more things.
Hello everyone!

As had been said I think which suspicious that it might be something related with the GPU or CPU, therefore I went google. I found this script:

#!/bin/bash
cd /usr/local/bin && wget -Nc smxi.org/sgfxi && chmod +x sgfxi && sgfxi

On this site: [https://forum.owncloud.org/viewtopic.php?t=7118](https://forum.owncloud.org/viewtopic.php?t=7118)

I ran this script and made sudo apt-get update and upgrade it seems to be all right. Also installed the ARandR and set my two screens, one be Asus 24" via HDMI and second is Dell 17" via VGA. The laptop has a screen 15.6" but I can't turn on because the GPU don't support all screens.
The output this script is:

> 
user@user:~/Documents$ sudo ./video.sh 
[sudo] password for user: 
--2016-06-03 10:21:45--  [http://smxi.org/sgfxi](http://smxi.org/sgfxi)
Resolving smxi.org (smxi.org)... 209.197.72.47
Connecting to smxi.org (smxi.org)|209.197.72.47|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://smxi.org/sg/sgfxi](http://smxi.org/sg/sgfxi) [following]
--2016-06-03 10:21:45--  [http://smxi.org/sg/sgfxi](http://smxi.org/sg/sgfxi)
Reusing existing connection to smxi.org:80.
HTTP request sent, awaiting response... 304 Not Modified
File &#8216;sgfxi&#8217; not modified on server. Omitting download.

ERROR: (211) You cannot start sgfxi with sudo. Please start sgfxi 
properly as root (use either 'sudo su -' (note the '-' at the end) 
to become root, or login as root directly). If 'sudo su -' does not 
work, please let the sgfxi maintainer know, and if your system 
has root locked (why would anyone do that?) then you will have to 
unlock root. 

See your distro manuals or help pages to fix this issue in that 
case, and also make sure to update any documentation or how-to's 
for running sgfxi with your distro. This means you, Ubuntu/Mint users!

Typical signs of sudo failures are respawnings of your desktop while 
sgfxi is running, or failures to create directories.

Exiting script now.



After I set all option on ARandR the screens sounds nice but when I restart or turn off and turn on the option which I chose disappear and I have config all set again. How can I freeze this sets and use them all time I turned on the pc? And How can I put the Panel on the Asus 22" screen? Although I choose the option Primary for the Asus 22" screen the panel remains on the 17" screen.

I can see and edit the /home/user/.screenlayout but how can I use this script(file) to setup my set at the time turn on the pc?

Thanks and sorry about my English, if you can understand please tell me which I will try do better.

---

