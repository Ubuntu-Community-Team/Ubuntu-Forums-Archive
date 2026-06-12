---
title: "start program on boot with sudo"
date: 2006-03-07
forum: Desktop Environments
---

### Post by jezjones on 2006-03-07
Hi, I hope this is an easy question.

How to a get a program to start when i start up my machine if it needs sudo permissions.

The reason is that i installed firestarter and it started with everything for a while. Then i started getting a message that i did not have permission to start firestarter as a disalog when i logged in, although firestarter would start.

So i removed all mention of firestarter from the system -> prefs -> sessions -> startup programs , so i dont get the dialog anymore, but i have to manually start firestarter.

How to add it back so it will start without intervention.

thanks.

---

### Post by Xian on 2006-03-07
[QUOTE=jezjones]The reason is that i installed firestarter and it started with everything for a while. Then i started getting a message that i did not have permission to start firestarter as a disalog when i logged in, although firestarter would start.

So i removed all mention of firestarter from the system -> prefs -> sessions -> startup programs , so i dont get the dialog anymore, but i have to manually start firestarter.

How to add it back so it will start without intervention.
[/QUOTE]

The only thing you are manually starting is the GUI of Firestarter. The actual firewall should be running fine and will be activated during boot. This is done automatically by the package installation scripts. If you want to check this enter the command below into a terminal:

$ sudo /etc/init.d/firestarter status

And you can always start the GUI as sudo in a terminal:
$ sudo firestarter

For further info read [Firestarter Security FAQ's](http://www.fs-security.com/docs/faq.php)

---

### Post by jezjones on 2006-03-07
cool  thanks very much, and thanks for the link that was exactly the type of info i was looking for. I guess i need to improve my googling.
:D

---

