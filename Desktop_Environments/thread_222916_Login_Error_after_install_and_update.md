---
title: "Login Error after install and update"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Donald F. Robertson on 2006-07-25
After installing Ubutu and installing the updates, I get the following error message.  (This did not appear before installing the updates.)

"User's $HOME/drive file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

I tried to find a $HOME directory using both the graphical interface and the command line, but it does not appear to exist (with that case).

This doesn't seem to affect operation so far.  Do I care?  If so, how do I fix it?

Thanks!

-- Donald

---

### Post by Draknats on 2006-07-26
This is the message I get when attempting to login.  Except, in my case, I'm unable to login to the GUI at all, so I'm somewhat paralyzed.

Try going into the User section of the Administrative panel.  Select your user, and then make sure that in the advanced options tab you see "/home/yourusername" and not something else.  I'm not talking about where it says "bash" though, that's something different, I believe.

The particulars of this suggestion are likely quite erroneous (the tab might not be called "Advanced options"), and it's likely that your error message is caused by something completely different.  Regardless, this is what I need to do to fix my problem, except my ability to navigate the terminal is severely limited.  Though ironially, I think I fixed the problem that I was trying to fix in the first place (recklessly trying to install a windows wifi driver is what put me in my current GUI paralysis).  I didn't know that you simply had to use the command "sudo" to use root's priviliges.

I ought to link to this in my post.

---

### Post by tty01 on 2006-07-26
> User's $HOME/drive file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions

try a sudo chown username /home/username  
make sure the folder your gonna chown is with your username.

> This is the message I get when attempting to login. Except, in my case, I'm unable to login to the GUI at all, so I'm somewhat paralyzed.

this is normally the same problem as Draknats.  You guys dont have permission to your own home folder.  Your gonna have to boot into recovery mode and chown it from there.

---

### Post by Donald F. Robertson on 2006-07-28
Didn't work.  The command appeared to be accepted, but the error still appears.  Any other ideas?

-- Donald

---

### Post by Draknats on 2006-07-29
Same here.  I used that command, and it seemed to be accepted.  Then I typed Exit to return to the login GUI, but I received the same error message as before.
That command should correct the error I made which I strongly believe to have caused the problem in the first place.  The error being that I changed the home directory of user 'draknats' to /home in a reckless attempt to install a wifi driver.

THough, a possible alternative would be for me to create an entirely new admin account in the terminal, and then log in with that to correct the problem of the draknats account.  

Any ideas on why the chown command didn't work?  Or any idea on how I can create a new user?  I tried sudo adduser, but couldn't get it to work.

---

### Post by fensirien on 2006-07-30
try:
sudo chown -R username /home/username

the -R flag will make the command operate on files and directories recursively

---

### Post by Draknats on 2006-07-30
Making the command recursive didn't seem to do anything either.

As before, the first error message says:

"Uesr's $HOME/.dmrc file is being ignored.  File should be owned by user and have 644 permissions.

Second one reads:

"Could not set mode 700 on private per-user GNOME configuration directory /root/.gnome2_private/: Operation not permitted."

Any ideas?

---

### Post by fensirien on 2006-07-30
[http://www.ubuntuforums.org/archive/index.php/t-91455.html](http://www.ubuntuforums.org/archive/index.php/t-91455.html)

---

### Post by Draknats on 2006-07-31
I went through the bulk of that link's contents.  It seems as though the others are just trying to get rid of the benign boot error; I can't even boot into the GUI.  gksudo nautilus doesn't even work.

I tried this:

sudo chmod 644 .dmrc
sudo chown draknats .dmrc
sudo chmod 755 /home/draknats
sudo chown draknats /home/draknats

Being nervous of using the damaged username to fix this, I also tried 'su root' and omitting the 'sudo' (and appending /home/draknats/ to the '.dmrc' to ensure that it affects the correct directory.

Still, that didn't change anything.

When I try to do 'sudo chown draknats /home/draknats', it tells me 'draknats is not in the sudoers file', which makes a lot of sense. 

Is there not some way for me to revert draknats' user permissions to the default administrator permissions?

---

