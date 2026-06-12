---
title: "How to connect to and disconnect from the Internet without using the command line"
date: 2006-03-19
forum: Desktop Environments
---

### Post by chrisav on 2006-03-19
Hello,

I'm new to GNU/Linux,

I finally managed to connect to the Internet with eagle-usb-2.3.2.tar.bz2 unpacked and installed in /opt/eagle-usb-2.3.2 (I'm using a Sagem Fast 800 usb modem).

Before I installed the 3 linux-headers-* packages from Synaptic. I don't know if it was necessary to install all of them.

Now I would like to know how to create a way to connect to and disconnect from the Internet without using the command line (without always having to go to "/opt/eagle-usb-2.3.2" and write "sudo startadsl" and later "sudo stopadsl"), just by clicking a link for instance. 

I could probably write a script but I know nothing about scripts.

Thanks in advance for your advice.
Chris.

---

### Post by Malac on 2006-04-30
Hi,
I'm a complete newbie myself but try this:

Right-click on the desktop and select "Create Launcher".
In the form change the command field to
 "sudo /opt/eagle-usb-2.3.2/start-adsl" (without the quotes)
Choose a new icon if you want.
Then name the link (e.g. "StartADSL") and save it.

Right-click on this Link and choose "Copy"
Right-click on desktop and choose "Paste"
Right-click on new Link and choose "Rename" call it "StopADSL"
Right-click on "StopADSL" choose "Properties"
Change command to "sudo /opt/eagle-usb-2.3.2/stop-adsl" (without the quotes)
You can also change the permissions if this is required in the properties form.

Long way round possibly but it does work.

Hope this helps.

---

### Post by louis_nichols on 2006-05-01
[QUOTE=Malac]Hi,
I'm a complete newbie myself but try this:

Right-click on an desktop and select "Create Launcher".
In the form change the command field to
 "sudo /opt/eagle-usb-2.3.2/start-adsl" (without the quotes)
Choose a new icon if you want.
Then name the link (e.g. "StartADSL") and save it.

Right-click on this Link and choose "Copy"
Right-click on desktop and choose "Paste"
Right-click on new Link and choose "Rename" call it "StopADSL"
Right-click on "StopADSL" choose "Properties"
Change command to "sudo /opt/eagle-usb-2.3.2/stop-adsl" (without the quotes)
You can also change the permissions if this is required in the properties form.

Long way round possibly but it does work.

Hope this helps.[/QUOTE]


Nice solution. Perhaps a little change, though: in launchers, instead of sudo, use gksu. This will give you a nice little gnome screen to enter your password.

---

