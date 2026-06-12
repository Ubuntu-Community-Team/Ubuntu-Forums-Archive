---
title: "Get root permissions for certain applications? i.e. hddtemp"
date: 2005-10-23
forum: Desktop Environments
---

### Post by idn on 2005-10-23
Is there a way to get permissions so I can run firestarter and hddtemp as a regular user? Or is this a bad practice?

---

### Post by blackpaw on 2005-10-23
oops.. sorry

---

### Post by Jenda on 2005-10-23
Sure. Just fire up a terminal and type "sudo hddtemp" or anything you wish.
If that ain't enough, you can also add a custom launcher to the panel (via right click) and type "sudo hddtemp" as its command. You have to check the "run in terminal" checkbox, because you WILL have to enter your password every time.

---

### Post by Zeroedout on 2005-10-23
[quote=Jenda]Sure. Just fire up a terminal and type "sudo hddtemp" or anything you wish.
If that ain't enough, you can also add a custom launcher to the panel (via right click) and type "sudo hddtemp" as its command. You have to check the "run in terminal" checkbox, because you WILL have to enter your password every time.[/quote] wont that just run the app as root? i thoguht he wanted it run as a regular user. If the sudo thing is what you were looking for though, try gksudo if you don't want to run the app in a terminal and want a password diolouge to pop up.

edit: I'm sorry, just read the subject but in his post he said regular user

---

### Post by Bitmastro on 2005-10-23
you can do that by doing "sudo chmod +s /usr/sbin/firestarter", but I don't think that using suid root is a good move in terms of security

---

### Post by Jenda on 2005-10-23
Yes, indeed. If you make the launcher ```
gksudo firestarter
```, it will give you a pwd prompt even without the terminal.

---

### Post by idn on 2005-10-23
Cool, thanks guys, I just wanted to run it in the background without the password prompt. There is a gdesklet for hddtemp but it wont work because it requires root to run the hddtemp command, and I'm not going to type in my password every 1 minute or whenever the refresh interval is. 

Cheers

---

### Post by poptones on 2005-10-23
What you want are smartmontools. Install it and read the manual; you can tell it to track changes in drive status and email you or just log the changes it detects to var/log/messages. You can tell your gdesklet to check that file for messages about the drive health, or you can be adventurous and write your own. 

But I wouldn't suggest tracking every minute. That's just way overkill. smtools comes setup to default to thirty minute checks. You don't want your drive busy handling temp polls every minute when you're sleeping or trying to watch a movie.

---

