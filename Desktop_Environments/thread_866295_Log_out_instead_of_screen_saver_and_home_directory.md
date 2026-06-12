---
title: "Log out instead of screen saver and home directory restore upon login"
date: 2008-07-21
forum: Desktop Environments
---

### Post by mikerobinson on 2008-07-21
I am the general manager of a hotel and I am installing kubuntu on our four guest computer terminals. I have them set up with 3 users, one with sudo access, the other two being regular users with no privelages, but one is in English and the other in Spanish. I want the user to be logged off instead of having the screen saver activated so that the next person can choose their language. Is this possible?

Also, I want to get a script that will delete the user's home directory upon login and then copy a backup home directory to the original location (it's only ~35 megs, so it will only take a few seconds). Is this recommended? A friend of mine suggested instead that the "machine to be loaded onto a ramdisk every time someone logs in". Is this something feasable? Would it be hard to set up and would it affect system performance?

Thanks for any help.

---

### Post by smartboyathome on 2008-07-21
> **mikerobinson said:**
> I am the general manager of a hotel and I am installing kubuntu on our four guest computer terminals. I have them set up with 3 users, one with sudo access, the other two being regular users with no privelages, but one is in English and the other in Spanish. I want the user to be logged off instead of having the screen saver activated so that the next person can choose their language. Is this possible?

Also, I want to get a script that will delete the user's home directory upon login and then copy a backup home directory to the original location (it's only ~35 megs, so it will only take a few seconds). Is this recommended? A friend of mine suggested instead that the "machine to be loaded onto a ramdisk every time someone logs in". Is this something feasable? Would it be hard to set up and would it affect system performance?

Thanks for any help.

For your first question: can they press "log out"? if so, then theres the solution to your first question.


For your second question: Here is a sample script I quickly wrote up to do what you are asking:
```
#!/bin/sh

rm -r /home/**name**
cp /home/**name**-backup /home/**name**
```

Replace name with the name of your account's username and store the original as the same name with a -backup at the end of it.


About your third and fourth questions: Something like that would be feasable, but would wreck havoc on system performance. Its basically like loading a livecd but the seek times would be faster since you are running off a hard drive instead of a cd.

---

### Post by mikerobinson on 2008-07-22
Thanks for the help. The user can use the Log Out button, however I was hoping for something a bit more automatic. If I were to guess, I could create a link to whatever the logout command is in /usr/share/applnk/System/ScreenSavers/ and then just select that one from the screensaver selection screen. I'm not sure about this one though and people could easily change it.

Also, thanks for the script that you have below, even if it is simple. However, one thing I'm not sure about is where exactly where to put it. If I just create an .xinitrc script, I'm just a bit concerned about the startup sequence. Does the script execute before other user settings are loaded? If so, it would basically defeat most of the purpose of doing this unless I can find somewhere else to put it. I was thinking in my startkde script might be a better place, but I'm not entirely sure. I would also need the current user as well so that I could do something like: ```
cp -r /home/{$username}-bak/ /home/$username
``` Can I get this from whoami and set it as a variable like ```
$username = whoami # ??
``` Sorry my shell script knowledge is pretty limited, I mainly program in PHP.

---

