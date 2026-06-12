---
title: "Password problems!"
date: 2006-01-12
forum: Desktop Environments
---

### Post by gravediggers on 2006-01-12
Just installed Kubuntu 5.10 on this machine and wanting to use Adept to do updates and Print Manager to install printer. Adept won't accept my root password, nor will print manager when I choose administrator mode. Can run as root in Konsole.
What is likely problem?

---

### Post by Clopy on 2006-01-12
This may sound silly, but have you tried typing your password in kedit and copy-pasting it in the password field? Maybe it's an encoding/language issue

---

### Post by gravediggers on 2006-01-12
Doesn't  paste (ctrl-V??)

---

### Post by manu0510 on 2006-01-12
Same problem when i try to set my lan.Ask my password and nothing hapen ,i can have acces to setings.

---

### Post by Divan Santana on 2006-01-12
[QUOTE=gravediggers]Just installed Kubuntu 5.10 on this machine and wanting to use Adept to do updates and Print Manager to install printer. Adept won't accept my root password, nor will print manager when I choose administrator mode. Can run as root in Konsole.
What is likely problem?[/QUOTE]
Its your password not roots password.
I think it even says that.

read the wiki on sudo

---

### Post by Clopy on 2006-01-12
Yes, it's the user password you have to provide not the root password ofcourse :)

If that is not the problem, try copy and pasting but not with shotcuts. just right clik->copy right click->paste

If copy and paste with control-c, control-v doesn't work, you're probably using a different language than english (at least for me that I use both english and greek i can't copy paste while i'm in greek)

---

### Post by gravediggers on 2006-01-12
Thanks guys!
 
I tried **my** password when I read your post this morning, but that said incorrect also. Now I seem to have some sort of a lockout - got some message about not being able to have a conversation with su (can't remember exact words - am away from home at the moment).
However, I will check out my user and group settings, and also pour through the sudo wiki, and I'm sure I'll work it out
 
By the way, if you read the wiki carefully it says:
 
[COLOR=red]>  
[COLOR=red]By default, the password for root is locked in Ubuntu. This means you cannot login as root or use su[/COLOR]. Instead, the installer will setup[COLOR=black] [COLOR=black]sudo[/COLOR] to allow the user that is created during install to run all administrative commands. [/COLOR]
[COLOR=black]This means that in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a [/COLOR][COLOR=#000000]password, it needs **YOUR password**, this means that a root password is not needed.[/COLOR]


[/COLOR][COLOR=black]And what my post said was"[/COLOR]
[quote=gravediggers] 
.........Can run as root in Konsole.
 
[/quote]
So I don't have the default setup, and so perhaps sudo is not set up correctly either! However, as I said I will have a play and work it out when I get home.
 
(I don't know why it asked me to choose a root password during install - it didn't happen with installing ubuntu on my other PC. Maybe because I set this one up as multi user workstation?)

---

### Post by gravediggers on 2006-01-13
I might need a little help to get my self out of a hole in the ground (nothing to do with my user name! LOL!). As mentioned above, my installation created an unlocked root account (I think), and some destroyed my sudo access for my user account. Now I have read the wiki on rootSudo, but I am a bit tired to make sense of it (likewise the man pages). I just want to get things back to normal, without making a mistake. I have done this before on another PC, but my memory fails me!

Can someone briefly run through the commands with me? Luckily I can still get a root shell in the terminal!

```
root@gandalf:/# more /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
```

```
root@gandalf:/# more /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:gravediggers
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:gravediggers,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:gravediggers,hal
floppy:x:25:gravediggers,hal
tape:x:26:
sudo:x:27:
audio:x:29:gravediggers
dip:x:30:gravediggers
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:gravediggers
sasl:x:45:
plugdev:x:46:gravediggers,hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
gravediggers:x:1000:
lpadmin:x:104:gravediggers
scanner:x:105:gravediggers
crontab:x:106:
ssh:x:107:
slocate:x:108:
messagebus:x:109:
hal:x:110:
saned:x:111:

```

---

### Post by gravediggers on 2006-01-13
bump!

---

### Post by gravediggers on 2006-01-13
knock! knock! fellow *nxers, anyone home?

---

### Post by gravediggers on 2006-01-13
?

---

### Post by hashimoto on 2006-01-13
[QUOTE=gravediggers]
```
root@gandalf:/# more /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
```

[/QUOTE]

Your username seems to be missing from the sudoers file. That is the reason you (as user) dont have the admin rights.
Open terminal (konsole), do
```
su
``` 
to log in as root, then
```
visudo
```
At the end of the file after the line:
```
root  ALL=(ALL) ALL 
```
add:
```
gravedigger ALL=(ALL) ALL
```
then save and exit. Administrative tasks should now work with your password.

---

### Post by gravediggers on 2006-01-13
Thanks for that! Back working again.

---

