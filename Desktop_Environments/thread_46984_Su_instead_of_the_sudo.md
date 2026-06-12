---
title: "Su instead of the sudo"
date: 2005-07-06
forum: Desktop Environments
---

### Post by mbanton on 2005-07-06
Smell.  

This is my first post in the ubuntu forum.  I am of Brazil, and my English is not of the best and I did this message with help of a translating, excuse eventual errors.  

I am with a doubt as regards utilization of the su instead of the sudo.  I utilize kubuntu 5.04

I created a sign for the root user with the command sudo passwd, and I tried disable the sudo, stirring in the files sudoers.  However now when it is going to perform some program that requires root by the menu of the kde, or call the administrative functions of the kde control center, the kdesu returns error.  I heard to speak that would be necessary rebuild the kdesu for that he had bear to su, seen that in the ubuntu is standard utilize only the sudo.  It is truth this, or some exists another one solution?

---

### Post by f1dave on 2005-07-06
Have you tried... 

sudo su

Then to exit root mode,

exit

---

### Post by bored2k on 2005-07-06
[QUOTE=mbanton]I am of Brazil, and my English is not of the best and I did this message with help of a translating, excuse eventual errors.  
[/QUOTE]
In IRC (Xchat):
> #ubuntu-pt on irc.freenode.net is for Portuguese discussion and support. 
[https://wiki.ubuntu.com/PortugueseDocumentation](https://wiki.ubuntu.com/PortugueseDocumentation)
[https://wiki.ubuntu.com/PortugueseDocumentation](https://wiki.ubuntu.com/PortugueseDocumentation)
[http://www.ubuntu-pt.org/](http://www.ubuntu-pt.org/)

---

### Post by mbanton on 2005-07-14
In the terminal I utilize the su and I turn root normally.  

I thank for the links of the documentation in Portuguese, however I found nothing about my problem there.

---

### Post by Gezzer on 2005-07-14
u can have a root logon if required
but first in a konsole try

su kcontrol
press enter
enter password
press enter

---

### Post by souki on 2005-07-14
I didn't like the sudo stuff at first time, but now I think it's great

When I need a root session I do this:
```
sudo -i
```
or this (you can change the shell here)
```
sudo -H bash
```
see the wiki [here](https://wiki.ubuntu.com/RootSudo) for more detailed informations

---

### Post by X_FISH on 2005-07-18
Hm... Another problem on my system (found this thread using the search function):

Example:

My root password is "foo"
My user password is "bar"

If I enter "sudo su -" I have to enter "bar" not "foo". Why? Why do I have to enter the "wrong" password?

Loggin in from console (no X) => root password IS "foo".

Regards, Martin

---

### Post by varunus on 2005-07-18
[QUOTE=X_FISH]Hm... Another problem on my system (found this thread using the search function):

Example:

My root password is "foo"
My user password is "bar"

If I enter "sudo su -" I have to enter "bar" not "foo". Why? Why do I have to enter the "wrong" password?

Loggin in from console (no X) => root password IS "foo".

Regards, Martin[/QUOTE]

This is because you're using sudo to execute the su command as root.  If you do this, sudo authenticates the su command, and if you run su as root, you don't need a password.  Therefore, you enter your own password.

---

### Post by mbanton on 2005-07-18
[QUOTE=Gezzer]u can have a root logon if required
but first in a konsole try

su kcontrol
press enter
enter password
press enter[/QUOTE]


marcelo@marcelo:~$ su kcontrol
Id desconhecido : kcontrol
marcelo@marcelo:~$

---

### Post by centremco on 2005-07-19
Is there a big difference/preference in using sudo <command> or su + pw then <command> as root?
Since it seems easier to me to use the su, pwd mehtod... Or is that too much of a good thing ? ;-)

---

### Post by mbanton on 2005-07-19
I not with himself use su + pw afterwards command.  See:

marcelo@marcelo:~$ su
Password:
root@marcelo:/home/marcelo # kcontrol
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-7372' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
ERROR: Communication problem with kcontrol, it probably crashed.
root@marcelo:/home/marcelo #


And my problem is not for commands in the terminal, and yes for the icons that call programs that require root, as the synaptic.

---

### Post by Feanor on 2005-07-19
if you are in kde use

kdesu <command>

so 

```
kdesu kcontrol
```

works perfectly.

I think to enable root user is useless when i can do sudo su and have the same effects.

---

### Post by mbanton on 2005-07-19
OK, works perfectly,
 however I should digitate the sign of the my user and not of the root.  And this is my problem.

---

