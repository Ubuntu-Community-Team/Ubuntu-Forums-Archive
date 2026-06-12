---
title: "how to log-in as root ??"
date: 2005-04-13
forum: Desktop Environments
---

### Post by deemer on 2005-04-13
Hi I can't log-in as root to my system I get graphic Login Manager and from this view I can log-in only as an user....:(

Regards

---

### Post by localzuk on 2005-04-13
Root account is disabled as default. 

Log in as user and use 'sudo' or 'gksudo' to run programs as root.

---

### Post by ssam on 2005-04-13
do you really want to log in to the desktop as root? unless you really know what you are doing this is not a good idea and not necissary. if you do need to then i think enabling a root password and checking over the 'login screen setup' control panel would probably let you.

other wise use 'sudo' on the terminal to do commands and launch applications you need to run as root.

sudo bash

will give you a root shell (or there is root terminal in the applications -> system tools menu)

sam

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=deemer]Hi I can't log-in as root to my system I get graphic Login Manager and from this view I can log-in only as an user....:(

Regards[/QUOTE]

If you really, *really* need to login as root, you have to start by setting root's password. Run **sudo passwd root** and enter a password. Then, go to the system settings menu and run the "Login Screen" applet. Look for the option marked "Allow root to log in locally" and enable it. These names might not be exact, as I'm at a Windows box at work right now and not my Ubuntu box at home.

Don't set the "allow root to log in remotely" unless you want to get pwned. In fact, don't login as root locally unless you really have to; it's safer to use sudo, especially if you have a cat. :)

---

### Post by deemer on 2005-04-13
Thanks a lot:) I am not going to log-in as root unless I have to:) Sorry for the question but what sudo really is?? I used to work on gennto so I am very new ubuntu user 

Regards

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=deemer]Thanks a lot:) I am not going to log-in as root unless I have to:) Sorry for the question but what sudo really is?? I used to work on gennto so I am very new ubuntu user [/QUOTE]

**sudo** is a tool that allows you to perform one action with root privileges. I'd recommend looking into using the **su** command as well. With **su**, you can login as a user, open a terminal, and have root privileges in that terminal window while running everything else with normal privileges.

---

