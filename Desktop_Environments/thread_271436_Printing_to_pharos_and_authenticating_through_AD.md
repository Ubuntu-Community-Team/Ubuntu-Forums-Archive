---
title: "Printing to pharos and authenticating through AD"
date: 2006-10-04
forum: Desktop Environments
---

### Post by jmerlin on 2006-10-04
I have two questions, the first of which I have found almost nothing on searching on the web ( on this forum even ), the second of which I have found 1000 different ways of doing it, which in my experience, tends to mean there are 999 ways to do it incorrectly and 1 way to do it correctly.

Here at my place of employment we are looking to set up some machines running Ubuntu, they're almost ready to go minus two major setup hurdles.  We need them to print through a pharos print station, and we need to have them authenticate through a windows Active Directory, our user domain - basically so people can enter the username/password they use on the rest of the machines here and log in just fine.

We've got Ubuntu 6.06 Dapper Drake ( using GNOME ) installed on this machine and are trying to set it up correctly before ghosting it to every other machine on which we wish to install linux.

If anyone has any suggestions, has faced these problems before and WON, or knows how to do what we are trying to do, please let me know how =>.

Thank you.

---

### Post by SendDerek on 2007-06-22
I don't know if this helps, but what you're trying to accomplish sounds a lot like you're working for the same school as I'm attending.

I made a tutorial for students to follow to get their Linux machines to print to the Pharos Stations and each test has been sucessfull.  As long as they are logging into an account that has the same username as their NetID, then it works.

BYU-Idaho accepted my tutorial and published it on their website.  Here is the link:

[http://www.byui.edu/wireless/linuxprint.htm](http://www.byui.edu/wireless/linuxprint.htm)


As for the other thing (Windows user accounts), it sounds like you may want to get in touch with BYU-Idaho's IT department.  They have a Linux Lab running Red Hat on 20+ computers and the students can login, access their shared "H:" drive, just like in the Windows labs.

---

### Post by HeWhoE on 2007-11-16
Is there a way to determine the location and name of the printers using config files on windows machines that are running the Pharos client?

This is what the **agent.INI** file looks like.
```
[General]

DB_ADD=123.456.789.10

DB_PORTNAME=psdbserver

DB_TIMEOUT=120

MAINDIR=C:\Program Files\Pharos

INST_UPG=i

DB_PORTNUM=2355

HOST&SVC_DIR=C:\WINDOWS\System32\drivers\etc

SET_IP_ADD=123.456.789.10

```

And here's the file, **popups.INI**.
```
[General]

DB_ADD=123.456.789.10

DB_PORTNAME=psdbserver

DB_TIMEOUT=120

MAINDIR=C:\Program Files\Pharos

INST_UPG=i

DB_PORTNUM=2355

HOST&SVC_DIR=C:\WINDOWS\SYSTEM32\DRIVERS\ETC

[Pharos Popups]

POP_POP_SELECT=PSS

POP_POP_ADD=123.456.143.210

POP_POP_PNAME=pspopupsvr

POP_POP_PNUM=28203

POP_POP_TIME=120

POP_JOB_OPT=A

[printer1]

name=Cowell B&W

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT1.PRN

server=PSS

spoolq=CowellBWQU

type=1

s_address=PSS

s_portname=printer

s_portnum=515

[printer2]

name=MERCColor

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT2.PRN

server=PSMM

spoolq=MERCColorFD

type=1

s_address=PSMM

s_portname=printer

s_portnum=515

[printer3]

name=REFBW 2

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT1.PRN

server=PSMM

spoolq=REFBW5400FD

type=1

s_address=PSMM

s_portname=printer

s_portnum=515

[printers]

total=1

[printer4]

name=COLORMERC

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT3.PRN

server=PSMM

spoolq=MERCColorFD

type=1

s_address=PSMM

s_portname=printer

s_portnum=515

[printer5]

name=Ref. 1 BW Single Sided Printer (2nd floor)

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT8.PRN

server=PSMR

spoolq=REFBW2125FD

type=1

s_address=PSMR

s_portname=printer

s_portnum=515

[printer6]

name=Ref. 1 BW Double Sided Printer (2nd floor)

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT9.PRN

server=PSMR

spoolq=REFBW2125FD

type=1

s_address=PSMR

s_portname=printer

s_portnum=515

[printer7]

name=Merc Color Single Sided Printer (1st floor)

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT10.PRN

server=PSMM

spoolq=MERCColorFD

type=1

s_address=PSMM

s_portname=printer

s_portnum=515

[printer8]

name=Cowell Color

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT2.PRN

server=PSS

spoolq=CowellColorFD

type=1

s_address=PSS

s_portname=printer

s_portnum=515

[printer9]

name=Cowell BW Double Sided Printer

port=C:\PROGRAM FILES\PHAROS\TEMP\PORT1.PRN

server=PSS

spoolq=CowellBWFD

type=1

s_address=PSS

s_portname=printer

s_portnum=515
```

---

