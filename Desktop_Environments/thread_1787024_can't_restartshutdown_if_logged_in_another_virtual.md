---
title: "can't restart/shutdown if logged in another virtual terminal"
date: 2011-06-20
forum: Desktop Environments
---

### Post by cccc on 2011-06-20
hi

I can't restart/shutdown my Natty with Gnome if I'm logged as root in another virtual terminal.
For example, if I click on System - "Shut Down" I get the Gnome Login Mask instead of simple shutdown the machine.
Howto allow this?

---

### Post by cccc on 2011-06-21
I've add the following lines in /etc/sudoers:```

myuser ALL=(root)NOPASSWD:/sbin/reboot
myuser ALL=(root)NOPASSWD:/sbin/halt
myuser ALL=(root)NOPASSWD:/sbin/shutdown
```but it doesn't help.

---

### Post by cccc on 2011-06-25
I solved this problem now!

Open /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy and change the following:```

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
      [B]<!--<allow_active>auth_admin_keep</allow_active>-->
      <allow_active>yes</allow_active> [/B]       
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
      [B]<!--<allow_active>auth_admin_keep</allow_active>-->
      <allow_active>yes</allow_active>[/B]
    </defaults>
  </action>

</policyconfig>
```

---

