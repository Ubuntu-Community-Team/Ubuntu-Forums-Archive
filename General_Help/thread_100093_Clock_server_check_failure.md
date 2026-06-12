---
title: "Clock server check failure"
date: 2005-12-06
forum: General Help
---

### Post by Seinfeld on 2005-12-06
Hi 

When I boot up my machine, ubuntu does the series of routine checks normally and they all pass. However, the clock/time check using _ntp.ubuntulinix.org_ always fails.
I do wish that test to pass rather than cancelling it..

Help ???:???: 

Thanks

---

### Post by cstudent on 2005-12-06
Is the machine on a dsl or cable modem? It has to have access to the internet when it does the check.

---

### Post by cydec on 2005-12-07
I'm having the same problem but I know what the origin is:

I'm only working with WiFi that has to be enabled with ndiswrapper.
He is never connected to an Access Point BEFORE he tries to update my clock.
Thats my problem, don't know if there is any solution for this thou.
(For my problem)

---

### Post by Seinfeld on 2005-12-08
Yes friends.. Of course.. I do have a DSL connection. It dials up at reboot.. Sorry if I did miss saying that.. But, HEY,  may be it dials up the DSL modem (expecially I am on a USB one) connection AFTER this particular clock server test ?? If so, how I can solve this issue and be ready online before that test ?? 

Help ?? ;)

---

### Post by aclaunch on 2005-12-08
Well you can install "ntp" and run this to connect to time servers; the boot up time check doesn't really matter and AFAIK it cannot be "fixed" if your connection is not active prior to the time check. I guess you could try to edit some of the boot scripts to get it to check last (after the connection is set) but why bother?

Alan

---

### Post by doitashimashite on 2005-12-08
You can skip it by pressing CTRL-C during boot.

If you want to disable this clock synchronizing thing then uncomment the lines in

/etc/default/ntpdate

(sudo gedit /etc/default/ntpdate)

---

### Post by Seinfeld on 2005-12-08
Guys.. The annoying thing that the USB modem takes a looooong time to load up its firmware and dial up the connection everytime the computer boots.  :rolleyes:  So there is no way solving this problem.. Yes you are right aclaunch..  ..cydec this seems similar to what you have with your WiFi I think.. doitashimashite, thanks for pointing out the file path

Exactly aclaunch.. Why bother ??? :razz: :razz: 

I will just leave it.. It's OK ...


Thanks to all//

---

### Post by cydec on 2005-12-15
Indeed same problem.
I'm just going to comment the line so he doesn't try to do it on startup.
It's not needed...

---

