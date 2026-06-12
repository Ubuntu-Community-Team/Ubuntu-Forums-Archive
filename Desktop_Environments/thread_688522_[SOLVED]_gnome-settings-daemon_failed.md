---
title: "[SOLVED] gnome-settings-daemon failed"
date: 2008-02-05
forum: Desktop Environments
---

### Post by yanny on 2008-02-05
Hi,

When I start Ubuntu I got an error telling me that gnome settings daemon failed to start or something.

When I type: gnome-settings-daemon start in terminal, I get this:


```
** (gnome-settings-daemon:8544): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-m5EidlfAcx: Connection refused

(gnome-settings-daemon:8544): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-m5EidlfAcx: Connection refused

(gnome-settings-daemon:8544): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:8554): WARNING **: failed to register with the message bus

root@ubuntu:/etc/network# gnome-settings-daemon restart

** (gnome-settings-daemon:8573): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-m5EidlfAcx: Connection refused

(gnome-settings-daemon:8573): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-m5EidlfAcx: Connection refused

(gnome-settings-daemon:8573): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object

** (gnome-screensaver:8581): WARNING **: failed to register with the message bus
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
```

---

### Post by Het Irv on 2008-02-05
Have you tried restarting your computer since the first time you saw this error.  I have had this happen on occasion and a restart later it worked fine.  I don't know of a more permanent fix.

---

### Post by yanny on 2008-02-05
Thank you very much, I restarted the computer and that error did not show and everything (font type and size) is back to normal.

From now on I know what to do when facing this problem again. :D

---

### Post by serfcx on 2008-02-06
had this problem and solved neatly as follows

Edit your etc/hosts file
the first line should read 127.0.0.1 localhost - change too 127.0.0.1 localhost "name" where "name" is the name of your computer (without the quotes)

Then go to System -> Preferences -> Sessions and add 
Name :- GDM Daemon
Command :- gnome-settings-daemon

Has worked for me.

---

### Post by yanny on 2008-02-06
Thank you very much! I've tried what you told, see if it works for me as well. ^^

OH NOO! I got an error when I restart apache2:
Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName.

This is what I have:

127.0.0.1       localhost                       ubuntu

---

### Post by serfcx on 2008-02-07
> **yanny said:**
> Thank you very much! I've tried what you told, see if it works for me as well. ^^

OH NOO! I got an error when I restart apache2:
Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName.

This is what I have:

127.0.0.1       localhost                       ubuntu

Beyond my competance - I do not run apache - sorry for problem created.

---

### Post by MaindotC on 2008-02-14
I just suddenly had the same issue.  What I did prior to this happening was:

My post on this form: [http://ubuntuforums.org/showthread.php?t=685351](http://ubuntuforums.org/showthread.php?t=685351) I was trying to fix the suspend feature on my T60 - followed all but one step from the wiki.

Installed Bitpim, xmame, Kxmame, kamefu, gfceu.

Modified desktop effect settings to include raindrop effects, ring selector, fire painting, and horizontal wobbling of windows.

Changed Dosbox startup res/window size to 1600x1200 then changed it back when it didn't do anything.

Lastly, I had my T60 vga-out plugged into a 21'' Samsung monitor set to 1600x1200.  I'll reboot now and hopefully it'll go away and hopefully not happen again.

---

### Post by MaindotC on 2008-02-14
Reboot worked, but now when I move my arrow over my minimized windows, it only shows a preview of a currently selected window.  Very frustrating.  I think it was something to do with that cpufreq-utils wiki - anytime you start manually editing configuration files you're opening more doors for problems.  We'll see.

---

### Post by shinji2001xyz on 2008-02-15
> **yanny said:**
> Thank you very much! I've tried what you told, see if it works for me as well. ^^

OH NOO! I got an error when I restart apache2:
Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName.

This is what I have:

127.0.0.1       localhost                       ubuntu

You may need to insert your FQDN in this line like this:
127.0.0.1       ubuntu.domain              ubuntu            localhost

then reboot.

if it's not that, you'll need to set up your httpd.conf...

---

### Post by Anduu on 2008-02-16
From time to time the gnome settings daemon just barfs...Its just a glitch that will be worked out eventually.

A simple restart is all thats required.

---

### Post by MaindotC on 2008-02-16
> **Anduu said:**
> From time to time the gnome settings daemon just barfs...Its just a glitch that will be worked out eventually.

A simple restart is all thats required.

Unacceptable.

---

### Post by Anduu on 2008-02-16
> **strAlan said:**
> Unacceptable.:rolleyes:

Well considering I would have to restart Windows every other day because it barfed,I find once in a blue moon for Linux more than acceptable.

---

### Post by MaindotC on 2008-02-17
> **Anduu said:**
> :rolleyes:

Well considering I would have to restart Windows every other day because it barfed,I find once in a blue moon for Linux more than acceptable.

True, but working at my school's helpdesk (which is all winblows) I've found that 90 percent of problems arise from ad/spy/malware and viruses.  Vista is having majour issues, but XP was simply a matter of keeping up-to-date patches and warning people about the potential harm of using Limewire (or more specifically, the stuff that you can get from Limewire, not the program itself).

---

