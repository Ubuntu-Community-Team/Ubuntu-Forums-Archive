---
title: "Connecting to another linux computer?"
date: 2009-04-24
forum: General Help
---

### Post by twin-08 on 2009-04-24
hey guys am new to ubuntu and I was helping a friend who has only seen ubuntu for the first time. I would like to know if there's anyway I can connect to his computer and help him out?

Thanks - Twin-08 -

---

### Post by WRDN on 2009-04-24
You could use [VNC]("https://help.ubuntu.com/community/VNC") or [SSH]("https://help.ubuntu.com/community/SSHHowto") (with possibly X11 forwarding, which allows you to run GUI applications)

---

### Post by twin-08 on 2009-04-24
ye I tried to use VNC I typed in his ip and it was just a blank screen for about 5mins then I closed

---

### Post by paradigm2 on 2009-04-24
> **twin-08 said:**
> hey guys am new to ubuntu and I was helping a friend who has only seen ubuntu for the first time. I would like to know if there's anyway I can connect to his computer and help him out?

Thanks - Twin-08 -

Is this Jaunty?

Probably the best way would be using the stock Remote Desktop.

Have him find his iP address and directly connect to the internet if possible (no router -- just to do this and then switch back).  Or if you want to walk your friend through forwarding ports on the router, you can do that.

Then have them go to:

System -> Preferences -> Remote Desktop.

HAve them check:

Allow others to view your Desktop

and 

Allow others to control your desktop


HAve him leave

"You must confirm each access to this machine" checked (for security.  They will need to approve the connection once you try to connect each time)

Also have them check "Require the user to enter this password" and you two should agree to a password using as secure means as possible.

Then have them leave "Only display an icon when there is someone connected" selected.

HAve them hit OK.

(they may need to reboot at this point -- have them do so just to be sure)


Then you connect using:

Applications -> Internet -> Remote Desktop Viewer.

Click CONNECT, Enter in the ip address, and click the new connect button.

You should get prompted for the password you both agreed to.  Enter it.

You should be connected as soon as they approve the connection on their end and you should be able to control their desktop now.

---

### Post by paradigm2 on 2009-04-24
> **paradigm2 said:**
> Is this Jaunty?

Probably the best way would be using the stock Remote Desktop.

Have him find his iP address and directly connect to the internet if possible (no router -- just to do this and then switch back).  Or if you want to walk your friend through forwarding ports on the router, you can do that.

Then have them go to:

System -> Preferences -> Remote Desktop.

HAve them check:

Allow others to view your Desktop

and 

Allow others to control your desktop


HAve him leave

"You must confirm each access to this machine" checked (for security.  They will need to approve the connection once you try to connect each time)

Also have them check "Require the user to enter this password" and you two should agree to a password using as secure means as possible.

Then have them leave "Only display an icon when there is someone connected" selected.

HAve them hit OK.

(they may need to reboot at this point -- have them do so just to be sure)


Then you connect using:

Applications -> Internet -> Remote Desktop Viewer.

Click CONNECT, Enter in the ip address, and click the new connect button.

You should get prompted for the password you both agreed to.  Enter it.

You should be connected as soon as they approve the connection on their end and you should be able to control their desktop now.

Actually now that I think of it, by default it might only allow local network access.  I'm unsure.  

Perhaps read this:

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

edit: apparently the link above is for a different version.

In addition if they do have a router and it uses upnp you could have them check the appropriate option to have it try to configure the network automatically.

---

### Post by twin-08 on 2009-04-24
thanks works now

---

