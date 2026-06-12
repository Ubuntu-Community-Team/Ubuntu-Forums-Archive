---
title: "LXDE and KeepassX"
date: 2011-03-04
forum: Desktop Environments
---

### Post by oODeanOo on 2011-03-04
I'm finding an issue with LXDE which I'm wondering if somebody can explain and possibly a fix.

I have an ASUS Eee 1005HA with 1GB of RAM, currently running Lucid Desktop edition, things running generally ok but thought I'd look into LXDE, intial thoughts are it's quick but there is one issue that stops me from using it.

I use KeepassX and when used with LXDE (Lubuntu or Mint LXDE 10) the problem is that when logging off with KeepassX running it never closes the application which leads to the database being left open (.lock file) so at next logon I can only open the database in Read-Only mode unless I delete the .lock file.

Any ideas?

Dean

---

### Post by kellemes on 2011-03-04
> **oODeanOo said:**
> I'm finding an issue with LXDE which I'm wondering if somebody can explain and possibly a fix.

I have an ASUS Eee 1005HA with 1GB of RAM, currently running Lucid Desktop edition, things running generally ok but thought I'd look into LXDE, intial thoughts are it's quick but there is one issue that stops me from using it.

I use KeepassX and when used with LXDE (Lubuntu or Mint LXDE 10) the problem is that when logging off with KeepassX running it never closes the application which leads to the database being left open (.lock file) so at next logon I can only open the database in Read-Only mode unless I delete the .lock file.

Any ideas?

Dean

What version of KeePassX are you using?
Can you start KeePassX from a terminal-window and post the output you see when you close the app?

---

### Post by oODeanOo on 2011-03-04
The KeepassX version would be 0.4.3 from respective Lubuntu or Mint LXDE repositories.   I am currently testing Mint LXDE but both versions have had this issue  both with the common factor obviously beinging  LXDE.

I'm not in front of the machine right now but will paste the output later on today.

Thanks for replying.

Dean

---

### Post by oODeanOo on 2011-03-04
Hi kellemes,

I've done as you've suggested and I see no message from the terminal when logging out or even when closing KeepassX manually.

Shutdown also causes this issue, to me it's like logout and shutdown do not send a signal to open applications to close gracefully but do something like a killall instead as even opening Abiword typing a few words and then logging off just closes Abiword without prompting to save the document.

Dean

---

### Post by kellemes on 2011-03-05
I'm sorry , guess I didn't read well, I've been having the flue last week.. ;-)
I thought you got the lockfile when closing the app. but it's when login off with KeePassX running..

I use KeePassX daily but I simply start and close the app, don't keep it in systray..
In the settingsdialog there is this setting: "Lock Database after inactivity of .. seconds" (in my case it's disabled).. does using this setting prevent the DB from creating a lockfile when you logof? Could be a possible workaround.. Just guessing..
By the way, when you keep your app running using this dbautolocking is more secure anyway.

Maybe you should try posting this question in [KeePassX-forum]("http://www.keepassx.org/forum/").

Good luck.

---

### Post by stinkeye on 2011-03-05
Does it make any difference if you enable/disable **Automatically save database on exit and workspace locking**
in the General(2) section of preferences?

---

### Post by oODeanOo on 2011-03-05
Hi Stinkeye,

Unfortunately not.  As I said previously it looks to be caused by logoff, reboot, shutdown appearing to "kill" applications, so not closing them.  If I compose a Abiword document and logout I am logged out without being prompted to save the document.

Dean

---

