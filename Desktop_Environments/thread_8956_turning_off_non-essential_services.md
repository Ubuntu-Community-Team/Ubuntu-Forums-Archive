---
title: "turning off non-essential services"
date: 2004-12-22
forum: Desktop Environments
---

### Post by sonetti on 2004-12-22
I'm using warty and have not altered anything yet, but need some advice ...
I have a single PC, I'm not on a network, I don't run a server, nor a printer.
 
1. which services can I safely turn off permanently. (I see them loading during boot)

2. how is this done

thanks in advance.

---

### Post by Juergen on 2004-12-23
Install 'rcconf'. 
With that you can see (and turn on/off the start of) the 'services' installed on your machine. 
Then use google (or this forum) to find out what each service does and decide yourself.

And btw: even a single computer is a little network, and you probably don't want to turn off inetd. 
Maybe start with  looking at cups, rsync, ppp

---

### Post by sonetti on 2004-12-23
I've managed to stop cups from running, it was using the most resources. I'll experiment with the other services, "rcconf" makes this easy, thanks for the help!

---

### Post by ubuntu_demon on 2004-12-23
By default no services are reachable from outside.

You can look what services are listening (local) with :

nmap -sV localhost

I recommend stopping postfix's smtpd. Since its useless unless you send mails directly from your pc.

smptd :

I commented the following three lines in /etc/postfix/master.cf :

pico /etc/postix/master.cf

#127.0.0.1:smtp inet n - - - - smtpd
#::1:smtp inet n - - - - smtpd
#submission inet n - - - - smtpd

after that do : sudo postfix reload

---

### Post by sonetti on 2004-12-23
done ... thank you 

@kevzbox:~ $ sudo rcconf
update-rc.d: /etc/init.d/postfix exists during rc.d purge (continuing)
 Removing any system startup links for /etc/init.d/postfix ...
   /etc/rc0.d/K20postfix
   /etc/rc1.d/K20postfix
   /etc/rc2.d/S20postfix
   /etc/rc3.d/S20postfix
   /etc/rc4.d/S20postfix
   /etc/rc5.d/S20postfix
   /etc/rc6.d/K20postfix
@kevzbox:~ $

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=sonetti]done ... thank you 

@kevzbox:~ $ sudo rcconf
update-rc.d: /etc/init.d/postfix exists during rc.d purge (continuing)
 Removing any system startup links for /etc/init.d/postfix ...
   /etc/rc0.d/K20postfix
   /etc/rc1.d/K20postfix
   /etc/rc2.d/S20postfix
   /etc/rc3.d/S20postfix
   /etc/rc4.d/S20postfix
   /etc/rc5.d/S20postfix
   /etc/rc6.d/K20postfix
@kevzbox:~ $[/QUOTE]
 don't remove postfix that isn't very smart :)
without postfix yo can't receive emails from processes when things go wrong. (for example cronjobs)

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=sonetti]done ... thank you 

@kevzbox:~ $ sudo rcconf
update-rc.d: /etc/init.d/postfix exists during rc.d purge (continuing)
 Removing any system startup links for /etc/init.d/postfix ...
   /etc/rc0.d/K20postfix
   /etc/rc1.d/K20postfix
   /etc/rc2.d/S20postfix
   /etc/rc3.d/S20postfix
   /etc/rc4.d/S20postfix
   /etc/rc5.d/S20postfix
   /etc/rc6.d/K20postfix
@kevzbox:~ $[/QUOTE]
 don't remove postfix that isn't very smart :)
without postfix you can't receive emails from processes when things go wrong. (for example cronjobs)

---

### Post by sonetti on 2004-12-23
ok I've re-enabled postfix 

then commented the top 3 lines in  /etc/postfix/master.cf to this ....

===============================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==============================================
#127.0.0.1:smtp inet n   -       -       -       -       smtpd
#::1:smtp       inet n   -       -       -       -       smtpd
#submission inet n      -       -       -       -       smtpd

then "sudo postfix reload"

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=sonetti]ok I've re-enabled postfix 

then commented the top 3 lines in  /etc/postfix/master.cf to this ....

===============================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==============================================
#127.0.0.1:smtp inet n   -       -       -       -       smtpd
#::1:smtp       inet n   -       -       -       -       smtpd
#submission inet n      -       -       -       -       smtpd

then "sudo postfix reload"[/QUOTE]
 yeah

If you've got an emailaccount somewhere you won't need smtpd enabled unless you want for example let a cronjob mail some logfiles.(but it doesn't save you much resources if you do nor does it increase your security)

---

### Post by sonetti on 2004-12-23
thanks for the help demon666_nl & juergen

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=sonetti]thanks for the help demon666_nl & juergen[/QUOTE]
 you're welcome

---

