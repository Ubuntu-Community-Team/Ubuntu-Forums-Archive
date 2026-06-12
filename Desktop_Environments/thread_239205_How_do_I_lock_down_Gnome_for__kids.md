---
title: "How do I lock down Gnome for  kids?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by tionik06 on 2006-08-18
I am configuring an Imac rev.A g3 computer for my neices and nephew to use. I have already created them an autologin user account but i am concerned that they will hack it again. Last time they ran debian and made it so X wouldnt start somehow. dont ask me!    :confused: 

Mainly what i want to do is make the panel menus and desktop area read only so they wont be deleting menus that took me hours to build and move application all around and make a mess. Other suggestions are also welcome on how i can keep the system stable.

I am on the latest 6.06 ubuntu.

---

### Post by hopstah on 2006-08-19
one thing you could do is make a backup of the /home/username directory of the account that you are using to log the kids in, and you could make the backup read-only, and write a script to restore the backup to the /home/username directory on login.  i don't know how to write the script, but that will undo anything in the menus and settings that they manage to screw up.

---

### Post by tionik06 on 2006-08-19
i dont know how to write that script either.

---

### Post by dasunst3r on 2006-08-19
For starters, DO NOT create an auto-login account.  Doing that is asking for trouble because I believe that it could allow global changes.  Set up a guest account for your... you know... and an account for yourself.  Every time they leave, just issue the command *sudo rm -rf /home/guest*.

---

### Post by tionik06 on 2006-08-19
Sorry, this isnt a computer im always going to be around to mantain. It needs to be setup so it can take care of itself. The kids are too young to spell correctly all the time so i have to leave autologin on. It auto logs into a user account, not a priviledged account.

---

### Post by Ramses de Norre on 2006-08-19
Hmm deleting the home dir everytime is a pretty brute way, they can't confiure anything then because it's always reset. (like amarok preferences, amsn themes and so on).
What you could do for the menus is ```
sudo chmod 700 /usr/bin/alacarte
``` which will make any user unable to execute alacarte without sudo. But of course they wont be able to add any menu entry neither (don't now whether they'll ever need that..)
Be sure not to give them sudo priviliges!

Ow and who will maintain the computer? Doing updates and stuff?

---

### Post by hopstah on 2006-08-19
if i'm not mistaken, this should work.  don't try it, though, until we get some other feedback by other users here.

say, you have your kids logged into an account called 'kids'.  and after you get everything configured as you want it, you could create a directory (lets say /backup/kids ) to backup the /home/kids directory to.  then run the command ```
sudo rsync -aS /home/kids/ /backup/kids/
```this will backup the /home/kids directory as you had it to the /backup/kids directory.  you may need to install rsync, but i'm not sure.  i would then change the permissions of the directory so that the kids won't be able to touch the backup copy```
sudo chmod 700 -R /backup/kids
```once that has been done, you could create a text file in which you will put a line of code that will instruct the computer to copy your backup copy of the kids' home directory (including all of the settings that you changed) back from your original backup to the /home portion of the drive.  this file will be located in the /etc/init.d directory so that it will be executed on every boot of the computer.

to do this, you could do something along these lines:```
sudo gedit /etc/init.d/kidsbackup
##within the /etc/init.d/kidsbackup file, insert this line
rsync -aS /backup/kids/ /home/kids/
##save and exit the file
sudo chmod +x /etc/init.d/kidsbackup
```

now, assuming that this works, it will add at least a little time to the boot process, and shouldn't eliminate any pictures or anything else that the kids downloaded, but it should restore all of the settings how you initially had them.

edit:  again, i would love input from those with more linux experience than I have.  this works in my head, but i don't know how practical this is.  to me it seems very reasonable, but maybe not to everyone else.

---

### Post by tionik06 on 2006-08-19
in response 2 posts above, no one will mantain the computer. Its already taken a week to get this going, original imacs are really slow... and i dont want a strange update to mess things up. I just wanna get it setup and rock solid and send it into battle.

Also thanks for the detailed, instructions, i'll wait for someone to say wether it will work or not cause it seems ive only got another week of freetime.

---

### Post by aysiu on 2006-08-19
Have you thought about using *kiosktool* to just lock it down?

[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)

It's in the Universe repositories.

---

### Post by tionik06 on 2006-08-19
is kiosk KDE only? i suppose i could switchem to kde if i had to.

---

### Post by RichardA on 2006-08-19
Pessulus. It's the new lockdown manager for Gnome. It can't do everything (like stop the mrebooting), but it'll lock the panel.
Just run it in the account you want to lock down.

---

### Post by hopstah on 2006-08-19
i would really love it if somebody could verify / quash (whichever is appropriate) my idea that i posted earlier.

---

