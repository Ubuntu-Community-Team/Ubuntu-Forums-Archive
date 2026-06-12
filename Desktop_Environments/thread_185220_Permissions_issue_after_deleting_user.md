---
title: "Permissions issue after deleting user"
date: 2006-05-31
forum: Desktop Environments
---

### Post by gt24 on 2006-05-31
I am running dapper and fiddling with a few things.  The account made by the installer (I shall dub it AccountA) is not used by me while AccountB (so dubbed by me) is my primarily used account created afterwards.  AccountB is on the Sudo'ers command chain and everything is peechy keen.  So, today, I decide that AccountA is no longer necessary and I delete it.  Big mistake...

Delete AccountA.... now AccountB has NO administrative rights.  I want to readd the AccountA but I don't know how to do this at the command line level and I haven't found an appropriate walkthrough on this forum.

Thus, I thought I was post my difficulties here.  First off, why does this happen?  Second off, how do I fix it?

<edit>
My groups ARE messed up.  My account is no longer permitted sudo access and in fact the account permissions are pretty slim.  So.... where do I need to append my user account in order to fix all of this?  Also, I used the graphical user utility to give me admin access before (which I don't have access to now).  I wonder how that graphical utility operated...
</edit>

---

### Post by XAsmodeanX on 2006-05-31
You can recreate the user with adduser and then set all the information for it and the password.  Alternatively check your /etc/sudoers file and make sure that you have this line:

root    ALL=(ALL) ALL
[username] ALL=(ALL) ALL

By just putting your username and not using groups to allow sudo you can bypass the group problems.  Give that a try, if it doesn't work then just comment it out.

---

### Post by gt24 on 2006-05-31
Thanks for the information, but I finally got everything to work and I have a walkthrough.

1) Log out, go into recovery mode
2) In recovery mode, edit /etc/group (I prefer nano as the editor, you do not and can not use sudo in this mode)
3) Add your username after the : for sudo and admin.  The group numbers are 27 and 112 respectively.  (If this doesn't work, come back to this step later on and add yourself to admin, group 0.  I don't think this is necessary though...).  Save and exit.
4) Reboot (shutdown -r now) and log in.  Things won't be fixed yet!!
5) You should now have System > Administration > Users.  Go there, type in your password, and then edit your account.
6) Readd yourself to ALL groups (yes, ironically this was done before I deleted user at UID 1000).  Apply changes
7) Logout, Login... enjoy your FIXED install.

Well, I learned something today, always good.  :)

---

### Post by garyng on 2006-05-31
login in as root and change /etc/passwd and /etc/group, that is where the account name <-> uid/gid mapping is. This way, you don't need to mess around other settings.

---

### Post by christinel4t on 2006-07-11
> 1) Log out, go into recovery mode
2) In recovery mode, edit /etc/group (I prefer nano as the editor, you do not and can not use sudo in this mode)
3) Add your username after the : for sudo and admin.  The group numbers are 27 and 112 respectively.  (If this doesn't work, come back to this step later on and add yourself to admin, group 0.  I don't think this is necessary though...).  Save and exit.
](*,) I tried this but I was told I did not have permission to write to this READ ONLY file.  I tried nano, vi and open office.  It says I am not the owner so I cannot use chmod either.  I have **_no_** root or administrative pasword as my friend changed his permissions while inside his own account, with the idea od then creating a new root account.  Any ideas?

---

