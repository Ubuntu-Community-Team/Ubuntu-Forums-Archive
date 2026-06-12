---
title: "Dont understand root on Ubuntu either"
date: 2004-12-29
forum: Desktop Environments
---

### Post by LatterDaySaint on 2004-12-29
My question is 4 example,when I want to use programs like Synaptic ect,I get told I need to add my root passwd to be able to use it,but I dont have one,and I have tried typing the word sudo as my passwd  as well and that did not work,maybe I could use terminal to get synaptic to work using sudo,but why does it ask for passwd if we dont have one,also can a hacker on internet who knows your using Ubuntu think < I dont need a passwd to get into this system because all I have to do is type sudo and have access to everything? anyway the reason I might be asking this so called dumb question is because I was told that typing sudo on terminal gives root access to what ever you want to use.

---

### Post by p!=f on 2004-12-29
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Ie: To run synaptic under root privileges
```

sudo synaptic

```
Ie: To get root prompt without setting up root password
```

sudo -s

```

---

### Post by LatterDaySaint on 2004-12-29
Im sorry but I think I was misunderstood,I tried what you said to do in terminal,and it then still asks 4 my root password. But what im trying to say is when I installed Ubuntu ,which I reinstalled because of this,is that it never asked me to give a root password during install to be able to use  in OS .just  asked me to give my user name and password instead,which means I dont have a root passwd to be able to use,and the reason I wrote what I said originally about synaptic asking 4 my passwd ect was because of what I read somewhere else in this forum of someone else saying they never got asked 4 a root passwd during install either ,and he was told that you dont need a root passwd because you just use sudo on everything ,which made me reply also about how hackers could exploit the sytem then if sudo is all they need.I hope someone knows what I am talking about and maybe knows which post in forum Im replying to,as I could be wrong but when I first installed Ubuntu a month or so ago on my P4,which I wiped so I could try another distro , Is Im preety sure I had a root passwd which was given me during that install at that time. so what has gone wrong this time.I got to admit ,linux seems to do some strange things on different PCs

---

### Post by hardcandy on 2004-12-29
While using sudo, you just use your user's password.

---

### Post by LatterDaySaint on 2004-12-29
Thank you, Very Good, Can you tell me if a root passwd is ever created during install at all ,as I just posted a question about how to create one after install, because I was preety sure I created a root passwd one time during install on my other PC sometime ago,but its possible im getting mixed up with another Distro,;                 Thanks also for the last answer as that helped alot.

---

### Post by hardcandy on 2004-12-29
There is a Howto on creating a root password in the Howto/FAQ forum.

---

### Post by LatterDaySaint on 2004-12-29
Thanks,now I just got to sort out what I wrote in my other post,before to many people see it.I have now worked it  out .I think Ubuntu is great.

---

### Post by Rancoras on 2004-12-29
[QUOTE=LatterDaySaint]Thank you, Very Good, Can you tell me if a root passwd is ever created during install at all ,as I just posted a question about how to create one after install, because I was preety sure I created a root passwd one time during install on my other PC sometime ago,but its possible im getting mixed up with another Distro,;                 Thanks also for the last answer as that helped alot.[/QUOTE]

Ubuntu is a bit different in that the root account is disabled by default.  It is intended that anything requiring root permissions be done with sudo.  Yes, you can re-enable the root account, but there really is no need.  Just continue to use sudo with the password for the account you created during install.

---

### Post by p!=f on 2004-12-29
If you don't want to be asked for the password tweak /etc/sudoers like this:
```

<your_username>     ALL=NOPASSWD: ALL

```

---

### Post by LatterDaySaint on 2004-12-30
Thanks again,Just want to add that after about 6 mths of using and trying a dozen or so distros through the sheer enjoyment of being inquisitive with all these different types of distros out there ,that I think I got a bit confused , Im sure that this type of sudo way of doing things will cause some other distros to take notice,I do really think thay ubuntu has a lot of Quallity,as it seems alot cleaner than other distros like Mandrake,  - thumbs up to Ubuntu & Slackware (yibbidee Yibada) Thats all Folks.

---

### Post by AndersAA on 2004-12-30
[QUOTE=p!=f]If you don't want to be asked for the password tweak /etc/sudoers like this:
```

<your_username>     ALL=NOPASSWD: ALL

```[/QUOTE]

just throwing in that that's a horribly bad idea... how often do you need to use sudo anyway, you shouldn't need to use it in day to day operations, and that is a gigantic security hole to open...

---

### Post by p!=f on 2005-01-02
[QUOTE=AndersAA]just throwing in that that's a horribly bad idea... how often do you need to use sudo anyway, you shouldn't need to use it in day to day operations, and that is a gigantic security hole to open...[/QUOTE]
Oh, really. Feel free to explain why is that so horrible idea when I'm behind a firewall on a desktop with a personal firewall running without a single service listening under my account... Perhaps you bring some light on this issue.
Seriously. You should make differences between a production server and a desktop.

---

### Post by offby1 on 2005-01-02
[QUOTE=p!=f]Oh, really. Feel free to explain why is that so horrible idea when I'm behind a firewall on a desktop with a personal firewall running without a single service listening under my account... Perhaps you bring some light on this issue.
Seriously. You should make differences between a production server and a desktop.[/QUOTE]

Easy enough -- although this is not an issue for you, many users are not behind a firewall, and often their passwords are not excellent.  You cannot assume that because your system is secure that it follows that theirs will be secure in the same ways.  sudo without passwords is very dangerous, because if someone gets a foothold on your machine so far as to be able to run even one shell command, you are rooted and there is little that you can do about it.

---

### Post by AndersAA on 2005-01-02
[QUOTE=p!=f]Oh, really. Feel free to explain why is that so horrible idea when I'm behind a firewall on a desktop with a personal firewall running without a single service listening under my account... Perhaps you bring some light on this issue.
Seriously. You should make differences between a production server and a desktop.[/QUOTE]


although offby1's said something too.
Firefox/downloads/mail on linux are not imune, yes, they are WAY better than their windows counterparts, but don't asume your box is secure because someone can't break remotly.  It's very possible to for example use a web exploit to get you to run a command, and with sudo that could do WAY more damage than you want it to.  

(note, most hackers are not interested in stealing your files, or moving your mouse around. It's far more likely they wanna setup a server and or use your computer as a zombie, so they later can use thousands of em to bomb one host. Therefor don't worry about evil hackers targeting you in specific, worry about stuff that targets groups, like web sites/emails/scripts/irc stuff. ).

---

### Post by javabiz on 2005-01-03
Steps for root
I either changed root's password in gnome under user admin or management or the following:  (can't remember--but I know I did it throught the gui of gnome or kde)!
1.  Go to Synaptic
2.  Search kde
3.  Select it to install
4.  After install--reboot
5.  Select option for kde desktop on the lower bar as opposed to Gnome.
6.  Pick whatever you want for kde options on install.
7.  Go to user management and change root's password.
8.  Now everthing will require root password--including 
# su
9.  Now that you are free--go tell the rest!

---

### Post by offby1 on 2005-01-03
[QUOTE=javabiz]Steps for root
I either changed root's password in gnome under user admin or management or the following:  (can't remember--but I know I did it throught the gui of gnome or kde)!
1.  Go to Synaptic
2.  Search kde
3.  Select it to install
4.  After install--reboot
5.  Select option for kde desktop on the lower bar as opposed to Gnome.
6.  Pick whatever you want for kde options on install.
7.  Go to user management and change root's password.
8.  Now everthing will require root password--including 
# su
9.  Now that you are free--go tell the rest![/QUOTE]
 Or, alternately, without all the hassle:

either A)
```
sudo su
passwd

```
or B)
```

sudo passwd

```

---

### Post by thekat on 2005-01-03
[QUOTE=offby1]Or, alternately, without all the hassle:

either A)
```
sudo su
passwd

```
or B)
```

sudo passwd

```[/QUOTE]

hmm.. I thought I had missed something..  :confused:  I just booted into Single user mode
and changed it.. 
Different than my SuSE box.. but a good feature nonetheless.. 
sudo is a good thing.. 

Oh.. I found about this distro on LinuxQuestions.. always wanted to try Debian.. but really didn't want to learn the Debian Way.. Ubuntu has done a great job here.. now if I could just get my printer to work.. :-)

Edit..
Ok.. now the printer works.. I am set..  :mrgreen:

---

### Post by p!=f on 2005-01-03
> **offby1]Easy enough -- although this is not an issue for you, many users are not behind a firewall, and often their passwords are not excellent.  You cannot assume that because your system is secure that it follows that theirs will be secure in the same ways.  sudo without passwords is very dangerous, because if someone gets a foothold on your machine so far as to be able to run even one shell command, you are rooted and there is little that you can do about it.[/QUOTE]

Most users don't need a firewall because they don't run any network services. 
I know lot of people who begin with Linux having their firewalls set up almost immediately because they've heard / read / got recommendation it's a good idea (TM).
As soon as you have no daemon listening you don't have to worry about the security that much.
And if you'd like to run some (web, ftp) daemon you'd like to set up some firewall to filter the traffic and read some paper, don't you? :)
[QUOTE=AndersAA]
although offby1's said something too.
Firefox/downloads/mail on linux are not imune, yes, they are WAY better than their windows counterparts, but don't asume your box is secure because someone can't break remotly. It's very possible to for example use a web exploit to get you to run a command, and with sudo that could do WAY more damage than you want it to.

(note, most hackers are not interested in stealing your files, or moving your mouse around. It's far more likely they wanna setup a server and or use your computer as a zombie, so they later can use thousands of em to bomb one host. Therefor don't worry about evil hackers targeting you in specific, worry about stuff that targets groups, like web sites/emails/scripts/irc stuff. ).
[/QUOTE]
I don't think it's very possible. If some exploit like that is announced, patch is probably already on the way for users so this method looks quite ineffective not to mention this does not happen every month in Mozilla world. :)
Btw, there could be an exploit in sudo directly.  said:**
> 
stay_setuid  	 
Normally, when sudo executes a command the real and effective UIDs are set to the target user (root by default). This option changes that behavior such that the real UID is left as the invoking user's UID. In other words, this makes sudo act as a setuid wrapper. This can be useful on systems that disable some potentially dangerous functionality when a program is run setuid. Note, however, that this means that sudo will run with the real uid of the invoking user which may allow that user to kill sudo before it can log a failure, depending on how your OS defines the interaction between signals and setuid processes.

Sounds scary... :)
source: [http://www.skywayradio.com/tech/security/sudo.html](http://www.skywayradio.com/tech/security/sudo.html)

If that option would be so suicidal there probably would be some note about it in the documentation and you would not find an option to compile sudo with completely disabled passwords.
> 
Q) How can I keep sudo from asking for a password?
A) To specify this on a per-user (and per-command) basis, use the 'NOPASSWD'
   tag right before the command list in sudoers.  See the sudoers man page
   and sample.sudoers for details.  To disable passwords completely,
   run configure with the --without-passwd option or add "!authenticate"
   to the Defaults line in /etc/sudoers.  You can also turn off authentication
   on a per-user or per-host basis using a user or host-specific Defaults
   entry in sudoers.

source: [http://www.courtesan.com/sudo/troubleshooting.html](http://www.courtesan.com/sudo/troubleshooting.html)
source: sudo apt-get source sudo

I think most hackers who want to use your machine for purposes other than stealing your files won't invest their time for searching NOPASSWD: ALL option via not very possible exploit but they rather take a look around for a machine running vulnerable daemon using some sniffing tools.

Btw if your /home partition, if any, is mounted without nosuid noexec options, potencional hacker could use your development environment and compile some nasty code to get root privileges / run some daemon / shell tricks etc. There're really more elegant ways to do something bad. :)

My point is that NOPASSWD: ALL option on a desktop is a thing you need not to worry so much. :)

---

### Post by jbh on 2005-01-04
enabling sudo all the time is not only insecure as hell, you can royally screw up your file system accidently and increase the chances of crashing when you are always a super user.

---

### Post by jbh on 2005-01-04
[QUOTE=p!=f]My point is that NOPASSWD: ALL option on a desktop is a thing you need not to worry so much. :)[/QUOTE]


bahah you should work for microsoft that's their philosophy

---

### Post by AndersAA on 2005-01-04
[QUOTE=p!=f]I don't think it's very possible. If some exploit like that is announced, patch is probably already on the way for users so this method looks quite ineffective not to mention this does not happen every month in Mozilla world. :)
Btw, there could be an exploit in sudo directly. ;)
[/quote]

It has happened, and it will happen again sooner or later, and yes sudo could probably be exploited some way or another aswell, but security is about layers, the more the better.

And how often do you use sudo?  Every system should use sudo very rarly.. once, maybe twice a day.  Do you really think writing in your password is so much work you need to open up security holes?  And it IS a security hole.

If you really need to run one application as root often, then you should setup sudo to allow you to run that one command without root, not all commands...

---

### Post by offby1 on 2005-01-04
[QUOTE=AndersAA]It has happened, and it will happen again sooner or later, and yes sudo could probably be exploited some way or another aswell, but security is about layers, the more the better.

And how often do you use sudo?  Every system should use sudo very rarly.. once, maybe twice a day.  Do you really think writing in your password is so much work you need to open up security holes?  And it IS a security hole.

If you really need to run one application as root often, then you should setup sudo to allow you to run that one command without root, not all commands...[/QUOTE]
 The one area where I'll reluctantly agree that p!=f has a point is in the stage where you're still setting up the system.  Since what I wish to use my linux systems for is NOT the usual desktop jazz (one as a development webserver, the other as the *developer*'s laptop) I have spent a LONG time tweaking config files, etc...

As a consequence, I've added my day to day use to the sudo group, who do not have to enter a password, simply to save time.  I recognize that it's a risk, but my time is worth more than the small amount of data I keep on the laptop, and my server is significantly safer than that.

Still, I'm not going to say that it's a GOOD idea, by any stretch of the imagination.  It is, however, practical.

---

### Post by ions on 2005-02-26
What if there's an app that needs to run as root?  Like the app that's used to add music file to a flash mp3 player (iRiver for example).  I have to run ifp-gnome as sudo to add music to my iRiver 790.  Problem is I have others that use my PC and would like to use that app for their iRiver and I don't want to give my password to them.  ifp-gnome was added to the 'Multimedia' section of my Gnome menu but of course since it isn't run as root from there it does not work.  How can I make it work without asking for a password?

---

### Post by ions on 2005-02-27
Answer: add this to /etc/sudoers

ALL ALL = NOPASSWD: /usr/bin/ifp-gnome

Then when you run it from the gnome menu have this as the command: sudo /usr/bin/ifp-gnome

*thanks to bob2 on #ubuntu :)

---

### Post by Davepet on 2005-02-27
I'm still confused, if I have 3 users on my machine & user #3 is logged in, can user#3 sudo, type his Pword & have root access to the entire box?

Sounds like a major security flaw if that's the case...

Dave

---

### Post by Pluk on 2005-02-27
Only if you have user #3 added to /etc/sudoers with:

user#3   ALL=(ALL) ALL

Ubuntu only adds the username you filled in during install to the sudoers file.

Any user after that have to be added manually to sudoers by root or by the first user.

---

### Post by macewan on 2005-02-27
It's like having a hall pass in school. Temp permission to do something that you usually aren't allowed to do.

---

### Post by kxs on 2005-11-06
[QUOTE=ions]Answer: add this to /etc/sudoers

ALL ALL = NOPASSWD: /usr/bin/ifp-gnome

Then when you run it from the gnome menu have this as the command: sudo /usr/bin/ifp-gnome

*thanks to bob2 on #ubuntu :)[/QUOTE]

Is it safe? And there`s really no other way?

---

### Post by AndersAA on 2005-11-06
Per default in ubuntu sudo users in the admin group, can run sudo on any command (which means sudo <command> to run it as root, and they only need their own password to do it).

However, if you like the above command in sudoers specifiy which command, then they can only run that specific command as root.  Additionally that also uses NOPASSWD which means they dont need any password to do it.

---

### Post by lakersforce on 2007-03-17
I know this thread is old, but I was browsing the forums and stumbled across it.

And I could not believe my own eyes!!!

P!=F offers the following advise:
> <your_username>     ALL=NOPASSWD: ALL
True, it can be useful in certain circumstances, for example if you are temperaly setting up your server offline. But the poster admits he/she is a total newbie! This advise is the worst possible that could be given. Its dangerous and opens up your computer for exploits!!

Another poster gives advise on how to setup a root account. No problem with that, but that should really never be done. Its a classic newbie mistake to open up a root account. Dont do that, use sudo!!

Alternatively you can make a temp root acces in a terminal by typing in:
> sudo -H -s
Its good for use when you have to run a lot of root commands. And the root acces is terminated as soon as you close the window.

And please remember: sudo is there for a reason!!

---

