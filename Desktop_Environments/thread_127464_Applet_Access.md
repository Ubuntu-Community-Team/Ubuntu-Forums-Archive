---
title: "Applet Access"
date: 2006-02-09
forum: Desktop Environments
---

### Post by Beastboy26 on 2006-02-09
Can anyone tell me how to give my nm-applet access to the "default keyring" without me haveing to type in a passoword everytime, in other words, I don't even want it to prompt me for access, it just gets it.

---

### Post by nanotube on 2006-02-09
"chmod u+s nm-applet" ?

---

### Post by Beastboy26 on 2006-02-09
with that I get this error: 

chmod: cannot access `nm-applet': No such file or directory

---

### Post by Beastboy26 on 2006-02-09
bump

---

### Post by nanotube on 2006-02-09
hi
sorry, the actual command you would want to use is as follows:

sudo chmod u+s /usr/bin/nm-applet

try that and see if that works.

---

### Post by Beastboy26 on 2006-05-01
Ok, i did the sudo chmod u+s /usr/bin/nm-applet command to handle the prompt for access to the "default keyring" today (May 1st 2006), and now the nm-applet has totaly disappered.   I tried sudo /etc/init.d/dbus restart and that didn't help.  What now? ](*,)

---

### Post by nanotube on 2006-05-02
[QUOTE=Beastboy26]Ok, i did the sudo chmod u+s /usr/bin/nm-applet command to handle the prompt for access to the "default keyring" today (May 1st 2006), and now the nm-applet has totaly disappered.   I tried sudo /etc/init.d/dbus restart and that didn't help.  What now? ](*,)[/QUOTE]

are you sure nm-applet is even started? do a 
```
ps -ax |grep nm
```
and see if nm-applet shows up.

---

### Post by Beastboy26 on 2006-05-03
this is the output: 

> user@pc:~$ ps -ax | grep nm
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 4978 ?        Ss     0:00 nm-applet --sm-config-prefix /nm-applet-JQGMb1/ --sm- client-id 1003f93f41000113962476200000083990000 --screen 0
 7378 pts/0    S+     0:00 grep nm
user@pc:~$ ps -eAF | grep nm
user     4978     1  0  6874  9328   0 00:13 ?        00:00:00 nm-applet--sm-config-prefix /nm-applet-JQGMb1/ --sm-client-id 1003f93f4100011396247620000008399 0000 --screen 0
user     7380  7365  0   720   796   0 00:19 pts/0    00:00:00 grep nm

I also tried just nm-applet to start the process... but it didn't work

---

### Post by nanotube on 2006-05-03
[QUOTE=Beastboy26]this is the output: 



I also tried just nm-applet to start the process... but it didn't work[/QUOTE]
hm well, it seems to be running. did you try a reboot?

---

### Post by Beastboy26 on 2006-05-03
i have done several reboot (due to traveling with my laptop), and I did 

sudo apt-get update
sudo apt-get dist-upgrade

and then another reboot:)

---

### Post by nanotube on 2006-05-03
well, i guess in that case, chmod it back to where it was before (sudo chmod u-s /usr/bin/nm-applet), and then edit your sudoers file with
```
sudo visudo
```
and add this line to it at the end:
```
username ALL = NOPASSWD: /usr/bin/nm-applet
```
save and exit. now you should be able to run ```
sudo /usr/bin/nm-applet
``` without entering your password. see if that solves your problem.

---

### Post by Nailor on 2006-05-05
Correct me if I'm not right but isn't this so called default keyring -"problem" (which I'm having too) an issue with encrypted keyring file holding passwords for encrypted networks in this case.

If sudo and/or +s-flag helps, I'd suggest gnome guys to check their encoding =)

---

### Post by Beastboy26 on 2006-05-07
[QUOTE=nanotube]well, i guess in that case, chmod it back to where it was before (sudo chmod u-s /usr/bin/nm-applet), and then edit your sudoers file with
```
sudo visudo
```
and add this line to it at the end:
```
username ALL = NOPASSWD: /usr/bin/nm-applet
```
save and exit. now you should be able to run ```
sudo /usr/bin/nm-applet
``` without entering your password. see if that solves your problem.[/QUOTE]

changed everything like you have it here, 
but it still did't slove my problem,
so in the mean time I have used System->Admin->Network to change networks (like in Breezy and before);
but I have also noticed that other programs will not run. (well, I guess that nm-applet is running, but....),  like printing serves gives an error of cupsd: Child exited on signal 15! usiing this cmd: ```
 sudo /etc/init.d/cupsys restart 
```

also vmware will not start

---

### Post by Beastboy26 on 2006-05-07
Got this after the last upgrade: 
```

Installing new version of config file /etc/acpi/sleep.sh ...
 * Checking battery state...                                             [ ok ]

Setting up gnome-session (2.14.1-0ubuntu4) ...

Setting up libtiff4 (3.7.4-1ubuntu3) ...


Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Beastboy26 on 2006-05-10
bump

---

