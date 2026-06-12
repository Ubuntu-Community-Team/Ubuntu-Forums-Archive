---
title: "sudo has locked me out... arrr.. where is root!"
date: 2006-01-08
forum: General Help
---

### Post by jezjones on 2006-01-08
Hi everyone, 

I am getting fed up of the problems of having to do everything as sudo.

I changed the permissions on the /home folder as i wanted to allow apache to have access to the folder in the home directory to serve locally.

This resulted in an error when i log in to gnome, 
"$HOME/.dmrc has the wrong permissions.. they should be 644".

After researching this i found that it was due to the changes i made to the home folder.

My problem is that now when i try and sudo to do anything i get an error saying that the user is not in the sudoers group and it will be reported.

SO how can become root to change back the permissions on that folder.
I have tried to login from a terminal as root but i just get an auth failure.
I have also tried to su - but again an auth failure.

Now i am stuck can someone please tell me how i can get out of this fix.
First thing i will do after that is create a root account that you can log in with as this is exactly the point of root or administrator access.

Thanks in advance and if anyone else is having the .dmrc problem is probably down to changing permissions on the home folder.

Jez

---

### Post by Thirsteh on 2006-01-08
If you can use sudo even though it gives you a warning you can do 'sudo bash' to open a root bash. If you can't do that, try to get into whatever GUI you used to remove yourself from the sudo group and put you back in it.

On another topic, if you want something to access a folder, you don't necessarily need to chmod EVERYTHING in that folder to ..say 0777, just do 'chmod 0777 /home/myuser', not 'chmod -R 0777 /home/myuser' or 'chmod 0777 *' inside your home folder.

Your problem there is pretty easy to fix, just do 'chmod 0644 /home/youruser/.dmrc'.

If it's all absolutely hopeless, you can gain root access by running the Linux kernel in single user mode, but if you don't know how to do that I strongly recommend you read some documentation on it. Google is your friend.

---

### Post by jezjones on 2006-01-08
HI there,

THanks for your response however it is not as easy as you suggest.

The sudoers message is an error not a warning, so that goes nowhere.
I didnt remove myself from the sudoers group, this is a symptom of having changed the permissions on the home folder. 

Additionally there is no way i can be re-added to the sudoers group with out sudo!!! 
catch 22.

I have now changed the permissions on the .dmrc file so that error no longer comes up... 


I will restart now in single user mode, i am familiar enough with that.

I appreciate your help, i think i will be able to fix it now, i have not done much with user account stuff like this. My experience of linux is that you use the root account to fix problems like this.

I still dont understand why the new batch of linux distros seem to be obsessed with getting rid of it! The lack of a root account has only made things more complex by juggling permissions more widely.

Thanks again

Jez

---

### Post by Tuf on 2006-01-08
I am not sure this will help you right now or until you fix the sudo problem.

But if you "sudo passwd root" it will ask you for a password twice. You will then be able to log in as root when you like. You can deactivate the root account with "sudo passwd root -l"

---

### Post by Azriphale on 2006-01-08
You can gain root access in other ways. You can try booting the recovery mode kernel, or using the install cd, and booting "rescue"

At the grub boot screen, select the second option (one with "(recovery mode)" on the end). Something like:

```
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
```
press enter to boot, and it should dump you in a root shell. Although I don't know if it does if the root password is not set. I guess it should. This is the single user mode.

Don't go hitting any buttons on your keyboard. Things Will break. 

While you are in the single user mode, you might want to go:
```
passwd root
```
to set a root password. You can then do the rest after rebooting, by logging in and running just running "su", entering your new root password when asked.

Go to the "/home" directory and reverse what you previously did. I don't know what it is that you did, but you might want to do:
```
chown -R your_user:your_user ./your_user
```
substitution "your_user" for your username
That will restore ownership of your home directory to you.

Again, I don't know what you did, if you used chmod. but you might also want to try the command that Thirsteh suggested:
```
chmod 0644 /home/youruser/.dmrc
```

---

### Post by Thirsteh on 2006-01-08
[QUOTE=Tuf]I am not sure this will help you right now or until you fix the sudo problem.

But if you "sudo passwd root" it will ask you for a password twice. You will then be able to log in as root when you like. You can deactivate the root account with "sudo passwd root -l"[/QUOTE]

Scheiss, forgot about that. Yeah, that's an option as well *blush*.

---

### Post by gnu2tux on 2006-01-08
Why don't you just sudo once then?

$sudo bash
Password: <foo>
# 

^
|
nice shiny root prompt until you log out!

Ali Ross

---

### Post by Azriphale on 2006-01-08
Unfortunately, none of that will work until at least the sudo problem is fixed, which will have to be done as root, which means single user mode. (I am assuming that a root password has not yet been set). This can be done in single user mode, then you can restart and use 
$ su
to get a root console.

"sudo" is returning an error saying the user does not have permission to use it.

---

### Post by Thirsteh on 2006-01-08
[QUOTE=gnu2tux]Why don't you just sudo once then?

$sudo bash
Password: <foo>
# 

^
|
nice shiny root prompt until you log out!

Ali Ross[/QUOTE]

[QUOTE=Thirsteh]If you can use sudo even though it gives you a warning you can do 'sudo bash' to open a root bash. If you can't do that, try to get into whatever GUI you used to remove yourself from the sudo group and put you back in it.[/quote]

:cool: way ahead of ya mate.

[QUOTE=Azriphale]Unfortunately, none of that will work until at least the sudo problem is fixed, which will have to be done as root, which means single user mode. (I am assuming that a root password has not yet been set). This can be done in single user mode, then you can restart and use 
$ su
to get a root console.

"sudo" is returning an error saying the user does not have permission to use it.[/QUOTE]

Read the current posts before you start posting ;)

---

### Post by Azriphale on 2006-01-08
[QUOTE=jezjones]My problem is that now when i try and sudo to do anything i get an error saying that the user is not in the sudoers group and it will be reported.[/QUOTE]

[QUOTE=jezjones]The sudoers message is an error not a warning, so that goes nowhere.[/QUOTE]

[QUOTE=jezjones]I have now changed the permissions on the .dmrc file so that error no longer comes up... [/QUOTE]
I assumed this was referring to the error that referred to .dmrc
[QUOTE=jezjones]"$HOME/.dmrc has the wrong permissions.. they should be 644".[/QUOTE]
I also assumed that this meant that the sudo error was not fixed:
[QUOTE=jezjones]I will restart now in single user mode, i am familiar enough with that.[/QUOTE]

Bad assumptions, I guess? perhaps also not having the page completely up to date.....
:mad:
:)

---

### Post by Thirsteh on 2006-01-08
Hehe I was actually referring to the part where I recommend trying out single user mode, but oh well. :D Cheers.

---

### Post by TimelessRogue on 2006-01-08
Hey, Thirsteh ... chill, man!  Everybody's trying to help and I have noticed that sometimes there may be a couple of us posting the same info and pretty much the same moment in time ... causes a flux in the universe so that we end up with semi-cloned posts ...

Long as the problem got fixed ...;)

---

### Post by jezjones on 2006-01-08
Thanks for so much interest in this thread!

I think between you i have not only the immediate fix for this, which is going in as single user and changing the permissions for the home folder, but some other fixes once i have sudo back.
I took a look at /etc/sudoers and it seems that my ordinary user account was not in the group that is allowed to sudo. I didnt make any changes to this account but was messing with the user group yesterday so this was probably the cause.
I added the normal user to the right group and now i can log in as normal error free.

Now i can look at the other suggestions you made and maybe i will create a root account, but i guess there is no need for that as long as i am happy enough with single user mode. I started linux without a gui so i am not too concerned about that, and with this forum and google handy it should be all good.

Thanks for all your suggestions, 

Jez

---

### Post by Azriphale on 2006-01-08
you don't need to create a root account, only to set the password.

Now that you have everything working again, just run:
```
sudo passwd root
```
it will ask you to enter and verify a password, and your root account will be working.

---

### Post by aysiu on 2006-01-08
By the way, a fix for your original problem (rather than changing permissions/ownership of the /home folder) would be creating a folder within your /home folder for Apache access and then symlinking it (middle-click-drag it and select **link here**) to /var/www.

---

### Post by jezjones on 2006-01-09
Thanks for the suggestion, but unfortunately apache et al is now on the back burner as this issue is coming up again.

I have removed apache and php as i need to recompile to add support for mysql... not sure why i should need to do this since it comes from apt, but there you go.

I use 3ddesktop to switch between desktops, cos its pretty.
Having booted into gnome without problem when i try and run this it gives an error ;-

> Attempting to start 3ddesktop server.
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

SO i looked this up and it seems to be a permission error on the /dev/dri folder. Yes this seemed odd to me too, that this should appear seemingly from nowhere.

SO i looked at the possbile solutions and since the device in this folder called card0 was owned by root and the group was video, i thought i would add my normal user account to video to solve it.

THis has now brought back the sudoers problem.

I thought i had an idea of how permissions and groups worked, but all the issues i've brought up in this thread seem to suggest that when you add a user to one group it is removed from another.... surely this cannot be right.

I am now wondering what else has be screwed by one change in permissions in the home folder, which is now affecting other stuff that is no-where near that.

I have gone to my home folder and found the hidden folder called .3ddesktop and it is owned by the normal user with permissions of 755 which should allow it to be accessed.

I am confused and worried for the future stability of my machine.

When i changed the original permissions on the home folder it was not with -R so the damage should have been fairly limited.

Any suggestions?

Thanks 
Jez

---

### Post by Azriphale on 2006-01-09
Its so nice to be home. I have to use a Win98 machine at work...

Now I am able to look at my /etc/group and /etc/sudoers files to help you.

This is probably a bit of a dirty way of fixing it, but I think it should work.

Log in as root.

first your /etc/group file.

open it up in a text editor, and you will find a whole lot of lines like so:
```
floppy:x:25:some_user,hal
tape:x:26:
sudo:x:27:
audio:x:29:some_user
```

where I have "some_user", your username should show up. It should appear on all of these following lines (in what I think is a default setup):
```

dialout
cdrom
floppy
audio
dip
video
plugdev
lpadmin
scanner
admin

```
If it is missing from any of those, add it, like in the examples above.

Also make sure there is a line that reads:
```

some_user:x:????:

```
replace ???? with your UID. By default this is 1000 for the first user created (during the install). It should be there already, otherwise there would be big problems. Which, I guess there are, actually.

Save the file and exit.

Now for the sudo problem

Now, type the command "visudo" into the console (logged in as root).

make it look like this:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

save and exit the editor.

Your user has been made a member of the admin group once again, so you should have sudo privelidges now.

Attached are my /etc/group and sudoers files

---

