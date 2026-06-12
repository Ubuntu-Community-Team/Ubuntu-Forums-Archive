---
title: "XFCE log-out password disabling"
date: 2005-04-09
forum: Desktop Environments
---

### Post by bored2k on 2005-04-09
By default XFCE 4.2 requires the user to input his/her password to shutdown or reboot, and I can't seem to stumble upon a solution to disable this. Anyone knows how to do this?

---

### Post by bored2k on 2005-04-09
So no one knows how to do this? odd..

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=bored2k]So no one knows how to do this? odd..[/QUOTE]
 hey no bumping after such a little time! :-P

---

### Post by dusu on 2005-04-09
Hi bored2k,

I also would like not to have to enter my password each time I log out.
I've been looking for an answer on [http://www.xfce.org/](http://www.xfce.org/) for an hour, and could not find any.
It seems hopeless  #-o 
I think it's just a feature of the xfce4-session-logout program !

---

### Post by bored2k on 2005-04-09
[QUOTE=dusu]Hi bored2k,

I also would like not to have to enter my password each time I log out.
I've been looking for an answer on [http://www.xfce.org/](http://www.xfce.org/) for an hour, and could not find any.
It seems hopeless  #-o 
I think it's just a feature of the xfce4-session-logout program ![/QUOTE]
 It's exactly what I did :-\ . That xfce Documentation is really poor :(. But still, I refuse to believe every XFCE user likes the feature and has it enabled at will !

---

### Post by Glanz on 2005-04-09
[QUOTE=dusu]Hi bored2k,

I also would like not to have to enter my password each time I log out.
I've been looking for an answer on [http://www.xfce.org/](http://www.xfce.org/) for an hour, and could not find any.
It seems hopeless  #-o 
I think it's just a feature of the xfce4-session-logout program ![/QUOTE]
 In you GDM setup (under "Applications" in the Xfce menu), you should be able to give yourself permission as user to log out without passwd by unchecking the "Secure Actions Menu" under the "Security" tab in the interface.

---

### Post by dusu on 2005-04-09
[QUOTE=Glanz]In you GDM setup (under "Applications" in the Xfce menu), you should be able to give yourself permission as user to log out without passwd by unchecking the "Secure Actions Menu" under the "Security" tab in the interface.[/QUOTE]

Unfortunately it is unchecked :( , so this is not yet the answer...

---

### Post by dusu on 2005-04-09
[QUOTE=bored2k]It's exactly what I did :-\ . That xfce Documentation is really poor :(. But still, I refuse to believe every XFCE user likes the feature and has it enabled at will ![/QUOTE]
Mmmm. I really like XFCE, but I have to admit it's really hard to find an answer on xfce.org (or at least this answer). Maybe all users *do* have to type their password to log out :confused:

---

### Post by bored2k on 2005-04-09
[QUOTE=dusu]Mmmm. I really like XFCE, but I have to admit it's really hard to find an answer on xfce.org (or at least this answer). Maybe all users *do* have to type their password to log out :confused:[/QUOTE]
 What's the point of not giving that option? I mean, I love [I loove] XFCE, but I simply can't use it with this problem. I'm not the only user on this computer and if someone wants to log into their OS or whatever, they can't (I ain't giving no password). I'm amazed there's no on/off switch in the control panel.

---

### Post by dusu on 2005-04-09
[QUOTE=bored2k]What's the point of not giving that option? I mean, I love [I loove] XFCE, but I simply can't use it with this problem. I'm not the only user on this computer and if someone wants to log into their OS or whatever, they can't (I ain't giving no password). I'm amazed there's no on/off switch in the control panel.[/QUOTE]

I agree it's a pain. I'm the only user of my computer so I do not have any major problem.
But could you restate more precisely why you cannot use XFCE ? I'm not sure I got the point !

---

### Post by bored2k on 2005-04-09
[QUOTE=dusu]I agree it's a pain. I'm the only user of my computer so I do not have any major problem.
But could you restate more precisely why you cannot use XFCE ? I'm not sure I got the point ![/QUOTE]
 Here's the scenario:
3 brothers
Me = Linux
2 = Windows

I leave my computer 24/7 downloading *backup* files, and if my brothers want to use the computer, they just click on Reset right? Well, if they have no password, they can't reset, thus they cant use it.

---

### Post by dusu on 2005-04-09
[QUOTE=bored2k]Here's the scenario:
3 brothers
Me = Linux
2 = Windows

I leave my computer 24/7 downloading *backup* files, and if my brothers want to use the computer, they just click on Reset right? Well, if they have no password, they can't reset, thus they cant use it.[/QUOTE]

Ok now I can see the problem ! Well I still do not know how to disable this password on log-out, but  you can always go around the problem like this (don't know if it suits you...) :
If your brothers just choose to quit the current session, instead of rebooting, they will end up in gdm, where they can choose to reboot the computer, withtout being asked any questions.

I know it's an ugly solution, so no need to tell !  :-D

---

### Post by Glanz on 2005-04-09
[b]Passwordless logout for Xfce 4.2
(add to /etc/sudoers)

[/b]  [font=Arial,Helvetica][size=2]your-username-here  ALL = NOPASSWD: /usr/sbin/xfsm-shutdown-helper

("your-username-here" is the username) Most important is "ALL", which means 'all hosts'  You may cut & paste that line into your sudoers file and it will work fine. Replace "your-username-here" with "ALL" if you want any user to be able to shutdown the machine.

...may have to logout/in to make that work after....
[/size][/font]

---

### Post by dusu on 2005-04-10
Thanks Glanz, this works ! :)
Let me simply add that the /etc/sudoers file should be edited by using the visudo command.

---

### Post by Glanz on 2005-04-10
[QUOTE=dusu]Thanks Glanz, this works ! :)
Let me simply add that the /etc/sudoers file should be edited by using the visudo command.[/QUOTE]
I have been using Xfce for a long time... I had to jog my memory to remember why my 'no-passwd' login worked. I did that quite some time ago and when I switched from the pure xfld to ubuntu, I kept some ofmy old configs.
Yes, the Xfce docs are not too good. I think I'll compile a 'tips & tricks' for userslike myself who really don't want to operate on the level of a L.Torvalds.

As far as the 'sudoers' trick goes, I have solved a lot of problems using similar tricks because changing permissions of config files themselves is not a recommended solution. It is always better to give permission to access certain files via sudo.

---

### Post by bored2k on 2005-04-10
[QUOTE=Glanz]I have been using Xfce for a long time... I had to jog my memory to remember why my 'no-passwd' login worked. I did that quite some time ago and when I switched from the pure xfld to ubuntu, I kept some ofmy old configs.
Yes, the Xfce docs are not too good. I think I'll compile a 'tips & tricks' for userslike myself who really don't want to operate on the level of a L.Torvalds.

As far as the 'sudoers' trick goes, I have solved a lot of problems using similar tricks because changing permissions of config files themselves is not a recommended solution. It is always better to give permission to access certain files via sudo.[/QUOTE]
 Thanks dude.

---

### Post by Glanz on 2005-04-10
[QUOTE=bored2k]Thanks dude.[/QUOTE]

My pleasure!:-D
I did it because I didn't want you to get bored:p

---

### Post by kb00heda on 2005-05-08
Just found this thread (and not a moment to late I may add). 

Works perfectly --- happy days! :)

---

### Post by doobit on 2006-05-30
I'm not too sure why this has become such an issue. The logout prompt has existed in older releases. There is more of a delay this time, maybe. 
You don't need to actually type anything in there. Just wait a minute and it will shutdown or reboot without you needing to put a password in.
At least it does on my computer.

---

### Post by aysiu on 2006-05-30
[QUOTE=doobit]I'm not too sure why this has become such an issue. The logout prompt has existed in older releases. There is more of a delay this time, maybe. 
You don't need to actually type anything in there. Just wait a minute and it will shutdown or reboot without you needing to put a password in.
At least it does on my computer.[/QUOTE] Are you using Dapper? They got rid of the logout prompt for Dapper.

---

