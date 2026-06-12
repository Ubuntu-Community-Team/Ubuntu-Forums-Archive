---
title: "SUDO dosen't seem to want to work."
date: 2005-12-05
forum: Desktop Environments
---

### Post by thespazzz on 2005-12-05
Before anyone askes yes i've checked on google and read the various articles.  None seem to pertain exactly to my problum.

Basicly I just installed Ubuntu,  logging into gnome there is the little update thingy in the top bar next to the clock.  It says I have updates available.  When I click on it I give it my password.  Then..... Nothing happens.

The same occurs basicly anytime I try a sudo command.

I checked the system log and i seem to be throwing these related errors.

08:03:11PM localhost sudo spazzz : command not allowed ; TTY=unknown ; PWD=/home/spazzz ; USER=root ; COMMAND=validate

08:36:11PM localhost sudo (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost= user=spazzz


Any idea's i'm totaly lost.

---

### Post by 23meg on 2005-12-05
Please post the contents of your /etc/hosts file. Do you get any errors when you sudo in terminal?

---

### Post by thespazzz on 2005-12-05
Here is my hosts file

127.0.0.1	localhost.localdomain	localhost	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And if I attempt to do anything from the terminal I get results like this 

spazzz@ubuntu:~$ sudo apt-get update
Password:
spazzz@ubuntu:~$
spazzz@ubuntu:~$ sudo ls
spazzz@ubuntu:~$ sudo vi /home/spazzz/test.txt
Password:
spazzz@ubuntu:~$

any command at all will just spit me back to a prompt with no output.

---

### Post by fpd on 2005-12-06
It is probably because **thespazzz** is not in the **sudoers** allow-file.  Try **man -k sudoer** to find a list of executables that you can run to view and edit your **sudoer** file.  To edit these files, you must be **su** (root user).  Maybe try **visudo** and put yourself under **root**.

---

### Post by thespazzz on 2005-12-06
That makes sense and i'm going to check it out.

Couple of questions though.  Doesen't Ubutu make the first user created during install a sudoer by default?  If so then why did it not do so for me?

Second of all if my account isn't a sudo enabled account then why isn't it telling me that in console when I attempt to sudo a command?

---

### Post by Sisyphe on 2005-12-06
Normally the command *sudo -l* tells you what you have the right to do using sudo.

I think that Ubuntu gives full access to sudo to the first user during install by making him/her member of the admin group.
Are you still part of that group ?

---

### Post by fpd on 2005-12-06
[QUOTE=thespazzz]That makes sense and i'm going to check it out.

Couple of questions though.  Doesen't Ubutu make the first user created during install a sudoer by default?  If so then why did it not do so for me?

Second of all if my account isn't a sudo enabled account then why isn't it telling me that in console when I attempt to sudo a command?[/QUOTE]
"First user as sudoer" - Can you tell us where you read that?  If I want to do **su** stuff, I either log in as **root** or jump from **fpd** to **su** and back when I am done.

"Second" - Perhaps Ubuntu wants to be super-duper-friendly, and they figure, no bad news is good news (that is to say, do not tell the user "No, you can not.")  If you log in as **root** and run **mail** you might see all the instances you tried to run a **su** command without proper privs.

Creating **user** accounts is to protect our (your) system by blocking us from many executables, files and directories.

---

### Post by doitashimashite on 2005-12-06
[QUOTE=fpd]"First user as sudoer" - Can you tell us where you read that?  If I want to do **su** stuff, I either log in as **root** or jump from **fpd** to **su** and back when I am done.[/QUOTE]

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Also, you can never login as root on a freshly installed Ubuntu system, unless you set the root password from a normal user account, like this:

sudo -s
passwd root

---

### Post by fpd on 2005-12-06
[QUOTE=doitashimashite][http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Also, you can never login as root on a freshly installed Ubuntu system, unless you set the root password from a normal user account, like this:

sudo -s
passwd root[/QUOTE]
Thank you for the link.  I noticed that I could not use root after installing.  I also had a whale of a time looking for dial-up ppp.  I gave up and fell back to Knoppix (a very forgiving Linux flavor) until I learned more from this forum on how to do it right.

---

### Post by BobSongs on 2005-12-06
To save you the bother of leaving the forum:

> The root account is disabled when you first install Ubuntu. The first user created during the installation has administrative rights on the system, and can run programs as root with [FONT="Courier New"]**sudo**[/FONT], using only their normal user password. For example: [FONT="Courier New"]**sudo apt-get update**[/FONT].

If you wish to use the root account in more traditional UNIX fashion, you can set the root password by typing [FONT="Courier New"]**sudo passwd root**[/FONT]. This will allow you to use [FONT="Courier New"]**su**[/FONT] or login as root on the console.

If you need a shell with root privileges, run [FONT="Courier New"]**sudo -s**[/FONT].

All uses of sudo will require the user's password.

The above text was swiped from the Ubuntu Linux [support page]("http://www.ubuntulinux.org/support/documentation/faq/root").

---

### Post by thespazzz on 2005-12-06
Alright... After doing some checking I have discovered that for whatever reason Ubuntu did not assign my user account sudo priveliges.  I'm working on fixing that now.

---

### Post by thespazzz on 2005-12-06
After doing some research on SUDO i must admit it dosen't make any sense to me.

How am I supposed to add myself to the SUDO list?

---

### Post by mcanada on 2005-12-06
I have been struggling with SUDO myself, but not in the same context as yours.

you can add yourself to the SUDO list by rebooting and selecting the Recovery mode from the GRUB prompt. This will log you in as the root user.

At this point you can type visudo and add your username into the list of allowable users.

---

### Post by thespazzz on 2005-12-06
I understood that part.  I don't understand how the sudoer file is setup.  How exactly do I enter myself into it?

---

### Post by mcanada on 2005-12-06
when you type visudo, the sudoers file is opened up with nano (command line text editor). In the file there is a section for users where you probably will find root in the list. Just copy what is already there but instead put your username "thespazzz".

When you are done modifying the file, hold down CTRL and hit the X key to exit. Confirm that you want to save the file and it will exit. That is all I did for my user.

---

### Post by thespazzz on 2005-12-06
Nevermind.  I figured it out.  I didn't understand the point of Alias's.

---

### Post by thespazzz on 2005-12-06
*laughs* Thanks mcanada.  I had JUST got it right when you replied.

---

