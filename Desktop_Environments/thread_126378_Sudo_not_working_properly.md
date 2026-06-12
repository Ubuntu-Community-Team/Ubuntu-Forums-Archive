---
title: "Sudo not working properly"
date: 2006-02-06
forum: Desktop Environments
---

### Post by nmatheis on 2006-02-06
Hello

Running x64 Breezy. All repositories in sources.list file enabled. Easy Ubuntu, as well.

After recent update/upgrade using apt-get, my sudo isn't working properly.  If I use sudo in the terminal and then open something that needs sudo authority (synaptic, one of the administration tools), I often get a message that the application has been opened without having to enter my password.  Looks like the sudo authority is hanging on even after I exit the application I used it for in the first place.  Sometimes I can't open one of the apps that needs sudo authority, my computer telling me that the sudo authority is tied up somewhere else (cannot get lock) even though I'm not running any apps that require sudo authority right then.

Any idea how to get this straightened out?  I'd like my sudo powers to work consistently and be able to enter into apps that require sudo only after entering my password.  And I'd like to be able to get into synaptic or admin apps and not have funky 'cannot get exclusive lock' errors come up when I'm not even using an app that requires sudo authority.

Thanks for any help!
Nikolaus
Any Ideas?

Thanks!
Nikolaus

---

### Post by nmatheis on 2006-02-06
bump for any help :)

---

### Post by RAOF on 2006-02-06
I don't think that sudo **requires** a lock :confused:.  Could you try running a root-requriring app from a console.  For example:
```
gksudo synaptic
```
and see whether/what error messages it spits out?  Can you get the output from something that doesn't work?  That'd help in diagnosing your problem.

---

### Post by nmatheis on 2006-02-07
[QUOTE=RAOF]I don't think that sudo **requires** a lock :confused:.  Could you try running a root-requriring app from a console.  For example:
```
gksudo synaptic
```
and see whether/what error messages it spits out?  Can you get the output from something that doesn't work?  That'd help in diagnosing your problem.[/QUOTE]
Here's the error message I get with gksudo synaptic...


[b]The "synaptic" program was started with the privileges of the root user without the need to ask for a password, due to your system's authentication mechanism setup.

It is possible that you are being allowed to run specific programs as user root without the need for a password, or that the password is cached.
This is not a problem report; it's simply a notification to make sure you are aware of this.[/b]


Synaptic starts most of the time but gives this error message maybe 1/4 - 1/2 of the time.  Sometimes though, it gives this message and then crashes/shuts down and won't let me in unless I restart.

Nikolaus

---

### Post by RAOF on 2006-02-07
As it says, that's not an error report.  Sudo in Ubuntu is set up so that it only asks for your password at most once every 15 minutes (I think).  That's just a notification of this fact - for me it only came up once (is there a "don't notify me again").

The crashing/shutting down part sounds like an actual problem.  What, if anything, is printed to the terminal when that happens?

---

### Post by nmatheis on 2006-02-07
[QUOTE=RAOF]As it says, that's not an error report.  Sudo in Ubuntu is set up so that it only asks for your password at most once every 15 minutes (I think).  That's just a notification of this fact - for me it only came up once (is there a "don't notify me again").

The crashing/shutting down part sounds like an actual problem.  What, if anything, is printed to the terminal when that happens?[/QUOTE]

I was starting Synaptic from the menu when it gave that message and acted like it was opening and immediately terminated.  And thanks for pointing out that it's not an error message.  Sadly enough, English ***is*** my first language :rolleyes:   Perhaps I should pay more attention to the actual content of the message box next time, eh?

In addition to this problem, I tried to use Gnomebaker and Graveman tonight and neither would work.  Gnomebaker froze while initiating - in between the splash screen and the working window.  Graveman told me that it was looking for my cd/dvd drive for one helluva long time and never found anything.  The CD/DVD Creator in the menu system worked though - I was burning an .iso of Kanotix Lite 64.  Both of these worked before my reinstall and ensuing upgrade.  Although before the reinstall, I had my system upgraded regularly.  And my Splash Screen Manager is gone from the menu and isn't in the Menu Manager, either.  Weirdness!!!

Can't wait till Dapper comes out!!!  On the positive side, seems that USB device handling is much better now.  Transmission to my external USB2 HD seems a little faster of late and I haven't gotten the "Cannot Eject Device" message lately (used to happen before upgrading - even when I can see that the drive is deactivated by the icon type).  Internet seems a bit faster, as well.  So good and not quite as good...

Nikolaus

---

### Post by RAOF on 2006-02-07
If you could just keep running synaptic and the other programs which sometimes don't work from a terminal, then post what error messages they write to the terminal, we can see if they shed any light on the problem(s).

---

### Post by bitonw on 2006-03-22
if i try

sudo apt-get update

in a terminal screen. i get nothing not even an passwd question or message.. checked serveral logs in /var/logs but can't find why it's not working.

ubuntu 5.10 clean install.

---

### Post by bitonw on 2006-03-23
sorted my problem [http://www.ubuntuforums.org/showthread.php?p=854227#post854227](http://www.ubuntuforums.org/showthread.php?p=854227#post854227)

bt

---

