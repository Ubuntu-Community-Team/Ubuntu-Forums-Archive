---
title: "How I fixed Ypops and message-notification for Evolution"
date: 2009-02-17
forum: General Help
---

### Post by ronaldrand on 2009-02-17
Hello, I'm on Intrepid, a two week-old installation or so, and I spent most of the day trying to fix bugs in Ypops and message-notification that are available in the Synaptic package manager. So I decided to post here for other users like myself what I did to go about fixing them.

First of all, Ypops.

It didn't start on reboot. I found out there was no bash file in /etc/rc2.d and my Ubuntu says it is on runlevel 2, so it wouldn't run on reboot (I think.) So I copied /etc/rc3.d/S99ypops over to /etc/rc2.d. I believe you have to be root to do this, or use sudo. It started running on reboot after that.

I also had to change my Yahoo settings from Classic mode to "Upgrade to the all-new Yahoo Mail" or I would get crazy errors from Evolution.

Ypops kept crashing intermittently (like every 2-3 minutes.) When I tried to restart it, it would always say "ypops not running". I had to change /etc/ypops.ini to QuiteMode=0. That was the final fix that made this work. (So far so good.)


Now for message-notification.

message-notification crashed Evolution every time I tried to configure it and then it gave an error "unhandled evolution mailbox". I fixed this bug by reinstalling mail-notification and mail-notification-evolution from here:
[http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/]("http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/")

(Thanks to this post for that fix: [http://ubuntuforums.org/showthread.php?t=973303]("http://ubuntuforums.org/showthread.php?t=973303")

However, every time I would close evolution, that error message would come back and the message-notification would blink at me in the system tray. I fixed this by running Evolution in the tray using alltray.

sudo apt-get install alltray

Then I made a bash file called evolution.sh:

#!/bin/sh
alltray -na evolution

Then I put that file in the System->Preferences->Sessions.

Now everything is running like a charm. (Crossing my fingers.)

I hope this helps someone who has the same trouble I had. I'm fairly new to Ubuntu. Good day.

---

### Post by edyeeh on 2009-02-20
> **ronaldrand said:**
> Hello, I'm on Intrepid, a two week-old installation or so, and I spent most of the day trying to fix bugs in Ypops and message-notification that are available in the Synaptic package manager. So I decided to post here for other users like myself what I did to go about fixing them.

First of all, Ypops.

It didn't start on reboot. I found out there was no bash file in /etc/rc2.d and my Ubuntu says it is on runlevel 2, so it wouldn't run on reboot (I think.) So I copied /etc/rc3.d/S99ypops over to /etc/rc2.d. I believe you have to be root to do this, or use sudo. It started running on reboot after that.

I also had to change my Yahoo settings from Classic mode to "Upgrade to the all-new Yahoo Mail" or I would get crazy errors from Evolution.

Ypops kept crashing intermittently (like every 2-3 minutes.) When I tried to restart it, it would always say "ypops not running". I had to change /etc/ypops.ini to QuiteMode=0. That was the final fix that made this work. (So far so good.)


Now for message-notification.

message-notification crashed Evolution every time I tried to configure it and then it gave an error "unhandled evolution mailbox". I'm not exactly sure how I fixed this, but I reinstalled it at one point. However, every time I would close evolution, that error message would come back and the message-notification would blink at me in the system tray. I fixed this by running Evolution in the tray using alltray.

sudo apt-get install alltray

Then I made a bash file called evolution.sh:

#!/bin/sh
alltray -na evolution

Then I put that file in the System->Preferences->Sessions.

Now everything is running like a charm. (Crossing my fingers.)

I hope this helps someone who has the same trouble I had. I'm fairly new to Ubuntu. Good day.


Thanks for the help. Haven't tried it but hopefully it works for me. I've been also looking for solution for the consistent problems i've been having with ypops almost giving up on it. Appreciate the kind gesture of posting it.

---

### Post by ronaldrand on 2009-02-20
No problem! It's now worked flawlessly for three days!!

Edit: I guess there was a flaw. With Evolution in Alltray and Fusion effects turned on, you can't drag and drop e-mail into folders. You have to right-click the email and click move to folder. The only fix I found for this is to turn effects off. I don't really need them and e-mail efficiency is more important to me so I turned them off.

System->Preferences->Appearance->Visual Effects tab->None.

Now I can drag and drop email into folders. This is a bug. In what? I don't know. Maybe Alltray, maybe evolution, who knows. Hope this helps someone.

---

