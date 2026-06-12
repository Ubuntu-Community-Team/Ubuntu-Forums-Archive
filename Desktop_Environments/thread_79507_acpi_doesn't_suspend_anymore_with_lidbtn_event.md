---
title: "acpi doesn't suspend anymore with lidbtn event"
date: 2005-10-20
forum: Desktop Environments
---

### Post by e45rpm on 2005-10-20
For some reason, on my laptop, closing the lid doesn't invoke a sleep state.  It was working, but it now doesn't work, and I can't figure out why.  I can invoke it manually through the "log out" menu option, so the sleep function works, it's just the laptop lid button event doesn't trigger it.

Here is my /etc/acpi/events/lidbtn file, which I changed the last line from lid.sh to sleep.sh
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/sleep.sh
```

I guess my question is, is the 'event' line wrong?  I know that the file & path that I am looking for is: /proc/acpi/button/lid/LID0/state where 'state' is the file.  If the event line isn't wrong, what else could the problem be?

---

### Post by kashms on 2005-10-20
I seem to have the same problem. It was working before and now it is not! Maybe because of an update, I don't know?

---

### Post by ranf on 2005-10-20
[QUOTE=e45rpm]For some reason, on my laptop, closing the lid doesn't invoke a sleep state.[/QUOTE]

In a terminal do:
```
sudo tail -f /var/log/acpid
```
then close the lid and look what new text lines appeared.

---

### Post by e45rpm on 2005-10-20
Here's what I got.  I don't understand what exactly is going on though.

```
[Thu Oct 20 15:06:21 2005] completed event "button/lid LID0 00000080 0000000c"
[Thu Oct 20 15:06:21 2005] received event "button/lid LID0 00000080 0000000d"
[Thu Oct 20 15:06:21 2005] notifying client 6778[111:111]
[Thu Oct 20 15:06:21 2005] completed event "button/lid LID0 00000080 0000000d"
[Thu Oct 20 15:06:32 2005] received event "button/lid LID0 00000080 0000000e"
[Thu Oct 20 15:06:32 2005] notifying client 6778[111:111]
[Thu Oct 20 15:06:32 2005] completed event "button/lid LID0 00000080 0000000e"
[Thu Oct 20 15:06:32 2005] received event "button/lid LID0 00000080 0000000f"
[Thu Oct 20 15:06:32 2005] notifying client 6778[111:111]
[Thu Oct 20 15:06:32 2005] completed event "button/lid LID0 00000080 0000000f"
[Thu Oct 20 15:06:37 2005] received event "button/lid LID0 00000080 00000010"
[Thu Oct 20 15:06:37 2005] notifying client 6778[111:111]
[Thu Oct 20 15:06:37 2005] completed event "button/lid LID0 00000080 00000010"
[Thu Oct 20 15:06:45 2005] received event "button/lid LID0 00000080 00000011"
[Thu Oct 20 15:06:45 2005] notifying client 6778[111:111]
[Thu Oct 20 15:06:45 2005] completed event "button/lid LID0 00000080 00000011"

```

---

### Post by kashms on 2005-10-22
I just tried to execute the sleep script in a terminal:

```

$ /etc/acpi/sleep.sh
/dev/mem: Permission denied
/dev/mem: Permission denied
/dev/mem: Permission denied

```
and putting sudo infront doesn't do anything! 

Suspend to RAM still works from the logout menu, though.

I have a suspicion that playing with gnome-power-manager changed some permissions.

The permission settings for /dev/mem looks a bit special (?!):

```

$ ls -l /dev/mem
crw-r-----  1 root kmem 1, 1 2005-10-22 13:43 /dev/mem

```
Can I give my user permissions for this or would that be dangerous?

---

### Post by kashms on 2005-10-22
When I have gnome-power-manager running closing the lid actually works now. The reason I wasn't using it before is that I felt it was a bit buggy (sometimes opening the lid immediately triggers another suspend). I'll try uninstalling it to see if it restores the original default behaviour, which worked perfectly.

---

### Post by ranf on 2005-10-22
[QUOTE=e45rpm]Here's what I got.  I don't understand what exactly is going on though.

```

[Thu Oct 20 15:06:21 2005] received event "button/lid LID0 00000080 0000000d"
[Thu Oct 20 15:06:21 2005] notifying client 6778[111:111]

```[/QUOTE]
The Acpi daemon reveives an event which the event= rule in your lidbtn should match perfectly.

After doing the change did you restart acpid?
```
sudo /etc/init.d/acpid restart
```

---

### Post by e45rpm on 2005-10-23
Here's what I get after I do /etc/init.d/acpid restart

```
[Sun Oct 23 00:49:39 2005] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Oct 23 00:49:39 2005] END HANDLER MESSAGES
[Sun Oct 23 00:49:39 2005] action exited with status 0
[Sun Oct 23 00:49:39 2005] completed event "button/lid LID0 00000080 00000002"
[Sun Oct 23 00:51:16 2005] exiting
[Sun Oct 23 00:51:18 2005] starting up
[Sun Oct 23 00:51:18 2005] 50 rules loaded
[Sun Oct 23 00:51:21 2005] client connected from 6764[111:111]
[Sun Oct 23 00:51:21 2005] 1 client rule loaded
[Sun Oct 23 00:51:40 2005] received event "button/lid LID0 00000080 00000003"
[Sun Oct 23 00:51:40 2005] notifying client 6764[111:111]
[Sun Oct 23 00:51:40 2005] executing action "/etc/acpi/sleep.sh"
[Sun Oct 23 00:51:40 2005] BEGIN HANDLER MESSAGES
[Sun Oct 23 00:51:40 2005] END HANDLER MESSAGES
[Sun Oct 23 00:51:40 2005] action exited with status 0
[Sun Oct 23 00:51:40 2005] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID0 00000080 00000003"
[Sun Oct 23 00:51:40 2005] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Oct 23 00:51:40 2005] END HANDLER MESSAGES
[Sun Oct 23 00:51:40 2005] action exited with status 0
[Sun Oct 23 00:51:40 2005] completed event "button/lid LID0 00000080 00000003"
[Sun Oct 23 00:51:44 2005] received event "button/lid LID0 00000080 00000004"
[Sun Oct 23 00:51:44 2005] notifying client 6764[111:111]
[Sun Oct 23 00:51:44 2005] executing action "/etc/acpi/sleep.sh"
[Sun Oct 23 00:51:44 2005] BEGIN HANDLER MESSAGES
[Sun Oct 23 00:51:45 2005] END HANDLER MESSAGES
[Sun Oct 23 00:51:45 2005] action exited with status 0
[Sun Oct 23 00:51:45 2005] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID0 00000080 00000004"
[Sun Oct 23 00:51:45 2005] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Oct 23 00:51:45 2005] END HANDLER MESSAGES
[Sun Oct 23 00:51:45 2005] action exited with status 0
[Sun Oct 23 00:51:45 2005] completed event "button/lid LID0 00000080 00000004"
```

Also, I can't invoke sleep mode with /etc/acpi/sleep.sh
I can only invoke sleep mode from the gnome menu: Logout->Suspend
Is there a way to find out what command gnome's logout menu item is using?

Thanks

---

### Post by ranf on 2005-10-23
[QUOTE=e45rpm]Here's what I get after I do /etc/init.d/acpid restart

```
[Sun Oct 23 00:51:40 2005] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID0 00000080 00000003"

```[/QUOTE]
This one looks interesting. Something is calling lm_lid.sh. Look into the other files in /etc/acpi/events if there is another one claiming to be responsible for "button/lid".

> 
Also, I can't invoke sleep mode with /etc/acpi/sleep.sh


If that doesn't work it also will not work from acpid. Have a look at "/etc/default/acpi-support".

---

### Post by e45rpm on 2005-10-24
> If that doesn't work it also will not work from acpid. Have a look at "/etc/default/acpi-support".

What should I be looking for?

---

### Post by ranf on 2005-10-24
[QUOTE=e45rpm]What should I be looking for?[/QUOTE]
```
grep SLEEP /etc/default/acpi-support
```

And this would also be interesting:
```
cd /etc/acpi/events/
grep lm_lid *
```

---

### Post by e45rpm on 2005-10-25
```
grep SLEEP /etc/default/acpi-support
```

gives me:

```
ACPI_SLEEP=true
ACPI_SLEEP_MODE=mem
```

and,

```
cd /etc/acpi/events/
grep lm_lid *
```

gives me:

```
lm_lid:action=/etc/acpi/actions/lm_lid.sh %e
```

Is there a way to tell what Gnome is using to suspend the computer?

I also found this thread, but it hasn't been so active as of late.
[http://www.ubuntuforums.org/showthread.php?t=71930](http://www.ubuntuforums.org/showthread.php?t=71930)

---

### Post by ranf on 2005-10-25
```
grep SLEEP /etc/default/acpi-support
ACPI_SLEEP=true
ACPI_SLEEP_MODE=mem
```

fine.

```
cd /etc/acpi/events/
grep lm_lid *
lm_lid:action=/etc/acpi/actions/lm_lid.sh %e
```

You could try running:
```
sudo /etc/acpi/actions/lm_lid.sh
```

> Is there a way to tell what Gnome is using to suspend the computer?

I don't know.

---

### Post by e45rpm on 2005-10-26
```
sudo /etc/acpi/actions/lm_lid.sh
```
that just tells me that laptop mode is alreay active.

```
/etc/acpi/sleep.sh
```
This just doesn't give me anything, and the computer doesn't do anything either.

grr, despite it being simply an inconvienience, it's still frustrating.

---

### Post by ranf on 2005-10-31
[QUOTE=e45rpm]
Is there a way to tell what Gnome is using to suspend the computer?
[/QUOTE]
By accident I found this in /etc/gdm/gdm.conf:
```

# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate

```

---

### Post by e45rpm on 2005-11-01
I've been trying to figure out how to use this new knowledge to get my laptop to go into sleep mode when I close the lid on my laptop.  So far I've only tried putting the new line into my /etc/acpi/events/lidbtn file like so:

```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/sleep.sh
action="/usr/sbin/pmi action sleep"
```

where the new 'action' line has gdm's "/usr/sbin/pmi action sleep" command.  Sadly, it didn't work.

---

### Post by e45rpm on 2005-11-04
would it help if I followed the instructions on this thread?
[http://ubuntuforums.org/showpost.php?p=428602&postcount=14](http://ubuntuforums.org/showpost.php?p=428602&postcount=14)

I think the biggest thing that pertains to me is what this command would do:
```
Add: acpisleep=s3bios in grub.conf
```

---

### Post by ranf on 2005-11-04
[QUOTE=e45rpm]
where the new 'action' line has gdm's "/usr/sbin/pmi action sleep" command.  Sadly, it didn't work.[/QUOTE]
How about trying pmi manually:
```
sudo pmi action sleep
```

I had a closer look at pmi: it does some checks, creates a lock file and then calls /etc/acpi/sleep.sh.

---

### Post by ranf on 2005-11-04
[QUOTE=e45rpm]would it help if I followed the instructions on this thread?
[http://ubuntuforums.org/showpost.php?p=428602&postcount=14](http://ubuntuforums.org/showpost.php?p=428602&postcount=14)

I think the biggest thing that pertains to me is what this command would do:
```
Add: acpisleep=s3bios in grub.conf
```[/QUOTE]
That would be: acpi_sleep=s3_bios in /boot/grub/menu.lst.

---

### Post by e45rpm on 2005-11-06
```
That would be: acpi_sleep=s3_bios in /boot/grub/menu.lst.
```

But what would this do for me if I added it to my grub settings?

---

### Post by Cannedbread on 2005-11-23
Hey dudes, i was having this problem too, but i think i have a fix.

[http://www.ubuntuforums.org/showthread.php?t=94204](http://www.ubuntuforums.org/showthread.php?t=94204)

---

### Post by ranf on 2005-11-24
[QUOTE=Cannedbread]Hey dudes, i was having this problem too, but i think i have a fix.

[http://www.ubuntuforums.org/showthread.php?t=94204](http://www.ubuntuforums.org/showthread.php?t=94204)[/QUOTE]
I have read your post. Your fix is not very elegant. There are three if's in this line. Two of them test if the 1st parameter is `force' or `sleep'.
A simple:
/etc/acpi/sleep.sh sleep
in the `action=' line of lidbtn should have worked too.

---

