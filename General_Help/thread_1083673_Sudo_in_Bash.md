---
title: "Sudo in Bash"
date: 2009-03-01
forum: General Help
---

### Post by daved2424 on 2009-03-01
I am trying to write a simple bash file. One of the lines has sudo at the beginning which of course requires the user to input their sudo password. Is there a way to run the script without having to type in the sudo password?

---

### Post by 3rdalbum on 2009-03-01
There is a way to add the script to the "sudoers" file so it won't prompt for a password to run the script. I am not sure of the syntax required for this.

The other method is to change the owner of the script so that root owns it, and then set the "setuid" flag on it. This means that the script will always run as the file's owner, i.e. root.

If you enable Advanced Permissions in Nautilus for the root user (gksudo gconf-editor; then apps > nautilus), then open a root file browser and get Properties for the script, you can change the owner and add the setuid ability.

---

### Post by Nepherte on 2009-03-01
Depending on the situation (for example, if it's a script that has to run at boot or a cron script), you can remove the sudo because it is executed as root already.

---

### Post by daved2424 on 2009-03-01
> **3rdalbum said:**
> If you enable Advanced Permissions in Nautilus for the root user (gksudo gconf-editor; then apps > nautilus), then open a root file browser and get Properties for the script, you can change the owner and add the setuid ability.

Are you able to explain this in a little more detail, I don't quite follow what I have to do.

---

### Post by Slim Odds on 2009-03-01
> **3rdalbum said:**
> There is a way to add the script to the "sudoers" file so it won't prompt for a password to run the script. I am not sure of the syntax required for this.

The "sudoers" files is a **who** file, not a **what** file. Meaning that it specifies **who** has privileges.

You don't usually need to change sudoers, you just add users to the **admin** group (which is already specified in sudoers).

---

### Post by trlkly on 2009-03-01
> **daved2424 said:**
> Are you able to explain this in a little more detail, I don't quite follow what I have to do.

I can give it a shot. 

[list=#][*]Use Alt-F2 to open the Run dialog box.
[*]Type in "gksudo gconf-editor" (without the quotes) and press Enter.
[*]Enter your password (if necessary)
[*]Double click **apps**, scroll down and double-click **nautilus**, and then click preferences.
[*]In the right pane, scroll down until you see show_advanced_permissions. Put a checkmark in its box.[/list]

Now, any time you want to change the setuid of a file, run "gksudo nautilus" (using ALT-F2 again).

----

I personally think it would be easier for you to do it all in a terminal, since you obviously know bash. Just cd to the directory that has the file, and then run the following two commands

```
sudo chown root *file*
sudo chmod ug+s *file*
```

----

Either way you choose, if you ever want to edit the file again, you'll have to open it as root. Run "gksudo gedit */path/to/file*", either in a terminal, or with ALT-F2. (replace gedit with your favorite editor. In a terminal, you could also use sudo instead of gksudo.)

---

### Post by geirha on 2009-03-01
> **3rdalbum said:**
> 
The other method is to change the owner of the script so that root owns it, and then set the "setuid" flag on it. This means that the script will always run as the file's owner, i.e. root.


For security reasons, the setuid bit is not honored for scripts, only binary executables...

---

### Post by daved2424 on 2009-03-01
That's great everyone. Thank you so much for your help.

---

### Post by trlkly on 2009-03-04
> **geirha said:**
> For security reasons, the setuid bit is not honored for scripts, only binary executables...

Seriously? As in, Ubuntu thinks it knows what's best for me and won't let me do what I want to do? That's a Microsoft move, if ever I heard one.

---

### Post by geirha on 2009-03-04
> **trlkly said:**
> Seriously? As in, Ubuntu thinks it knows what's best for me and won't let me do what I want to do? That's a Microsoft move, if ever I heard one.

Not really Ubuntu. Linux in general. And also many other unix implementations disable setuid for scripts due to security holes.

---

### Post by 3rdalbum on 2009-03-04
> **geirha said:**
> For security reasons, the setuid bit is not honored for scripts, only binary executables...

Ahh, well, I learn something new every day. And I couldn't remember how to do setuid on the command-line. And I thought there was an area of "sudoers" that allowed you to specify commands that could be run with sudo, for all users. I guess I fail Ubuntu 101 :-D

Can anyone suggest a better solution than setuid? UNIX people tell me that setuid root must be used sparingly to avoid tempting the crackers :-)

---

