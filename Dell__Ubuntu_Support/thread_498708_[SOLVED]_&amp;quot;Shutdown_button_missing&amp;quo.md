---
title: "[SOLVED] &amp;quot;Shutdown button missing&amp;quot;"
date: 2007-07-11
forum: Dell  Ubuntu Support
---

### Post by Graham_Rostill on 2007-07-11
When I click the "Log off, Switch User, Power down computer, etc" button. Since the updates from 10 July 2007 I haven't had the option of "Shutting down"  I only have "Log off, Switch user, Lock Screen, Hibernate and Suspend"

Is there anything I can do to remove this bug? Any help would be great.

---

### Post by fishpie on 2007-07-12
I have seen this problem when kde's kdm login manager is being used instead of GNOME's gdm. If you are using kdm and want to switch back to gdm use the following command ```
sudo dpkg-reconfigure gdm
```

---

### Post by Graham_Rostill on 2007-07-14
I tried this just in case it had switched to KDE instead of GNOME. But it hasn't made any difference. The button is still missing. Is there an easy way to add/remove it that I have done by mistake... Lets cover all the basics/bases here. lol

Any help welcome, it's beginning to be a pain.

---

### Post by DonA on 2007-07-15
Hello.

I saw this once before on my E1505 laptop running Dell-preloaded Feisty.  I seem to recall that I had Synaptic or Update Manager open at the time.  It was as if the unit didn't want to shutdown in "mid update".  I exited the package manager, and the Shutdown button magically reappeared.  (Of course this might be entirely coincidental.)  If you haven't run Synaptic or Update Manager since the problem began, you might want to start it--and maybe download something that you can later remove--and let it exit normally.  Then maybe the Shutdown button will be back.

Just a thought.  Good luck.     ..DonA

---

### Post by Sambooe on 2007-07-15
This worked for me.....right click on task bar and click on "add to panel"....then click on the "QUIT" aplet.

---

### Post by Graham_Rostill on 2007-07-15
Neither of the two replies worked. I tried adding to pannel, but the results were the same, and as far as starting and shutting down of applet manager goes, all was normal and still the button is missing. Has anyone else experienced this, or am I just some sort of freakish find that can't figure out what's wrong.

Thank you for your help so far I look forward to resolving this issue.

---

### Post by mssever on 2007-07-16
This worked for me: [http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button](http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button)

---

### Post by DonA on 2007-07-16
The suggestion by mssever sounds quite reasonable.  If that doesn't work (which I suspect it may not, since you indicate that you still have all of the other action buttons), I'd still operate under the premise that some file or flag has been set by the OS that is blocking a normal shutdown.  Out of curiosity, I wonder if you were to issue the shutdown command from a terminal, might that clear things?  Have you tried:
[INDENT]
sudo shutdown now
[/INDENT]
or something like that?  It may at least give some indication of what's amiss.

..DonA

---

### Post by NilsE on 2007-07-16
> **Graham_Rostill said:**
> When I click the "Log off, Switch User, Power down computer, etc" button. Since the updates from 10 July 2007 I haven't had the option of "Shutting down"  I only have "Log off, Switch user, Lock Screen, Hibernate and Suspend"

Is there anything I can do to remove this bug? Any help would be great.

System/Administration/Login Window


Make sure "Show Actions Menu"  and "Include Host Name..." is checked.

If the login window option is not there go into Main Menu and select it under system admin apps.

---

### Post by Graham_Rostill on 2007-07-16
The showactions button wasn't checked. All is fine now, thank you all for your help.

---

### Post by josephh on 2007-07-24
> **mssever said:**
> This worked for me: [http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button](http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button)

Thank you.  This was an easy fix to the problem.

---

### Post by ramsuhas on 2008-06-24
I had the same problem.

NilsE's solution worked.

Thank you.

---

