---
title: "Strange Characters in the man page"
date: 2006-06-29
forum: Desktop Environments
---

### Post by huygens on 2006-06-29
Hello,

I happen to have weird characters in my man page each time a *special* character should be displayed.
So for example when I do a 'man iostat' I get the following output (just a relevant part is shown here):
```
IOSTAT(1)                     Linux Userâ<80><99>s Manual                    IOSTAT(1)



NAME
       iostat - Report Central Processing Unit (CPU) statistics and input/outâ
<80><90>
       put statistics for devices and partitions.
```

This man page is OK to read, but sometimes the number of special symbol is so big that it become difficult or even impossible to read the man page.

Any help or suggestion would be greatly appreciated.

Huygens

PS: I have installed Dapper Flight 5 and constantly upgraded it. I thought it was some kind of localisation problem, so I was waiting for update, but it seems that it isn't the case.
I have installed my Ubuntu with English US localisation (for what I remember), before swithcing it to English UK from the System->Adminstration->Language Support facility.

---

### Post by glotz on 2006-06-29
(**man iostat** > *No manual entry for iostat*)

Does that occur on every man page?

---

### Post by huygens on 2006-06-29
[QUOTE=glotz]Does that occur on every man page?[/QUOTE]

Yes, for example, if I do a 'man ls' (which every one has) :
```
--color[=WHEN]
              control  whether  color is used to distinguish file types.  WHEN
              may be <80><98>never<80><99>, <80><98>always<80><99>, or <80>
<98>auto<80><99>

```

But I have this also with man find, hdparm, iptables, etc.

I also have this when I am on the console, or using gnome-terminal or konsole or xterm!

I am using zsh for SHELL, but this occurs also with bash :(

Huygens

---

### Post by huygens on 2006-08-14
Hi there,

I have been creating a new account, and I do not have the problem in the man page. Seems that I had some problems during update from Kubuntu 5.10 to Ubuntu 6.06 Flight 5 (and subsequent updates).
So as anyway my motherboard went broken, I will re-install Ubuntu from scratch by wiping my hard disk (I have a backup...). I hope this will solve this issue and maybe other unspotted once ;) .

Huygens

---

### Post by pablo13 on 2006-08-14
Hi ... for me that seems to be something related with your shell init script. I don't know much about zsh but in bash would be .bashrc or in tcsh woul be .cshrc or .tcshrc. I mean that you have probably changed something of this file or you have copied from another linux machine ... and that's why your new user doesn't have that problem.

It seems to me like the character coding it's messed up. Could you give us the output for 

echo $LANG

or the output for the locale command

Bye,
Pablo

---

### Post by pablo13 on 2006-08-14
Oh ... I didn't read the mainboad part. But still if you bring your old .zshrc (or whatever is called) you will still have the same problem.

Bye,
Pablo.

---

### Post by huygens on 2006-08-14
> **pablo13 said:**
> Oh ... I didn't read the mainboad part.

:) well, once replaced, I could still boot under my old installation and check the env. variable you mentionned. None the less, I will re-install Ubuntu and wipe out my account, anyway all my data are backed-up.


Huygens

---

### Post by huygens on 2006-08-15
> **pablo13 said:**
> Could you give us the output for 
echo $LANG
or the output for the locale command

So for the output of locale (which includes LANG) is:
```
$ locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```Which is correct for my settings.
I switched back my profile to use bash by default. I did not touch the .bashrc. The man a readable but for the non-standard characters, I see a black square instead of <80><90>. So it is kind of an improvement...
Anyway the differences between the .bashrc I have and the one created for the new user are:
```
9c9
< #export HISTCONTROL=ignoredups
---
> export HISTCONTROL=ignoredups
19c19
< if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
---
> if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
70,77c70,72
< #if [ -f /etc/bash_completion ]; then
< #    . /etc/bash_completion
< #fi
<
<
< # This line was appended by KDE
< # Make sure our customised gtkrc file is loaded.
< export GTK2_RC_FILES=$HOME/.gtkrc-2.0
---
> if [ -f /etc/bash_completion ]; then
>     . /etc/bash_completion
> fi

```If I copy this new .bashrc to my home directory. I still have the same problem.

Huygens

---

### Post by meowsqueak on 2006-10-29
Put 'export LC_ALL=C' in your .bashrc - fixes the problem for me.

---

### Post by huygens on 2006-10-31
Thanks for the info, I'll try it the next time I have this problem.
I manage to solve it by wipping my account and creating a blank new one :-)
But thanks anyway for your help!

Huygens

---

