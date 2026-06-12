---
title: "Sync V630i"
date: 2007-10-14
forum: Desktop Environments
---

### Post by Ficik on 2007-10-14
I'm trying to sync my SE V630i with Kontact's calendar. At first I tried to find my phone (works only as su):

```
ficik@ficik-laptop:~$ sudo syncml-obex-client -u
Found 1 USB OBEX interfaces
Interface 0:
        Manufacturer: Sony Ericsson
        Product: Sony Ericsson V630
        Interface description: Sony Ericsson Device 043 USB WMC OBEX Interface
Use '-u interface_number' to connect
```

When I try to sync it using versions 1.1 or 1.0 I get this:
```
ficik@ficik-laptop:~$ sudo syncml-obex-client -u 0 --slow-sync text/x-vcalendar std.ics --version 1.1 --wbxml
connection with device succeeded
Received an Alert for the DS Server at std.ics: Type: 201, Last 0, Next 11
Slowsyncing
Just received a new session with ID 1
Received the DevInf
Session 1 reported final. flushing
There was an error in the session 1: wrong initial node
```

When I try same with version 1.2 phone print that sync failed and syncml print this:
```
ficik@ficik-laptop:~$ sudo syncml-obex-client -u 0 --slow-sync text/x-vcalendar std.ics --version 1.2 --wbxml
connection with device succeeded
/build/buildd/libsyncml-0.4.1/libsyncml/sml_session.c:1023:E:smlSessionGetSessionID: Assertion "session" failed
Aborted
```

What's wrong? thx

---

### Post by darigaz625 on 2007-10-21
hey, i am trying to do the same.

how did you connect your phone to the pc? i tried with the usb cable, and then the phone software crashed...

also, do you know a possibility to access the files on the phone's memory stick using ubuntu? 

any help appreciated ;)

---

### Post by Ficik on 2007-11-11
I'm using usb cable and I can access data only  on Memory Stick.

---

### Post by El_Matthews on 2007-12-20
did anybody succeed in this?

---

