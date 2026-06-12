---
title: "What are these random daemons / processes?"
date: 2009-01-22
forum: General Help
---

### Post by grndslm on 2009-01-22
I'm trying to trim down an Ubuntu 8.04 install.. and I'd like to know understand these processes / daemons are actually doing and if I need them.

In System | Prefs | Sessions, what the heck is "User folders update"... the command xdg-user-dirs-gtk-update gives me no info.

In System | Admin | Services, do I really need anacron, atd, powernowd, acpid, apmd??  apmd is deprecated, right?  acpid is only necessary for laptops, or do desktops need it also?  Do desktops need powernowd?  I won't be adding anything to anacron or atd, so are they really starting necessary services??

And I'm prety sure I'll need klogd & sysklogd, but what's the difference between them... what're they doing?

Thanks in advance!

---

### Post by cariboo on 2009-01-22
What are you trying to accomplish?

Jim

---

### Post by grndslm on 2009-01-22
A barebones Ubuntu install that will work on all computers so that I can use remastersys to distribute to friends/family.  I don't need the power manager and network manager on my desktop, but I'm going to be keeping those for laptops.  I'm removing the bluetooth daemon because it can be activated later if needed.

---

### Post by grndslm on 2009-01-22
AHEM... bump

---

### Post by snova on 2009-01-22
> **grndslm said:**
> In System | Admin | Services, do I really need anacron, atd, powernowd, acpid, apmd??  apmd is deprecated, right?  acpid is only necessary for laptops, or do desktops need it also?  Do desktops need powernowd?  I won't be adding anything to anacron or atd, so are they really starting necessary services??

anacron might be safe to disable. Check /etc/anacrontab for any daemons that look important first.

atd is another daemon for automated command execution that might be safe to disable. I'm not sure how to check it, though.

powernowd: "powernowd (1)        - control the speed and voltage of cpus"

acpid - I suggest leaving this one...

apmd - Yeah, it is, but that doesn't mean it's not being used...

acpid is used anywhere you can suspend/hibernate (I'd guess).

> And I'm prety sure I'll need klogd & sysklogd, but what's the difference between them... what're they doing?

klogd is the kernel log daemon, syslogd is for the system log. I'm not really sure what specifically goes to the latter... but it does get used.

But... why? These daemons hardly use *any* memory (atd, for example, is way down at the bottom of the list), and depending on the program itself, they might not be using *any* CPU time at all. There's really no reason to disable them.

---

### Post by grndslm on 2009-01-22
> **snova said:**
> But... why? These daemons hardly use *any* memory... There's really no reason to disable them.
Well, I simply doing want anything running ever if it's not necessary.  I don't need bluetooth and don't know anybody that uses it.  I don't need apport running.  I don't need Visual Assistance, Evolution Alarm Notifer, the new hardware driver checker, etc.  And I also don't want the Update Notifier running.  I'll be happy with updating packages when I have a problem.

Anacron is half full o' crap I'll never use, like exim.  I thought Ubuntu used Postfix anyway?  Perhaps some package I've installed auto-installed exim?

I guess from that list, I'm only gonna disable apmd.

Lastly, what is the "User folders update" thing showing in the Gnome Session app?

---

### Post by grndslm on 2009-01-22
Alright, well... I kinda figured out what it does, but not really.  I don't understand why I can't just place some empty folders like Documents/ Music/ Pictures/ & Videos/ in /etc/skel/ and have them be automatically created for every new user.  No need for another program to do that ever.  Am I wrong?

---

### Post by grndslm on 2009-01-26
OK... so I upgraded to Intrepid, and now there's a few more processes /daemons I'm not exactly positive what I should do with them...

Has anybody disabled these and not had a problem??

- GNOME Keyring Daemon Wrapper - nm-appplet uses this for wireless networks, and nothing else, right?
- GNOME Settings Daemon - is this gconfd?
- GNOME Settings Daemon Helper - can i live without it?
- Window Manager - will metacity really not start?

---

### Post by chrisccoulson on 2009-01-26
> **grndslm said:**
> OK... so I upgraded to Intrepid, and now there's a few more processes /daemons I'm not exactly positive what I should do with them...

Has anybody disabled these and not had a problem??

- GNOME Keyring Daemon Wrapper - nm-appplet uses this for wireless networks, and nothing else, right?
- GNOME Settings Daemon - is this gconfd?
- GNOME Settings Daemon Helper - can i live without it?
- Window Manager - will metacity really not start?

GNOME Keyring Daemon - I'm not sure what will happen if you disable this.

GNOME Settings Daemon - no, it's not gconfd. You will find that all sorts of wierd stuff will happen if you disable this, such as theming will not work. You need this.

GNOME Settings Daemon - see above

Window Manager - it is actually a bug that this is shown in the Session Properties Dialog and is fixed in Jaunty. The effect of disabling it will depend on the contents of gconf key "/desktop/sessions/required_components/windowmanager", but you'll probably end up with no window manager (metacity will not start) on the default install.

User Folders Update - This localizes the default directories (Desktop, Videos, Music, Pictures, Public and Private) when you log in with a different language. You can disable it if you only ever use 1 language, and you'll probably save a couple of micro-seconds each time you log in. So, you might gain a few milliseconds of your life back each year for unchecking it ;)

---

### Post by oldos2er on 2009-01-26
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by grndslm on 2009-01-26
Yes... I ran across that last night before I fell asleep.  Good stuff.

The correct answer is, don't disable those 4, I guess.  I'm assuming that the Keyring Daemon is only needed on laptops (at least for most people), which means it's needed for my purposes.  The other three seem like they should just be mandatory for all users... right?  I'd be pissed if I was retarded and allowed to turn any of the three off thru the GUI and have my window border and/or widgets gone.  Silly gnomes.

---

### Post by grndslm on 2009-01-28
> **chrisccoulson said:**
> GNOME Settings Daemon - no, it's not gconfd. You will find that all sorts of wierd stuff will happen if you disable this, such as theming will not work. You need this.

GNOME Settings Daemon - see above

Window Manager - it is actually a bug that this is shown in the Session Properties Dialog and is fixed in Jaunty. The effect of disabling it will depend on the contents of gconf key "/desktop/sessions/required_components/windowmanager", but you'll probably end up with no window manager (metacity will not start) on the default install.Window Manager definitely shouldn't be available in the Sessions app, and I'm pretty sure that Gnome Settings Daemon & Gnome Settings Daemon Helper shouldn't be available for end-users to disable either.  Are you guys sure that this isn't gconfd & gconf??

---

