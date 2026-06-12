---
title: "Problem with XFCE"
date: 2005-04-30
forum: Desktop Environments
---

### Post by SGC on 2005-04-30
I installed XFCE from synaptic today , but when i try to logon I only get the XFCE logo  without the taskbar or anything :?

Any suggestions to solve this problem?

---

### Post by Nob on 2005-04-30
[QUOTE=SGC]I installed XFCE from synaptic today , but when i try to logon I only get the XFCE logo  without the taskbar or anything :?

Any suggestions to solve this problem?[/QUOTE]
 press ALT+F2
type next:
xfce4-panel [u will get fxce panel]
xftaskbar4 [tasbar]
xfdesktop [desktop]
xfwm4 [window manager]

after that logout and SAVE CURRENT SESSION.. then log in again

---

### Post by SGC on 2005-04-30
Thanks Nob

---

### Post by az on 2005-04-30
Are you starting xfce4 or xfce4-session?

---

### Post by SGC on 2005-04-30
> Are you starting xfce4 or xfce4-session? 
I think it is a session since I log to it from KDM


Now , I has another problem, I can't save the settings, the check box is hidden (see the screenshot)

---

### Post by Nob on 2005-04-30
ummmmmm... let me see... try logging in as root, and then save settings..

---

### Post by SGC on 2005-04-30
[QUOTE=Nob]ummmmmm... let me see... try logging in as root, and then save settings..[/QUOTE]

Actually I was logged in as a root (as always) , when I used to have the previous problems, but when I try to log as a normal user (I hate the limitations of a normal user) it works directly without entering the commands that you mention it above.

---

### Post by az on 2005-04-30
[QUOTE=SGC]I think it is a session since I log to it from KDM


Now , I has another problem, I can't save the settings, the check box is hidden (see the screenshot)[/QUOTE]


Look to see if in the list of sessions you have, there are two XFCE entries, one called xfce and one called xfce-session.  Use the latter.

---

### Post by SGC on 2005-04-30
In my KDM there is only "xfce Session"

---

### Post by Nob on 2005-04-30
[QUOTE=SGC]Actually I was logged in as a root (as always) , when I used to have the previous problems, but when I try to log as a normal user (I hate the limitations of a normal user) it works directly without entering the commands that you mention it above.[/QUOTE]
 ok, than u'll have to do it manually :)

gedit /etc/xdg/xfce4-session/xfce4-session.rc

and check the [failsafe] part of file:
mine xfce4-session.rc is like this [as root]
```
[General]
SessionName=Default
SessionName[de]=Standard

# Disable management of remote clients by default. The user
# has to explicitly enable this for security reasons.
DisableTcp=True


# This the default session launched by xfce4-session if the
# user hasn't saved any session yet or creates a new session.
[Failsafe Session]
Count=4
Client0_Command=xfwm4
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=True
Client2_Command=xftaskbar4
Client2_PerScreen=True
Client3_Command=xfdesktop
Client3_PerScreen=False


# Default splash screen selection.
[Splash Screen]
Engine=mice
```

if its the same, i dont know whats the problem [than you probably killed these commands and somehow saved session].. 
if not, copy it and save, then reboot ;)

---

### Post by SGC on 2005-04-30
My xfce4-session.rc file is same as yours

---

### Post by Nob on 2005-04-30
[[IMG]http://img172.echo.cx/img172/7452/sessions8np.th.jpg[/IMG]](http://img172.echo.cx/my.php?image=sessions8np.jpg)
check the option Automatically Save session On Logout
then run these commands above..
then logout, reboot, log in... and if everything is working fine u can uncheck that option ;)

---

### Post by SGC on 2005-05-01
Thanks Nob for your help , but when i try to run any item from settings menu, both the panel and the taskbar turn into white for a second then nothing happens.

EDIT: 

I manage to  choose "Automatically Save session On Logout" using gnome (that running xfce program from gnome), then I loged in to XFCE and run the four commands , after that I restart the computer and logged to XFCE, and .......................... the preivous session does not saved  ](*,)

---

### Post by Nob on 2005-05-01
uhhhhh... damn it... 
then try this way - from gnome reinstall xfce.. i mean, completly remove it from synaptic, ant download and install it again..
i really dont know what problem might be... ^@$*@^$

---

