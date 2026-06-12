---
title: "xfce problem"
date: 2007-08-19
forum: Desktop Environments
---

### Post by kystorms on 2007-08-19
i have ubuntu FF installed, got xfce and it works kind of slow, and I am wondering about this error i get when i first try to sign in:

cannot look up internet address lisac-desktop. This will prevent xfce from working correctly. It may be possible to correct problem by adding lisac-desktop to the the file /etc/hosts/ on your system.

my problem is. i am unsure how to do this, and if i can do this, will it hopefully fix the speed problem i am suffering?

I love xfce, because it seems so clean, 
for info purposes, i simply choose xfce frm sessions as a choice.

thank you for any and all help.

:confused::confused:

---

### Post by Happy_Man on 2007-08-19
Well... why don't you try it? 

```
gksudo gedit /etc/hosts
``` and add in "lisac-desktop"

---

### Post by kerry_s on 2007-08-19
> **kystorms said:**
> i have ubuntu FF installed, got xfce and it works kind of slow, and I am wondering about this error i get when i first try to sign in:

cannot look up internet address lisac-desktop. This will prevent xfce from working correctly. It may be possible to correct problem by adding lisac-desktop to the the file /etc/hosts/ on your system.

my problem is. i am unsure how to do this, and if i can do this, will it hopefully fix the speed problem i am suffering?

I love xfce, because it seems so clean, 
for info purposes, i simply choose xfce frm sessions as a choice.

thank you for any and all help.

:confused::confused:

my guess is that is some kind of auto start entry you tried to add. check your autostarted applications folder. you can just delete the "lisac" file if you dont need it.

sudo updatedb
locate lisac

---

### Post by kystorms on 2007-08-20
> **Happy_Man said:**
> Well... why don't you try it? 

```
gksudo gedit /etc/hosts
``` and add in "lisac-desktop"

okay when i did that here is what i got in the terminal ( and I am total newb here, so please be patient with me :-)

lisac@lisac-desktop:~$ gksudo gedit /etc/hosts
(gedit:25114): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and here is what the output was in the gedit file -
127.0.0.1 localhost
127.0.1.1 lisac-desktop.newwavecomm.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

NOW... do i still add in my lisac- to that opened gedit file? is the message in the terminal posted at top a problem that I need to fix and if so, HOW?

:confused:

---

### Post by Happy_Man on 2007-08-20
> **kystorms said:**
> okay when i did that here is what i got in the terminal ( and I am total newb here, so please be patient with me :-)

lisac@lisac-desktop:~$ gksudo gedit /etc/hosts
(gedit:25114): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and here is what the output was in the gedit file -
127.0.0.1 localhost
127.0.1.1 lisac-desktop.newwavecomm.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

NOW... do i still add in my lisac- to that opened gedit file? is the message in the terminal posted at top a problem that I need to fix and if so, HOW?

:confused:
Well.... no. Not yet. Do what kerry_ s suggests, and see if that helps any. 

The GNOME error is normal, btw.

---

### Post by kerry_s on 2007-08-20
> **kystorms said:**
> okay when i did that here is what i got in the terminal ( and I am total newb here, so please be patient with me :-)

lisac@lisac-desktop:~$ gksudo gedit /etc/hosts
(gedit:25114): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and here is what the output was in the gedit file -
127.0.0.1 localhost
127.0.1.1 lisac-desktop.newwavecomm.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

NOW... do i still add in my lisac- to that opened gedit file? is the message in the terminal posted at top a problem that I need to fix and if so, HOW?

:confused:

```
127.0.0.1 localhost
127.0.1.1 lisac-desktop.newwavecomm.net

```

this part is wrong, im guessing "lisac-desktop" is what you choose for your host name and this "newwavecomm.net" is probably
 your router.

this is what it should look like

```
127.0.0.1 localhost lisac-desktop
127.0.1.1 lisac-desktop

```

try and fix that.

---

### Post by kystorms on 2007-08-22
> **kerry_s said:**
> ```
127.0.0.1 localhost
127.0.1.1 lisac-desktop.newwavecomm.net

```

this part is wrong, im guessing "lisac-desktop" is what you choose for your host name and this "newwavecomm.net" is probably
 your router.

this is what it should look like

```
127.0.0.1 localhost lisac-desktop
127.0.1.1 lisac-desktop

```

try and fix that.

hi

okay, as i said i am a total newbie and scared to death to change stuff without being SURE what I am doing, so I will ask just one more question is that is ok -
do i manually rewrite the code and change with is there from my net address to the one you refer to up  here > 
this is what it should look like

```
127.0.0.1 localhost lisac-desktop
127.0.1.1 lisac-desktop

```

thanks once again, u folks are awesome at helping us all out!!!

:KS

---

### Post by kerry_s on 2007-08-22
> **kystorms said:**
> hi

okay, as i said i am a total newbie and scared to death to change stuff without being SURE what I am doing, so I will ask just one more question is that is ok -
do i manually rewrite the code and change with is there from my net address to the one you refer to up  here > 
this is what it should look like

```
127.0.0.1 localhost lisac-desktop
127.0.1.1 lisac-desktop

```

thanks once again, u folks are awesome at helping us all out!!!

:KS

yes, just use your text editor as root->
press alt+f2 and type> gksu leafpad /etc/hosts
you can highlight copy & paste or just type it out manually
then just close it when it offers to save choose yes
then reboot your system to see if it worked.

---

### Post by kystorms on 2007-08-23
:KS:KS:KS:KS:KS

just wanted to say thank you to all of you for helping me, what you suggested worked perfectly!

:popcorn: you all rock!

---

