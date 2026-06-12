---
title: "How do I login as root ?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by jbarntt on 2006-03-05
Just installed 5.10, dual boot with Windows. I need to configure a ppp connection for my modem. I could do it with the "Live" from CD version, but not with the installed version, which I attribute to my inability to login as root.

I can go to a terminal window and su to root, which I had to do to edit lilo.conf, so that at bootup I could choose which OS to boot, but I really don't want to do this for every admin thing I need to do.

I tried System-> Administration-> Login screen help

and was prompted for a password. My user and the root user have the same password, so no doubt what to enter, but then nothing happens.

Do I need to change to runlevel 3, and then do startx ? I would prefer to be able to login to Gnome as root, when I need to, or to be able to su to root in Gnome.

Thanks,

Joel

---

### Post by t_huankiat on 2006-03-05
I thought the first user account created during installation is the root?

---

### Post by pbransford on 2006-03-05
In ubuntu, root is disabled by default and you should use sudo to admin.

eg. "sudo command", "sudo -s" for shell
for GUI apps, go to run command, and do "gksudo -S command"

If you do need root though, do this:

"sudo passwd root" and set a password. Note that this breaks the sudo config i think, and doing it is not recommended as sudo does the job quite well.

---

### Post by jbarntt on 2006-03-05
Thanks pb,

Will try the 'sudo password root' command. Seems odd to me, as I'm used to SUSE and redhat. For a non-networked system, the security is overkill, and non-intuitive.

Joel

---

### Post by jbarntt on 2006-03-05
The command 'sudo password root' does not then allow me to login to Gnome as root. How do I login in as root ? The inabilty to do something as simple as setup a dialup connection for my modem is very frustrating. 

The thing I like about Linux type osen is the abiltity to make it work the way I want. The inability to login as root by default is crazy. 


Joel

---

### Post by qyot27 on 2006-03-05
You can configure the root password through the Users and Groups option under System->Preferences (or Adminstration, I can never seem to remember where that one is), just in case you do need to change the password and would rather do it through the GUI (you will need to tell it to show all users before you can modify the root password, though).  There's also an option in the GDM configuration (System->Administration->Login Screen Setup) to allow the root user to login from the welcome screen.

As has been stated before in other threads I've read, this is something that's generally discouraged, because of the lack of password security.  I very rarely use it; the last time I did was when I installed Ubuntu on my family's main computer, I think, and that was a few weeks ago.

---

### Post by jbarntt on 2006-03-05
Hi gyot27.

I've already tried what you suggest. I get prompted for a pasword, which I enter, (my login and the root pasword are the same), and then nothing happens, nothing.

I appreciate the need for security re: root login, but there must be some way to do it ! I tried starting in runlevel 3, but got the same old Gnome login window.

Thanks,

Joel

---

### Post by aysiu on 2006-03-05
There's no reason to login as root.
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by jbarntt on 2006-03-05
Thanks and good-bye to Ubuntu,

What kind of OS is it where root/admin/Administrator cannot login ? This is crazy. I can't create a ppp dialup connection ?? On the job I admin Netware, Linux and Windows servers, where I routinely login as the root user. For a simple home desktop OS, why is this so difficult ?

Guess I'll check out Mandriva. Years ago I liked Mandrake on the desktop, and it did allow root access. Ubuntu seems to dissallow root access, and thereby access to a lot of sys config stuff - bizarre to say the least.

Joel

---

### Post by jbarntt on 2006-03-05
[QUOTE=aysiu]There's no reason to login as root.
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)[/QUOTE]


There is a very good reason to login as root, otherwise why does the account exist ?

The link you pointed me to tells me nothing about how to add a ppp dialup connection. I apparently need root access to do that.

What an assinine os it is that creates a root account, but denies access to it.

Joel

---

### Post by aysiu on 2006-03-05
Why is it asinine? I don't see any Mac OS X users complaining about sudo. Just because the account exists and gets used doesn't mean you have to log in as that account.

You still haven't made a convincing case for logging in as root.
Anything I need to do I can do with sudo.

If I want to run a command in the terminal with root privileges, I preface the command with the word *sudo*.

If I want to graphically file browse as root, I launch the command ```
gksudo nautilus
```

Please, give me a concrete example of when you need to log in as root. I'm waiting.

Maybe this link will help you with dial-up:
[http://www.ubuntuforums.org/showthread.php?t=138189](http://www.ubuntuforums.org/showthread.php?t=138189)

---

### Post by jbarntt on 2006-03-05
My Mac OS X users, (graphics dept), computers can be logged in as the root root user, my Ubuntu system cannot.

So tell me, how do I create a ppp dialup for my modem using sudo ?

Further, I want to be able to login as root, sorry if you think I shouldn't be able to do so.

---

### Post by qyot27 on 2006-03-05
I'm just guessing here, but the problem is probably arising because the root and user passwords are identical, like you've said before.  Either that, or it's related to this issue:

[http://www.ubuntuforums.org/showthread.php?t=139738](http://www.ubuntuforums.org/showthread.php?t=139738)

I've never had an issue logging in as root or using (gk)sudo commands, even when I first installed Ubuntu, and that was the first time I'd ever intensively used Linux at all.  The difference is likely that I made the root password different than the user password.

If you really need to get root access (i.e. to change the root password or correct those lines so it won't choke), there is a Windows driver that gives a person access to ext2/3 partitions through Windows Explorer, which can then be used to get into those files to correct such errors using Notepad or Wordpad.  And considering it's Windows, that means unrestricted access.  That's even more security-stripped than the other option I mentioned.

[quote=aysiu]Why is it asinine? I don't see any Mac OS X users complaining about sudo.

You still haven't made a convincing case for logging in as root.
Anything I need to do I can do with sudo.

If I want to run a command in the terminal with root privileges, I preface the command with the word sudo.

If I want to graphically file browse as root, I launch the command
```
gksudo nautilus
```
Please, give me a concrete example of when you need to log in as root. I'm waiting.[/quote]
It's not recognizing the passwords to allow elevated permissions.  gksudo or sudo commands won't launch if the password isn't accepted.  They're seeking a way to gain elevated access, but something's standing in the way.

---

### Post by aysiu on 2006-03-05
[QUOTE=jbarntt]My Mac OS X users, (graphics dept), computers can be logged in as the root root user, my Ubuntu system cannot.[/quote] Really? Can you walk me through the steps to log them in as root. Mac OS X uses the same sudo model Ubuntu does. You have to go out of your way (using the command-line) to allow users to log in as root in Mac OS X, and even then they can't do it graphically--only through the terminal.

> 
So tell me, how do I create a ppp dialup for my modem using sudo ? Read the link.

> 
Further, I want to be able to login as root, sorry if you think I shouldn't be able to do so. I just haven't heard a convincing case for logging in as root. You haven't tried using the sudo model--you've just dismissed it as "asinine" for no apparent reason. I've tried both models extensively.

---

### Post by aysiu on 2006-03-05
[QUOTE=qyot27]
It's not recognizing the passwords to allow elevated permissions.  gksudo or sudo commands won't launch if the password isn't accepted.  They're seeking a way to gain elevated access, but something's standing in the way.[/QUOTE] People fiddle around with enabling root in Ubuntu and not really knowing what they're doing and then even sudo doesn't work properly any more. I hate it when this happens--then they blame the sudo model even though they didn't bother to use it correctly.

---

### Post by jbarntt on 2006-03-05
Login in as root, Administrator, on the Max OS X system is easy - reboot, you will se an icon for each user, click on it and enter the password, not so tough.

Re: ppp account, I read your link, no info there about the issue.

Lastly I don't care if you think I shouldn't be able to login as root, it's none of your damn business - I want to be able to login as root, just like I can in OS X, SuSE, Redhat, Mandrake, Netware, Windows - - you get the pricture. Is this so difficult to comprehend ? I want control of my pc. If you don't want root access, fine, I do.

---

### Post by aysiu on 2006-03-05
[QUOTE=jbarntt]Login in as root, Administrator, on the Max OS X system is easy - reboot, you will se an icon for each user, click on it and enter the password, not so tough.[/quote] That's not logging in as root. Sorry. It isn't. 

> 
Lastly I don't care if you think I shouldn't be able to login as root, it's none of your damn business - I want to be able to login as root, just like I can in OS X, SuSE, Redhat, Mandrake, Netware, Windows - - you get the pricture. Is this so difficult to comprehend ? I want control of my pc. If you don't want root access, fine, I do. sudo gives you control of your PC, just as it does in Mac OS X, which does not let you log in as root, despite your insistence it does. Mac OS X makes your user account an administrator who generally operates as user. When you're making system-wide changes, you're prompted for your *user* (sudo) password to temporarily assume root privileges. This is the same thing Ubuntu does.

This is not the same as logging in separately as root. It is logging in user and temporarily assuming root privileges. In Ubuntu **and** Mac OS X, you **control your PC** using sudo. You don't log in separately in a root account. I'm just telling you how it's done.

Does this link help?
[http://www.ubuntuforums.org/showthread.php?t=112026](http://www.ubuntuforums.org/showthread.php?t=112026)

I've been searching around these forums, but I just haven't found that much about ppp in general.

To understand more about why sudo is not asinine, read about the actual thought process that went into choosing sudo as a model instead of root. I'm sure Apple probably thought the same thing; otherwise, they would have created a separate root account as well.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by jbarntt on 2006-03-05
OK, I give up. I cannot login as root with Ubuntu, all I can do is sudo to a particular executable, which in the case of my dialup connection seems to be mysteriuous. What this tells me is that Ubuntu is worthless  - I have to know the path and name of every damn executable I need to run ? 

Re: OS X, maybe the Administrator login isn't fully root, seems to allow installation of all software, network configuration, and anything else I need to do for these folks.

For myself, I see Mandriva or SuSE in my future.

P.S. - Why is setting up a dialup connection so difficult in Ubuntu, shouldn't this be easy ?

---

### Post by aysiu on 2006-03-05
Dial-up is supposed to be easy? I didn't know that. Of course, I don't have dial-up, either.

By all means, if Mandriva and SuSE make it easy to configure dial-up, use them. Use  whatever works for you.

---

### Post by Shikai on 2006-03-05
So let me get this straight...instead of clicking System > Administration > Networking, entering your password (after making sure the account you were on was a member of the admin group, to allow usage of sudo), then configuring the ppp connection...you decided to try and change root's password, enable logging on root through gdm, and completely trashed sudo, thus making it even more difficult to get one ppp connection going?

Hmmm...yeah, must be crappy Ubuntu's fault.</sarcasm>

You're exactly the sort of person the sudo model was created for.

---

### Post by aysiu on 2006-03-05
I know I may seem like an a**hole to jbarntt, but it doesn't make sense to me to call a system "asinine" instead of learning how to use it.

I, too, came from the traditional root/user model, as my first two Linux OSes were Blag and Mepis. At first, Ubuntu's sudo confused me. After a while, though, I realized it made a lot more sense *and* was faster.

Then I found out Mac OS X uses the same model (I found this out when enabling Fink on my wife's Powerbook). Since Mac is known for its user-friendliness, I figured Ubuntu's probably on the right track.

It's far easier to press a launcher with the command ```
gksudo nautilus
``` and enter my password to browse temporarily as root than to log out of user, log in as root, make changes, log out of root, and log back in again as user.

And I do really believe you should use what works for you. I don't care if people use Ubuntu or use SuSE or Mandriva or Fedora or Linspire or Mepis or PCLinuxOS or whatever. Use what works for you. If Ubuntu is "asinine" to you, don't use it.

---

### Post by jbarntt on 2006-03-05
You gotta be kidding me, of course setting up a dialup connection is easy. Remember Win95, nothing to it - phone number and dns server ip addy is all that is needed. This is pc 101, isn't it ? Just pointy clicky stuff, my 78 year old dad has done it with those two pieces of info.

Do you know anything about computer OSen ?

---

### Post by aysiu on 2006-03-05
If it's a WinModem, it's easy in Windows, but it won't be easy in Linux.
Read more [here](http://www.debian.org/releases/stable/i386/ch02s04.html.en#id2517701).

---

### Post by jbarntt on 2006-03-05
[QUOTE=Shikai]So let me get this straight...instead of clicking System > Administration > Networking, entering your password (after making sure the account you were on was a member of the admin group, to allow usage of sudo), then configuring the ppp connection...you decided to try and change root's password, enable logging on root through gdm, and completely trashed sudo, thus making it even more difficult to get one ppp connection going?

Hmmm...yeah, must be crappy Ubuntu's fault.</sarcasm>

You're exactly the sort of person the sudo model was created for.[/QUOTE]

Excuse me, I'm trying to login as root. IS THAT SUCH A BIG THING TO ASK ? TO LOGIN AS A PARTICULAR USER ON MY ON SYSTEM ?

As I said before, no problem With Netware, SuSE, Redhat, Windows, why such a problem with my humble non-networked home pc ?

---

### Post by aysiu on 2006-03-05
[QUOTE=jbarntt]Excuse me, I'm trying to login as root. IS THAT SUCH A BIG THING TO ASK ? TO LOGIN AS A PARTICULAR USER ON MY ON SYSTEM ?[/quote] How about instead of writing angry posts, you just read this link: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It explains *everything*, including how to log in as root.

> 
As I said before, no problem With Netware, SuSE, Redhat, Windows, why such a problem with my humble non-networked home pc ? Why do you want to use Ubuntu so badly if SuSE and Red Hat so readily detect your dial-up? I'm just curious.

---

### Post by jbarntt on 2006-03-05
Its a hardware modem, USR 56k pci, recognized by Ubuntu. I don't do winmodems. The issue is that I cannot setup the dialup connection w/o root privleges, but I cannot get root privileges.

---

### Post by aysiu on 2006-03-05
[QUOTE=jbarntt]Its a hardware modem, USR 56k pci, recognized by Ubuntu. I don't do winmodems. The issue is that I cannot setup the dialup connection w/o root privleges, but I cannot get root privileges.[/QUOTE] If it's a script like *setup.sh* just run ```
sudo ./setup.sh
``` If you want to browse as root, just do Alt-F2 ```
gksudo nautilus
``` and browse to where you want to be. If you want use the networking settings, go to System > Administration > Networking and enter your *user* password--this will temporarily give you root privileges.

I don't know how else to tell you this. I've stated the methods numerous times and even linked to explanations for **how to enable root**, but you don't seem to want to read how to do it--you'd rather just complain that you can't.

---

### Post by jbarntt on 2006-03-05
No OS detects a dialup connection - you have to make it, i.e., phone # to ISP and ISP's dns server(s). 

You really have no clue.

---

### Post by aysiu on 2006-03-05
[QUOTE=jbarntt]
You really have no clue.[/QUOTE] Yes, that's right. I have no clue. Sorry. I'll shut up then.

---

### Post by jbarntt on 2006-03-05
I do enter my password and Nothing, NOTHING happens. The screen is blank. Just the wallpaper. Ziltch, nada, nothing, etc.

---

### Post by jbarntt on 2006-03-05
[QUOTE=aysiu]Yes, that's right. I have no clue. Sorry. I'll shut up then.[/QUOTE]

aysiu,

I apologize for being insulting. I appreciate you tried to help me, and I repaid you unkindly.

I like linux type OSen because they allow me control, unlike MS and Apple. Ubuntu seems to be not about user control, so I will get a different distro.

Again, I apologize for my rudeness.

Best Regards,

Joel

---

### Post by aysiu on 2006-03-05
I understand you're frustrated, but I really do believe you should just use what works for you--obviously Ubuntu doesn't. Best of luck with whatever you use.

---

### Post by jbarntt on 2006-03-05
[QUOTE=aysiu]I understand you're frustrated, but I really do believe you should just use what works for you--obviously Ubuntu doesn't. Best of luck with whatever you use.[/QUOTE]

Thank you asyiu, and goodnight.

Peace,

Joel

---

### Post by codejunkie on 2006-03-05
[QUOTE=jbarntt]aysiu,

I apologize for being insulting. I appreciate you tried to help me, and I repaid you unkindly.

I like linux type OSen because they allow me control, unlike MS and Apple. Ubuntu seems to be not about user control, so I will get a different distro.

Again, I apologize for my rudeness.

Best Regards,

Joel[/QUOTE]
ubuntu dosen't lock you down it's just kinda hidden ;) i use the root account all the time you just have to enable it with ```
sudo passwd root
```and then enable it in gdm by running```
sudo gdmsetup
```navigate to security and check the allow root login box. just a hint if you did an **expert install**, the root account is enabled and sudo is disabled, but you still have to enable root logins through gdm you can do that by opening a terminal run ```
su
``` enter the root password you set and then run```
gdmsetup
```and check the box for root logins.

---

### Post by pbransford on 2006-03-05
Give Ubuntu a chance. Other than the wierdness of root/sudo it's a solid distro. Easy to use with more frequent updates than debian.

---

### Post by OffHand on 2006-03-05
In OS X you can login as a root btw.
You will have to enable it tho.
(and I'm not talking about admin but real root access)  ;)

---

### Post by towsonu2003 on 2006-03-05
did the op figure out ppp (dial up) configuration? check out second link in my signature, see the table of contents for ppp configuration if this is not a winmodem (which seems not to be from your posts). I prefer wvdial and don't have a clue about gui alternatives to wvdial.  

as per root login issues, I like it bc ubuntu wants to appeal the newbie coming from windows (I mean, we don't even have compilers, kernel headers, and some core development packages installed by default). It also wants to be "out-of-the-box happy -little need for root-. Newbies coming from windows will want to be administrators hile using gui, bc they are used to it. that's screws up the security model of linux (multi-user). with disabling sudo, newbies will have to look at forums to find sudo, and thanks to posters like aysiu, will know that root login makes linux sexurity useless (root can do everything, including erase everything while working[1])

in the meantime, when I have to type too many root-required commands (ifconfig + iwconfig + iwlist _ dhclient for wireless), I use sudo -i and check what I type 4 times bf hitting <enter>. 

good luck getting used to ubuntu configurations. 

[1]don't you post the command for that! I have seen users do it and trash installations.

---

### Post by handy on 2006-03-06
[QUOTE=aysiu]I understand you're frustrated, but I really do believe you should just use what works for you--obviously Ubuntu doesn't. Best of luck with whatever you use.[/QUOTE]

Aysiu, you certainly set an exemplary example for the rest of us.

I tip my hat to you.

---

