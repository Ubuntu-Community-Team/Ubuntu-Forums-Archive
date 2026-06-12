---
title: "need help, quick! =/"
date: 2005-07-30
forum: Desktop Environments
---

### Post by da_unruled on 2005-07-30
well, I was trying to install the FTP server using this guide
[http://ubuntuforums.org/showthread.php?t=51611&highlight=ftp](http://ubuntuforums.org/showthread.php?t=51611&highlight=ftp)
now, I was at the point where I made the dir's and set the new home folder for the Ftpuser....
then linux starting acting funny so I rebooted, and it appears I am now stuck in that ftpuser account without admin priviledges (I appear to not be able to -sudo- anything)

if I try to go system-> admin-> users it says:
enter password., so I type the password for my regular account(the ftp account has the same pass. anyway)
then it says 

```
failed to run users-admin
child terminated with 1 status
```

all my favourites/customised stuff is now not there, (eg. back to default resolution etc etc). How can I switch back?

---

### Post by bored2k on 2005-07-30
[QUOTE=da_unruled]well, I was trying to install the FTP server using this guide
[http://ubuntuforums.org/showthread.php?t=51611&highlight=ftp](http://ubuntuforums.org/showthread.php?t=51611&highlight=ftp)
now, I was at the point where I made the dir's and set the new home folder for the Ftpuser....
then linux starting acting funny so I rebooted, and it appears I am now stuck in that ftpuser account without admin priviledges (I appear to not be able to -sudo- anything)

if I try to go system-> admin-> users it says:
enter password., so I type the password for my regular account(the ftp account has the same pass. anyway)
then it says 

```
failed to run users-admin
child terminated with 1 status
```

all my favourites/customised stuff is now not there, (eg. back to default resolution etc etc). How can I switch back?[/QUOTE]
 I don't have an aswer to your question, but here's a suggestion: Next time you have a problem when following a thread on our forums, make sure you post your problem on _that_ thread. Support will be much better.

---

### Post by da_unruled on 2005-07-30
[QUOTE=bored2k]I don't have an aswer to your question, but here's a suggestion: Next time you have a problem when following a thread on our forums, make sure you post your problem on _that_ thread. Support will be much better.[/QUOTE]
I understand.. I didn't want to clutter that thread though, but ok, I will keep that in mind :)

anyway... the weird thing is... I did login in my 'regular' account, yet..blegh..I dunno..
arggg  :-#  :-#  :-#  :-#

edit: I just attempted "sudo login" and used my password, and it says
[HTML]unruled is not in the sudoers file.  This incident will be reported.[/HTML]
this is really weird.... how can my main user suddenly not have admin rights? ](*,)  ](*,)

please guys, I need this restored somehow.... the way it is now, my linux is completely broken....unuseable and I was just starting to get the hang of it...:(

---

### Post by frodon on 2005-07-30
If I understand well since you rebooted your computer you cannot login with your usual user.
Maybe, if the user and group window was opened when your computer crashed, the file where the users are defined has been corrupted.
I'm not an expert about that kind of problem but you should try to find this file and see what's wrong in.
However if you can't solve the problem you can create a new user with full permissions then cut and paste all the content of your usual home directory in the new one.

---

### Post by da_unruled on 2005-07-30
[QUOTE=frodon]If I understand well since you rebooted your computer you cannot login with your usual user.
Maybe, if the user and group window was opened when your computer crashed, the file where the users are defined has been corrupted.
I'm not an expert about that kind of problem but you should try to find this file and see what's wrong in.
However if you can't solve the problem you can create a new user with full permissions then cut and paste all the content of your usual home directory in the new one.[/QUOTE]
well... the thing is, in the login screen, I am still logging in using the regular username.... however, when its done loading, its as if I am under the other account (if that makes any sense).
how would I create a new user? (like i said, system-admin-users doesnt work), gives me 218 error now, before error 1.

---

### Post by cwaldbieser on 2005-07-30
Could you just boot into single user mode and make sure your old user is in the /etc/sudoers file?  You could also just create a new user and "mv" and "chown" all your old files if you needed.

---

### Post by da_unruled on 2005-07-31
[QUOTE=cwaldbieser]Could you just boot into single user mode and make sure your old user is in the /etc/sudoers file?  You could also just create a new user and "mv" and "chown" all your old files if you needed.[/QUOTE]
 that sounds like a good idea, the thing is... I am new to linux, and I do not know how to boot into 'single user mode' and verify that.
also, how would I go about creating a new user (since I cannot seem to be able to do anything through the system->admin->users).

thank you for your input..

---

### Post by cwaldbieser on 2005-07-31
This is a link to the unofficial starter guide.  The section labeled "Rescue Mode" should explain what you need to do to log in as root without a password.  It is very similar to booting up in "Safe Mode" in Windows.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by da_unruled on 2005-07-31
[QUOTE=cwaldbieser]This is a link to the unofficial starter guide.  The section labeled "Rescue Mode" should explain what you need to do to log in as root without a password.  It is very similar to booting up in "Safe Mode" in Windows.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)[/QUOTE]
 well I got root access after the rescue mode.... but its all in the console... and I cannot or do not know how to add/remove users that way.
I tried changing passwords with
'passwd root'
newpassword
but it didnt make a difference.

I am lost guys...a noob in help (if I cant get this fixed, I might drop linux and that would be a pity, this is like my 3rd attempt at it, and things always seem to not go my way..Im sure it can be fixed...)

---

### Post by frodon on 2005-07-31
If you want to create a new user in a console use [adduser](http://www.linuxheadquarters.com/howto/basic/adduser.shtml) command with the [options](http://www.annodex.net/cgi-bin/man/man2html?8+useradd) you want.
Don't hesitate to search exemples with google or do a "man adduser" command to get  more informations.
Try useradd command and then post questions if you have problems using it.

---

### Post by cwaldbieser on 2005-07-31
OK, well some things to help you in the terminal:

+ frodon already covered "adduser" in this thread.
+ "nano" is a pretty user friendly editor.  If you do a lot of editing at the console, there is also "vi", but the commands for that are more obscure until you get used to them.  nano shows the commands at the bottom of the screen.
+ You will want to examine your "/etc/sudoers" file and make sure it has entries like:

```
# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
unruled    ALL=(ALL) ALL
```

So in order to edit this file, you would:
```
# nano /etc/sudoers
```

+ You will want to make sure your normal user's password is set correctly:
# passwd unruled

+ If none of that works, then you probably want to add a new user.  Make sure that user is added to the /etc/sudoers file.  Then you can boot back into normal mode and copy over all your old files, etc.  You will probably need to change ownership of the files before you have permission to do anything useful with them:

```
$ sudo chown -R -v newuser /home/unruled
```
That will recursively change the file ownerships to your new user.  Then you can just copy the files over using the normal method to your /home/newuser directory.

If you are unsure about any of the steps, just ask.

---

### Post by da_unruled on 2005-08-01
[QUOTE=cwaldbieser]OK, well some things to help you in the terminal:

+ frodon already covered "adduser" in this thread.
+ "nano" is a pretty user friendly editor.  If you do a lot of editing at the console, there is also "vi", but the commands for that are more obscure until you get used to them.  nano shows the commands at the bottom of the screen.
+ You will want to examine your "/etc/sudoers" file and make sure it has entries like:

```
# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
unruled    ALL=(ALL) ALL
```

So in order to edit this file, you would:
```
# nano /etc/sudoers
```

+ You will want to make sure your normal user's password is set correctly:
# passwd unruled

+ If none of that works, then you probably want to add a new user.  Make sure that user is added to the /etc/sudoers file.  Then you can boot back into normal mode and copy over all your old files, etc.  You will probably need to change ownership of the files before you have permission to do anything useful with them:

```
$ sudo chown -R -v newuser /home/unruled
```
That will recursively change the file ownerships to your new user.  Then you can just copy the files over using the normal method to your /home/newuser directory.

If you are unsure about any of the steps, just ask.[/QUOTE]
 thank you for the detailed instructions, I will attempt to follow them now. I appreciate your help immensely :)

edit:

thanks so much, you have saved me!
I rebooted into recov. mode, logged in as root. Then nano'd the sudoers file first with the line you gave me, rebooted but it didnt help. So then I created a new user 'bob', added him into the sudoers file along with the unruled one. Then rebooted, logged in as bob, managed to get into system-<admin->users and for some reason the home folder and the priveleges had been taken off of the unruled user.
I restored them, logged out, logged in, and all is good.

THANK YOU! :)

---

