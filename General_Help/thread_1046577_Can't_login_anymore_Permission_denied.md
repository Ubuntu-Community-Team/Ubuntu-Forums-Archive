---
title: "Can't login anymore: Permission denied"
date: 2009-01-21
forum: General Help
---

### Post by phonky on 2009-01-21
Hi there

strange things happening...

I restored a previously backuped partition with PING
(Partimage Is Not Ghost).

That all went fine.

On bootup, grub finds the correct partition, and starts booting.
The familiar "xubuntu" blue bar comes up, and loads fine.

However, at the end of the process, when gdm should come up, I don't get
any login screen. Instead I get the plain text (tty) login screen.
I can enter any user name, but on enter I immediately get
"Permission denied".

No root or user login. No slightest idea what to do at this point...
Anybody a suggestion? thanks

---

### Post by LowSky on 2009-01-21
[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html)

---

### Post by Titan8990 on 2009-01-21
Choose Ubuntu recovery mode from the grub window. When prompted, select the root shell.

From here you can add a new user:


adduser USERNAME

then add them to the admin group:


adduser USERNAME admin


Give it another try with the new user and see if it could log in.

---

### Post by gjoellee on 2009-01-21
> **phonky said:**
> Hi there

strange things happening...

I restored a previously backuped partition with PING
(Partimage Is Not Ghost).

That all went fine.

On bootup, grub finds the correct partition, and starts booting.
The familiar "xubuntu" blue bar comes up, and loads fine.

However, at the end of the process, when gdm should come up, I don't get
any login screen. Instead I get the plain text (tty) login screen.
I can enter any user name, but on enter I immediately get
"Permission denied".

No root or user login. No slightest idea what to do at this point...
Anybody a suggestion? thanks

I found this: > What?! You forgot your password? What are you going to do now? You can't reinstall; you have all your critical files on your machine!

No big deal. Don't sweat it. We can change your password so easily it's not even funny. 

The Howto:
1. Boot up your computer, and when you see the screen that says something like "Press ESC to enter grub," press ESC (the escape key) as soon as you can. 

2. Now you should see a menu with many options. Use the arrow keys to navigate to the newest kernel (the one with the highest number) that has "(recovery mode)" written next to it. Now, hit enter (return).

3. Next, your system should boot up normally. BUT, you WILL NOT see the boot splash. Don't worry about that. Lots and lots of text WILL fly past you.

4. Now you are at a root shell. 

5. Type

passwd username

replacing username with your username

6. Now a little thing will come up and say "New UNIX Password" or similar. Type the new password that you want. Hit enter. Type it again. Hit enter

7. Then, your password has been changed! Type

shutdown -r now


8. Your system is now rebooting. Once it comes back up, login with your new username and password.

9. There is no step nine.


That was easy, too easy. Congratulations! \\:D/ 


---

### Post by Titan8990 on 2009-01-21
The above is missing a step that was added in 8.04 and is also in 8.10. You must select the option to get a root shell, it doesn't just "happen" anymore.

---

### Post by phonky on 2009-01-21
Thanks to the fast replies guys, but...

I think I haven't been clear.
I know my password.

When I am at the login prompt, I can only
type my username (or root, or whatever), and immediately get
"Permission Denied" when I press Enter -

BEFORE I can enter the password!

OK so far. Restarted in recovery mode and got to the
root shell as suggested. 
When I type
```
passwd USERNAME 
```
I get
```
passwd: Permission denied
passwd: password unchanged
```

And the last suggestion:
```
adduser SOMENEWUSERNAME
```
yields
```
Adding user SOMENEWUSERNAME...
Adding new group SOMENEWUSERNAME (1000) ...
Adding new user SOMENEWUSERNAME with group SOMENEWUSERNAME
Creating home directory /home/SOMENEWUSERNAME ...
Copying files from /etc/skel ...
passwd: Permission denied
passwd: passwd unchanged
Try again? [y/N]
chfn: PAM authentication failed
adduser> /usr/bin/chfn SOMENEWUSERNAME returned error code 1. Exiting 
```

Looks like my password file is corrupted or even
that my users do not even exist...
althought /etc/shadow has an entry with my username...

I am baffled

---

### Post by bigbrovar on 2009-01-21
tryrunning this in terminal.    ```
sudo passwd --unlock root
 sudo usermod --lock root
```  could be a [bug]("https://bugs.launchpad.net/ubuntu/hardy/+source/shadow/+bug/238755")

---

### Post by phonky on 2009-01-22
Thanks for all who helped guys.

I think my restore of the partition with PING didn't work terribly well...
I then realized that ALL programs needing some shared libraries, when trying to execute, displayed an error message:
"Invalid ELF format"

That was even the case for man, startx, etc. No clue what this means...

So in the end I decided to do a rather unelegant, cumbersome, ugly, etc. etc. etc. "workaround" and re-installed the whole xubuntu - at considerable time expenditure and even some data loss (own stupidity by backing up multiple user accounts with a single command (cp -rpf) from a specific user without back-checking that all files were there - of course the other user's file are not all readable from there...).

But at least it is all running now...
More lessons learnt

---

### Post by jimv on 2009-01-22
That's sad.  I just used PartImage (I booted up with an Ubuntu Live cd and installed PartImage) the other day and it worked perfectly.

---

### Post by phonky on 2009-01-23
Well, you know, I maybe had to pay the price for the well known
problem of "I-am-a-long-time-techie-and-dont-need-to-RTFM".

I actually just wanted to save one single partition from a whole bunch on my old drive. Of course, without reading the manual, I just followed the startup of the PING booting process via live cd. That made an image of my partition, but with the whole hd info so it would need to restore all the other partitions too (my interpretation). 

Well, in short, I did a whole lot wrong, I think. That's why I am blaming myself in the first place.

---

### Post by sh4d0w808 on 2009-01-23
phonky: If U want to create a backup about your current Ubuntu system, I recommend to try out Remastersys.

---

