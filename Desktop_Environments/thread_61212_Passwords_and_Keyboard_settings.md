---
title: "Passwords and Keyboard settings"
date: 2005-08-30
forum: Desktop Environments
---

### Post by groucho on 2005-08-30
Hello all,

   1. Is it possible that the keyboard settings for individual users be completely different, such that you could be typing something with certain keys for one user and be typing something completely different for another. 

   2. Is it possible that the keyboard settings in the text editor be different than, say, the settings when you run a SUDO or try to authenticate to run some root-level app through the GUI?

The reason I ask is, well first I'm quite the linux/ubuntu newbie (installed yesterday and LOVING it!!), but also I recently ran into a problem:

 After creating a second account for my girlfriend, everything worked fine. But after logging her out, I was unable to login to my main account. Moreover, the root password consistently failed when I tried to sudo from her account.

 I opened a text editor and realized that one of the characters wasn't appearing as it should. The problem was the keyboard settings (I had initially selected the keyboard as default CA instead of default US on my main user account, but I switched it over. it appears that this doesn't switch the default, so my GF's account was also using default CA).

 So now THAT'S fixed, and my password types fine into a text editor. But I still can't logon!!

 So, fastforward, I reset my root and main user password by overriding the grub menu, and now I can logon in my main user account and do all the admin stuff there, but I STILL can't do any sudo commands from my girlfriend's account (I get "incorrect password" or something to that effect).

Any ideas? I'm 99% sure it's got something to do with the GUI and the keyboard settings, but I'll be darned if I can figure it out, and I've not been able to find any posts on it.

Any help would be much appreciated!!

---

### Post by ebrowne on 2005-08-30
Hey,
The sudo password is the users password.  If you want your girlfriend to be able to execute commands as root you have to add her to the sudores file by doing a 
% sudo visudo

And add her account to the file goolgeing sudoer should help.  But you can always add admin to her groups.



Hope this helps.

---

### Post by stoffe on 2005-08-30
[QUOTE=groucho]Hello all,

   1. Is it possible that the keyboard settings for individual users be completely different, such that you could be typing something with certain keys for one user and be typing something completely different for another. 

   2. Is it possible that the keyboard settings in the text editor be different than, say, the settings when you run a SUDO or try to authenticate to run some root-level app through the GUI?

The reason I ask is, well first I'm quite the linux/ubuntu newbie (installed yesterday and LOVING it!!), but also I recently ran into a problem:

 After creating a second account for my girlfriend, everything worked fine. But after logging her out, I was unable to login to my main account. Moreover, the root password consistently failed when I tried to sudo from her account.

 I opened a text editor and realized that one of the characters wasn't appearing as it should. The problem was the keyboard settings (I had initially selected the keyboard as default CA instead of default US on my main user account, but I switched it over. it appears that this doesn't switch the default, so my GF's account was also using default CA).

 So now THAT'S fixed, and my password types fine into a text editor. But I still can't logon!!

 So, fastforward, I reset my root and main user password by overriding the grub menu, and now I can logon in my main user account and do all the admin stuff there, but I STILL can't do any sudo commands from my girlfriend's account (I get "incorrect password" or something to that effect).

Any ideas? I'm 99% sure it's got something to do with the GUI and the keyboard settings, but I'll be darned if I can figure it out, and I've not been able to find any posts on it.

Any help would be much appreciated!![/QUOTE]
 When you do sudo, you use your current users password as confirmation that you know what you are doing. So, for doing sudo work when logged in as your girlfriend, you'd have to use her password (provided she's a user allowed to do admin ops) or switch users to your account. 

You can switch user in a terminal only with the command "su username", leaving the desktop logged in as your gf, but allowing you do enter commands as you, with your pw.

Hope that gives a few clues. :)

---

