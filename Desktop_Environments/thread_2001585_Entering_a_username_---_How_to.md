---
title: "Entering a username --- How to?"
date: 2012-06-11
forum: Desktop Environments
---

### Post by Neill_R on 2012-06-11
Login in at the Ubuntu desktop on a Ubuntu server. there is my install user name but no where to enter a user-name. for example 

Domain-name\Active_directory_User_name 

or  

[email]Active_directory_User_name@Domain-name.co.uk[/email] 


I know i can ctrl-alt-f2 and login to a text window  but i want to connect via the GUI
 

what do I have to configure so that there is an option in the login menu to allow me to enter my details

---

### Post by sudodus on 2012-06-11
What service and what gui do you use?

- service: samba? ssh?
- and gui: nautilus? or some special gui?

---

### Post by Neill_R on 2012-06-11
here is my current login screen there is no place to enter a user-name

---

### Post by Neill_R on 2012-06-11
i don´t use a service. I just want to login at the console terminal but don have any means of entering my user-name

---

### Post by sudodus on 2012-06-11
The screen in your screen-dump picture is a login screen to Ubuntu running in a virtual machine (a local login screen, where the local users should be listed, underneath the black patch). I don't think you can log in to a remote computer at this screen, but I may be wrong. But after a normal local log in, you can log in to a remote computer with some server program, for example sshd or smbd (for ssh or samba).

Do you want to log into the local computer (via a keyboard, mouse and screen connected directly to the computer you call a server), or do you want to log in to a server via another computer (a client computer), connected to the server via a wired or wireless network? Or do you want to login via the virtual machine to the host computer of that virtual machine?

---

### Post by sudodus on 2012-06-11
If you have more than one user, they should be shown on the log in screen. In the attached file I have edited a detail of your screen-dump: added the users guru and sudodus.

In my installation, these names are clickable (as well as Guest Session), so click to select them!

If you click on the round symbol (presently with the Ubuntu logo), you can select different desktop environments, and the selection is remembered until next time you boot/log in.

---

### Post by Neill_R on 2012-06-11
The screen in your screen-dump picture is a login screen to Ubuntu  running in a virtual machine (a local login screen, where the local  users should be listed, underneath the black patch). I don't think you  can log in to a remote computer at this screen, but I may be wrong. But  after a normal local log in, you can log in to a remote computer with  some server program, for example sshd or smbd (for ssh or samba). THIS IS NOT WHAT I AM TRYING TO DO

Do you want to log into the local computer (via a keyboard, mouse and  screen connected directly to the computer you call a server),  YES

---

### Post by Cheesemill on 2012-06-11
Edit /etc/lightdm/lightdm.conf and add the line:
```
greeter-hide-users=true
```
to the bottom.

---

### Post by Neill_R on 2012-06-11
> **sudodus said:**
> If you have more than one user, they should be shown on the log in screen. In the attached file I have edited a detail of your screen-dump: added the users guru and sudodus.

In my installation, these names are clickable (as well as Guest Session), so click to select them!

If you click on the round symbol (presently with the Ubuntu logo), you can select different desktop environments, and the selection is remembered until next time you boot/log in.


I have one local user but I want to login as a domain user (Centrify has allow this machine to join my domain) if I log in at the text screen CTRl-ALT-F2 i can create a new user folder under /home  but that does not add a entry in the GUI login screen.

---

### Post by mcduck on 2012-06-11
Edit /etc/lightdm/lightdm.conf and add this line:

```
greeter-show-manual-login=true
```

After that, restart lightdm:

```
sudo service lightdm restart
```

Now you should be able to use the "Other" login option.

---

