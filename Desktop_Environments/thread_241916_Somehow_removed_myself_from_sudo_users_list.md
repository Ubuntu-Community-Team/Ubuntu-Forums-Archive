---
title: "Somehow removed myself from sudo users list"
date: 2006-08-23
forum: Desktop Environments
---

### Post by cajunaggie on 2006-08-23
For reasons unknown to myself I seemed to have removed my username from the sudo users list. Whenever I attempt to use sudo as a command I get the following output:
```
jonathan is not in the sudoers file.  This incident will be reported.

```
I can't access the users/groups GUI through the system>administration menu (I'm guessing as a result of not being on the sudo list). Does anyone know of a solution, or some sort of backdoor root mode I can get in to fix this?

---

### Post by amohanty on 2006-08-23
Ok try this:

1. from grub, drop into the recovery console by selecting the recovery option in the menu.

2. type **whoami** to verify that you are root.

3. then type **vi /etc/groups** to edit the groups file.

4. type **exactly** as provided below (if you have not used vi before). Stuff between < and > means keyboard key:
<ESC>
/
admin
<ENTER>

5. Use the arrow keys to go to the end of the line and type **exactly** as below (I am assuming your username is jonathan:
a
jonathan
<ESC>
wq
<ENTER>

5.5 (forgot) verify that the admin group is in the sudoers list by doing a **cat /etc/sudoers**
You should see **%admin ALL=(ALL) ALL**
as the last line.

6. reboot by doing a **shutdown -r now**

See if it works.

HTH
AM

---

### Post by nanotube on 2006-08-23
or instead of using vi, you could use nano, which is a more intuitive text editor, to perform these same steps (add your user to the admin group in /etc/group file). :)

---

### Post by amohanty on 2006-08-23
**real** men use vi... 

wait!! or was it emacs

:)

---

### Post by jackn on 2006-08-23
No Panic.

[Post #7]("http://www.ubuntuforums.org/showthread.php?t=239250"), no text-editing required.

Jackn

---

### Post by cajunaggie on 2006-08-23
My thanks to y'all for your assistance. I have sudo powers again! :cool:

---

### Post by kalikiana on 2006-08-24
> **cajunaggie said:**
> My thanks to y'all for your assistance. I have sudo powers again! :cool:

Just a litte tip for the future: You really should set a root password (sudo passwd root) just for cases like this. ;)

---

### Post by Ramses de Norre on 2006-08-24
No you shouldn't, what's the use of sudo if you set a root password too?
Best bet seems to me adding admin AND your username to /etc/sudoers, the change is small that both lines will get deleted and it wont harm when you get removed from the admin group.

---

