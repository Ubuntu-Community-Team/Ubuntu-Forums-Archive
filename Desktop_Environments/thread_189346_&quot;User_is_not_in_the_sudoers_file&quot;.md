---
title: "&quot;User is not in the sudoers file&quot;"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Clinton on 2006-06-05
I ahve been having a number of problem swith the upgrade from 5.10 - 6.06

I am currently in a position that I can login but then i am presented with a blank screen and nothing happens. Therefore I have trying a number of different commands but I get no response from whatever command I put it. The onyl response I have had is'

user is not in sudoers file. the incident has been reported.

I am at a lost at what to do, any advice would be greatly appreciated

---

### Post by Lunar_Lamp on 2006-06-05
Sorry if this sounds silly, but have you tried adding the user to the sudoers file?

To do this you need to log in as ROOT (e.g. using 'su' in a terminal), and then use the command "visudo".

This is what my sudoers file looks like:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

If that is the same as yours, try adding your user to the admin group ('adduser NAME admin')

---

### Post by localzuk on 2006-06-05
This will not work, as su is disabled...

In order to add a user to the sudoers file, you need to be logged in as the original user that was set up during installation. Then you can use sudo -s in order to get a root terminal.

---

### Post by Clinton on 2006-06-05
[QUOTE=localzuk]This will not work, as su is disabled...

In order to add a user to the sudoers file, you need to be logged in as the original user that was set up during installation. Then you can use sudo -s in order to get a root terminal.[/QUOTE]

Again i get the same problem when doinga sudo command, I tried sudo -s from the original user, but again there is no response I just get a request for my password, which I enter, then nothing..... Just a new command line

---

### Post by americanLoki on 2006-06-05
[QUOTE=Clinton]Again i get the same problem when doinga sudo command, I tried sudo -s from the original user, but again there is no response I just get a request for my password, which I enter, then nothing..... Just a new command line[/QUOTE]

Does the prompt ending also change from # to $ (or the reverse, I'm getting off my overnight shift right now and my brain is a little wonky)?

When typing sudo -s it makes it so every command run after that is automatically run as sudo. The effect is the same as if you had an active root or su account and typed su at the prompt. So if you do type this be careful so as not to cause harm to your system. This goes away once you type exit or close your terminal window.

---

### Post by Clinton on 2006-06-05
[QUOTE=americanLoki]Does the prompt ending also change from # to $ (or the reverse, I'm getting off my overnight shift right now and my brain is a little wonky)?

When typing sudo -s it makes it so every command run after that is automatically run as sudo. The effect is the same as if you had an active root or su account and typed su at the prompt. So if you do type this be careful so as not to cause harm to your system. This goes away once you type exit or close your terminal window.[/QUOTE]

It ends with $, I donät see any #. 

Interestingly, I have just tried to login using the failsafe gnome session, i then get this message

"Could not fing the GNOME installation. Running the failsafe.xterm session instead.

Any reason why it should nät be finding  the installation?

---

