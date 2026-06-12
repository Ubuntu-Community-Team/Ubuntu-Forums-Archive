---
title: "Samba &amp; ufw wierdness"
date: 2010-12-18
forum: Desktop Environments
---

### Post by acag on 2010-12-18
First things first. I am fairly new to the Linux scene and as such have a lot to learn. Please be gentle. Now to the particulars. I am running 10.04 LTS 32 bit. I am attempting to connect to a Windows share on a Synology DS211J NAS unit. When ufw is disabled, I am able to Connect to Server with no problems, When ufw is enabled, I receive the following message:

[COLOR=Red]Cannot display location "smb://myuserid@diskstation/backups/"
Failed to mount Windows share[/COLOR]


   I read the following thread:
[http://ubuntuforums.org/showthread.php?t=806000&highlight=samba+ufw](http://ubuntuforums.org/showthread.php?t=806000&highlight=samba+ufw)

I then proceeded to terminal mode and entered:
[COLOR=Blue]sudo ufw allow from xxx.xxx.x.x/5 to any app Samba   [/COLOR](where xxx.xxx.x.x is my router IP address).

I received the following message:
[COLOR=Red]Warn: Rule changed after normalization
Rule added[/COLOR]

I then entered:
[COLOR=Navy]sudo ufw status[/COLOR]

The response was:
[COLOR=Red]Status: Active[/COLOR]

[COLOR=Red]To                 Action           From
Samba          ALLOW         192.0.0.0/5

[COLOR=Black]The IP address listed is nowhere near the IP address I entered in my ufw allow command. In fact, the only items that matched are the 192 and the /5.

Can someone explain to me what happened? As a newbie, I am very confused by this behavior. The results are consistent, no matter how may times I enter the command. Any assistance in this matter would be greatly appreciated.

By the way, I still can't Connect to Server with ufw enabled.

Thanks!
[/COLOR][/COLOR]

---

