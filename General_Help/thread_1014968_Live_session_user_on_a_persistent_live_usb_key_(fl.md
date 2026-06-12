---
title: "Live session user on a persistent live usb key (flash drive)"
date: 2008-12-18
forum: General Help
---

### Post by Ben63 on 2008-12-18
Hi,

How can I get rid of the "live session user" or at least remove him the sudo rights?
I installed ubuntu live on my usb key with the software "create a usb startup disk", part of the ubuntu 8.10.
I use the persistent mode to keep my changes after reboot.
But any time I start on my usb key it logs on the "live session user" (also named "ubuntu") who has fulll rights. I would like to simply have the greeter asking me for the user I wanna use and it's password.
I can not find any documentation for it ; The sole thing I found about it is [http://ubuntuforums.org/showthread.php?p=6393378#post6393378](http://ubuntuforums.org/showthread.php?p=6393378#post6393378) but no solution is given in there.

Thanks

---

### Post by Ben63 on 2008-12-19
Anybody having an idea about this?

---

### Post by Cincinnatux on 2008-12-24
Ben, sorry you haven't gotten an answer yet.  Sadly, I'm underqualified to give you a worthy answer, but I'll share what little I know.  The only way I've found to eliminate the security risk presented by the live session user is to do a full install of Ubuntu to the USB pendrive (treating the pendrive like it was a secondary hard drive).  I have done this successfully with an 8 GB Kingston HyperX USB pendrive.

Best of luck to you,

Cincinnatux

---

### Post by emptythevoid on 2008-12-30
Alright, I might be able to answer this one.  Go ahead and boot your computer using your USB stick.  As you said, this should automatically log you in as the "live session user" also named "ubuntu" that has root access.

First, we're going to make a new user account for you.  Go to System->Administration->Users and Groups.  Tell it you want to Add User.  Make up a name for your account and enter a password.  Before you hit OK, though, you might want to check the User Privileges tab.  By default, the options to "administer the system" "configure printers" "connect to wireless and ethernet networks" and "share files with the local network" are NOT checked.  Since this is your account, I'd suggest checking all of the options (you'll still need to enter a password when you do something that can affect the system).  Once you've got all that taken care of, click OK.

Next, go to Sytem->Administration->Login Window.  Go to the Security tab.  Uncheck "Enable Automatic Login" and "Enable Timed Login."  These are the settings that are causing Ubuntu to automatically log into the live session user.  Unchecking these options will bring up the normal user/password prompt when you boot up.  

Now, at this point, if you put in "live session user" in the login screen and left the password field blank, you can still login as the live session user with root priviledges.  For some reason, this "live session user" doesn't show up as an account in the Users and Groups.  When I had this problem, I was going to just put a password on the account, and this is what I did:  Log in as the "live session user."  Go to System->Preferences->About Me and click on Change Password.  Leave "current password" blank and click Authenticate.  Go down to the next two fields and put in a strong password, then click Change Password, then Close.  

But when I logged off and went to log back in as the live session user, it wouldn't let me log in with the password OR leaving it blank.  It's as if the act of setting a password for the live session user makes the account unusable, which is ultimately the goal.  I have rebooted my machine to make sure the change is saved, and indeed I can no longer log in as the live session user.  Why this is the case, I cannot explain.  But it's working for me.  Hope this helps.

---

### Post by emptythevoid on 2008-12-30
PS: From what I've read, if your flash drive is large enough (like 8 GB at least), you can opt to perform a full, normal Ubuntu install on to a flash drive (provided you make sure that you have GRUB install into the MBR of the flash drive), however I've also read that unless you change some settings, the tmp and swap partitions are going to be on your flash drive as well and that may cause your flashdrive to wear out prematurely (since flash has a limited number of writes).  I know you can work without a swap partition (or leave the swap but adjust how "swappy" your system behaves) and you can make the /tmp as a ram disk, but it's beyond my scope of experience and would require some more research on the forums.

---

### Post by emptythevoid on 2008-12-30
Oh, and I suggest removing the Tracker program to prevent unnecessary activity on the flash drive.  Just go to Applications->Add/Remove, search for *tracker*, uncheck it, and apply changes.

---

### Post by Ben63 on 2009-01-06
Thanks a lot for the responses.

It worked well, I could set up a password for the user ubuntu and it doesn't log in automatically anymore in gnome :)
It still uses it to start the system though and when I do ctrl-alt-F[1..6] I can find ubuntu logged on ; though now that this has a password I guess it's not really a security problem.
I also wanted to add some restrictions for the user ubuntu in the /etc/sudoers file (using visudo).
"ubuntu ALL:PASSWD: ALL" ; not really sure it is totally correct but I got asked for a password now when I want to sudo with the user ubuntu.
Unfortunately, for some reason I don't understand, it never accept my password even if it is the correct password :(
I also cannot make a "su" from any user to any user other than root.
I have no idea why...


But the good point is that I didn't need to install ubuntu on the flash drive, just run the persistent live session on it :)
So for the /tmp and the swap, I guess in my case there is no swap and the /tmp is already a ramdisk.

---

### Post by Mooh Bear on 2012-10-13
Just did this today on Ubuntu 12.04. Edit file [FONT=Courier New][COLOR=DarkRed]/[/COLOR][/FONT][COLOR=DarkRed]et[/COLOR][FONT=Courier New][COLOR=DarkRed]c/lightdm/lightdm.conf[/COLOR][/FONT].

Change the line
```

autologin-user=ubuntu

```to
```

autologin-user=

```

---

### Post by wildmanne39 on 2012-10-13
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

