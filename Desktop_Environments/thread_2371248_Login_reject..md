---
title: "Login reject."
date: 2017-09-12
forum: Desktop Environments
---

### Post by starwars-geek98 on 2017-09-12
I'm having a weird problem. When I try to connect to my account in xubuntu it rejects me and kicks me out immediatly (no message, just a black screen). 
The backstory is, that I ran a command to supposingly reset my GPU cause my system would lagg every now and then no matter what I was running. The command, though I don't remember -it was about lightdm- unfortunately cause over the past days I've been trying a lot of commands in tty to fix it... But without success.
If anybody knows I would be more than happy to try his/her solution! :)

Thank you!

---

### Post by BenginM on 2017-09-12
Hiya , I suggest you try this :

switch to a Virtual console with Ctrl+Alt+F1 , login with your user credentials and run:

$ sudo apt install slim
$ sudo service lightdm stop
*$ *sudo dpkg-reconfigure lightdm
 hit enter for the first OK, then highlight slim with the arrow up-d key, then hit Tab & OK . $ sudo reboot

ones you reach the slim DM login with your user credentials , when you reach the desktop session look at the logs in /var/log/lightdm , Xorg.0.log .

if slim doesn't take you to the desktop and still kicked back , then it's something else preventing you to login graphically .. might be a user permission , Graphic, i mean if you don't remember the commands used that lead to this ,then who knows!

---

### Post by BenginM on 2017-09-13
IF the cause is lightdm , then by all means feel free to report a bug against it  , in a terminal : $ ubuntu-bug lightdm

---

### Post by starwars-geek98 on 2017-09-13
Thanks for the reply!

Undortunately nothing happend, and I'm still unable to enter my account.

---

### Post by BenginM on 2017-09-13
Which graphic card the system bootin' with ?

login to your old user from a virtual console , try creating a new user account with useradd , and login with it graphically from the display/login manager :
$ useradd -c 'Starwars Geek' -m geek98
$ passwd testpwd
geek98 will be the new user name , testpwd , the new password . or change it as you like.

from the virtual console switch to the X session with Ctrl+Alt+F7 , or reboot . and login with the new accout.

---

### Post by starwars-geek98 on 2017-09-14
Thanks again for your interest! 

First of all, I'm using AMD RADEON HD 2400 PRO.

Secondly, I have already made a second account before posting here but ultimately have lost all my data in the other non-accessible acount.

---

### Post by starwars-geek98 on 2017-09-14
Would an ugrade via my non-accessible acoount graphical wise, to 17.04 fix the problem?

---

### Post by BenginM on 2017-09-14
Did you installed the [FONT=UbuntuMono, courier, monospace][COLOR=#333333]fglrx driver, or the AMDGPU-PRO ?[/COLOR][/FONT]

[FONT=UbuntuMono, courier, monospace][COLOR=#333333]are you able to access the second account graphically , and what about the guest account ?

what do you mean by graphical wise..! you think this is a graphic issue? because so far we don't know what's the problem. we're troubleshooting in the dark here. and how/why you would you lose your data that's beyond me. Now before you go and upgrade to 17.04 know that it's buggy, in fact it's more buggy than 16.04 + 17.10 put together. So it's up to you. one thing i would check the permission on [/COLOR][/FONT][COLOR=#111111][FONT=Consolas].Xauthority , [/FONT][/COLOR].ICEauthority are owned by the user and not root! otherwise i would remove them and restart lightdm or which ever is used, or even reboot.

---

### Post by starwars-geek98 on 2017-09-14
When I check about drivers in terminal it says driver=radeon so I do not know.

I mean that my main account (the one that I have lost graphical access to but can still access from tty).

I am not so skilled in the terminal to access and do things with my files etc.

I run ubuntu 17.04 to another more powerfull machine and they are fine though except the store...

I will test the last suggestion thanks!
[B]
EDIT:
          Checked permision in the two files and it is r-w for the two of them. [/B]

---

