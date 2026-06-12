---
title: "execute command before lightdm starts"
date: 2013-01-01
forum: Desktop Environments
---

### Post by zerocooler on 2013-01-01
Hello
I am trying to execute some commands before and after llightdm starts

This is how part of my  /etc/init/lightdm.conf looks like:

```

    exec irsend SEND_ONCE AVR260 KEY_POWER &
    sleep 10 ;
    exec lightdm &
    sleep 30 ;
    exec irsend SEND_ONCE AVR260 KEY_POWER2


``````
irsend SEND_ONCE AVR260 KEY_POWER
```is used to turn on my amplituner
then i wanted to add some sleep to make sure it is up
after that lightdm should start
and when all services start from ~/.config/autostart
amplituner should be turned off by command 
```
exec irsend SEND_ONCE AVR260 KEY_POWER2 
```So this is how it looks like now
On reboot amplituner starts - that part works fine.
On TV screen i am stuck on shell login screen and nothing hapends further
Then amplituner shuts down as expected.
So why i have problem with that "exec lightdm" command?
How can i modify this script to do what i want?

Happy New Year to everyone

---

### Post by steeldriver on 2013-01-01
I think your issue is the use of 'exec' - that *replaces* the current (shell) process so afaik the script will never reach the following commands?

TBH I'm not sure that putting these commands directly in /etc/init/lightdm.conf is the 'right' way to do what you want - there may be some predefined hooks in the upstart mechanism for that kind of thing (greeter-setup-script maybe?)

---

### Post by zerocooler on 2013-01-01
well my knowledge of ubuntu is rather minimal so far.
I struggle with each problem - small stepps so far.

lightdm was the only way i could think of.
if exec command interrupts anything why last one is executed?
I mean amplituner turns off as desired.
just middle part seems broken
exec lightdm

:confused:

---

### Post by zerocooler on 2013-01-01
Ok then seems im doing it wrong way.
Command for turning on amplituner:

```
irsend SEND_ONCE AVR260 KEY_POWER
```

i need to start that after lirc starts and before lightdm is called.
What would it be the best place to put that or what would be best way to call it?
If anyone have idea preety please help me - i struggle with it whole afternoon

---

### Post by Lars Noodén on 2013-01-01
Wouldn't you use the 'pre-start' stanza in lightdm.conf to run a script before lightdm starts?  Again, avoid 'exec'

---

