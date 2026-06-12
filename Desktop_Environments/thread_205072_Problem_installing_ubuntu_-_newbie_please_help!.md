---
title: "Problem installing ubuntu - newbie please help!"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Ferdi on 2006-06-27
I'm new to linux, so you'll have to bear with me.  I do have a little experience with unix, but it was very limited.  I have tried to install 2 different (SuSE 10.1 and Ubuntu) distributions of Linux on my computer, and have had problems with both installations.  I've tried SuSE 10.1 (which was a purchased version) and was able to get it installed and to the KDE desktop.  However, upon reboot it gave me a service module error and took me to the login:  but it would not let me login.  I know the login and password, because i used the same thing for both.  Anyways, I then gave up (after 2 reinstalls and a repair) and tried Ubuntu, which I just download from the site the other day.  It installed, however when I restart the computer it boots up and goes to a screen saying, **"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and group gdm.  Please correct the ownership or GDM configuration and restart GDM."**  It then goes to 

[B]Ubunta 6.06 LTS ferdi tty1
ferdi login:[/B]

(The word "**ferdi**" above is my name which I used to keep everything simple for myself during the installation process.)  Can anybody help, I really want to get Linux to work on my computer and don't want to purchase a Windows XP OS.  Any advice will be appreciated.  Keep in mind that I'm new to this and will need some detailed advice if possible. Thanks.

---

### Post by alanphil on 2006-06-27
It would help to know the following:

1. What are the specs on your computer? Make, model, etc
2. What Ubuntu CD did you download and install?

---

### Post by Ferdi on 2006-06-27
AMD 700 Mhz processor (Athlon, I believe)
35 gig harddrive
256 MB memory
FIC motherboard (I believe)
Sis based graphics card
Linsys 10/100 ehternet card
unsure of which sound card.

It was put together by a store, so there is no "brand".
I downloaded the ubuntu cd that is for the x86 versions, since the processor is not 64 bit.  The computer is probably 6-7 years old if that helps at all.  Please let me know if you need anything else. Thanks

---

### Post by Ferdi on 2006-06-28
No other help?  I'm currently trying a reinstall of the Dapper live-install CD.  I'm guessing there is some hardware conflict, since the computer is old.  But it would be nice to get a little guidance as what to do at the command prompt.  It won't let me use the **su root** command, because it asks for my password and when I type it in it says "authentication failed".  I know the password is correct because I used the same one for the local user account.  Any help?

---

### Post by alanphil on 2006-06-28
Ferdi -- Does Ubuntu run OK when you boot from the CD?

When you see this prompt:
Ubunta 6.06 LTS ferdi tty1
ferdi login:

you should try to login using your "ferdi" password. Not a root password. So you will enter user name, then user password for ferdi.

If you are seeing the same error message as before, you will need to change to the /var/lib/gdm directory and fix the permissions and ownership issues and see if that helps. Continue this thread if you can get that far....

---

### Post by ffderrick on 2006-06-28
It has been my experience that most linux distro's install better on older hardware.  If the Install Cd starts and works properly, your hardware is supported.  There may be something wrong with the download.  Did you check your download with md5sum? 
md5sum is a way to check a file against the original to make sure it is the same and not corrupted.
You can google md5sum to learn more.

---

### Post by shrift on 2006-06-28
Hmmm a couple of things.

Your PC name is "ferdi" correct? Are you saying that you ALSO made your USERNAME, and PASSWORD to be "ferdi"?

Just trying to figure out if your using the correct info to login to the PC. 

The GDM thing seems like a problem, but you should still be able to login to the TTY console.

Ubuntu does not use the "su root" command. We use "sudo" you simply type sudo before any command that requires root access. There is not root account on an ubuntu machine.  So essentially you just need to log into the machine with the username you setup during the install, and the password you chose to go along with that. The "root" or more accurately the "sudo" password is going to be the exact same password as the you originally setup. So, to make it simple, there is only one password, and it is the only one you entered during the install.

Ok, so if you can get logged in to the TTY terminal, then we can start getting that GDM issue fixed. Let me know if you get in there.

---

### Post by Ferdi on 2006-06-28
I was able to log in the the TTY terminal.  I then used the command "**sudo chown root:gdm /var/lib/gdm**" as suggested by someone on another thread.  I then logged into the root account with the command "**sudo -i**" and used the "**shutdown -r now**" command to restart the computer and whala!!! It booted in to graphical log in screen.  However, after shuting the computer down again and rebooting, it now goes to the same blue and gray screen, but with a different message.  It now says "**could not start the X server (your graphical environment) due to some internal error.  Please contact your system administration or check your syslog to diagnose.  In the meantime this display will be disabled.  Please restart GDM when the problem is corrected.**"  Afterwards I'm able to log in to into the root account and use the shutdown and restart command to get to the graphical user log in, but this is an annoying process and there's no way my parents or brother will be able to figure this out.  Any other ideas?  I haven't tried the md5sum program yet but will try tomorrow or friday if nothing else works.  As far as the PC name, login and passwords I used the same thing for all of them which is "ferdi".  Should I change them to something else, if so please advise how to do this.  One final thing, ubuntu runs perfect from the CD and perfect once I get to the graphical user login, it's just the inital bootup.  Thank you.

---

### Post by shrift on 2006-06-29
Great. That is what I was going to tell you to do once you got logged in. No need to change your username or password if it's working.

When you get the GDM message, tell it that yes, you want to view the details. Scroll to the bottom of the message and read the last 1/4 of it or so. There should be some helpful information in there. After you close that debug thing, it will ask you if you want a detailed report, you can look at that too if the first part wasn't informative enough.

Let me know if you need help figuring that out.

---

### Post by Ferdi on 2006-06-29
Actually the blue and gray screen only has an "OK" at the bottom.  There is no where to select to view the details or a detailed report.  That's why I'm kind of lost as to how to know what is exactly wrong.  Is there a command I can type at the ttyl prompt to look at a report or is there somewhere to pull up a report?  Maybe there is something I can look at or adjust once I can get to the GNOME desktop.  I can get there if needed, it just requires me to shutdown and restart the computer to bypass that error message.  But that is kind of strange that it brings the message up the first time, but after restarting it seems to bypass it and go to the graphical login for GNOME.  Any ideas?

---

### Post by butternut on 2006-09-19
I went through the same problems. There's a simlar thread in which I posted a potential explination and hint toward's a solution.

[http://www.ubuntuforums.org/showpost.php?p=1517449&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=1517449&postcount=6")

My guess is, that for some reason, your root filesystem is mounting with errors, and remounts as read only, which causes issues because gdm probably needs write access to some folders. The issue is likey to be found in /etc/fstab which is the file responsible for mount configuration at bootup.

Hope this helps :-)

---

