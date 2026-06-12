---
title: "CUPS doesn't accept user and password"
date: 2006-09-22
forum: Desktop Environments
---

### Post by cccc on 2006-09-22
hi

I'd like to add a new parallel printer on dapper drake using:

[http://127.0.0.1:631](http://127.0.0.1:631)

but CUPS won't accept a user and password, even root. 

what's wrong and howto solve this problem ?


p.s.
on debian I didn't have such problems.

---

### Post by mik9dt on 2006-09-22
The following link got my printers up and running

[http://www.cups.org/articles.php?L317](http://www.cups.org/articles.php?L317)

Hope that helps

---

### Post by Giggity on 2006-09-22
I'm having the same problem with not being able to use my username:password, and the suggestion in the guide posted above to use root:rootspassword fails as well.  Any tips?

---

### Post by kerry_s on 2006-09-22
The web access of cups is crippled in ubuntu you have to use the gnome-cups-mangager. If you have the read me file still installed for cups it tells how to uncripple cups web access.

---

### Post by bennyj on 2006-09-22
I was having the same problem with the user and password not being accepted in the cups web interface.This is what fixed it for me.

open a terminal
type in "adduser cupsys shadow" (without quotes)press enter.dont forget sudo!
then type in /etc/init.d/cupsys restart

You should see it restarting in the terminal.
now browse to the cups web interface and add your printer.

Hope this helps
Benny

---

### Post by cccc on 2006-09-23
other way is:

in /etc/cups/cupsd.conf add the following lines:```

Port 631
RunAsUser Yes
User cupsys
Group lpadmin
```

add user "cupsys" to the group "shadow"```
sudo adduser cupsys shadow
```

pls do not forget:
```
sudo /etc/init.d/cupsys restart
```

add the printer [http://localhost:631/](http://localhost:631/) using root and that's it !


to sign with your account:```

<Location />
Deny From All
Allow From @LOCAL
</Location>
```

---

### Post by Tallowwood on 2006-09-24
Hi all, I am also having trouble with this issue. 

I'm running DD.6.06 - did not try CCCC's solution because those lines are commented out in my conf file. It says:
# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

So I tried benny's solution: 
[QUOTE=bennyj;1532952 (snip) open a terminal, type in (sudo) "adduser cupsys shadow" (without quotes), press enter (snip) then type in /etc/init.d/cupsys restart] 

Output was:
 * Restarting Common Unix Printing System: cupsd [all OK]
start-stop-daemon: warning: failed to kill 7180: Operation not permitted, cupsd: Child exited on signal 15! [not so good]

Shame really. I'm installing a Brother mono laser (5250DN) hooked to usb-printserver on Netgear FWG114P wireless router. I found up-to-date linux drivers in both rpm & deb livery and good help (for deb, suse & red-hat at least) on the brother web pages, but they want me to use cups-web.

Anyone know why cups-web-interface was crippled in ubuntu?
Anyone done this who can spare time to help?

Tallowwood

ps. thanks & best wishes to all FOSS coders, creators and workers everywhere.

---

### Post by veloct on 2006-09-24
That worked just fine for me also. Nice tip Benny.

---

### Post by cccc on 2006-09-24
> **Tallowwood said:**
> Hi all, I am also having trouble with this issue. 

I'm running DD.6.06 - did not try CCCC's solution because those lines are commented out in my conf file. 

don't comment out, just add on the end of /etc/cups/cupsd.conf

greetings
cccc

---

