---
title: "Not so automatic updates"
date: 2006-09-18
forum: Desktop Environments
---

### Post by lwr on 2006-09-18
I noticed that my little update notification symbol hadn't popped up in the top right in GNOME (I want to call it the system tray, but it's probably got a less Windows-like name) for a while. So I went to System>Administation>Update Manager, and there's loads of updates waiting for me. Can anybody tell me why the update notifier icon hasn't been telling me these things, and how to I get it back? Thanks for your help.

Luke

---

### Post by lwr on 2006-09-23
I've still got the same problem. I've tried adding more notification areas to the gnome panel, and I know there are updates waiting, but I still can't see the update icon. Any ideas? Thanks.

---

### Post by dentaku65 on 2006-09-23
...right click on the bar, choose "add to panel", then under Utilities choose "Notification area" and then click on the Add button...

---

### Post by lwr on 2006-09-23
Thanks for that. I've added about 3 I think, but still no update notification. I tried logging out then logging back in again, but that didn't help. Any other ideas?

---

### Post by peabody on 2006-09-23
I know this is a windowsy thing to suggest, but have you rebooted lately?

---

### Post by lwr on 2006-09-30
Thanks for your suggestion peabody. I've done quite a few reboots recently, but it doesn't seem to have effected my problem. Does anybody else have any suggestions?

---

### Post by Topper_H on 2006-10-01
This bug happens to me since I upgraded from Dapper-beta to Dapper LTS, there are plenty of people mentionning it but I never found a proper answer (yes I have a notification area, yes I reinstalled the package, yes I rebooted plenty of times, no luck) :(
I filed a bug on malone a few months ago but for some reason they seem to be sweeped off...

I just hope Edgy is going to fix this.

---

### Post by brucewagner on 2008-01-09
Ok, I'm a total newbie.... But...

I ran across this the other day, on my laptop...

Under System-->Administration-->Software Sources-->Updates tab....

I found that, on my laptop, "Automatic Updates" was NOT checked....

When I checked it, I was immediately notified of tons of new updates, and they came in...

~~~~

Now, as a side note...

(1)  Under Ubuntu updates, I know I want the first two (security updates, and recommended updates), but what about the 3rd and 4th one?   Do I want Pre-released Updates and Unsupported Updates?   They don't sound good... eh?

(2)  Also, is it only Ubuntu system files that are updated, or are all third-party apps updated as well?  For example, is my accounting software, GNUCash, automatically updated too?

---

### Post by laney on 2008-01-09
> **brucewagner said:**
> 

Now, as a side note...

(1)  Under Ubuntu updates, I know I want the first two (security updates, and recommended updates), but what about the 3rd and 4th one?   Do I want Pre-released Updates and Unsupported Updates?   They don't sound good... eh??

gutsy-proposed (pre-release): The testing area for releases proposed for -updates. If deemed good enough, packages will eventually progress from -proposed to -updates. You probably want to leave this off as the packages released here may be unstable.

gutsy-backports (unsupported): Software which is updated in the development version (Hardy) can be re-packaged and released to Gutsy users through gutsy-backports.

More info [here]("https://help.ubuntu.com/community/UbuntuBackports").

> **brucewagner said:**
> (2)  Also, is it only Ubuntu system files that are updated, or are all third-party apps updated as well?  For example, is my accounting software, GNUCash, automatically updated too

Updates for any installed package (where "installed" means installed via apt-get or synaptic) in any repository you have enabled will appear here.

---

### Post by brucewagner on 2008-01-09
Thanks, laney!

---

