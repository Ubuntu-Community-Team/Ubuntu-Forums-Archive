---
title: "Login Trouble?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by PittNsciGuy on 2006-08-11
So I'm working on a laptop setup to be dual bootable with Ubuntu and Windows XP.  Not even 5 minutes ago I was logged on to my Ubuntu partition, had to restart to do some stuff in Windows very briefly, and then restarted so I could log back onto my Ubuntu partition.  When I go to login, however, it now tells me that I have entered an invalid password....though I have obviously done nothing to change it.  Additionally, I have not downloaded any new updates or changed my configurations for at least three days (during which I have had no issues).  I'm new to Ubuntu and Linux in general, so I thought I'd see if anyone could help troubleshoot the problem.  Any help will be greatly appreciated!  Thanks!

---

### Post by murataht on 2006-08-11
take it easy man. it is not so hard to fix. 

from the grub select the recovery mode, and boot into it.

there you become root. use su to be the user, and run passwd

for example:
#su username
$passwd

now, you have the new password, and boot into the gdm, and try it. it should work now. good luck.

---

### Post by PittNsciGuy on 2006-08-12
Thanks for the reply!  I tried what you suggested, however when I tried to switch from root to my username it told me that my username is invalid?  So I guess the next question is can I restore my username, and will it restore all of my congfigs, settings, and permissions with it?  Any help is greatly appreciated at this point!

---

### Post by bulldog on 2006-08-12
A wild guess,but is your Caps enabled?

You should only use lower case caracters for your login-name!

---

### Post by PittNsciGuy on 2006-08-12
That was actually the first thing that I checked.  Tried both my username and password with and without caps just in case too. :( Thanks for the idea though!

---

### Post by murataht on 2006-08-12
if that says your username is bad, you should check if it is in the userlist:
(still in the safe mode, you are still the root)

#cat /etc/passwd | grep "username" 

(in the above line, replace the "username" with your real username).

if it shows there is your username, then you can change the password. if it does not show anything like your username, then try to add one like that. with adduser command.

#adduser   (from here, you go with interactive process of creating the new user).

then add the new user to the the admin group, so that the new user can use the sudo command. reboot, login to gdm, and try to restore from the old user.

PS: you should also check if the home folder for the old user exists. by:

> ls /home

if this shows the folder, then you should be alble to use it. 

try to learn some adminstrative commands, and this will help all the time. and don't give up easily, this way you learn more. good luck.

Murat

---

### Post by PittNsciGuy on 2006-08-14
Hey Murat...Thanks for replying again!  So I ran the first command (cat /etc/passwd...), but the command didn't return anything.  However, ls /home does indeed show that my user folder is still intact and present?  I guess I was just wondering which commands I need to enter with the adduser command to make the new user with full privilages so that I can restore the old user to the user list and such?  Or is there a shorter way to just restore the original user to the list somehow?  Thanks for all of the help so far!
Steve

---

### Post by murataht on 2006-08-14
hi steve, you are welcome. :)

i think you can restore the old settings in this way:

1) go into the recovey mode. 

2) make a backup /home/username

(make a back up of /home/username, just in case)
#tar czf /home/username.tar.gz /home/username

3) adduser username
(interactively enter the new password, name, etc. and you don't have to enter all other informations: like room numner, etc.)

if this is succesfull, reboot and go into gdm, try your username. it should work now. and the old settings should be present, (if not, you can recover it from the back up. (sudo tar xzf /home/username.tar.gz -C /home))

good luck.

---

### Post by Ramses de Norre on 2006-08-14
Don't forget to run ```
adduser username admin
``` in recovery mode to gain sudo priviliges.

---

### Post by PittNsciGuy on 2006-08-14
Hooray...it worked!!  GDM was a little sluggish on the reboot after I restored the user, but everything seems to be back online and operating as usual.  Thanks again for all of your help :-)  So, out of random curiosity, any idea what in the world caused this issue in the first place?

---

### Post by murataht on 2006-08-17
Good to see you fixed it. 
about the reason, i don't know. maybe some upgrade, or something else. 
keep the ubuntu spirit up. 

see you around.

Murat

---

