---
title: "Ubuntu Login Problems"
date: 2005-12-14
forum: General Help
---

### Post by galvatron1983 on 2005-12-14
Hiya, 

Thanks to the forum for your help on getting me started on Ubuntu, unfortunately I have a bigger problem that Im totally stumped on. 

I successfully installed Ubuntu on a partition on my hard drive shared with Win XP. For some reason everytime I get to the Ubuntu login screen upon start up, it wont accept my login details. Im pretty sure I carefully entered my login details when I was asked to create them during installation, but it wont let me in. 

Ive treid variations on spelling and case but nothing seems to work, and I cant tell if its my username or my password or both thats wrong. Ive already tried a reinstall, and the same problem occurs. 

Have I got some kind of corrupted installation? Can anyone help?

---

### Post by kaamos on 2005-12-14
What is the error it gives you?

did your password of username happen to contain spaces?

---

### Post by galvatron1983 on 2005-12-14
The error I get is 

Incorrect username or password. Letters must be typed in the correct case. 

I took great care typing the username and password when creating the account during installation. Im pretty sure caps wasnt on, and I didnt put any spaces in....

Will I need to reinstall again or is there a way to recover my passwaord from a command line?

---

### Post by RAOF on 2005-12-14
Boot into recovery mode (from the Grub prompt at the very start of booting), and then run "passwd <yourusername>".  That should set your password to something new.

---

### Post by galvatron1983 on 2005-12-14
Just booted into the recovery mode and got to the Unix command line, typed in the line suggested and I succesfully managed to change the password to what I think was my username....still no luck, ubuntu refuses to log me in. 

It must be something to do with my username. Is there a way I can access a list of the user accounts on the machine from the command line?? There must be something wrong with the spelling of my username. 

Thanks a lot for your help btw....

---

### Post by RAOF on 2005-12-14
The "passwd" command only works on usernames that actually exist.  So, for example, if I type "passwd chris", it works, 'cause that's my username.  If I type "passwd notauser" it says "unknown user notauser".

This suggests that there's something else wrong.  Can you login at a terminal?  Press Ctrl-Alt-F1 once Ubuntu has booted to get to a terminal-login prompt.  If you can login there, it must be a problem with the graphical login manager.

---

### Post by galvatron1983 on 2005-12-14
Got to terminal and entered my username and password. Successfully logged in this way. I got to a trevor@ubuntu :~$ prompt, where trevor is my username. 

I tried again just to see what happens and it failed to log me in at the command line the second time. So I went through the process of changing the password at the command prompt again, got back to the ubuntu login window and its still refusing to log me in...

This is getting weirder....

---

### Post by Ted_Smith on 2005-12-26
Same problem for me too. I tried console and GUI login and I get refused every time. I have tried the passwd command which said user not recognised (which is odd because I was logged in for over a month before rebooting!). So I used 'useradd' to create a new username with -p password, rebooted, still not joy. Locked out. Great :-(

---

### Post by algaris on 2005-12-27
I am also having the same problems as the above. Anybody help out?

---

### Post by Ted_Smith on 2005-12-28
This is driving me mad. Here's what I've done so far.

Rebooted and used the Recovery Console as root. Ran 'useradd ted', then I ran 'passwd ted' and entered a password for me. I tried to run the -m switch with useradd so it would create the Home directory of 'ted' by default but it didn't work for some reason. Rebooted. Login accepted...hooray I thought....but then the errors came. I can't remember them all now, but it started with 

"Your home directory is not listed as 'home' but it does apppear to exist. Do you want to login with the root (/) directory. It is unlikely anything will work unless you use a failsafe session". 

I click Yes, but then I get "Your $HOME.dmrc file has incorrect permissions and is being ignored. Must be owned by user with 644 permissions" or something like that...I can't quite remember. I click OK to that and then it says something about the session lasting less than 10 seconds and there may be a problem with the installation etc etc. I click OK and I get thrown back to the GNOME login screen. 

So I Ctrl Alt F1 to the terminal. Login as ted and that works. I type 'ls' and navigate to 'home'. In there (to my delight) is my old home folder but it's been renamed to 'ted2'. In ted2 is all my stuff!! So I tried to rename 'ted2' to 'ted' using 'rename ted2 ted' and vm but neither worked. I was hoping I could change the folder name and then reboot and all the files it needed earler would now be found! But no joy there either. Basically whenever I tried to sudo it didn't prompt me for the root password and whenever I tried to login as root and enter the password it says incorrect password. Great!  

This is why I find it so hard to keep with Linux because nothing is ever easy! As much as I want to grasp it problems like this really put me off. I just want to login in! Help!

Ted

---

### Post by galvatron1983 on 2005-12-28
Im hoping to get into Linux, and at first I was a little put off by how command line heavy it was, have being spoilt by the seamless all-GUI experience of Mac OS X. Despite this Im keen to learn and get everything working. 

I just treid to reinstall Ubuntu using an official pressed Ubuntu install CD. Got back to the login screen, and once again Im being refused entry, same problem. 

Could it be something to do with my PC set up??? :confused:

---

### Post by Ted_Smith on 2005-12-30
Have you tried all the things I tried in my last post (post 10 of this topic)? What results did you get if so?

---

### Post by Ted_Smith on 2006-01-01
I have given up and gone for a re-install too. After installation, and while logged in, I did the 'sudo passwd myusername' command first, and entered a new password before rebooting. I rebooted, and it seems to be OK - it's let me in. 

I recall reading a week or two ago (forgot to copy the URL, sorry) that there was a bug in the iso packages in the settings of one of the files that affected users in the way we are having problems. It was something to do with a value being shown as an * instead of a , or something, visa versa maybe, in one of the system files. I can't emember anything more than that though. I then read that this had been corrected in all new iso's. So may I suggest you re-download the latest Ubuntu iso and re-install from that instead of the one you're using. I would add that this post was only a couple of weeks old so this is a recent discovery. The posting was at LinuxQuestions.org I think. 

Let us know how you get on. I seem to be fixed now though.

---

### Post by galvatron1983 on 2006-01-01
Just out of boredom I attempted to change the password of my user account in the recovery mode just to see if Ubuntu might start letting me log in. I decided to use something simple and have a single letter as my password. After seeting the password and loading GNOME it logged me in! 

I tried resetting the PC to log in again. I entered my log in details and it refused me, so I thought here we go again. Strangely I entered the same details again and I was logged in...bizarre! 

No I havnt tried any of the steps you described earlier, they seem a little daunting to a GUI spoilt mac user like me! :???:

---

### Post by Calib on 2006-01-11
Ugh.  Excact issue as you guys.  Sold a 3800 Inspiron on Ebay -- thought I might try to send it out to the buyer with Ubuntu 5.04 on it.  Laptop has no NIC card for web updates.

After install -- and close attention to Username and Password: it won't except the log-in.  I went into the recovery mode and went through same steps as discribed in the discussion.

---

### Post by FloSynergy on 2006-01-11
hi all,

i'm having the same issue.
can't log in as su in concole, can't sudo stuff. ready to chuck my laptop at the wall.:mad: 

going to see a friend tonite who is a real linux expert, but he works with slackware.
still, i'm hoping he'll have an answer.

good luck.

---

### Post by Lizm on 2006-01-11
I've got what seems to be the same problem. 
Total Linux nooby altho trying to upgrate programming skills
Used the Breezy iso from 10 Jan, ie the latest version, but it asked for user name and password multiple times during installation until I cancelled out. It appeared unable to set up the username. 
now won't let me log in 
There's a definite bug in the installation files but with a family on holidays around me I don't have opportunity to take the reporting much further at the moment. 

Any suggestions as to next step?

---

### Post by habpi on 2006-01-11
I remember I had that problem when I gave a first try of Ubuntu 5.04. Lately I installed SUSE 10.0, but it's cumbersomely slow, and not a good choice for my scientific programming. So I added Ubuntu 5.04 (the same CD) on a separate drive, and had this problem AGAIN :rolleyes: 
I have tried to log in console and mess around, but cannot get in via Gnome. 
Well, I will give 5.10 a shot, to see what happens.

---

### Post by jerrykenny on 2006-01-11
This is really weird guys . . . 

a good script to add a new user would be

useradd -m -G audio users video sudo gdm cdrom -s /bin/bash fred

keep the username all lower case . . . . no spaces

then do 

passwd fred

and give fred a password.

Good luck

---

### Post by Ted_Smith on 2006-01-12
As per my earlier posts, the way to resolve this is as soon as Ubuntu has finished the install, Ctrl Alt F1 to the non GUI console, log in(which it allows when not in GUI) and run 'passwd username' and repeat the password that you used during setup for your username (even though you just used to log into the console). The problem is that the installer is not recording the username and password properly during install and when you reboot you lose the login session entirely. 

Once you've run passwd you should then be able to reboot and log in using the GUI. If you're beyond that stage (like I was at first) just accept the inevitable inconvenience of having to re-install the OS and then run the above. Once you've gone beyond that initial log in you're doomed. 

Ted

---

### Post by FloSynergy on 2006-02-10
are you sure about that?

my friend helped me to sort this problem out by entering a non-gui console, and then changing the su-password to be identical with the root password. it seems that this is not necessarily identical and can cause the kind of trouble encountered in this thread.

---

