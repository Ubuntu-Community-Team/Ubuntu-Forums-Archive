---
title: "how to permanently disable gnome-keyring-daemon"
date: 2010-12-29
forum: Desktop Environments
---

### Post by gmoore777 on 2010-12-29
I will pay good money for someone to tell me how to
permanently disable the gnome-keyring-daemon.

I've seen posts where there was a work around to store
passwords in clear text. That's not a real solution.
I've seen posts where killing the process and removing
~/.gnome2/keyrings is a temporary solution until next time
you log in or reboot machine.
Removing the package, will force removal of the whole kitchen sink.
That's too intrusive.

There must be a way to stop this thing from starting up, ever.

I tried commenting out the entries in the /etc/pam.d/* files
that refer to "pam_gnome_keyring.so", and have also unchecked the 3 keyring related entries under System --> Preferences --> Startup Applications,
which are affiliated with these 3 files:
  /etc/xdg/autostart/gnome-keyring-secrets.desktop 
  /etc/xdg/autostart/gnome-keyring-pkcs11.desktop 
  /etc/xdg/autostart/gnome-keyring-ssh.desktop    

But I still get this one process once I log into the console window:
/usr/bin/gnome-keyring-daemon --start --foreground --components=secrets

There must be one more file somewhere that says, "hey when someone logs in and starts up gdm, start the gnome keyring daemon".

---

### Post by mcduck on 2010-12-29
Removing it would break all the programs that use it to store their passwords and keys.

What's wrong with just removing the keyring password if you don't want to use a login password or unlock the keyring manually? It's really not like removing the keyring would make any noticeable performance increase or anything like that... Quite the opposite, really, as you'd have to make every keyring-using program more complicated so that they could each handle their own keys. Using a single tool to handle this for every program is much more sensible (and resource friendly) solution.

---

### Post by gmoore777 on 2010-12-29
i don't want to turn this into a debate of why a customer (me) wants a thing a certain way, but gnome-keyring-daemon, is considered by some people to be a nuisance.
One particular problem is when a user VNC's to the console, in some cases the gnome-keyring pops up looking for a password, which of course is impossible to enter, since, the user has not completed the VNC connection to the console to even see it.
I'm not looking for a solution to this VNC problem, I want to disable gnome-keyring-daemon permanently.
It's a password vault application, and we don't want it enabled.

---

### Post by TenPlus1 on 2010-12-29
[http://ubuntuforums.org/showthread.php?t=796410&page=2](http://ubuntuforums.org/showthread.php?t=796410&page=2)

---

### Post by mcduck on 2010-12-29
> **TenPlus1 said:**
> [http://ubuntuforums.org/showthread.php?t=796410&page=2](http://ubuntuforums.org/showthread.php?t=796410&page=2)

That's not  about disabling the keyring, that's just an ugly way to reset (or unset) the password, while the same can be done directly through the keyring manager without destroying all the saved data while doing it. :D

Actually disabling or removing the keyring would break all the programs that depend on it.

---

### Post by gmoore777 on 2010-12-30
"depend" on it. You mean, the program would fail and prevent
you from running that particular application?

Name a couple programs that "depend" on the gnome-keyring being up and running?

Then I will  kill the gnome-keyring process and run the application that you will mention and report back to you on 
what actually happened.

---

### Post by mcduck on 2010-12-30
Killing the process would not work, it starts automatically when any program requests for data from the keyring.

But you could start by testing apps like Evolution, Empathy, Ubuntu One and the Network Manager. :)

(of course they still *work*, you just need to type all your passwords and such every time you start the programs, as they have no way to store the passwords for you)

(remove execute permission from /usr/bin/gnome-keyring-manager and log out and back again to see what works and what fails without it)

---

### Post by gmoore777 on 2010-12-31
hey mcduck, thank you for that very simple suggestion of changing
the permissions of /usr/bin/gnome-keyring-daemon.
(there is no gnome-keyring-manager anywhere on the machine)

It worked!

The gnome-keyring-daemon process does not start up.

I am able to set up an Evolution email account without the 
"Choose password for new keyring" dialog popping up after
entering my email password during setup and then
able to get my email.

I also am able to change my System -->Preferences-->RemoteDesktop
password without the same dialog popping up.

I have noticed an expected error in /var/log area:

auth.log: Dec 31 13:58:10 bee02 gdm-session-worker[1704]: gkr-pam: couldn't run gnome-keyring-daemon: Permission denied
auth.log: Dec 31 13:58:10 bee02 gdm-session-worker[1405]: gkr-pam: gnome-keyring-daemon didn't start properly properly


So nothing bad has happened, as of yet. I will reply back to this thread if I find anymore useful information.

Having said all of that, I also have discovered a second
method of "disabling" gnome-keyring-daemon.

1.)
comment out the pam_gnome_keyring.so entries in the 
/etc/pam.d files:

/etc/pam.d/common-password: #password optional pam_gnome_keyring.so
/etc/pam.d/gdm: #auth    optional pam_gnome_keyring.so
/etc/pam.d/gdm: #session optional pam_gnome_keyring.so auto_start
/etc/pam.d/gnome-screensaver: #auth optional pam_gnome_keyring.so

One or more of these pam.d entries cause this process to start up when logging into the Console window:
  /usr/bin/gnome-keyring-daemon --daemonize --login

2.)
Comment out the "Exec" line in 
 /usr/share/dbus-1/services/org.freedesktop.secrets.service 

like this:
  # Exec=/usr/bin/gnome-keyring-daemon --start --foreground --components=secrets

Commenting this out will prevent the following process 
from starting up at login time and also during the time
when setting up Evolution, and there is no current
gnome-keyring-daemon process running.

/usr/bin/gnome-keyring-daemon --start --foreground --components=secrets


Note: there is another very similar file that I did not need
to edit but may be worth mentioning. That file is:
   /usr/share/dbus-1/services/org.gnome.keyring.service


3A.)
I was fiddling with these settings previously but I have
not determined that they have any effect but is worth mentioning
that a user may want to uncheck these:
System-->Preference-->Startup Applications -->
       "Certificate and Key Storage"
       "Secret Storage Service"
       "SSH Key Agent"

3B.) a more permanent way to uncheck them for all users and make the entry un-editable is with these 3 commands. (requires a reboot or maybe just a logout to take effect)

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory  --type bool --set /apps/gnome-keyring/daemon-components/secrets FALSE
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory  --type bool --set /apps/gnome-keyring/daemon-components/pkcs11 FALSE
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory  --type bool --set /apps/gnome-keyring/daemon-components/ssh FALSE

It will be interesting to see if the next package updates of gnome-keyring or libpam-gnome-keyring will override the above edits and/or pop up a dialog asking which edits to keep: maintainers or the users.

---

### Post by Larry Hammer on 2011-02-24
Thank You tired of that thing my self.
as far as security goes if trying to hack the laptop they already got keep em busy fine with me.

---

### Post by WyleECoyote on 2011-05-14
thank you gmoore777

I have installed Debian testing(wheezy) and I was looking all over for an option like this because when I try the "unsafe storage" "fix", the buttons are non-responsive, there is NO command line option to disable it, and is a known bug but no one wants to fix it or give a way to disable the stupid keyring.

---

### Post by sdundon on 2012-12-15
Removing execute permissions working great on Lubuntu 12.10.  With gnome-keyring-daemon I can't copy/paste my SSH key from keepassx.  Fixed!

---

### Post by wildmanne39 on 2012-12-15
Old thread closed.

---

