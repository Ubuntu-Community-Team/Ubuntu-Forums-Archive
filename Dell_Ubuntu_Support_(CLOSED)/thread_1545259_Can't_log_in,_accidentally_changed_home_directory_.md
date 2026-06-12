---
title: "Can't log in, accidentally changed home directory name, trapped!"
date: 2010-08-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonny180 on 2010-08-03
I was fiddling around and I can't log in, only into failsafe terminal

i think it's something to do with me accidentally changing my home directory name

how can I solve this problem?

please help!

thanks

---

### Post by mikewhatever on 2010-08-04
Can't you rename the home directory to what it was, accidentally or on purpose?

---

### Post by jonny180 on 2010-08-04
I would do that but I can't log in and I don't know how to do it from the failsafe terminal

---

### Post by denver on 2010-08-04
You should be able to get to a login screen, even if you have no homedir.

Boot your system normaly, and after you get to the login screen do the following:

- press ctrl+alt+F1 (virtual terminal. This is in text mode, but dont panic)
- login using your username/password. You should be warned about not finding your homedir. It will still og you in, and default to / (root dir) as a home.
- login as root:

```
sudo su
```

- get the name of your home dir (as it should be):

```
grep ${SUDO_USER} /etc/passwd | awk -F ":" '{print $6}'
```

- rename the home folder back to what it should be

```
mv /home/<current name> /home/<correct name>
```

NOTE: replace <current name> with whatever name you gave your home folder, and <correct name> with the result from the grep command above.

- set permissions (just in case you changed those too :)

```
chown -R ${SUDO_USER}:${SUDO_USER} /home/<correct name>
chmod 750 -R /home/<correct name>
```

After you do this, you should be able to login in GDM.

Good luck!

---

### Post by jonny180 on 2010-08-04
I did as you said, on the second step I copied it exactly and it produced the correct name for the home directory
BUT when changing the name it said /home/<current name> does not exist, i made sure i entered everything correctly:S 
 
thanks for helping, but what now?

---

### Post by denver on 2010-08-04
> **denver said:**
> 
```
mv /home/<current name> /home/<correct name>
```

**NOTE: replace <current name> with whatever name you gave your home folder, and <correct name> with the result from the grep command above.**

- set permissions (just in case you changed those too :)

```
chown -R ${SUDO_USER}:${SUDO_USER} /home/<correct name>
chmod 750 -R /home/<correct name>
```


Are you sure you payed close attention to the portion where it says to REPLACE <curent name> and <correct name> with the apropriate values?

<correct name> should be the result of this command:

```

grep ${SUDO_USER} /etc/passwd | awk -F ":" '{print $6}'

```

<correct name> should be whatever you renamed your home folder to...

To get a listing of whats in your home folder just type in this command:

```
ls /home/
```

---

### Post by jonny180 on 2010-08-04
ah, ok ive loggod in now, with <correct name> as the one I originally changed it to, and <current name> as the one I changed it from
 
All the tabs have gone from the bar (where I had all my websites shortcutted, and the wallpaper is just black,
is this just a side-effect or is there something else I need to do?
 
 
Thanks for your help, I really appreciate it! :D

---

### Post by denver on 2010-08-04
Glad to hear you managed :). Might be a permissions problem. Please check if any data is missing from your account (personal files, desktop icons and such).

Also, after logging in, open a terminal and type:

```
whoami
```

This will show you the username you are logged in as.

See if the files are owned by you:

```
 ls -l ~/
```

you should see your username somewhere in the directory listing (second and third columns). If not (and ONLY if not), issue the following command:

```
sudo chown ${USER}:${USER} -R ${HOME}
```

Best of luck!

---

