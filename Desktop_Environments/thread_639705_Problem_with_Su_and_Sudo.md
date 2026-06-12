---
title: "Problem with Su and Sudo"
date: 2007-12-13
forum: Desktop Environments
---

### Post by chazz-bg on 2007-12-13
first a little prehistory - i am on dual boot with ubuntu and xp , but now i realise that my ubuntu partition is small , so i decide to move the root fs to other ext3 partition ,  everything works fine but i have problem with su and sudo , when i want to become super userwith su i get this answer ```
chazz@MetalZone:~$ su
Password: 
su: Authentication failure
Sorry.

```
but i'm sure that i didn't wrong with my pass 
 and when i tried to use sudo i get this answer ```
chazz@MetalZone:~$ sudo passwd
sudo: must be setuid root
``` , i found way to fix the second problem - change mod of /usr/bin/sudo , but i have to be a super user ,and i cant do this because the second problem , i will be really glad i i find solution here

---

### Post by bistros on 2007-12-13
Were you the first user on the system (which is set up with administrative privileges)?

If so, you should be able to enter sudo passwd to create a root password.  The first prompt is for your own password - as administrator during system setup you were entered into sudoers. Therefore sudo will work for you.

If sudo doesn't work for you, you probably weren't the first user and therefore the real first user should grant you administrative privileges.  Without privileges you can't change the modulus (wrong idea to begin with).  You don't make a world accessible binary setuid root - it's like putting a box of working keys outside your house.

Either you are looking to defeat  system security or you didn't set up the system.

---

### Post by chazz-bg on 2007-12-13
right now i'm playing with live cd and im trying to fix that ( to return the original owners an mods of sudo and su ) and i hope it works , infact i just was testig the new system that i copyed , and tryed to fix trough the original system , but i screw her sudo too , cus i was too lazy to write the whole path to sudo :D

omfg , i just needed 5 more minutes in google to find a solution , , anyway 10x to care about me ,bye for now :)

---

### Post by bistros on 2007-12-13
Hunh?

You can't modify a filesystem on an ISO9660 format CD.  Therefore tweaking the modulus of the executable isn't just a bad idea - it is impossible.

You do _not_ need to do this.  When logged in as the user created during live CD run, just sudo passwd and set a password for the superuser.  Once you done this, su and your are in as root.

If you don't understand this, you aren't experienced enough to administrate a *nix system.

Bill Strosberg, CISSP

---

### Post by danwood76 on 2007-12-13
there is no su in ubuntu use sudo -s ;)

---

### Post by Jouke74 on 2007-12-13
After you have given a password to root in the users menu , there is definitively a "su" as well... It's just not the best thing to use it all the time.

---

### Post by danwood76 on 2007-12-13
I think the idea with ubuntu is not to use the root user, that is why its locked out and disabled to start with.
Theres no reason to enable it, sudo is fine and if you need the console as root then sudo -s

---

### Post by bistros on 2007-12-13
Root is not available by default, but that doesn't mean it isn't proper and necessary at times to log in as root.  Typing sudo constantly is a real pain.

You have to be careful as root, but that goes for sudo usage as well - you can get in just as much trouble using sudo as you can being logged in as root.  Ubuntu does not implement program by program sudoers control as it could. sudo -s works fine from an xterm, but if you need to log in from a console, or you are recovering from failure you are screwed if you haven't set a root password.  

Not everyone needs training wheels all the time, although I'm an advocate for their usage by wobbly beginners.

Bill Strosberg, B.Sc., CISSP

---

### Post by gabuleon on 2007-12-17
Ok I have read the info on the site about sudo but this was the most recent thing similar to the issue i'm having with my install.  Ive been playing around with different versions and decided to try ubuntu as a friend recommended it to me.  I have experienced consistent problems trying to follow the documentation to get sudo to work for me.

I have installed the Ubuntu 7.10 Server "Alternate".  My first login was as the user I created during the install.  I have been unable to successfully get sudo to work for me at all.  I don't think I am doing anything wrong but it is not working so I have to be.  Can I get some advice for this issue.

---

### Post by gabuleon on 2007-12-17
On top of this as a side note.. I also have a desktop version of 7.10 that I installed. (actually the one I am on at this very minute).  I had the same problem with it where from the terminal I could not run the sudo command and kept telling me I wasnt a part of the sudoers.  As it started with X windows gnome configuration I did find a workaround.  I went to the System -> Administration -> Users and Groups.  I setup a password for root.  Turned around and logged into the SU and modified the groups file to allow me into the sudo group and it worked for me.  Now I dont know if it is because sudo helped load the x windows system as if that was the reason I got around it. Only problem is that on the server version I have installed on the other computer it doesnt by default load an x windows system, and as I am still new to (but wanting to get more comfortable with the command line) I would think that I just need to do the same thing from the command line.  So if anyone comes across this and has some further suggestions for me I am all ears.  Thanks!

---

