---
title: "bothersome root terminal behavior"
date: 2006-04-25
forum: Desktop Environments
---

### Post by dannemil on 2006-04-25
For some reason, when I invoke a root terminal now I get a terminal window that takes about 3 minutes before a prompt appears. A regular, user terminal does not have this problem. Is there any way to reinstall the terminal-emulator to stop this bizarre behavior or otherwise diagnose why it takes so long to get a prompt to appear in the window?

I am running breezy.  -- Jim

---

### Post by Sparkalo on 2006-04-25
It sounds to me like something's the matter with gksu.  I'm not too knowledgable in the area, but what happens if you try to run:
```
gksu /usr/bin/x-terminal-emulator
```
in a normal terminal?

---

### Post by dannemil on 2006-04-25
[QUOTE=Sparkalo]It sounds to me like something's the matter with gksu.  I'm not too knowledgable in the area, but what happens if you try to run:
```
gksu /usr/bin/x-terminal-emulator
```
in a normal terminal?[/QUOTE]

If I execute: ```
gksu /usr/bin/x-terminal-emulator
``` from a normal terminal, it asks me for the root password, then I get

Failed to run /usr/bin/x-terminal-emulator:
 Wrong password.

The problem with this is that I know that the root password is correct, and that I am typing it correctly, etc.

---

### Post by dannemil on 2006-04-26
[QUOTE=Sparkalo]It sounds to me like something's the matter with gksu.  I'm not too knowledgable in the area, but what happens if you try to run:
```
gksu /usr/bin/x-terminal-emulator
```
in a normal terminal?[/QUOTE]

Here is one more piece of diagnostic information. When I run the following from a user terminal

```
gksudo /usr/bin/x-terminal-emulator
```

The root terminal will now open with a prompt, but I get the follwing error messages:


[I](gnome-terminal:12241): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

(gnome-terminal:12241): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: asse rtion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
[/I]

So instead of opening the root terminal with ```
gksu /usr/bin/x-terminal-emulator
```, 

I used ```
gksudo /usr/bin/x-terminal-emulator
```.

```
gksudo /usr/bin/x-terminal-emulator
``` 

still gives me the error message that the password is incorrect.

Thanks, Jim

---

### Post by Ramses de Norre on 2006-04-26
By default gksudo requires your user password.

---

### Post by Sparkalo on 2006-04-26
> problem with this is that I know that the root password is correct, and that I am typing it correctly, etc.

Then you set your root password?  The password for your default user (and the one you enter for the sudo command) is NOT the same as your root user password in Ubuntu.  To test to see if it's been set try running the **su** command and logging in as root.  If the password you thought was root fails, you probably need to set your root password.

Seeing as I don't know the way to do this in Breezy (am currently testing Dapper), I'm not going to try to tell you how, besides, there's a great little workaround that should solve your problems.

Execute this in a terminal:
```
sudo -i
```
The above should give you a root terminal without using su.

If you want to create a launcher, right click on gnome-panel -> add to panel -> custom application launcher (at the top of the window)

Then Enter whatever you want as the name and such, the command is still sudo -i and make sure that you have "run in terminal" checked. (in case it's different in Breezy, I can't remember, check the screen attatched).

Have fun!

---

### Post by steve.carren on 2006-04-27
I'm having the same problem. I recently installed updates on a couple of machines and the problems started happening after that.

I have not found a solution yet either.

---

