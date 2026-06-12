---
title: "Printing to remote HP LaserJet 1022nw (command-line)"
date: 2006-05-31
forum: Desktop Environments
---

### Post by zoot_ on 2006-05-31
Hi there

I am able to print from Thunderbird to the printer which I've setup via gnome-cups-manager. However, for applications such as Gnucash, where one must specify a command, I'm unable to print. I see that despite the printer being added via gnome-cups-manager, that it is not listed when running lpq. How do I set this up?

The printer is on the local wireless network and gnome-cups-manager is configured to print to it using JetDirect.

I'd appreciate it if someone could point me in the right direction. 

Thanks

(Ubuntu Dapper, up-to-date as of 2006-05-31 16:00 GMT)

---

### Post by zoot_ on 2006-05-31
I've found this link and am studying it....

[http://www.linuxjournal.com/article/5331](http://www.linuxjournal.com/article/5331)

---

### Post by zoot_ on 2006-05-31
The solution is to set the printer to be the 'default', either via the CUPS web interface, or (I'm guessing here), /etc/cups/printers.conf, by setting 'OpPolicy' to 'default'. Ermmmm... I didn't bother, but setting it to the default printer via gnome-cups-manager will suffice too \\:D/

<DefaultPrinter LaserJet-1022>
Info LaserJet-1022
DeviceURI socket://192.168.0.3:9100
State Idle
StateTime 1148820488
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

... and restarting CUPS, also assumed ;)

To temporarily enable CUPS web administration (of a user, foo, say):

$ sudo adduser cupsys shadow
$ sudo adduser foo lpadmin

Then navigate to the CUPS web interface via [http://127.0.0.1:631](http://127.0.0.1:631)
Click on the 'Manage Printers' button
Click on the 'Set as default' button for the printer concerned

edit: when prompted for a password, enter user: foo and password: foo's password

After setting this up, I suggest you remove the user 'cupsys' from the shadow group.

Now you can use the lp commands without specifying a print queue per se. For example:

lp /tmp/some_file.txt and it will print to the remote JetDirect interface

Done and dusted, woohoo! :rolleyes:

---

