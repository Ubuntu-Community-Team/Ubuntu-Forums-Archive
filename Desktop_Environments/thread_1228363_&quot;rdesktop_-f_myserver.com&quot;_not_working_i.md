---
title: "&quot;rdesktop -f myserver.com&quot; not working in startup applications command line"
date: 2009-07-31
forum: Desktop Environments
---

### Post by shirubia on 2009-07-31
Hi all I'm having a problem with SYSTEM>PREFERENCES>STARTUP APPLICATIONS>COMMAND

I created a new startup app to launch remote desktop when a user logs in. This is what I'm entering into the COMMAND line:

rdesktop -f myserver.com

This works in a terminal window, but doesn't work in STARTUP APPLICATIONS>COMMAND.

I've read a couple threads about this issue, but they weren't resolved or the answer wasn't given. I'm completely new to Ubuntu so any help is greatly appreciated!

Thanks!

---

### Post by XanTrax on 2009-07-31
> **shirubia said:**
> Hi all I'm having a problem with SYSTEM>PREFERENCES>STARTUP APPLICATIONS>COMMAND

I created a new startup app to launch remote desktop when a user logs in. This is what I'm entering into the COMMAND line:

rdesktop -f myserver.com

This works in a terminal window, but doesn't work in STARTUP APPLICATIONS>COMMAND.

I've read a couple threads about this issue, but they weren't resolved or the answer wasn't given. I'm completely new to Ubuntu so any help is greatly appreciated!

Thanks!

Maybe try:

```

sh -c "rdesktop -f myserver.com"

```

---

### Post by shirubia on 2009-08-03
> **XanTrax said:**
> Maybe try:

```

sh -c "rdesktop -f myserver.com"

```

Hi XanTrax,

Thanks for the quick reply, I tried it.. but sadly it didn't work.. Do you have an idea of why its not working? Or some other way to work around this issue?

---

### Post by asmoore82 on 2009-08-03
try ```
/usr/bin/rdesktop -f *myserver.com*
```

---

### Post by shirubia on 2009-08-03
> **asmoore82 said:**
> try ```
/usr/bin/rdesktop -f *myserver.com*
```

Hi thanks for the reply,

I tried this as well and its not working.. I noticed that there's another auto-start application called "Remote Desktop" I tried deleting it but it wont let me.. Could this be why its not working? 

I also found this link: [http://www.riccardoriva.com/archives/443](http://www.riccardoriva.com/archives/443)

I tried to do it this way, but I don't have access to save files in the right places etc.. I tried working around this by saving scripts onto my desktop, but still didn't work..

Any other suggestions?

---

### Post by shirubia on 2009-08-04
The Ubuntu Box is connected to via WiFi, could that be why its not working? It might be that the command is running correctly, but in order to finish it needs to be connected to the internet first. Because the command runs before the box is connected, it does not work..

---

### Post by shirubia on 2009-08-04
Snaps! That was why~ WONT WORK VIA WIFI!

Thanks for everyones help.

---

### Post by XanTrax on 2009-08-05
> **shirubia said:**
> Snaps! That was why~ WONT WORK VIA WIFI!

Thanks for everyones help.

Well, I know rdesktop and tsclient are very temperamental when connect so if Wifi hasnt established a connection yet and you try to execute the rdesktop command on login, then it will hang in the background for awhile until it realizes there is a connection and then bring it up.  At least, I remember with tsclient that if you had no internet connection and/or you were trying to connect an unestablished/unknown host, it wouldnt say much and would just sit in the background for awhile until it finally prompted you saying there was no connection established.  

I know you're new, but, you can try writing a script that waits until there is an established connection (hint: watch command) and then executes the rdesktop command once a connection has been established and puts the rdesktop process in the background, then exits the script.

---

