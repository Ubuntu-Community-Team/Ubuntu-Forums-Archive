---
title: "Broken Ubuntu session (_IceTrans)"
date: 2005-12-16
forum: General Help
---

### Post by Redeyes_Gambit on 2005-12-16
}{i, 

I seem to have a little problem on my hands. I have appearantly broken one of my log-ons under Ubuntu :( . I was using ubuntu as usual when a few weird things happened: I tried to launch amarok music player and encountered an error which I stupidly didn't log, but it started up anyway, and then icon on the upper right corner (the equivelent of system tray in win) had strangely dropped down to the left hand side, just below the top bar. I closed amarok and launched XMMS instead, but when I tired to open a song it said something about checking something to do with the soundcard. Again I was stupid and didn't log it figureing a re-start would fix it. Well I re-started and when I tried to log into my primary profile (the one i was using) I get this Message:


Your session lasted less than 10 seconds. If you have logged out yourself this could mean there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem.

then there is a checkbox to show details. I have seperated each line in the log with a (enter)

(checkbox) Veiw details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running:usr/bin/x11/sessreg/ -a -w /var/log/wtmp -u sessreg /var/run/utmp

etc/gbm/Xsession: Begining session setup...

_IceTransTransNoListen: unable to find transport: tcp

_IceTransmkdir: ERROR: Cannot create /dev/x

_IceTransPTSOpenServer: mkdir(/dev/x) failed, errno = 13

_IceTransOpen: transport open failed fop pts/gambuntu:

_IceTransMakeALLCOTSServerListeners: failed to open listener for pts

_IceTransISCOpenServer: protocol is not supported by a ISC connection

_IceTransOpen transport open failed for isc/gambuntu

_IceTransMakeALLCOTSServerListeners failed to open listeners for isc

_IceTransSCOOpenServer: protocol is not supported by a SCO connection

_IceTransOpen: transport open failed for sco/gambuntu

IceTransMakeALLCOTSServerListeners: failed to open listeners for sco

** (gnome-session: 9207): WARNING ** unable to read ICE Authority file: /home/greg/.iceauthority


Whats the prognosis doc? will it live again?

---

### Post by teaker1s on 2005-12-16
go into the home folder of the user using
'gksudo nautilus' to access as root

rename iceauthority to 'bakiceauthority' then log out and try logging in as the user(a new iceauthority will be created) if it works your sorted if not you still have old file

---

### Post by Redeyes_Gambit on 2005-12-16
*bangs head into desk for being so stupid*

Umm, slight problem. When I typed gksudo nautilus in the coomand line a password box popped up and I (being the un-inteligent person I am) typed in the wrong passwrod and now when I type gksudo nautilus it says:

(nautilus:10701): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and I don't get a box to type in a password anymore. Not even with the normal sudo command

*bangs head into desk again*

(edit):

Ok, maybe that was the right password, I don't know. I get that error but it might not have been from a bad password. Anyway so I did the gksudo nautilus thing (still getting the error but it launches) and I browse to the appropriate directory but there is no iceauthority file!

This is probably why it can't read it yes? ;)

---

### Post by teaker1s on 2005-12-16
my bad!!
terminal 
'sudo nautilus'

or for later use create a desktop launcher with command 
'gksudo nautilus'

ctrl-alt-backspace and login again, failing that reboot

---

### Post by Redeyes_Gambit on 2005-12-16
Well, seeing as though there is no iceauthority file there to delete what I may do to solve my problem is just copy all my files under my messed up login to a new one (thankfully I had created an "emergency" login for just this sort of occasion :D )

thanks for the help and the sudo nautilus thing, that will alow me to move the stuff i need out of my old login to a new one. Merry Christmas!

---

### Post by Redeyes_Gambit on 2005-12-17
Ok.... Seems as though the problem is more seriouse than I anticipated. Now the terminal under my new login is busted. THE TERMINAL! >:P . I was trying to launch nautilus with sudo. I type it out, it asks for my password and then it... just... sits there. nothing happens. So I thought I'd try and put in: 

sudo apt-get install stupid

(not that my machine terribly needed any more stupid but hey) and it also just sat there. doing nothing. at all. period.

At this point I'm just gonna try and forget about it for saturday and try and relax. Go play some games on my other machine where I know what I'm doing.

Some help would be mightily appreciated.

---

### Post by teaker1s on 2005-12-18
maybe this may help

[http://www.ubuntuforums.org/showthread.php?t=80599&page=2&highlight=icetrans](http://www.ubuntuforums.org/showthread.php?t=80599&page=2&highlight=icetrans)

---

