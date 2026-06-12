---
title: "Shutdown asks for password"
date: 2011-03-24
forum: Desktop Environments
---

### Post by miutsu on 2011-03-24
Whenever I try to shutdown from GNOME it will ask for a password and say something like "System policy ... users" I don't remember much of it. On KDE there is no shutdown option and I have to log off to shutdown, on Gnome I just put my password in and it works, but I don't want to have to do that so how do I turn this off.

---

### Post by matt_symes on 2011-03-24
Hi

It might be worth looking at the settings in your policykit console file.

Please post the output of

```
cat /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

Please post between code tags. To do this highlight the text and press the # button above where you type. This will make it much easier to read.

Kind regards

---

### Post by miutsu on 2011-03-24
Here's the contents of that file:

```

<?xml version="1.0" encoding="UTF-8"?>                                         
<!DOCTYPE policyconfig PUBLIC                                                  
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"                  
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">        

<!--
Policy definitions for ConsoleKit
-->                              

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

</policyconfig>

```

---

### Post by matt_symes on 2011-03-24
Hi

Is it only you logged in when you have to enter your password to shutdown ?

Also please post the output of 

```
groups
```

Also please post the output of 

```
who
```

Kind regards

---

### Post by miutsu on 2011-03-28
here's groups:
```

miutsu adm dialout cdrom plugdev lpadmin admin sambashare

```and this is the output of who:
```

miutsu   tty7         2011-03-28 11:19 (:0)
miutsu   pts/0        2011-03-28 11:19 (:0)

```

---

### Post by matt_symes on 2011-03-28
Hi

> System policy prevents shutting down the system while multiple users are logged in

Is that the _exact_ error message you are getting ? If not what is the exact error message ?

Kind regards

---

### Post by miutsu on 2011-03-29
When I click on shutdown it produces a small window that states exactly:

```
[B]System policy prevents stopping the
system when other users are logged in[/B]

An application is attempting to perform an action that
requires privleges. Authentication is required to perform this
action.
```


under details it states:
```

Action: org.freedesktop.consolekit.system.stop-multiple-users

```


it provides an "Authenticate" button and a "Cancel" button
Cancel logs out
Authenticate shutsdown, but only if I type my password in first

---

### Post by matt_symes on 2011-03-29
Hi

Yes. I don't know why you are getting that message as you seem to be the only one logged in but there may be a fix for this.

Open a terminal and type

```
sudo nano /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

Enter your password. It will not be echoed to the screen. This is normal.

Look for the section

```
<action id="org.freedesktop.consolekit.system**.stop-multiple-users**">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
```

and change to 

```
<action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>
```

Then look for this section

```
<action id="org.freedesktop.consolekit.system**.restart-multiple-users**">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
```

and change to

```
<action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>
```

Press ctrl + o to save and ctrl + x to exit.

Hopefully that will fix it.

Kind regards

---

### Post by miutsu on 2011-03-30
Thanks, that solved my problem in Gnome, but in KDE the shutdown button still doesn't come up, does this mean that I should re-install KDE or is there some other way to fix it?


Edit: I found out that the reason that I cannot shutdown from KDE is because I am using GDM, is there a way to shutdown from within KDE while still using GDM?

---

### Post by matt_symes on 2011-03-30
Hi

> **miutsu said:**
> Thanks, that solved my problem in Gnome, but in KDE the shutdown button still doesn't come up, does this mean that I should re-install KDE or is there some other way to fix it?

You have both Gnome and KDE desktops installed and select which one to use from GDM ?

> Edit: I found out that the reason that I cannot shutdown from KDE is because I am using GDM,

Where did you read this ? It's been a long time since i had both Gnome and KDE installed in the same installation but i am sure i remember i could shutdown from both.

> is there a way to shutdown from within KDE while still using GDM?

You can do it from a terminal. Open a terminal and type

```
sudo shutdown -h now
```

or to reboot

```
sudo shutdown -r now
```

This could be scripted and added as a launcher as a temporary solution and called with ksudo /path/to/script. You would have to enter your password to shutdown but at least you could  shutdown. A temporary workaround. You would remove sudo if you did this and rely on ksudo.

In the meantime, i will do some research for you.

Kind regards

---

