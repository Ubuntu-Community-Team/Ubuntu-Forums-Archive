---
title: "Crontab output"
date: 2006-09-12
forum: Desktop Environments
---

### Post by subzero79 on 2006-09-12
I have written this script for backing up my winxp installation. Also i've added this script to crontab to perform this backup periodicly. 

```
#!/bin/bash
umount -v /media/sda1
mount -t xfs -v /dev/sda2 /media/sda2
ntfsclone -s -O /media/sda2/win_xp.img /dev/sda1
umount /media/sda2
umount /media/sda1
mount -a

```

How do i generate an output telling me that the script is running when crontab runs it? Do i have to add commands inside the script or add something to crontab? Maybe popping up the gnome-terminal with the script running but don't know how to that.

thanx

---

### Post by mssever on 2006-09-12
The simple way is simply to include an echo statement. cron mails you the output or a program, so if you have a mail reader (such as mutt or pine) installed, you'll get it. Evolution can probably handle local mail as well, but I wouldn't know for sure.

If you want a realtime popup, you could experiment with zenity, but zenity would only work if you were logged on. even then, I don't know if cron allows anything interactive to happen during execution. Cron is really designed for set-it-and-forget-it uses.

Probably the best thing would be to simply make sure that it's running properly (by using echo statements or top), and then let it quietly do its thing. Once you know you've configured it properly, then if you look at your computer clock, you'll know whether or not it's running, without it having to tell you.

EDIT: for notifications, change the script. Crontab doesn't support such things.

---

### Post by subzero79 on 2006-09-12
ok thanks. So the mail output can be sent to an external address or has to be only local?

i've manage to get the output popping the gnome -terminal like this

export DISPLAY=:0 && sudo gnome-terminal -x /home/user/scripts/backupxp.sh

for echo to work it must be at the initial start of the script?

---

### Post by mssever on 2006-09-12
> **subzero79 said:**
> ok thanks. So the mail output can be sent to an external address or has to be only local?
Mail is sent to the owner of the crontab. That's your user if it's your crontab, or root of it's root's crontab. /etc/aliases defines who gets whose mail. You can create a file called ~/.forward that contains an email address. All of that user's mail will then be forwarded to the specified address. This is assuming that your system is configured such that it is capable of sending external mail.
> i've manage to get the output popping the gnome -terminal like this

export DISPLAY=:0 && sudo gnome-terminal -x /home/user/scripts/backupxp.shI'd be interested to hear what happens if you're logged out when that job starts... My guess is that it will fail miserably.

> for echo to work it must be at the initial start of the script? 
It can be anywhere in the script. I just thought of someting, though. I believe that cron waits until the process is finished before sending mail. That way, you'll only get one message, instead of potentially many. Of course, this also mens that you won't get real-time notification. You could play around with sendmail, though.

---

### Post by mssever on 2006-09-12
One other comment: you can't use sudo in your crontab scripts, because cron runs non-interactively, and thus can't ask for a password. If your script requires superuser privileges, call it from root's crontab: ```
sudo crontab -eu root
```

---

### Post by subzero79 on 2006-09-12
calling the terminal to the front display works with sudo. I been testing now. that is not an issue because this machine logs in automaticly every time it powers on.
So i've put the script in /usr/sbin folder and cron the job in the root crontab but it doesn't starts. Do i have to be logged as su to start the root crontab?

---

### Post by mssever on 2006-09-12
If it works with sudo or gnome-terminal, then fine. But you need to be aware that you're trying to use cron in a way that wasn't intended and that problems could crop up. One potential problem that comes to mind is if you boot at such a time that cron tries to run your job as soon as it starts. You won't be logged in yet because the machine will still be in the boot process, so the job will probably fail. Admittedly, this might not actually happen, but it could. Since cron is designed to be non-interactive, you'd be better off to make your script non-interactive, IMHO.

If you used the root crontab command I gave you, the script should run as root when scheduled. Check your syntax. You don't need to worry about su because cron runs regardless of whether that user is logged in.

Also, cron doesn't care where your script is located, as long as it can find it and the script is executable--with a proper shebang line at the beginning.

---

