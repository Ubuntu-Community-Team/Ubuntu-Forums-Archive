---
title: "Oops! I deleted my top panel and now I'm lost"
date: 2010-06-01
forum: Desktop Environments
---

### Post by KingArthur72076 on 2010-06-01
Well I was trying out new stuff and now I remove the top panel. I only been working with Ubuntu for two days so I'm at a lost trying to get around without it. How do I put it back the way it was?

---

### Post by xpluto on 2010-06-01
Have you tried (1) running "killall gnome-panel" to restart the panel,  (2) ending and restarting your gnome session, and (3) rebooting your  computer?

---

### Post by cj.surrusco on 2010-06-01
Check out this thread.
[HTML]http://ubuntuforums.org/showthread.php?t=141038[/HTML]
Follow the instructions on how to reset the gnome panel to default.

---

### Post by KingArthur72076 on 2010-06-01
> **xpluto said:**
> Have you tried (1) running "killall gnome-panel" to restart the panel,  (2) ending and restarting your gnome session, and (3) rebooting your  computer?


I just restarted the computer...still nothing. I don't know how to "killall gnome panel". If I need the terminal to do it, how do I make it come up without the panel?

---

### Post by xpluto on 2010-06-01
press  Alt+F2    and type "gnome-terminal"
then insert the command's in terminal

---

### Post by cj.surrusco on 2010-06-01
> **KingArthur72076 said:**
> I just restarted the computer...still nothing. I don't know how to "killall gnome panel". If I need the terminal to do it, how do I make it come up without the panel?

"You might have a scrambled gconf directory.
I have gone to /tmp, removed the gconfd-<username> directory, removed the .gconf* directories under the home directory and then re-logged in.

I was operating on the theory that I was hosed either way. What I got was a vanilla-default login with stock panel contents, but I could then re-customize them."

You did this and it still is the same?

---

### Post by cj.surrusco on 2010-06-01
Also, while you're at the terminal try completely removing gnome-panel and reinstalling.

```
sudo apt-get purge gnome-panel;sudo apt-get install gnome-panel
```

---

### Post by ajgreeny on 2010-06-01
I think you should have renamed **/home/username/.gconf/apps/panel** as a backup and logged out and in again.

That should give you the default two panels again and allow you to customise them as you wish.

---

### Post by KegRaider on 2010-06-04
Thanks ajgreeny,

This worked great for me!  Of course, the rename command I used was..

$ [B]cd /home/username/.gconf/apps/panel 
[/B]$** mv**[B] panel backup.panel

[/B]I had most of my panel recreated, but just looked bad.  Now it's back to defaults and I'm happy again now. Yay

KegRaider.

---

### Post by drpjkurian on 2010-06-04
Hi
please mark the thread as solved

---

### Post by KingArthur72076 on 2010-06-04
will do...thanks everyone for the help.

---

