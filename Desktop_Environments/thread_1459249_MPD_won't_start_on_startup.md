---
title: "MPD won't start on startup"
date: 2010-04-21
forum: Desktop Environments
---

### Post by denarced on 2010-04-21
I've added mpd to System->Preferences->Startup Applications several times and it always just disappears and of course isn't started.
I have used both mpd and /usr/bin/mpd as the command.
I have done a log search as follows:
```
sudo find /var/log -type f -mtime -5 -exec grep -i -e 'mpd' '{}' \+
```
and nothing significant was found, e.g. an error message indicating that the mpd startup command was removed.

Anyone know a solution ?

Much thanks in advance.

---

### Post by Brandon Williams on 2010-04-22
Post the contents of your ~/.config/autostart/XXX.desktop file, where XXX is the name used to represent mpd in your Startup Applications screen. If necessary, 'grep mpd ~/.config/autostart/*.desktop' to figure out which file it is.

Also, take a look at ~/.xsession-errors to see if there are any useful log messages there (post the content if you're not sure).

And finally, take a look at the mpd log file to see if there are any useful log messages there. By default, the log file is /var/log/mpd/mpd.log if you run mpd at system startup. Presumably you run mpd as a regular user (if not, why add it to 'Startup Applications'?), so your log file will not be in the default location.

---

### Post by denarced on 2010-04-22
So,
naturally I couldn't post the content's of the mpd.desktop
file since it didn't exist. Found nothing in .xsession-errors
and nothing at .mpd/mpd.log either. xsession-log wasn't long
and I can say for sure that there was nothing on this issue
but mpd.log is huge since it's set on verbose.

So I thought, let's re-create the problem: I added the startup
again and checked the error logs. Nothing
But now it started ok. That's the damnest thing, it got fixed
all on it's own. That's just not possible. Either I ****ed up
on the first attempts or the problem is intermittent. The for-
mer is more likely but I will post the error if the problem
occurs again.

---

### Post by dannymichel on 2010-04-28
[edit] sorry, fixed

---

### Post by bodinux on 2010-06-13
May I suggest that you edit /etc/default/mpd to start mpd automatically with the configuration file of your choice ?

---

### Post by jpkotta on 2010-06-13
There are 2 common ways to run mpd.  The way that is set up by default is system wide, where mpd looks at /etc/mpd.conf and is started by /etc/init.d/mpd (and automatically at boot by links in /etc/rc?.d/).  The other way is to start it as a normal user in your ~/.xsession or your window manager or whatever.  Then it will get its config from ~/.mpdconf.  Either way, you have to tell it to start in some way (either the rc?.d links or something on login) and you have to edit the mpd.conf.  I usually run it as a normal user, and I've found that there can be interactions if a system-wide mpd is also running, so I always delete the mpd symlinks in rc?.d/.

---

### Post by engmex on 2010-12-15
I have a similar problem i.e. mpd is not starting as a service at boot.  I can't understand why running the sripts are in /etc/init.d and /etc/init the symbolic links are in /etc/rc*.d. If I run the script from intit.d or rc*.d at the command line it starts fine.  Any suggestions?

---

### Post by jpkotta on 2010-12-16
Have a look at errors.log and mpd.log in /var/log/mpd/.

---

### Post by engmex on 2010-12-17
> **jpkotta said:**
> Have a look at errors.log and mpd.log in /var/log/mpd/.
Thanks for the reply!  I already checked those files there is no message.

---

### Post by engmex on 2010-12-18
I've found the problem, but not the solution!  The problem is that I want mpd to listen to connections on my local network, but when the mpd script is called by upstart the network has not come up yet.  I've tried changing the mpd script to K99, but that doesn't help because it is still called before the network has time to assign the IP address.  Any suggestions?
Additionally I have another question.  One of the reasons that it took me so long to find the problem is that I'm not getting any error messages.  I understand that the init scripts are now called by upstart, but where are they logged to.  I can't find any messages in any log file anywhere.

---

