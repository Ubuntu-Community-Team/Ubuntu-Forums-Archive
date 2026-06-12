---
title: "How can I share my printer?"
date: 2005-07-24
forum: Desktop Environments
---

### Post by unzari on 2005-07-24
I need to share my printer with my Windows laptop.  I've installed 'samba' (and 'nfs'), but I cannot find any option in the printer panel applet or elseswhere to turn on sharing.  Can somebody tell me how to do this?

Thanks...

---

### Post by aggiechemist on 2005-07-24
You need a few things:

1. The IP address of the Linux system.
2. The IP address of the windows box.
3. The cupsd.conf file on your linux system.

In brief, open up the cupd.conf file. Find the section about allow certain IP addresses. By default, there will be one allow address: 127.0.0.0.
You will add a line something line Allow 192.16.1.*, where you are going to use the IP address of the windows computer.
Save that.
Restart the cups system with  /etc/init.d/cupsys restart in a terminal.
Go to the windows computer.
Say add printer, from a network, and that you will provide the address yourself.

The address will be something like http://192.16.1.34:631/printers/printer_name. This will use the IP of the linux box, and printer name will also get replaced with the actual printer name.
Add the drivers and you will be all set.

That is the quick version of it. There are many many threads and howtos on this already. Just a more general piece of advice, there are thousands of threads here. Chances are that any problem you run into already has a massive database already out there. Make sure you search before posting questions. If any of the steps I listed are unclear, just go up to the search function and play around. Just as an example, printer sharing is covered in depth [here](http://ubuntuforums.org/showthread.php?t=27736).

---

### Post by unzari on 2005-07-25
[QUOTE=aggiechemist]You need a few things:

1. The IP address of the Linux system.
2. The IP address of the windows box.
3. The cupsd.conf file on your linux system.

In brief, open up the cupd.conf file. Find the section about allow certain IP addresses. By default, there will be one allow address: 127.0.0.0.
You will add a line something line Allow 192.16.1.*, where you are going to use the IP address of the windows computer.
Save that.
Restart the cups system with  /etc/init.d/cupsys restart in a terminal.
Go to the windows computer.
Say add printer, from a network, and that you will provide the address yourself.

The address will be something like [http://192.16.1.34:631/printers/printer_name](http://192.16.1.34:631/printers/printer_name). This will use the IP of the linux box, and printer name will also get replaced with the actual printer name.
Add the drivers and you will be all set.

That is the quick version of it. There are many many threads and howtos on this already. Just a more general piece of advice, there are thousands of threads here. Chances are that any problem you run into already has a massive database already out there. Make sure you search before posting questions. If any of the steps I listed are unclear, just go up to the search function and play around. Just as an example, printer sharing is covered in depth [here](http://ubuntuforums.org/showthread.php?t=27736).[/QUOTE]
 Hi... Thanks for the reply.

After a fair amount of messing around, I got this to work.  Your method was basically right, but you also have to uncomment some other  lines in 'cupsd.conf' (the relevant "<Location...>" entries for printers, admin, browsing, etc.).  I also set 'AuthType' to 'None'.  In contrast to the linked article, that person had a very different device entry, such as "smb://bla bla"... Mine shows the following:  DeviceURI usb://Canon/S530D

This bit of Ubuntu still needs a bit of work in the UI! :-)

---

### Post by aggiechemist on 2005-07-25
I whole heartedly agree about Ubuntu needing improvement in the UI here. Given that it generates so many complaints (literally a few dozen people a week have your problem) I would think we can look forward to improvement in Breezy Badger (the next big release due out in a few months).

---

### Post by fuqxit on 2005-07-26
What I got from another forum (not sure where???), that worked for me, is Network Printer(Windows Printer(SMB)/Host=<workgroup>/<hostname>/Printer=<printer_sharename>... and it printed. I had searched for days and was ecstatic when I heard the printer start clicking. I had seen lots of suggestions for editing files, but this was it! Hope it works. :roll:

---

