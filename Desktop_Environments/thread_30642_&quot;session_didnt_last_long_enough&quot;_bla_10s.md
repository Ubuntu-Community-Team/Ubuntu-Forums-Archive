---
title: "&quot;session didnt last long enough&quot; bla 10secs."
date: 2005-04-29
forum: Desktop Environments
---

### Post by spotlight2001 on 2005-04-29
[PROBLEM DESCRIPTION]:
I have hoary it worked fine ...

now on boot; graphical logon screen ... on logging on I get the messgage something like "your last session lasted less than 10seconds some error ... maybe space ..."

The error message from .xsession-erros:
###########
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "walter"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
/etc/gdm/Xsession: line 217: exec: x-terminal-emulator: not found
###########

[ERROR CAUSE]:
those entries I made in /etc/environment:
JAVA_HOME=/usr/local/java
PATH=${PATH}:${JAVA_HOME}/bin

[SOLUTION]:
removal of those lines ... I thought I could do global envs in /etc/environment according to some other forum posts.

---

### Post by Alexander Kirillov on 2005-04-29
[QUOTE=spotlight2001]I have hoary it worked fine ...

now on boot; graphical logon screen ... on logging on I get the messgage something like "your last session lasted less than 10seconds some error ... maybe space ..."

The error message from .xsession-erros:
###########
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "walter"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
/etc/gdm/Xsession: line 217: exec: x-terminal-emulator: not found
###########

i searched the web for the error
1) space requirements:
"df" tells me that there should be enough space. ~62% of a 4.2gb partiton used -> ~2gb free
2) permission settings:
i logged to another terminal ... permissions /home/walter where all walter:walter correctly[/QUOTE]
 Can you check which type of session is selected in your login screen (Gnome, KDE, Failsafe)?

---

### Post by spotlight2001 on 2005-04-29
[QUOTE=Alexander Kirillov]which type of session is selected in your login screen (Gnome, KDE, Failsafe)?[/QUOTE]

gnome is selected ... 

with "gnome failsave" I dont get the above msg but something like:

"failed execute xscreensaver ... file/folder not found" ...

Reinstalling the xscreensaver doesnt help (i got on other terminal an aptitude reinstalled xscreensaver like packages)

---

### Post by alastair on 2005-04-29
For X startup, the following happens :

/etc/gdm/Xsession (a text file - shell script) - runs (run-parts) all files in the dir $SYSSESSIONDIR i.e.

run everything in /etc/X11/Xsession.d/

The files in here set up the environment and actually spawn a desktop e.g. gnome.

You get an error about "ls" being "not found" on line 73 of /etc/gdm/Xsession

The only "ls" I have in /etc/gdm/Xsession is line 82 :

    for F in $(ls $1); do

This failing ("ls" not found?) is VERY odd. What might have screwed up your X setup?

You could put some debug "echo" statements in the /etc/X11/Xsession.d/ files - see where things crash.

---

### Post by shakin on 2005-04-29
```

$ sudo rm ~/.ICEauthority

```

Then try to login. That's how I usually fix the problem. I believe when it happened to me it was because I had started K3b as root user.

---

### Post by spotlight2001 on 2005-04-30
[QUOTE=shakin]```

$ sudo rm ~/.ICEauthority

```

Then try to login. That's how I usually fix the problem. I believe when it happened to me it was because I had started K3b as root user.[/QUOTE]
 > rm ~/.ICEauthority

didnt work either. file was there and deleted by me.

then I created another user. couldnt logon with new account ... same error msg.

then I aptitude-purged the gnome/x/... packages 
on trying to reinstall those packages, system didnt reinstall them although it confirmed everything with ok/done/...
now i dropped the partition and made a reinstall ...

I think the original problem occured after a unsuccessful (suspend)RESUME

anyway thx for all help I appreciate that very much. You are good ppl

---

### Post by wxlidar on 2005-05-02
Check the permissions of /tmp. I had this problem last week. Gconfd (or similar) needs to mess around (for lack of a better term) in /tmp when you login. The permissions on my /tmp had been changed so only root had write access. Once I corrected this everything was fine.

-Dave

---

### Post by cdhotfire on 2005-05-02
question, why do u want to add those entries?

you can grab java out of backports
```

$ sudo gedit /etc/apt/sources.list

```

add these

deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-extras main universe multiverse restricted

```

$ sudo apt-get update
$ sudo apt-get install sun-j2re1.5

```

but, if you want to keep at this problem for kicks, go ahead, i wont stop you.:?

---

