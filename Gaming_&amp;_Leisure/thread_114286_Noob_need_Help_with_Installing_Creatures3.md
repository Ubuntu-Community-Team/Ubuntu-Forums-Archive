---
title: "Noob need Help with Installing Creatures3"
date: 2006-01-08
forum: Gaming &amp; Leisure
---

### Post by sk33t3r on 2006-01-08
Hello - I am having one heck of a time. I got Creatures3 installed but it wouldn't start by clicking on the icon in the games directory. I tried this, and now I have a big problem not with just starting  the game but as it suggested the same problem I was having, and now I can't log back into my desktop and need some help. I tried this here command

 Quote:
mv /bin/ls /bin/ls-real && echo '#!/bin/bash' >/bin/ls && echos-real --time-style=locale $@ >>/bin/lsls && chmod a+x ls

that is located here: [http://ubuntuforums.org/showthread.php?t=42316]("http://ubuntuforums.org/showthread.php?t=42316")

My gnome-session has got a permissions problem, and now I can only get into the fail safe terminal, I also can't "ls" to anywhere and get this: bash: /bin/ls: Permission denied. Please help me out with this problem, and possibly also helping me to resolve the problem of getting the game to load up. I have posted a warning on the page I have referred to so that someone else won't have this happen to them as well.....

---

### Post by sk33t3r on 2006-01-08
I am going to get some sleep, I will check back in later. Thanks in advance for helping me out with this....:confused: 

Howard

---

### Post by Perfect Storm on 2006-01-08
I got Creatures 3 intstalled. You have the Creature 3 game which also have Docking Station and another add-on? Or is it the Docking Station only?

---

### Post by sk33t3r on 2006-01-08
[QUOTE=Artificial Intelligence]I got Creatures 3 intstalled. You have the Creature 3 game which also have Docking Station and another add-on? Or is it the Docking Station only?[/QUOTE]

The Creatures 3 version I have is the full version called Creatures 3 Internet Edition that has all 3 game type installers and it looks to also have the installer for windows as well. I am waiting for some help on getting it installed, did you have any problems getting your version installed on Breezy. If so can you help me out with my problem and maybe also help me get the game installed?

---

### Post by Perfect Storm on 2006-01-08
Here's what Kassetra told me to do when I had trouble installing it (both her and I are playing Creature 3 ^^). The problem is caused by it's made for an ealier Red Hat version, but there's a workaround.

First copy the whole CD to your harddisc in a folder

```

cd /where/you/saved/the/CD
sudo sh install-c3.sh

```

When installed:

```

sudo gedit /usr/local/games/creatures3/creatures3

```

In that file you just open find all the **$11** and change them out with **$10** and save.

Go back to where you saved the creatures3 CD 
Then:

```

cd dockingstation
sudo gedit dstation-install

```

Change all the **$11** with **$10** and save.

Install dockingstation:
```

sudo sh dstation-install

```

Back to where you saved the Creatures3 CD.

Then:

```

cd magmanorns
sudo cp MagmaNornEggs.agents /usr/local/games/creatures3/My$Agents

```

You should find Creatures 3 launchers in applications tab --> Games
One launcher that show the intro and one to run the game.

If not run a killall gnome-panel


EDIT: Forgot the $ infront of **11**

EDI: EDIT: If you want to run docking station open terminal and type: **dockingstation nocheck**

---

### Post by sk33t3r on 2006-01-08
[QUOTE=Artificial Intelligence]Here's what Kassetra told me to do when I had trouble installing it. The problem is caused by it's made for an ealier Red Hat version, but there's a workaround.

First copy the whole CD to your harddisc in a folder

```

cd /where/you/saved/the/CD
sudo sh install-c3.sh

```

When installed:

```

sudo gedit /usr/local/games/creatures3/creatures3

```

In that file you just open find all the **11** and change them out with **10** and save.

Go back to where you saved the creatures3 CD 
Then:

```

cd dockingstation
sudo gedit dstation-install

```

Change all the **11** with **10** and save.

Install dockingstation:
```

sudo sh dstation-install

```

Back to where you saved the Creatures3 CD.

Then:

```

cd magmanorns
sudo cp MagmaNornEggs.agents /usr/local/games/creatures3/My$Agents

```

You should find Creatures 3 launchers in applications tab --> Games
One launcher that show the intro and one to run the game.

If not run a killall gnome-panel[/QUOTE]


I would like to try this a you have suggested but I can't login to the gui, I can only get into the failsafe terminal due to entering these commands: mv /bin/ls /bin/ls-real && echo '#!/bin/bash' >/bin/ls && echos-real --time-style=locale $@ >>/bin/lsls && chmod a+x ls
By enter these commands it has messed up the permissions or something on my gnome-session and also "ls". Do you or anyone else know how to fix this first so I can get back into the Ubuntu gui?

---

### Post by Perfect Storm on 2006-01-08
See if this help:

```

sudo mv /bin/ls-real /bin/ls

```

If not then you have to redo your gnome session.

---

### Post by sk33t3r on 2006-01-08
[QUOTE=Artificial Intelligence]See if this help:

```

sudo mv /bin/ls-real /bin/ls

```

If not then you have to redo your gnome session.[/QUOTE]

Tried this and it didn't work, How do I redo my gnome session? Even though my gnome session is messed up it seem that my xubuntu session is to, I just can't get in the the gui passed the gdm login, when I enter my Username: and then Password: , I get a box with a lightbuld stating: I could not start your session and so I have started the failsafe xterm session. Windows now have focus only if you have your cursor above them. To get out of this mode type 'exit' in the window in the upper left corner. And then when I click on OK it throws me into the failsafe xterm.....:(

---

### Post by Perfect Storm on 2006-01-08
Okay, try this:

```

sudo rm /home/username/.ICEauthority
sudo chown -R username.username /home/username
sudo chmod -R 775 /home/username
sudo mv /home/username/.gnome2 /home/username/0.gnome2
sudo mv /home/username/.gconfd /home/username/0.gconfd

```

---

### Post by sk33t3r on 2006-01-08
[QUOTE=Artificial Intelligence]Okay, try this:

```

sudo rm /home/username/.ICEauthority
sudo chown -R username.username /home/username
sudo chmod -R 775 /home/username
sudo mv /home/username/.gnome2 /home/username/0.gnome2
sudo mv /home/username/.gconfd /home/username/0.gconfd

```[/QUOTE]

When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory

Another question: when entering this: sudo chown -R username.username /home/username do I enter it im my case this way: sudo chown -R howard.howard /home/howard ?? And the same with the rest of the commands with username=howard since that is my login account...

---

### Post by kassetra on 2006-01-08
[quote=sk33t3r]When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory

Another question: when entering this: sudo chown -R username.username /home/username do I enter it im my case this way: sudo chown -R howard.howard /home/howard ?? And the same with the rest of the commands with username=howard since that is my login account...[/quote]

yes.

and you are doing sudo rm /home/howard/.ICEauthority, correct?

---

### Post by sk33t3r on 2006-01-08
[QUOTE=sk33t3r]When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory

Another question: when entering this: sudo chown -R username.username /home/username do I enter it im my case this way: sudo chown -R howard.howard /home/howard ?? And the same with the rest of the commands with username=howard since that is my login account...[/QUOTE]

 I have enter the commands and only had the problem with: When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory , But now I still have the same problem but I get this box first the the one I have already specified: Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions. I then click OK and the other box still pops up. 

RANT - Isn't there any way that I can just reverse the command that caused all of this before I end up really messing up my system worse. I can't belive it this freaking hard to just install a standard game that was built for linux. Maybe the problem is that Ubuntu doesn't follow some standard that Redhat and some of the other distrobutions follow. I don't know except that it shouldn't be this hard to install or do anything on Ubuntu. I will admit that Linux still is not up to the ease of using as windows, but it shouldn't take days to get something simple done.

---

### Post by sk33t3r on 2006-01-08
[QUOTE=sk33t3r]I have enter the commands and only had the problem with: When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory , But now I still have the same problem but I get this box first the the one I have already specified: Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions. I then click OK and the other box still pops up. 

RANT - Isn't there any way that I can just reverse the command that caused all of this before I end up really messing up my system worse. I can't belive it this freaking hard to just install a standard game that was built for linux. Maybe the problem is that Ubuntu doesn't follow some standard that Redhat and some of the other distrobutions follow. I don't know except that it shouldn't be this hard to install or do anything on Ubuntu. I will admit that Linux still is not up to the ease of using as windows, but it shouldn't take days to get something simple done.[/QUOTE]

***By looking into this deeper I have located what may have caused this problem from when I enter this command that I enter in opening this thread, I have noticed that the person with the link I provided entered it wrong in thier Howto: by seeing this located in this thread here: [http://www.gamewaredevelopment.co.uk/forums/showthread.php?t=3007&highlight=ubuntu]("http://www.gamewaredevelopment.co.uk/forums/showthread.php?t=3007&highlight=ubuntu")

Thanks so much for the help so far, but I am not sure what to do next. I just don't want to goof up my system anymore then it is.... I needs some help here please....;)

---

### Post by kassetra on 2006-01-08
[quote=sk33t3r]I have enter the commands and only had the problem with: When I do this "sudo rm /home/username/.ICEauthority" I get rm: cannot remove ' .ICEauthority': No such file or directory , But now I still have the same problem but I get this box first the the one I have already specified: Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions. I then click OK and the other box still pops up. [/quote] Have you done these two commands:
```
sudo chown -R howard.howard /home/howard
sudo chmod -R 775 /home/howard

``` 
[quote=sk33t3r] RANT - Isn't there any way that I can just reverse the command that caused all of this before I end up really messing up my system worse. I can't belive it this freaking hard to just install a standard game that was built for linux. Maybe the problem is that Ubuntu doesn't follow some standard that Redhat and some of the other distrobutions follow. I don't know except that it shouldn't be this hard to install or do anything on Ubuntu. I will admit that Linux still is not up to the ease of using as windows, but it shouldn't take days to get something simple done.[/quote] Actually No. What you need to understand is this: You issued a command on your box to destroy the current debian standard ls command and turn it into some hacked up version of the old, non-standard 2001 redhat ls command. The ls command is a core command in the Linux/Unix world... and so the changes you told it to do have trickled into your current desktop sessions.

This *would* have been a simple install; I helped Artificial Intelligence setup his game in less than 10 minutes.

In the Windows world, for a comparison, you've just removed the ability for you/the computer to open/look at/use *ANY* folder on the system.

---

### Post by Ampersand on 2006-01-08
Just skimmed through the thread, but would it be possible for you to create a new username. Try running 
```
sudo useradd username
```
(replacing username with whatever you want the username to be). You should then hopefully be able to log in at least.

---

### Post by kassetra on 2006-01-08
[quote=sk33t3r]***By looking into this deeper I have located what may have caused this problem from when I enter this command that I enter in opening this thread, I have noticed that the person with the link I provided entered it wrong in thier Howto: by seeing this located in this thread here: [http://www.gamewaredevelopment.co.uk/forums/showthread.php?t=3007&highlight=ubuntu]("http://www.gamewaredevelopment.co.uk/forums/showthread.php?t=3007&highlight=ubuntu")

Thanks so much for the help so far, but I am not sure what to do next. I just don't want to goof up my system anymore then it is.... I needs some help here please....;)[/quote]

What they are attempting to do to the machine is convert the 2005 version of the ls command into one that is more suited to when the install script was written (2001) ... this is *not* recommended.

The $11 for $10 swap in the script is *safe* - because you are not messing with core commands on your system - you're editing the script to install the game.

---

### Post by kassetra on 2006-01-08
[quote=Ampersand]Just skimmed through the thread, but would it be possible for you to create a new username. Try running 
```
sudo useradd username
``` (replacing username with whatever you want the username to be). You should then hopefully be able to log in at least.[/quote]
then what you would do - if you choose to go this route is copy over your files from your original /home/username

but you must be careful about copying files over that start with a .   -- these are likely the files that are messed up currently.

then, following this route, after you have finished copying over your files, you could remove the previous user and change the new user to the old username.

---

### Post by sk33t3r on 2006-01-08
[QUOTE=Ampersand]Just skimmed through the thread, but would it be possible for you to create a new username. Try running 
```
sudo useradd username
```
(replacing username with whatever you want the username to be). You should then hopefully be able to log in at least.[/QUOTE]

But but doing this the permissions that are system wide still won't be reversed. 

After it taking me 2 weeks to get my system all built up and running great, I can't believe that it has only taken one command to mess it up. I wouldn't have entered it but trusted doing it since it was in a Howto: from the Ubuntu site. I like Ubuntu and it runs great, but I am serious having second thoughts.... Isn't there any way that I can reverse what has been caused by entering this evil command that caused this in the first place? :???:

---

### Post by kassetra on 2006-01-08
[quote=sk33t3r]But but doing this the permissions that are system wide still won't be reversed. 

After it taking me 2 weeks to get my system all built up and running great, I can't believe that it has only taken one command to mess it up. I wouldn't have entered it but trusted doing it since it was in a Howto: from the Ubuntu site. I like Ubuntu and it runs great, but I am serious having second thoughts.... Isn't there any way that I can reverse what has been caused by entering this evil command that caused this in the first place? :???:[/quote] 
Please listen.

You read a HOWTO from the Hoary section of this site, not from the Breezy section of this site. Breezy is not the same as Hoary. Just as Hoary was not the same as Warty. It is just like you cannot do things in Windows 98 the same way you do things in Windows XP.

Also one of the things you must understand about Linux is that when you issue any command with su or sudo - you are telling the computer "do as I say, no matter what I say." That is very powerful and can be very dangerous.  Think of the damage you can do with a single command on a windows box (as administrator - since all accounts have administrator access by default) - format c:\

Now, as I have now asked already, have you issued the commands:
```
sudo chown -R howard.howard /home/howard
sudo chmod -R 775 /home/howard
``` These two commands tell your system that /home/howard once again belongs to the user named howard; and that user has read/write/execute permissions over that entire directory (which is what the errors you are receiving when trying to login are about.) The permissions errors you are receiving are *only* related to your home directory - so you do not need to worry about the system-wide permissions (since the system is still running - even if you cannot login, you see?)

Also, the first command that changed your ls back into the regular command has stopped any issues you have created - and you have been locked out of your regular session for this time so the amount of damage that the command you issued is possibly very small - and only limited to the issues you are experiencing now.

---

### Post by sk33t3r on 2006-01-08
[QUOTE=kassetra]Please listen.

You read a HOWTO from the Hoary section of this site, not from the Breezy section of this site. Breezy is not the same as Hoary. Just as Hoary was not the same as Warty. It is just like you cannot do things in Windows 98 the same way you do things in Windows XP.

Also one of the things you must understand about Linux is that when you issue any command with su or sudo - you are telling the computer "do as I say, no matter what I say." That is very powerful and can be very dangerous.  Think of the damage you can do with a single command on a windows box (as administrator - since all accounts have administrator access by default) - format c:\

Now, as I have now asked already, have you issued the commands:
```
sudo chown -R howard.howard /home/howard
sudo chmod -R 775 /home/howard
``` 

 Yes, I have entered these two commands. I entered all of them but the only one that din't work was the one pertaining to >ICEauthority.

These two commands tell your system that /home/howard once again belongs to the user named howard; and that user has read/write/execute permissions over that entire directory (which is what the errors you are receiving when trying to login are about.) The permissions errors you are receiving are *only* related to your home directory - so you do not need to worry about the system-wide permissions (since the system is still running - even if you cannot login, you see?)

Also, the first command that changed your ls back into the regular command has stopped any issues you have created - and you have been locked out of your regular session for this time so the amount of damage that the command you issued is possibly very small - and only limited to the issues you are experiencing now.[/QUOTE] I also added a new user as suggested by Ampersand above in the thread.  I added a new user as creature with the password as creature. I attemp to login in and enter  the password and am faced with a box: Your home directory is listed as: '/home/creature' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session. I get a yes no choice. If I chose either one I go to the failsafe xterm. Then I get a box: Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Then I have only the choice to press OK.  Then I get another box that I have aready shared stating : I could not start your session ,, blah ,, blah  Please Help me out....

---

### Post by sk33t3r on 2006-01-09
bump.... I still am trying to get help on fixing my problem, anyone willing to help out a linux dumby..... I admit that I can't fix this with out some help....

---

### Post by sk33t3r on 2006-01-09
[QUOTE=sk33t3r]bump.... I still am trying to get help on fixing my problem, anyone willing to help out a linux dumby..... I admit that I can't fix this with out some help....[/QUOTE]


UPDATE: I have now typed: gnome-session onthe the xterm failsafe command line and am into the gui. Is there anyone that is will to read abit of this thread and help me repair this from what I caused from entering the evil command that I used to get into this mess....

---

### Post by sk33t3r on 2006-01-09
Thanks for your help guys..... I am making the decision of just reinstalling rather then spending days trying to get help at fixing this mess.... In my learning linux and the Ubuntu Distro, I have been logging and keeping track of my many mistakes,as well as the workarounds, guides and howtos: I am finding that it is easier and faster to just reinstall the whole system and gain the experience and knowledge shared by others here in the forums. I can reinstall in a matter of hours now. I still would like to install this game and after I reinstall I will ask for assistance(hand-holding)lol.... Rather then trying something that is for a lower division of Ubuntu and messing my system up. I know that I can learn mre by fumbling around and reading this and trying that. But, I am not trying to be a rocket scientist, I just want to learn how to use linux enough to enjoy it and not have to get really dirty in it.... I like windows and will always continue to use it since it I have been using it for 15 years and counting.  I have just become bored with it and have been trying out linux off and one for the past 7 years. I still for some reason can't seem to understand it as well as windows. But, I still enjoy building/ testing it on what ever computer or laptop systems that I own..... I know that this is a long winded closure to this thread. But somebody might enjoy what I have shared here. I am of to rebuilding this laptop once again with the distro that I have found to work the best so far..... If by chance someone reads this thread and knows what the working approach would have worked, I would be ears open.

---

### Post by Perfect Storm on 2006-01-09
Sorry, that you have to reinstall. The howto you followed have been moved and deleted, so it won't harm anyone else.

Please don't hesitate to post/ask if you run into installation/setup trouble.



.:=The AI Dude=:.

---

