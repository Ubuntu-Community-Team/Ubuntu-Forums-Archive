---
title: "how to rename username"
date: 2009-05-19
forum: General Help
---

### Post by smitty96 on 2009-05-19
Hi, I'm wondering if there is any way to rename my login username? I would just delete it and make a new one, but then all my settings would be lost. In the "users and groups" section, I can only change the "real name", but not "user name". If there is any way to do this through a terminal, or if I have to login as root, please tell me how. Thanks,

[CENTER]Tim[/CENTER]

---

### Post by mikezila on 2009-05-19
When it comes to your short username, all sales are final.  The only way is to make a new one.

You could make a new one, then rename your old home folder.  A few apps might break, but most should be fine.  Just make sure you change it so that your new name owns all of the files in the home folder you're renaming.

---

### Post by Brandon Williams on 2009-05-20
Yes, it's possible and easy. This command will rename the account 'oldname' to 'newname', create a new home directory called '/home/newname' to be the home directory, and then move everything from '/home/oldname' into '/home/newname': 'sudo usermod -d /home/newname -m -l newname oldname'. You'll want to logout and login immediately after running the command. It's probably best to login to a console session to do this, rather than a gui session, since some parts of the gui might stop working after the change.

See 'man usermod' for more information.

---

### Post by coffeecat on 2009-05-20
> **Brandon Williams said:**
> Yes, it's possible and easy. This command will rename the account 'oldname' to 'newname', create a new home directory called '/home/newname' to be the home directory, and then move everything from '/home/oldname' into '/home/newname': 'sudo usermod -d /home/newname -l newname oldname'. You'll want to logout and login immediately after running the command.

See 'man usermod' for more information.

Are you sure this will work? Tbh I've never used usermod like this before and I was intrigued by your post. I've a dummy account called 'fred' which I was happy to play with so I tried:

```
 sudo usermod -d /home/bill -l bill fred
```...which changed the login name (according to System > Administration > Users and Groups), but didn't rename /home/fred to /home/bill, or create a new /home/bill. Notwithstanding this, I tried logging out and then in again as bill only to get an error saying there was no home and did I want to use root's home? Which seemed an unlikely offer since I hadn't given fred-bill adminstrative privileges and, sure enough, when I OK'd that I was confronted with a hung xserver (a black screen anyway). So I ctrl-alt-F1-ed into a virtual terminal to do a reboot and I had to..

```
sudo mv /home/fred /home/bill
```... and go back into Users and Groups to change the real name for this account from fred to bill before I could log out and in again successfully.

Before the OP tries this, did I do something wrong?

---

### Post by Soul-Sing on 2009-05-20
to rename Computername ===> /etc/hosts and /etc/hostname 
: "man usermod"
(username is difficult, there are sudo issue's..)

---

### Post by Brandon Williams on 2009-05-20
> **coffeecat said:**
> Before the OP tries this, did I do something wrong?

Yes, you did something wrong, but only because I screwed up in my original post :-(

The command line should be 'sudo usermod -d /home/newname **-m** -l newname oldname'. The -m flag is very important, because it's responsible for moving the home directory. I apologize for leaving that out of my previous post.

Another thing I forgot to mention is that you should run this command from a console login, not a graphical one, since some elements of the gui session will stop working after you run the command.

I updated my original post to make sure that no one will use the bad command line with the missing flag. Thanks for pointing out my mistake. I should have been more careful.

---

### Post by smitty96 on 2009-05-22
Alright, but I don't know how to do a console login. Sorry, I'm a newb.

---

### Post by Brandon Williams on 2009-05-27
> **smitty96 said:**
> Alright, but I don't know how to do a console login. Sorry, I'm a newb.

Sorry ... I didn't notice your update until now ...

Logout from your graphical session, back to the gdm login screen. Then press Ctrl+Alt+F1 to get to a console login prompt. Login and run the command from my earlier post to change your username and homedir, and then log out. Finally, press Ctrl+Alt+F7 to get back to the gdm login screen.

---

### Post by Locutus_of_Borg on 2009-05-27
it is a good idea to run a script to change all instances in your new home directory of your old user name to your new user name after you copy over your old settings

```
#!/bin/bash
startdirectory="/home/NEW_USER_NAME/"
searchterm="OLD_USER_NAME"
replaceterm="NEW_USER_NAME"

        for file in $(grep -l -R $searchterm $startdirectory)
          do
           sed -e "s/$searchterm/$replaceterm/ig" $file > /tmp/tempfile.tmp
           mv /tmp/tempfile.tmp $file
           echo "Modified: " $file
        done


```
put in your old and new user names in the appropriate places in the above, chmod +x the script, then run it

i've done this several times, no problems apart from the occasional instance of your old user name appearing in files outside of ~ which is rare and easily fixed with a text editor

---

