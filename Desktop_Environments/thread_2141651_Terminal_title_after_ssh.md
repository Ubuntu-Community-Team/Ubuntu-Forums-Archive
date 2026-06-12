---
title: "Terminal title after ssh"
date: 2013-05-03
forum: Desktop Environments
---

### Post by tjay0 on 2013-05-03
Hi guys,
I am looking for a way to change the title of my tabs when i am SSHing into a different server.
I have about 200 servers and i can have about 20 of those open at once.
I was wondering if there was a simple way to automatically change the title of each tab as i ssh to a new server.
ATM i am just right clicking and using the Set title.. option.

Is there a way that i can automate this without editing the .bashrc on every server?

---

### Post by ajgreeny on 2013-05-03
Are you sure it's not the .bashrc file in the client that needs editing, rather than every server.

I do not know for certain, and am not using SSH at the moment, so I am just throwing this out as a possibility.

---

### Post by tjay0 on 2013-05-03
Well all the solutions i have found through Google are saying you will need to edit .bashrc on the remote server as it will run during initialisation  of bash on connection and will run the command to change the title bar.

I need something that will do it from the client side.

---

### Post by prodigy_ on 2013-05-03
[http://unix.stackexchange.com/questions/14113/is-it-possible-to-set-gnome-terminals-title-to-userhost-for-whatever-host-i](http://unix.stackexchange.com/questions/14113/is-it-possible-to-set-gnome-terminals-title-to-userhost-for-whatever-host-i)

See the last answer.

---

### Post by tjay0 on 2013-05-03
Thank, but no joy

That script would work but it assumes that the remote server has bash install.
I am remoting to FreeBSD servers and they done all have bash installed.

Plus that script will over write any .bash_profiles you have setup

---

### Post by prodigy_ on 2013-05-03
Then you should switch to Konsole or some other terminal emulator that allows dynamic titles. I don't think it's possible to achieve what you want using Gnome Terminal.

---

### Post by tjay0 on 2013-05-03
Isn't Konsole for the KDE environment though?
Isn't there one for Gnome?

---

### Post by CharlesA on 2013-05-03
You can use Konsole on Gnome. I much prefer it to the default terminal that comes with Gnome.

---

### Post by prodigy_ on 2013-05-03
Installing Konsole will pull a lot of dependencies but you won't have to change your DE session.

---

### Post by LewisTM on 2013-05-03
You could enable byobu on each server. Then each time you login, you will be taken to a custom screen session with all running tasks waiting for you. By default, byobu  displays the login info in the terminal title: user@host (ip.address) - byobu
```
byobu-enable
```
Cheers!
[ATTACH=CONFIG]242147[/ATTACH]

---

