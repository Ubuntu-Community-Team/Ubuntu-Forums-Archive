---
title: "Run script before desktop starts up impossible"
date: 2011-05-21
forum: Desktop Environments
---

### Post by thohms on 2011-05-21
Hi community,

I have a big issue which I try to find a solution for 3 days now.
I'm running a script inside /etc/gdm/PreSession/Default that syncs my home dir for the current user. The script itself works fine, but I cannot get the desktop to start after the script is finished. No matter what I tried desktop starts although script is still running and right now I'm afraid it might have to do with upstart.

Does anyone have an idea how I can prevent the desktop to be started after my script is finished?

Using Ubuntu 11.04 Natty and Gnome.

Thanks for any help,
Thomas

---

### Post by prshah on 2011-05-21
> **thohms said:**
> 
Does anyone have an idea how I can prevent the desktop to be started after my script is finished?

Have you considered the "wait" command?

Unfortunately I have no experience with these commands and so cannot help beyond this suggestion. Maybe the man pages will help.

---

### Post by Toz on 2011-05-21
> **thohms said:**
> Hi community,

I have a big issue which I try to find a solution for 3 days now.
I'm running a script inside /etc/gdm/PreSession/Default that syncs my home dir for the current user. The script itself works fine, but I cannot get the desktop to start after the script is finished. No matter what I tried desktop starts although script is still running and right now I'm afraid it might have to do with upstart.

Does anyone have an idea how I can prevent the desktop to be started after my script is finished?

Using Ubuntu 11.04 Natty and Gnome.

Thanks for any help,
Thomas

Can you post back the contents of your /etc/gdm/PreSession/Default file and if possible, the sync script itself?

---

### Post by thohms on 2011-05-22
Hi guys,

thanks for your answers. Meanwhile I found a solution that works.
To answer the first question: Yes I've used the wait command, but it seemed to be ignored.
What I did now is: putting the call to my script into PostLogin instead. Now everything works as expected. Before I didn't want to use it as I needed the user's $DISPLAY value for zenity to use, but changed my script by passing the current $DISPLAY value to the script instead of searching for it within the script itself.
It seems that PreSession runs the scripts, but also runs the Session itself at the same time. I'm pretty sure this somehow has to do with the Upstart emits, but can't confirm as I still did not really dive into the Upstart stuff.
Putting scripts into PostLogin waits for the scripts to return an exit state before session is started and so does exactly what I needed.

Thanks again for your fast answers,
Thomas

---

### Post by fatriff on 2011-05-22
I've played around with the WAIT command, I didn't have much luck with it..

Instead I use SLEEP 1.. Which is the lowest setting you can SLEEP for but it works great with everything i've tried so far.

---

### Post by thohms on 2011-05-22
> **fatriff said:**
> I've played around with the WAIT command, I didn't have much luck with it..

Instead I use SLEEP 1.. Which is the lowest setting you can SLEEP for but it works great with everything i've tried so far.

Tried sleep as well, but this also didn't work in PreSession where in PostLogin it did work, but also the wait command.

---

