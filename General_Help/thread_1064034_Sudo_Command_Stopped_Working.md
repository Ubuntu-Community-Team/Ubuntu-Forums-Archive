---
title: "Sudo Command Stopped Working"
date: 2009-02-08
forum: General Help
---

### Post by Darlixus on 2009-02-08
Well, I wanted to change the hostname of my linux box so I just went on the Terminal and typed in:

```
su
<passwrd>
hostname <hostnamehere>
```

Now I know I should have typed in:

```
gksudo gedit /etc/hostname /etc/hosts
```

Now everytime that I type in the command sudo I get this:

```
darlixus@<myhost>:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

```

I'd like to know how to get sudo back working.

Thanks in the advance.

---

### Post by Darlixus on 2009-02-08
> **julian5 said:**
> Well, while I was working through, my sudo stopped working normally. It was right after entering the commands to modify .profile.
It would seem that you have screwed up your PATH.
See the section on shell config in this Unix FAQ ([http://forums.macosxhints.com/showthread.php?t=40648](http://forums.macosxhints.com/showthread.php?t=40648))

--Julian

I'd rather reinstall than read all that O_O

But thx anyways =]

---

### Post by gettinoriginal on 2009-02-08
What is your output of ```
gksudo gedit /etc/hostname /etc/hosts
```

---

### Post by Darlixus on 2009-02-08
> **gettinoriginal said:**
> Sorry, wrong thread

I finnally thoud i'd get an answer and puff :(

> **gettinoriginal said:**
> What is your output of ```
gksudo gedit /etc/hostname /etc/hosts
```

It opens the files hostname and hosts with the text editor via root.

---

### Post by cariboo on 2009-02-08
Have you restarted since you tried to change the host name? the cahnge won't take place until after a reboot. The command you should run to show what /etc/hostname outputs is in a terminale type:

```
hostname
```

and for the hosts file:

```
cat /etc/hosts
```

Jim

---

### Post by Darlixus on 2009-02-08
> **cariboo907 said:**
> Have you restarted since you tried to change the host name? the cahnge won't take place until after a reboot. The command you should run to show what /etc/hostname outputs is in a terminale type:

```
hostname
```

and for the hosts file:

```
cat /etc/hosts
```

Jim

I know lol, I already changed the hostname and the hosts file back to normal and the hostname shows normal on terminal too but it doesnt work.And yes, i've rebooted after that.

Im using a VM btw..

---

### Post by doas777 on 2009-02-08
> **Darlixus said:**
> Well, I wanted to change the hostname of my linux box so I just went on the Terminal and typed in:

```
su
<passwrd>
hostname <hostnamehere>
```

Now I know I should have typed in:

```
gksudo gedit /etc/hostname /etc/hosts
```

Now everytime that I type in the command sudo I get this:

```
darlixus@<myhost>:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

```

I'd like to know how to get sudo back working.

Thanks in the advance.


ummm, perhaps I'm misunderstanding your issue. if you type ```
sudo
``` and press enter, you should get 
```
alpha10@21of2:~$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


```

because you have not added any parameters. if you want it to work like su, use 'sudo -s'
```

alpha10@21of2:~$ sudo -s
[sudo] password for alpha10: 
root@21of2:~# 
```

hope that helps

---

### Post by Darlixus on 2009-02-08
> **doas777 said:**
> ummm, perhaps I'm misunderstanding your issue. if you type ```
sudo
``` and press enter, you should get 
```
alpha10@21of2:~$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


```

because you have not added any parameters. if you want it to work like su, use 'sudo -s'
```

alpha10@21of2:~$ sudo -s
[sudo] password for alpha10: 
root@21of2:~# 
```

hope that helps

lol soz, I was confusing the su command with the sudo command.

---

### Post by todak on 2009-02-08
Typing **sudo** by itself does nothing. Typing **sudo <command-name-here>** will get you the response you desire. ;)

---

### Post by Darlixus on 2009-02-08
k, thx guys ;)

---

