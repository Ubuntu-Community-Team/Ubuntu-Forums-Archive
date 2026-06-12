---
title: "Temporary root privilages???"
date: 2009-04-15
forum: General Help
---

### Post by Augsburg on 2009-04-15
Does anybody know how to allow a non-privelaged user root privelages while a script is being run?

Here's the setup:  I have automatic login setup for a non-privelaged user.  When x starts, gnome-terminal prompts the user for a username and password to authenticate against a netware server.  Meanwhile, a daemon is run as root which sleeps for 45 seconds, then logs the user out.

To prevent the user from being logged out, I need another command in the Authentication script to kill the daemon process.

I know one work around could be to create a group with the non-privelaged user in it, then chmod root:group, but i would like for this to be only temporary.


countDownDaemon.sh:
  #!/bin/sh
  sleep 45
  logout

---

### Post by Alekz_ on 2009-04-15
Well.. I didn't understand exatly what you want.. But if you wanna run something with root privilages, then you can use `sudo`.

Something like:

sudo kill 'pid'

You can set the `kill` comando to be used without authentication in /etc/sudoers

I don't know if it's what you looking for...

[]'s

Alekz_

---

### Post by Augsburg on 2009-04-15
The user is not in the sudoers file (and he shouldn't be) and i do not want to allow this unprivelaged user to permanently be able to use the kill command.  I was just hoping there was a way to allow this user to have root privelages without using a sudo or root password.  Thanks for the prompt response, though.

---

### Post by Monotoko on 2009-04-15
No there isnt....if he isnt a sudoer i dont think there is any way to run things under root.

There might be a way using permissions though, if you tell me exactly what you would like this user to be able to do.

---

### Post by Alekz_ on 2009-04-15
Well.. You could set a stickbit on the /bin/kill but it's the same of set the user in the sudoers file! I'm not able to think about anything else! 

Unless I missunderstood what you want to do! :)

[]'s

Alekz_

---

### Post by Augsburg on 2009-04-15
> **Monotoko said:**
> No there isnt....if he isnt a sudoer i dont think there is any way to run things under root.

There might be a way using permissions though, if you tell me exactly what you would like this user to be able to do.

within the login script, after the user has authenticated, i would like to kill the countDownDaemon.sh Daemon with something like:

pkill countDownDaemon.sh

only i don't want to sudo it

---

