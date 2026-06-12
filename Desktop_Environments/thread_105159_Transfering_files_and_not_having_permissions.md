---
title: "Transfering files and not having permissions"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Yoshimitsu8 on 2005-12-17
Hi Everyone,
Here is my situation. I'm trying to back up my files on another machine. One machine has SMB (using Breezy) working fine the other (using Hoary) doesn't. I have got to the point where I can transfer the files over to Breezy computer, however I don't have any permissions (make changes, delete, etc.) and it has a big pad lock thing on it (when you look at the folder or whatever). 

Basically I'm just backing up my stuff on the Breezy computer and then upgrading to Breezy on my current Hoary computer (another question, if I make another partition for my /home files, can I upgrade in the future without having to backup all my stuff, reinstall, and then transfer back?)

So I'm wondering how you transfer files onto a new computer and keep permissions (or gain permissions to files that you don't have permissions to)? 

Note: I know almost no command line

Thanks,
Another Ubuntu N00B

---

### Post by aysiu on 2005-12-17
[QUOTE=Yoshimitsu8]
So I'm wondering how you transfer files onto a new computer and keep permissions (or gain permissions to files that you don't have permissions to)? 

Note: I know almost no command line[/QUOTE] Well, you're about to learn. You're in Breezy, right?

To open a terminal, go to Applications > Accessories > Terminal

Let's assume, for the sake of these instructions, that the files you transferred are in a folder called *documents* on your desktop. Let's also assume your username on the Breezy machine is yoshimitsu.

After you transfer all the files, type this in the terminal ```
sudo chown -R yoshimitsu:yoshimitsu /home/yoshimitsu/Desktop/documents
```

**Note**: It's case-sensitive--capitalization counts.

---

### Post by afhp on 2005-12-17
[QUOTE=Yoshimitsu8] I have got to the point where I can transfer the files over to Breezy computer, however I don't have any permissions (make changes, delete, etc.) and it has a big pad lock thing on it (when you look at the folder or whatever). [/QUOTE]

Did the system actually ask you to log in when accessing the Samba share ? If not you're accessing it through a restricted guest account, hence the lack of permissions. Try to mount the Samba share logging into it as the user on the Samba machine.

Or use scp, that'll give you practice with the command line ;)

---

### Post by Yoshimitsu8 on 2005-12-20
Hey guys,
aysiu your command worked great. However now I have another problem. I have the files backed up on computer A (running Breezy) and installed a fresh install of Breezy on computer B. Now I'm trying to get the files off of A onto B, however I can't get the computer to show the shared files in network servers (under "Places"). I tried a few different things and nothing has worked. What is an easy way to share these files? I have tried the following:

-Right click on the folder and say "Share this folder"
-Tried random command line things from online trying to make it a public folder (all found from [http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway) )
-typing in smb://198.162.1.45/home/king and a few other combinations
-tried using the WINS server thing (but have no clue what that is)
-I tried making another user, but I didn't know how to give them access to the files  that was on the user I backed up the stuff, but I have no clue what I'm doing so that doesn't help.


It has been asking me for a username, domain, and password. I have tried EVERY combination of usernames on both computers, with the domain names of each computers (set when you share a file), and each password. I have tried like every combination and it never gets me to the files.
ANY help would be appreciated.
I am starting to really hate Ubuntu/Linux because it not user friend AT ALL. Everything says how easy it is, but it is not. You have know a lot about command line, permissions, networking, and tons of junk. I thought I had a small clue about computers, but I guess not.
Sorry it's late and I'm just really pissed off and I just want this crap to work!
Thanks

---

### Post by Yoshimitsu8 on 2005-12-20
Well there was divine intervention and it magically worked. I think what made it work was I set up network passwords for both computers and then used that, but it still seems a bit odd that the username and passwords weren't associated with one another. Oh well it worked and I'm fine until I have to do it again and I think I might be able to do it again.
Thanks again guys

---

