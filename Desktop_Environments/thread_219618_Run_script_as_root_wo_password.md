---
title: "Run script as root w/o password?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-20
How do I run a script as root, without giving it my password?

I wrote a quick script to shutdown/reboot my pc that replaces the usual method due to a minor bug in my implementation of xgl/compiz.  The script is this:

```
#!/bin/sh
# for a nice icon use icon from /usr/share/icons/Human/48x48/apps

echo "Type 's' and press enter to shutdown, 'r' and enter to reboot, or any other key to cancel"

read INPUT

if [ "$INPUT" = "s" ]; then
sudo shutdown -h now

elif [ "$INPUT" = "r" ]; then
sudo reboot

else exit

fi

```

It is currently located in /home/user/scripting.  I tried:

chown root shutdown.sh

followed by:

chmod 4755 shutdown.sh

This doesn't work.  I just want the script to not ask me for a password when I shutdown/reboot via this method.  Please help!

---

### Post by Ramses de Norre on 2006-07-20
Add a line like this to /etc/sudoers:
```
ramses ALL= NOPASSWD: /usr/sbin/firestarter
```
This line gives user ramses permissions to run firestarter without giving a password.

And for the script: why don't you set the input for shutdown to h, then you can change the rest of the script to just ```
sudo shutdown -$INPUT now
```

---

### Post by jayemef on 2006-07-20
I'm fairly certain that ubuntu gives users access to shutdown/reboot/halt by default, or am I mistaken? Did you try running this without the sudos? Otherwise the comment above should work.

---

### Post by geco on 2006-07-20
from a terminak, to edit your sudoers file
```

sudo visudo

```

theno you can set something like this
```

 /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

Cmnd_Alias HALT = /sbin/halt -p, /sbin/shutdown -h now
Cmnd_Alias REBOOT = /sbin/reboot, /sbin/shutdown -r now

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL=NOPASSWD: HALT, REBOOT

```
to save it type
```

ESC
wq
ENTER

```

since you are member of admin group (you can check it typing "id" from a terminal) now you can shutdown your computer typing
```

halt

```
and reboot it typing
```

reboot

```

...anyway you can edit /etc/sudoers with any text editor but you need root privileges :)

byebye

---

### Post by Ramses de Norre on 2006-07-20
After setting such a line in /etc/sudoers you still need to enter ```
**sudo** halt
```
And you need to be root to shutdown the machine, this is a security setting.
You can shutdown the pc as regular user through the GUI though, but I don't know how this works.

---

### Post by Lunar_Lamp on 2006-07-20
> And you need to be root to shutdown the machine, this is a security setting.
You can shutdown the pc as regular user through the GUI though, but I don't know how this works.

Indeed - that was why I was sure it was possible to do what I wanted.

---

### Post by geco on 2006-07-20
> **Ramses de Norre said:**
> After setting such a line in /etc/sudoers you still need to enter ```
**sudo** halt
```
And you need to be root to shutdown the machine, this is a security setting.
You can shutdown the pc as regular user through the GUI though, but I don't know how this works.

You're right. I forgot that I sat up an alias to avoid this.
I edited my .bashrc file adding th lines
```

alias halt='sudo halt -p'
alias reboot='sudo reboot'

```

well, actually I use .bash_aliases file, but there is no much difference :)

Anyway I'm able to reboot and halt my computer from terminal, no need to be root with my sudoers file (and my aliases!)

byebye

---

### Post by Lunar_Lamp on 2006-07-20
This is the only problem I have with linux really.  There is so much customisation possible, it's so easy to forget what you have customised.  By virtue of windows being less friendly to customisation, there is less need to track what you have changed.

---

### Post by Ramses de Norre on 2006-07-20
Now that's really a luxuery problem!

---

### Post by Lunar_Lamp on 2006-07-20
Indeed, but I was wondering if there was a way to solve it.  No real ideas yet, other than writing a "Giant Configuration Tracker", which acts as a GUI to every config file on the system, and is able to track changes etc, and relate them to each other, magically reading your mind with your intentions... as you can see, I have no idea how to solve the problem, or even know if it is possible to solve.

---

### Post by geco on 2006-07-20
exercise, exercise, exercise... when you use linux it's not so hard to recover what you did ;)
you will know where - more or less - thing must be :)
anyway in this case it's only my memory's fault :D

---

### Post by Lunar_Lamp on 2006-07-20
That's my point - it would make linux more user-friendly if someone was able to invent a way that we didn't need to use our memory for this kind of thing (unless of course we wanted to).  If I could think of a way to go about doing it, I would probably start coding on it - heh.

---

### Post by HighInBC on 2008-06-09
Here is what I do when I want to allow a single root command to be ran without challenge:

[LIST=1]
[*]Create a new ssh keypair just for this one command
[*]Go to the target computer, be it your localhost or another system and open the /root/.ssh/authorized_keys file
[*]You may need to create /root/.ssh/authorized_keys if it does not already exist, if you do then you need to set /root/.ssh to 700 and authorized_keys to 600 with the chmod command
[*]On its own line place: command="shutdown -h now" <your public key here>
[*]Now you should be able to do: ssh -i <private key> root@<host>
[*]The command should run as root without any challenge, that private key can execute that root command and only that root command.
[*]To run a command on the same machine just use "localhost" as your host
[/LIST]

I have a whole folder full of launchers to run updates and different hosts I maintain, and to start and stop different services. It is rather handy, and very secure as the keys cannot be used for other commands.

---

