---
title: "Basic users administration"
date: 2006-10-04
forum: Desktop Environments
---

### Post by imaginos on 2006-10-04
The idea is to have 2 users on my computer. One has all privilegdes like root, and other user is there for everyday use (and it will be used by several people).
So, this "standard" user should not be able to perform administrative tasks. I would even like to make system dirs like (/etc, /bin, /sbin...) invisible to it, but on the other hand, "standard" user should be able to connect to the internet (ADSL connection) and that is done by starting a script that requires sudo command. Well, if user knows sudo command, he can damage my system, so it is not a good idea to tell root password to everybody. Is there a way to limit a "range" of sudo, but just for that particular user? It is that script that invokes ADSL connection that needs sudo (pppd), and people using computer should be able to connect/disconnect as they wish.

Since I want to disable "sudo" for this user for security reasons, and on the other hand, enable connection to internet using pppd, I am not sure how to make this work.

---

### Post by mark_g on 2006-10-04
I think you misunderstand the working of sudo, I know I did too in the beginning.
The idea of sudo is to let users execute a limited set of commands with another user's privileges, so they don't have full administrator rights, which is something you obviously don't want. All you need to do is edit the sudoers file, by executing 'visudo' and add a line like this:

username  ALL=(root) /usr/bin/pppscriptname

The ALL simply means this works on all of your pc's in the network or in your case probably just your single pc.

(root) means execute as root

/usr/bin/pppscriptname is the _full_ path to your script, it's important you don't just type 'pppscriptname' or someone could just create his/her own script pppscriptname with commands you don't want them to run

Hope this helps you out.

---

### Post by imaginos on 2006-10-04
Thank you for this info, now I see I didn't understand sudo at all. 

I followed your advice, and it works, but when I make launcher width command
sudo /usr/share/ADSLconnect
and put it on desktop it will not work unles i check "Run in terminal", and when it runs it opens the terminal and I have to enter users (not admins) password. It is bearable, but is there a way to avoid any entering of password in this case? The same launcher started by admin without "Run in terminal" will work, but started by user it will not.

And one more question:
Is there a way to FORCE font and desktop settings for this user (fonts, dpi and make some unremoveable icons on desktop)? 
And if I ever make more users, can I set their default/mandatory desktop settings and privilegdes?


---

I forgot to ask even more important thing.
User must not be able even to see some of the partitions, while I, as admin, must be able to see them all. I want user to see only it's home folder and one entire partition hdb5 (for music, video, etc...) The user must not be even aware of other partitions.

I tried editing fstab, and putting umask=007 for all partitions except the shareable one, but it didn't work. When user opens file browser there are all mounted partitions listed. There are even icons on his desktop! Users can not write to them, but it would be better not to wake up their curiosity by making them aware of extra partitions. :]

---

### Post by mark_g on 2006-10-05
I'm not sure I understand, but is ADSLconnect a shortcut to a shellscript you wrote or the script itself?
If it's a shortcut, you don't need to add this shortcut to the sudoers file, only the command this shortcut executes.
Also, if you want to run graphical programs with sudo, you need to use the command gksudo instead, but I'm not sure this is the case.
To avoid typing the password, you could modify the sudoers file (always use visudo to do this!) as following

george   ALL=(root) NOPASSWD: /bin/touch, /bin/cat

About the font and desktop settings, when you create a new user, all files in the /etc/skel directory are copied into the user's home
directory, so you could set all files and settings appropriately in that directory.
To prevent users from changing this, you can set the normal permissions appropriately or set them immutable. When they are set immutable, not even root can delete them. You can do this executing 'chattr +i file' and if you want to delete them (as admin) you first need to do 'chattr -i file'
If you like an easier alternative, you could check out Kiosk, a gnu
program that allows the setting of restrictions.

About being unable to see the partitions, also just setting permissions appropriately will stop users from reading and writing to these. I don't know how to hide these, although there probably is a way to do so. If your data is really important, consider using TrueCrypt to store them in hidden, encrypted volumes.

---

### Post by imaginos on 2006-10-05
&#65279;> I'm not sure I understand, but is ADSLconnect a shortcut to a shellscript you wrote or the script itself?
It is a launcher. I created it by right clicking on desktop and choosing "Create laucher". In the "command" field I entered: sudo /usr/share/ADSLconnect

> If it's a shortcut, you don't need to add this shortcut to the sudoers file, only the command this shortcut executes.
But the laucher calls the script, and script calls several commands that require sudo, so I thought that the best solution is to sudo the script itself?
Am I wrong?

> To avoid typing the password, you could modify the sudoers file (always use visudo to do this!) as following
george ALL=(root) NOPASSWD: /bin/touch, /bin/cat
I've tried this, but I still can not start ADSLconnect unles i check "Run in terminal" and manually enter password.

BTW, this hint of yours triggered one question: is there the (official or unofficial) standard or rule about where should I put files that are to be shared (rwx) between users? It seams natural to place them all in /usr/share, but is it a good practice in terms of security?

> About the font and desktop settings, when you create a new user, all files in the /etc/skel directory are copied into the user's home directory, so you could set all files and settings appropriately in that directory.
Thank you, this is the info I was looking for.
Is there a good web page describing purpose of Ubuntu/linux directories. I managed to find descriptions only for "first level" dirs (/etc, /bin, /boot...), but not for deeper dirs.

> If you like an easier alternative, you could check out Kiosk, a gnu program that allows the setting of restrictions.
When I start Applications->Add/Remove there is a Kiosk program, but information about it states that Kiosk is for KDE envirnoment. Is it safe to try installation on Ubuntu/gnome?

> About being unable to see the partitions, also just setting permissions appropriately will stop users from reading and writing to these. I don't know how to hide these, although there probably is a way to do so. If your data is really important, consider using TrueCrypt to store them in hidden, encrypted volumes.
Is there an init script specific to every user? As far as I understand, inittab calls scripts in init.d/rcX.d (via /etc/rc X) and after all of those scripts are executed, login screen comes out and asks for username and password. Is there another script/set_of_scripts that is invoked after the user logs in? If so, is it possible to unmount certain partitions in one of those scripts?

Even better solution would be mount only crucial Ubuntu partition in fstab, and let admin's startup script mount other partitions that I want to remain invisible to other users.


Thank you for the answers!

---

### Post by mark_g on 2006-10-06
There is no init script specific to every user. Gnome and KDE have their own way of autostarting certain programs. In KDE, you just put them in /home/username/.kde/Autostart. In Gnome, you can add them in the Control Center > Sessions > Startup Programs.

Creating a script that unmounts certain partitions seems a good solution to me. If you want to use the rcX scripts, you could mount the basic partitions in runlevel 2 and when you need the other ones, you can go to runlevel 3, by typing 'sudo runlevel 3'.

For a description of the dirs in a unix/linux system, this is a nice graph:
[http://www.secguru.com/files/cheatsheet/linux-file-structure.jpg](http://www.secguru.com/files/cheatsheet/linux-file-structure.jpg) There are minor differences between different linux distributions concerning the file structure, but local programs are typically added in /usr/local/bin.

I wasn't aware Kiosk was KDE-only (although the K is a subtle hint of course). There is a Gnome counterpart called pessulus.

About executing the script without giving the password, it works for me in KDE. I don't really know why it doesn't in Gnome. I'll try to do it in Gnome when I have the time and let you know the difference.

---

### Post by mark_g on 2006-10-09
I tried it in Gnome and it worked perfectly for me. I just followed these steps:

1. add user rights using visudo:
> testuser ALL=NOPASSWD: /home/otheruser/myscript

2. create a launcher on the desktop
command: sudo /home/otheruser/myscript
run in terminal: not checked

---

### Post by imaginos on 2006-10-09
Thank you, 
now it works when I put the line without (root), as you suggested. Great! :)

BTW, the filesystem chart is very usefull.

I am now trying to mount some partitions for admin user via startup called script. I thik I will have to edit sudoers file, as you said.

Thanks again! :)

---

