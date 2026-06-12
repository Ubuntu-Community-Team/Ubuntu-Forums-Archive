---
title: "Home and User folders missing error"
date: 2007-11-24
forum: Desktop Environments
---

### Post by m623d on 2007-11-24
Hi
 I have 7.10 installed (great by the way) I'm a novice Linux user, so please bear with me!
Anyway, I installed the latest Wine app then read it shouldn't be installed as root so tried to uninstall with a term command.
I then had to reboot, but now I get an error saying the Home and User folders dont exist and it fails to start.

Please help

---

### Post by m623d on 2007-11-24
anyone pls? I've had to go back to windows!
cant use Ubuntu at all

---

### Post by m623d on 2007-11-24
can no one offer any advise at all? even stupid ones?
I really need help
pls

---

### Post by kellemes on 2007-11-24
> **m623d said:**
> Hi
 I have 7.10 installed (great by the way) I'm a novice Linux user, so please bear with me!
Anyway, I installed the latest Wine app then read it shouldn't be installed as root so tried to uninstall with a term command.
I then had to reboot, but now I get an error saying the Home and User folders dont exist and it fails to start.

Please help

Can you remember the term-command you issued?

---

### Post by m623d on 2007-11-25
yes, it was this:
sudo rm -rf ~/.wine

---

### Post by schauerlich on 2007-11-25
Are you sure there wasn't a space between "~" and "/.wine"? If so, that would delete your whole home directory, recursively, without asking you.

---

### Post by m623d on 2007-11-25
I dont think so, I just copy and pasted from the wine website, the same as I did just here
From the recovery console I can change to Home directory, but there is nothing in it.
When I try to log on it says it cannot find Home or User folders and asks if I want to bypass (I think) I say yes and it just restarts back to the log on screen

---

### Post by schauerlich on 2007-11-25
Well, one way or another, your home directory got deleted. Your options as far as I see are to use some sort of data recovery utility, or start over.

---

### Post by coolguy2006delhi on 2007-11-25
Its better to make another user account and just delete the old one.

---

### Post by m623d on 2007-11-25
is it not possible to re make the home directory?
dont really want to re install again, took me ages to get the desktop effects to work.
I dont mind losing my user cause thats all backed up, isnt there any other way?

thx

---

### Post by schauerlich on 2007-11-25
You could create a new user and migrate your backup into the new user's directory.

---

### Post by m623d on 2007-11-25
> **coolguy2006delhi said:**
> Its better to make another user account and just delete the old one.


How do I do that?
sorry but I am a novice!

---

### Post by schauerlich on 2007-11-25
```
useradd new_username
``` To change the password: ```
passwd new_username
```

---

### Post by schauerlich on 2007-11-25
[http://ubuntuforums.org/showthread.php?t=484828](http://ubuntuforums.org/showthread.php?t=484828)

See this thread for more information about adding users.

---

### Post by m623d on 2007-11-25
ok, will give that a go.

so do I enter the complete command you gave or do I substitute the 'new_username' for my chosen name?

Thanks

---

### Post by schauerlich on 2007-11-25
If you want your new name to be bob, run ```
useradd bob
``` then ```
passwd bob
```

---

### Post by kellemes on 2007-11-25
> **m623d said:**
> ok, will give that a go.

so do I enter the complete command you gave or do I substitute the 'new_username' for my chosen name?

Thanks

Replace with your chosen name indeed..

---

### Post by m623d on 2007-11-25
ok, tried that, but it came up with the same error on sign in.

'Home directory is listed as /home/user does not exist, do you want to log in as root directory on home directory?'

click yes and an error comes up that session only lasted 10 seconds then quit and back to login screen

---

### Post by m623d on 2007-11-25
it does also come up with some info about still running setup in the background. Wine?
and directs me to [www.gtk.org/setuid.html](www.gtk.org/setuid.html)

but that is of no help to me!

---

### Post by m623d on 2007-11-27
anyone?
:(

---

### Post by m623d on 2007-12-21
still wont work, anyone help?

---

