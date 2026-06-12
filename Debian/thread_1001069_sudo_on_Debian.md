---
title: "sudo on Debian"
date: 2008-12-03
forum: Debian
---

### Post by cl333r on 2008-12-03
Hi folks,
While installing Debian (stable and testing) it asks for a root and for a user password. But when I try to do anything as root I'm being told that I'm not part of the "sudoers".
Is there any point and click solution to be able to use sudo as in our (much) more user-friendly Ubuntu?

---

### Post by cmay on 2008-12-03
no. not point and click. but its easy to edit to sudoers file. 
i have a tread on it in the debian subforum. i am a open solaris live cd right now and i cant exactly remember the right path to the file . search the debian sub forum or my older posts and there is a perfect explaination and example. 
hope it helped .

---

### Post by cmay on 2008-12-03
i forgot. 
open terminal and type visudo.
then edit the sudoers file. 
save by pressing f2 (your using nano)
and that is it.
mine looks like this. 

> root=ALL(ALL)ALL
cmay=ALL(ALL)ALL

at least this is how i remember it to be.

---

### Post by K.Mandla on 2008-12-03
Moved to Debian subforum.

---

### Post by nvteighen on 2008-12-04
Don't forget to look at:
```

man sudoers

```

---

### Post by markharding557 on 2008-12-07
just open a root terminal or use gksu sudo is not needed

---

### Post by kerry_s on 2008-12-07
> **markharding557 said:**
> just open a root terminal or use gksu sudo is not needed

some people prefer sudo as it is safer, my root is locked(sudo passwd -l root). 1 of the first things i do on my debian install is change it to sudo, by adding myself to sudoers and the changing gksu(gksu-properties).

---

### Post by dizee on 2008-12-09
I much prefer to use sudo, out of habit more than anything. I have a habit of changing to root so often to do things such that su becomes annoying with its extra requirement to enter the username. It'd work well if you did all your admin stuff at the same time, though.

---

### Post by del_diablo on 2008-12-10
What is it with you people? You only need to type su once, unless you close down the terminal.

user~ su
password:
user#

*sig*

---

### Post by basenvironment on 2008-12-10
tabbed terminal....

tab1  - su to root
tab2 - user

minimize to taskbar

):P

---

### Post by dizee on 2008-12-11
> **del_diablo said:**
> What is it with you people? You only need to type su once, unless you close down the terminal.

user~ su
password:
user#

*sig*
Yeah, but the idea of leaving an open root terminal worries me.

Knowing me I'd go to delete something and do some serious damage by accidentally picking the wrong terminal window. 

Besides, I'm used to sudo.

---

### Post by polmir on 2008-12-20
Another way to run programs as root.
Type in user terminal:```
su-to-root -c /path/to/program
```
For example:```
yy@xx:~$ su-to-root -c /usr/sbin/synaptic
About to execute synaptic.
This command needs root privileges to be executed.
Using su...
Enter root password at prompt.
Password:
```
or```
yy@xx:~$ su-to-root -c synaptic
About to execute synaptic.
This command needs root privileges to be executed.
Using su...
Enter root password at prompt.
Password:
```
or
```
yy@xx:~$ su-to-root -c gedit
About to execute synaptic.
This command needs root privileges to be executed.
Using su...
Enter root password at prompt.
Password:
```

---

### Post by shadylookin on 2008-12-28
go into the terminal
su
enter password
visudo

you'll see something that looks like this 
> 
# User privilege specification
root    ALL=(ALL) ALL


add your usersname ALL=(ALL) ALL under root like this
> 
# User privilege specification
root    ALL=(ALL) ALL
YOUR_USERNAME_HERE ALL=(ALL) ALL


hit ctrl+o
write to /etc/sudoers 
ctrl+x

and now you can use sudo

---

### Post by CREEPING DEATH on 2009-01-23
When INSTALLING Debian (I've only done this with the old-style blue-screen installer), press Esc when it asks for a root password.  It will then take you back to the menu.  Press Enter.  When it asks about Root, tell it "No".  It will then set up as Sudo.
This isn't always an option, some (recent, but obsoleted) versions of D-I don't allow it.

CD

---

### Post by Frak on 2009-01-24
Here's a simple string that you can use
```
su -
echo '**loginname** ALL=(ALL) ALL' >> /etc/sudoers
```

Loginname is your login name; mine would be frak

Close the terminal, go back into the terminal, and you should be able to use sudo.

---

