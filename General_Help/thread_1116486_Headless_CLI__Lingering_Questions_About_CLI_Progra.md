---
title: "Headless CLI | Lingering Questions About CLI Programs &amp; Such"
date: 2009-04-04
forum: General Help
---

### Post by BurkDP on 2009-04-04
Less than a year ago I set up a headless server that I ssh into and use for various things and have been figuring out how to use Linux since then. With the upcoming release of Jaunty I thought I'd do a clean install and use this as an opportunity to get some answers to lingering questions I've had.

Since I'm basically self-taught my knowledge has large gaps, so indulge me if some of these questions have very obvious answers. I don't have all the time in the world to scour the internet for answers, so I figured posting to such a large forum would be easier and give better quality answers.

I'd like verbose answers but simply putting up a link to a tutorial, or a terse "f'n newb it's simple <explanation goes here>" is cool. Actually, any response at all would be appreciated.

Also, I had a friend who was gracious enough to let me setup a personal wiki on his webhosting account. I kept notes of how I set my server up, what I've done as I've used it and information collected from around the web. I can't let random people create accounts on my wiki because I didn't want anyone randomly defacing it, and he didn't want to be hit with spam accounts. So if any person who reads this post and has the time to look it over and leave some suggestions in the comments I'd really appreciate it. (please ignore the spelling/grammar errors & formatting weirdness - it is a really really rough draft)
*You can see it here: [http://burk.crabula.com/index.php?title=New_Headless_Ubuntu_Server_Guide](http://burk.crabula.com/index.php?title=New_Headless_Ubuntu_Server_Guide)


Most Pressing Question:
[LIST]
[*]Can I use a separate password for logging in to my account and sudo? I use sudo often enough (ex. "sudo aptitude update") that I'd like a short easy password (bad ex. "sudo"), but I'd like a very good and secure login password for increased security. (My theory is if someone managed to crack my login they could crack any sudo password as well, so it wouldn't be an inherently less secure setup.)
**( ^ have already gotten good feedback on. )**
[*]Can I use a pass phrase instead of password for login? (ex. "Wee PaSsphRase ; w00t!1!" vs "pasword123")?
[/LIST]



Should Be Simple But I Can't Figure Out:
[LIST]
[*]What is the default console font installed in a minimal CLI only install? Is it terminus? If not, how can I switch it?
[/LIST]


Network Related:
[LIST]
[*]Is there a good tutorial for MoBlock?
**( ^ have already gotten good feedback on. )**
[*]I found when I installed it that it blocked svn (ex. couldn't "svn up" a folder). What else does it blacklist by default? Is there a configuration file I can use when I want to add something to the whitelist instead of running "dpkg -reconfigure"?
**( ^ have already gotten good feedback on. )**
[*]ufw related:
[**]Does MoBlock play well with ufw?
**( ^ have already gotten good feedback on. )**
[**]If I use a non-standard ssh port, do I have to enable it specifically in ufw or will "ufw allow OpenSSH" work?
[**]Which of these do I want to use for ProFTP: Apache, Apache Full, Apache Secure?
[*]If I use a non-default port for ssh does that work with denyhosts?
[/LIST]


Looking For Guides Or Help On Installing & Using:
[LIST]
[*]Gmail Backup [http://www.gmail-backup.com/](http://www.gmail-backup.com/) - it hints that you can use it from the command line but i can't seem to find any documentation on how to set it up. Do you need to compile, or install it? (I generally use "checkinstall" whenever I compile something to create a .deb and use it with the package manager so if it has to be compiled I'd like someone to simply point it out)
[/LIST]


Would Like to Know:
[LIST]
[*]If you can get notifications on a GUI install whenever an update requires a restart, where can you get that info from the command-line? I prefer to use aptitude over apt-get and I know it does logging so does that help?
[**]I've read that you almost never need to restart due to updates on a CLI-only install, but on the those occasions you do it'd be handy to be notified.
[*]I found the pmount program, and it makes mounting DVDs easy as I don't need to sudo, but I can't get it to work with USB drives. I occasionally need a quick'n'easy, non-sudo way to one-off mount them. Is there a way to make it pmount work with USB drives, or is there a similar program to do that?
[**]Basically I want to know if it's possible to emulate how the GUI Ubuntu automounts drives and creates a link to it on the desktop (or in this case $HOME), removing them when it's unmounted.
[**]If not, could someone give any pointers on whipping up a quick bash script to do that?
[**]I know the ubuntu documentation wiki recommends the "usbmount" program, but I've never had it work for me. Is there something I have to do beyond "sudo aptitude install usbmount" to get it to work?
[/LIST]


Misc:
[LIST]
[*]I've noticed that in using dvdbackup (w/libdvdcss2 natch) that a hidden folder in ~ called ".dvdcss/" gets filled with stuff. It's not particualrly big but I was wondering if it's contents are safe to delete. If so I was thinking of a simple cron job "@monthly rm -rf $HOME/.dvdcss/*"
[*]Can I alias "rm -rf /"? I just thought it'd be handy to add something like that in my .bash_aliases file so instead of borking my system it'd echo a message like "don't bork your system". (Not that i'd ever do use the command, but I'd rest easy aliasing the 7 deadly linux commands [http://www.junauza.com/2008/11/7-deadly-linux-commands.html](http://www.junauza.com/2008/11/7-deadly-linux-commands.html))
[*]How do I enable the framebuffer? I know that some programs can do graphics without installing an X server using the framebuffer, but whenever I try (ex links2 -g) I get this message:
[/LIST]
```

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.

```
[LIST]
[*]Just out of curiosity, can you use the framebuffer on an ssh connection (like in my connected terminal)? Or is that an idiotic thing to ask...
[/LIST]

---

### Post by fabricator4 on 2009-04-05
You can disable sudo for all ordinary users by editing the /etc/sudoers file.

comment out the line that is something like
admin all = (all) all

That will effectively remove sudo permission for the admin group of which your user will be part.

Note: make sure you set up a working root password first!

In a terminal type:

sudo passwd root

and follow the prompts to type in a password.  It's debatable whether this will actually make your system more secure, and no doubt it has been debated!

You will now need to login to a terminal session with su, or login a root at a console session.

I believe you can use a phrase as a password, however you need to be extremely careful with the root password as if you manage to get any invalid characters into the password it will disable the root login completely.

Chris

---

### Post by BurkDP on 2009-04-05
thanks for the prompt advice, but what I envisioned was having a separate password for logging onto my computer (I guess that would be my user) and having a different password for sudo. I didn't really want to get rid of sudo altogether so much as I wanted a short password for it & a longer pass phrase for logging on. I might be mistaken in the assumption that it's not as stupid as it sounds, working with the theory that once someone has managed to breach my more complex user password they could break whatever password I'd have for sudo.

Are a sudo password & root password the same? Like I implied, I'm prone to making mind-bogglingly stupid assumptions, and if that's true than my idea would be bad - very bad.

---

### Post by fabricator4 on 2009-04-05
Hi, no your user password and your sudo password are the same.  Sudo is just an extension of your user privileges via the admin group, which is why you can't have a separate password for it.

The easiest way to have a completely separate password would be to have a root password and disable your admin privileges for your normal login as outlined.

As far as I know.

For security it would actually be best if your user did not have sudo privileges, though it's debatable as I said, because it would arguably be less secure if you also used that root login remotely.

Another approach would be to make another user with no admin privileges for day to day tasks, and keep your user with admin privileges for sudo tasks.  If you want to make the sudo privilege stick type "sudo su".  Don't forget to logout when you are finished.

You'd probably want to make another group such as "usergroup" and make both users members so that they could access the same home directories.

Chris.

---

### Post by BurkDP on 2009-04-05
Thanks. That was actually very helpful.

---

### Post by jre on 2009-04-05
> Is there a good tutorial for MoBlock?
Well, you've already [this]("https://help.ubuntu.com/community/MoBlock") on your wiki. That's a good start. Read it again.
Note that moblock-control has been renamed to blockcontrol.

> I found when I installed it that it blocked svn (ex. couldn't "svn up" a folder). What else does it blacklist by default? Is there a configuration file I can use when I want to add something to the whitelist instead of running "dpkg -reconfigure"?

MoBlock does not block any special services like svn. Instead it blocks based on large IP blacklists. That means your svn server's IP is on the blacklist.
You can allow ports (here you may add svn's port) or IPs (your svn server's IP) in /etc/blockcontrol/blockcontrol.conf (look at /usr/lib/blockcontrol/blockcontrol.defaults as a reference).
Further you can allow IP ranges in /etc/blockcontrol/allow.p2p and select your blocklists (the default is quite hard) in /etc/blockcontrol/blocklists.list.
**Take care to allow incoming connections either for ssh or the IP of the machine that you use to log in your server.**

> Does MoBlock play well with ufw?
I guess so. Generally it plays well with other iptables based firewalls if you **"blockcontrol restart" after** every start/change of the firewall. Have a look at [post #1 in this thread]("http://ubuntuforums.org/showpost.php?p=5016102&postcount=1"): How to make sure that MoBlock is integrated correctly with any other firewall

---

### Post by BurkDP on 2009-04-05
wow a maintainer, thanks for the information.

---

