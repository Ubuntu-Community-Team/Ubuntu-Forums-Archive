---
title: "Change logout options?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Pjotr123 on 2006-09-22
When I press the red button on the right top corner of the screen, in order to shut the computer down, I am presented with no less than six options. I would like to have fewer options presented to me. 

How can I do that in Ubuntu Dapper Drake? I already know how to do it in Xubuntu, under Xfce, but I can't find the Gnome way.

Greeting, Pjotr.

---

### Post by leoquantus on 2006-09-22
lol pjotr ga schaken!!!!!!!!!1

---

### Post by Rui Pais on 2006-09-22
Hi,
you can at least disable Suspend and hibernate buttons, if those are the ones you not want/use:

check 2nd post of [this thread]("http://ubuntuforums.org/showthread.php?p=1476027#post1476027").

About ways to disable the other buttons i don't know... but if you want to be a little more radical and disable all, you can choose that option on Gnome Sessions under System->Preferences->Sessions, uncheck 'Ask on Logout'.

hope that helps.

---

### Post by Pjotr123 on 2006-09-23
Thanks, that is at least somewhat less.

Greeting, Pjotr.

---

### Post by leoquantus on 2006-09-23
kramnik tegen topalov...........

---

### Post by leoquantus on 2006-09-23
ben voor kramnik

---

### Post by louferd on 2006-09-29
Is there a way to actually disable the reboot and shutdown options, though?  

I have a lab I'm converting to Dapper, and the bonehead users don't bother reading the choices before clicking whatever is in the lower right of the dialog.  Unfortunately, that's the shutdown button, and so the one machine with the finicky power-on button requires me to make a trip to the lab to turn it on every time one of these morons clicks without reading.  I don't mind people having the capability, but there's no reason for it to be on the logout dialog.  The only things that belong on that are (in my opinion) "Logout" and the cancel button.

---

### Post by Rui Pais on 2006-09-29
> **louferd said:**
> Is there a way to actually disable the reboot and shutdown options, though?  

I have a lab I'm converting to Dapper, and the bonehead users don't bother reading the choices before clicking whatever is in the lower right of the dialog.  Unfortunately, that's the shutdown button, and so the one machine with the finicky power-on button requires me to make a trip to the lab to turn it on every time one of these morons clicks without reading.  I don't mind people having the capability, but there's no reason for it to be on the logout dialog.  The only things that belong on that are (in my opinion) "Logout" and the cancel button.

well if you only want them to logout (which is in fact the logical, obvious option the case) you can simply delete the option of show the logout splash. 
Your users only press the logout icon on menu or panel and they session simply close. 
It's easier for them (they wouldn't need to press yet another button on a 1-only button splash window) and certainly would make your life easier.

Check 'Sessions' on menu System->Preferences, 1st tab, unable 'Ask on logout'. 
Ensure first that the last session didn't finish with a Reboot or that will became the default for logout ;)

---

