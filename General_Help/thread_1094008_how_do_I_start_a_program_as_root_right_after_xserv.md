---
title: "how do I start a program as root right after xserver is up"
date: 2009-03-12
forum: General Help
---

### Post by sam1948 on 2009-03-12
?
I am using ubuntu 8.10 and I added to session this line
gksu <my_script>
but then I have to enter my password every time it starts

---

### Post by jackflap on 2009-03-12
You can add your username to your sudoers file so that it doesnt prompt you for a password.

For detailed info check [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Otherwise just do the following:

sudo gedit /etc/sudoers

And add the following line to that file replacing your username and the full path to your scripr:

<your username> ALL=(ALL) NOPASSWD: <my script>

---

### Post by sam1948 on 2009-03-12
thanks 
but i am trying to run 
```
ifconfig eth0 192.168.1.100
```
and its involved with some kind of variables (i think)
which i still non permited 
```
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
```

?

---

### Post by jackflap on 2009-03-12
make sure to add a sudoers line for the 'ifconfig' command specifically.

also, in your script where you call ifconfig, you should call 'sudo ifconfig <blabla>'

In this case, you dont even need to run 'gksu <my script>' since it's the ifconfig specifically that requires the sudo.

---

### Post by sam1948 on 2009-03-12
thank u very much
worked pefect

---

