---
title: "Openbox Menu -- Can't shutdown or restart"
date: 2012-12-29
forum: Desktop Environments
---

### Post by ChristopherAdams on 2012-12-29
I've recently installed Ubuntu's mini.iso with Openbox and Simple Login Manager, on an Acer Aspire One netbook. I want to be able to shutdown and restart from the Openbox menu, but I can't get it to work. There are a number of threads with solutions here on the Ubuntu Forums, but none of them has worked for me.

Here is the XML I have in my 'menu.rc' file:

```
<item label="Restart">
    <action name="Execute"> 
       <prompt>Are you sure you want to Restart?</prompt> 
       <command>sudo shutdown -r now</command>
    </action>
  </item>  <item label="Shutdown">
    <action name="Execute">
    <prompt>Are you sure you want to Shutdown?</prompt> 
       <execute>sudo shutdown -h now</execute>
    </action>

```

In place of the command 'sudo shutdown -h now', I have used 'sudo /sbin/shutdown -h now', 'sudo /sbin/halt', 'gksu shutdown -h now', 'x-terminal-emulator -t sudo shutdown -h now', and even 'x-terminal-emulator -t shutdown -h now'. Nothing works.

My visudo file looks like this:
```

# User privilege specification
root	ALL=(ALL:ALL) ALL
%shutdown ALL=(root)NOPASSWD: /sbin/reboot
%shutdown ALL=(root)NOPASSWD: /sbin/halt
%shutdown ALL=(root)NOPASSWD: /sbin/shutdown

%admin ALL=(ALL)ALL
%admin ALL=NOPASSWD: /sbin/reboot, /sbin/halt, /sbin/shutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

```

Any help anyone could give me would be appreciated.

Thanks, 
Chris Adams.

---

### Post by ChristopherAdams on 2013-03-09
If anyone is searching for the solution to this problem, here it is (from 'Nelz' a moderator on the 'Linux Format' forum): 
  "I susepct that sudo wants a password but doesn't have a terminal to ask for it. You could try gksudo instead, or use visudo to edit /etc/sudoers to allow /sbin/shutdown to be run without a password. 	 ```
visudo
```  Then add  ```
yourusername ALL = NOPASSWD: /sbin/shutdown
```" 
 (Thanks again, Nelz! -C.A.)

---

