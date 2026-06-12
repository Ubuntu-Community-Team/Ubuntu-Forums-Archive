---
title: "Locked out by the screensaver?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by btilly on 2006-01-25
I've never seen pr heard of anything like this.

I have my screensaver set to automatically lock when I am idle for a certain time.  I come back, type my password, and everything is fine.  I do it all the time.

Until today.

I tried my password, and got denied.  Well I sometimes don't hit shift in the right places, so I thought nothing of it and tried it again.  By the fifth time I was thinking that something was wrong.  I looked for the obvious (caps lock, etc), but couldn't find any reason why it wasn't working.

After a few dozen tries I used Alt-Ctrl-F3 to switch to a login prompt.  Logged in.   Nope, my password wasn't changed on this machine.  Switched back to F7.  It won't accept my password.  Switch login, enter name and password.  It works, tells me that I'm logged in already, asks if I want to go back to the original login.  I decide to, and I'm back and the failed password screen.  I try a few more times.

I switched back to F3, sudoed "killall xscreensaver", and switched back to F7.  I'm in!  I can switch focus between windows.  I can't type into my terminals.  No rescuing anything that I have open.  Grrr...

Ctrl-Alt-Backspace and a login later, and here I am.

My system is Ubuntu 5.10.  Last updated Tuesday last week.  (I'm going to update it now.)  Using only Ubuntu repositories.  I've noticed that it doesn't always accept my password, but until now I thought that was just sloppy typing.

If anyone has ideas for what I can do to keep this from happening again, I'm all ears.  If anyone has advice for how I can bypass the screensaver lock, I'm also all ears.  (Remember, I can get to a command prompt.  I can even get logged in to X.)

Given the fact that I have to unlock the screensaver several times per day, it certainly isn't failing very often.  But when it did fail, it was truly irritating.

Thanks,
Ben

---

### Post by lucascr on 2006-02-02
I solved a problem like your with the following:
> sudo chmod 4755 /usr/bin/kcheckpass

See: [http://www.ubuntuforums.org/showthread.php?t=105071](http://www.ubuntuforums.org/showthread.php?t=105071)
I Hope this help.

Luca

---

### Post by kevinbsmith on 2006-03-21
The same thing was happening to me, but I don't have kcheckpass installed, so the solution above didn't apply. For me, it was unix_chkpwd that was giving the error, showing up in /var/log/auth.log as:

Mar 21 08:23:31 localhost unix_chkpwd[29018]: check pass; user unknown

Eventually I found a thread elsewhere that mentioned /etc/shadow, and for some reason my /etc/shadow was owned by group "voice" instead of group "shadow". I suspect it has something to do with my recent Hoary->Breezy upgrade, as I noticed some other files were now owned by "27" or something like that.

I chgrp'd /etc/shadow and that solved the problem. It would be great if someone could write a little sanity-check tool that would look at all the file owners and groups in /etc and point out any problems or inconsistencies.

---

### Post by r3v3rs3pa on 2006-04-05
[QUOTE=lucascr]I solved a problem like your with the following:

'sudo chmod 4755 /usr/bin/kcheckpass'

I Hope this help.

Luca[/QUOTE]
um, 4755? i'm sure it is 755
sudo chmod 755 /usr/bin/kcheckpass

just in case anyone didn't know...

thanx Lucascr, i appreciate the info, i was locked out myself.

---

### Post by oyvindaa on 2006-04-27
[QUOTE=r3v3rs3pa]um, 4755? i'm sure it is 755
sudo chmod 755 /usr/bin/kcheckpass

just in case anyone didn't know...

thanx Lucascr, i appreciate the info, i was locked out myself.[/QUOTE]

Is it 755? Because the 4755 one didn't work for me. Still get denied.

Will have to try the 755 one then. Thanks.

Edit: sudo chmod 755 /usr/bin/kcheckpass didn't work either!

How do I disable the screensaver password?

---

