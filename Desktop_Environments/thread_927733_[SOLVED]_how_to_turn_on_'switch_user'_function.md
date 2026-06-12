---
title: "[SOLVED] how to turn on 'switch user' function?"
date: 2008-09-23
forum: Desktop Environments
---

### Post by robgr85 on 2008-09-23
Hi!

I was working on ubuntu feisty, everything was ok (I could switch users as I wanted), but now, after upgrade to hardy heron I can not do that. After locking screen there is no longer "switch user..." option available. How to turn it on?

Cheers,
Robert

---

### Post by robgr85 on 2008-09-26
No chance to turn it on?

---

### Post by lswb on 2008-09-26
Start up the configuration editor: Main menu/Applications/System Tools/Configuration Editor. 

(If it is not on the menu, add it back with the menu editor, or start it from a terminal by typing "gconf-editor")

Now use Edit/Find from the Config Editor menu; type in the phrase "lockdown"
In the bottom list box there will be 1 or more entries, click on "/desktop/gnome/lockdown"
Then uncheck "disable_user_switching" in the Name/Value box at the top right.
You may have to logout and login to the gnome desktop before the setting takes effect.

---

### Post by robgr85 on 2008-09-27
> **lswb said:**
> 
Then uncheck "disable_user_switching" in the Name/Value box at the top right.
You may have to logout and login to the gnome desktop before the setting takes effect.


The problem is, that it is unchecked and user switching does not work :(

---

### Post by lswb on 2008-09-27
Okay, I think I found the correct key this time.

Using the config editor again, search for "gnome-screensaver" then try the key with the name "user_switch_enabled"

---

### Post by robgr85 on 2008-09-27
"pattern not found" :( brr :( 

...but I probably solved it myself :D :D (it will be clear after the system restart and I will write about it tomorrow). I've installed pessulus, and there was an option 'Allow user switching', I've checked that box, and hope that the results will be visible after rebot.

Cheers.

---

### Post by Xiong Chiamiov on 2008-09-27
> **robgr85 said:**
> Hi!

I was working on ubuntu feisty, everything was ok (I could switch users as I wanted), but now, after upgrade to hardy heron I can not do that. After locking screen there is no longer "switch user..." option available. How to turn it on?

Cheers,
Robert
Although I don't have multiple users on my computer, I've always used K -> Sessions -> Lock and start new session (or something similar).  That will bring you to the login screen again.

---

### Post by robgr85 on 2008-09-27
> **Xiong Chiamiov said:**
> Although I don't have multiple users on my computer, I've always used K -> Sessions -> Lock and start new session (or something similar).  That will bring you to the login screen again.

the problem is, that there is no that option (even after reboot) grr... why I decided to upgrade to hardy heron :/?

---

### Post by Xiong Chiamiov on 2008-09-28
Hmm, I remember having something like that when I had to start X manually (with startx).  Do you have anything funky going on like that?

---

### Post by robgr85 on 2008-09-28
> **Xiong Chiamiov said:**
> Hmm, I remember having something like that when I had to start X manually (with startx).  Do you have anything funky going on like that?

no, my system starts automaticly without any console commands from me. Any Ideas? Is it only my system's problem, or every user of Ubuntu Hardy Heron has "switch user" option disabled?

Cheers,

edit: I solved that problem, removing xserver-xgl package solved that problem
:)

---

