---
title: "gmail-notify problems"
date: 2006-09-09
forum: Desktop Environments
---

### Post by villindesign on 2006-09-09
Hello, I mistakenly deleted the gmail notifier on the panel and now I can not find a way to replace it. I tried un-installing and reinstalling gmail notifier, but this did not work. I am not talking about launching the application, b/c it is working (if I get mail, the notification pops up), but there is no icon that changes from red to blue now, so I have to be present when the pop up happens to know. Any ideas?

Thanks, Britt

---

### Post by orb9220 on 2006-09-10
did you put it in startup programs in session manger?

system>prefs>sessions  add  gmail-notify on startup programs tab

---

### Post by villindesign on 2006-09-10
Yes, the program starts up and even notifies me when I have mail, but the the little icon that is red for no mail and blue for mail is not on the panel anylonger...I deleted it. I am trying to learn out to get the icon back.

Thanks, Britt

---

### Post by BlacKat_K on 2006-09-10
> **orb9220 said:**
> did you put it in startup programs in session manger?

system>prefs>sessions  add  gmail-notify on startup programs tab
Side question,how do you add things to the startup list?Just by adding their name or do they need a specific command?

---

### Post by Anonii on 2006-09-10
> **BlacKat_K said:**
> Side question,how do you add things to the startup list?Just by adding their name or do they need a specific command?
You need to know their command. For example to open Amarok in the startup you add "amarok" to open gmail-notify you add "gmail-notify" and to start Mozilla Firefox you add "firefox".

Without quotes, obviously <:
Most times, the command is the name of the program.

---

### Post by villindesign on 2006-09-10
Maybe another way to solve this is to completely remove gmail-notify. I did use Synaptic's "remove completely" tool, but when I reinstalled gmail-notify, it did not ask me for my account information - so somewhere there was still some information stored about my account. I did a search for all files with *gmail* in them and deleted them, but even then when I reinstalled, gmail-notify knew my account information. I think if I could completely remove gmail-notify from my computer, then I could go through the account set-up again. So, does anyone know how to do this?

Thanks, Britt

---

### Post by kostkon on 2006-09-10
I suppose any configuration files or folder for gmail-notify would be in your home folder as hidden.

---

### Post by villindesign on 2006-09-10
I thought so too, but i don't see any... Oh- found it in file .notifer.conf... Ok, I'll delete this, and remove gmail notifier and reinstall. Maybe this will work.

Thanks, Britt

---

### Post by Anonii on 2006-09-10
Synaptic's remove completely is apt-get remove --purge? That should have removed your configuration files, except if you have allready messed up with them.

---

### Post by villindesign on 2006-09-10
Didn't work... I just had to type my username and passwd again. hmm. Well, if anyone else figures this out, please let me know.

Thanks, Britt

---

### Post by villindesign on 2006-09-10
Yeah, the config file does not get purged, and I did not edit the file myself. it is in my home folder as .notify.config ...

---

### Post by BlacKat_K on 2006-09-10
> **Anonii said:**
> You need to know their command. For example to open Amarok in the startup you add "amarok" to open gmail-notify you add "gmail-notify" and to start Mozilla Firefox you add "firefox".

Without quotes, obviously <:
Most times, the command is the name of the program.

Yes that worked and i added Firestarter on the list but when i reboot it tells me i need privilege rights to start it,cause firestarter only starts with my administrator password.Is it possible toremove the password from firestarter?

---

### Post by villindesign on 2006-09-10
I *think* you have to change the chmod of the file. I would navigate to the firestarter command and type $ls -l to see the owner. Then I think you use the chmod command to give yourself permission to execute it.

$chmod u=rwx firestarter

Maybe that will work?

---

### Post by villindesign on 2006-09-10
OH! I figured this riddle out. Right click on the (any) panel and select "[FONT="Courier New"]Add to Panel[/FONT]". Then, in the section labeled "[FONT="Courier New"]Utilities[/FONT]", select "[FONT="Courier New"]Notification Area[/FONT]". That is it. :)

---

### Post by buddah3618 on 2007-08-07
Hi,

I can't say that I'm having the issue you described. However, the issue I'm having with "gmail-notify" is the icon in the panel does turn "Blue" to indicate new mail, but, when I right click & select "Go to Inbox" nothing happens. I'm wondering if the linux pop-up blocker is stopping it. But, that being said - nothing else appears to be affected by that. I have to bookmark the webpage in order to check my Gmail. Any ideas??

Thanks
buddah3618

---

### Post by brickbat on 2007-08-18
have you configured it properly?

---

