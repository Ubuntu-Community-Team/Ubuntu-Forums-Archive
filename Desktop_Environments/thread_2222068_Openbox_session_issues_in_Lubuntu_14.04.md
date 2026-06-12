---
title: "Openbox session issues in Lubuntu 14.04"
date: 2014-05-05
forum: Desktop Environments
---

### Post by vasa1 on 2014-05-05
I was quite happy logging into "Openbox" instead of Lubuntu when on 13.10. But now, in 14.04, I finding something odd.

Although everything works "normally", my **~/.xsession-errors** picks up quite a few errors. If I run the default Lubuntu session, the only entry I see is:
> Script for ibus started at run_im. and ~/.xsession-errors.old has 
> Script for ibus started at run_im.
init: lxsession main process (3519) terminated with status 1
init: Disconnected from notified D-Bus bus

In an Openbox session most programs I run seem to be adding entries to ~/.xsession-errors even though the programs seem to function just fine.

Can some kind soul with Lubuntu 14.04 please run an Openbox session for a while and see if ~/.xsession-errors gets more entries relative to the Lubuntu session?

---

### Post by bapoumba on 2014-05-05
@vasa : I'll look into it tonight. I have no pure openbox session here as far as I can tell, will set up one. I've wanted to try that out in a while.
To note, I have to exit ibus in lubuntu 14.04 for Chromium to work.

---

### Post by vasa1 on 2014-05-05
> **bapoumba said:**
> @vasa : I'll look into it tonight. I have no pure openbox session here as far as I can tell, will set up one. I've wanted to try that out in a while.
To note, I have to exit ibus in lubuntu 14.04 for Chromium to work.
Thank you :) I'll look forward to your findings.

Yes, turning off ibus is needed to enter text in Chromium:
[https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007293.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007293.html)
and
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

But Chrome 34 doesn't have the problem.

---

### Post by bapoumba on 2014-05-05
[http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126)
I had bookmarked this thread. Any other link that I may need ?

---

### Post by bapoumba on 2014-05-05
Sorry to bump, I could not resist and had a look. I can indeed choose the openbox session when I  log in. Will need further investigations as I am stuck with a querty keyboard when I'm using azerty here. Will try the language settings from the LightDM screen, but I do want my system in English with a French keyboard. Need to go to work for now ;)

---

### Post by vasa1 on 2014-05-05
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126)
I had bookmarked this thread. Any other link that I may need ?

That thread has other links scattered about and also points to stinkeye's help in sorting out Openbox's right-click menu.

---

### Post by vasa1 on 2014-05-05
> **vasa1 said:**
> ... 
In an Openbox session most programs I run seem to be adding entries to ~/.xsession-errors even though the programs seem to function just fine.

Can some kind soul with Lubuntu 14.04 please run an Openbox session for a while and see if ~/.xsession-errors gets more entries relative to the Lubuntu session?
Many of the errors/warnings/messages have this format:
```
(*program_name*:*PID*): GLib-CRITICAL **: Source ID *nnn* was not found when attempting to remove it
```and this seems to be some sort of upstream GNOME issue: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368)

I don't know why these aren't seen in a Lubuntu session if they are of a general nature.

---

### Post by bapoumba on 2014-05-05
Logged in from openbox. Not easy with the wrong keyboard setting, in particular for the password :)
My current file :
```
cat .xsession-errors
Script for ibus started at run_im.
Unable to create /home/bapoumba/.dbus/session-bus
Script for ibus started at run_im.
nm-applet-Message: using fallback from indicator to GtkStatusIcon
QGtkStyle was unable to detect the current GTK+ theme.

(x-terminal-emulator:1646): Gtk-WARNING **: Unknown property: GtkTable.valign

(x-terminal-emulator:1646): Gtk-WARNING **: Unknown property: GtkTable.valign

(x-terminal-emulator:1646): Gtk-WARNING **: Unknown property: GtkTable.valign

(process:1666): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

```
I suppose the nm-applet error comes from me auto-starting it in lubuntu.

Edit : I could sort out the keyboard layout "detail", ouf :)

---

### Post by vasa1 on 2014-05-05
```
(process:1666): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```is known to come [from Firefox]("bugzilla.mozilla.org/show_bug.cgi?id=833117#c7").

Did you get any error associated with PCManFM?
I get ```
** (pcmanfm:6198): WARNING **: modules directory is not accessible
```only in the Openbox session.

---

### Post by bapoumba on 2014-05-05
> **vasa1 said:**
> ```
(process:1666): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```is known to come [from Firefox]("bugzilla.mozilla.org/show_bug.cgi?id=833117#c7").

Did you get any error associated with PCManFM?
I get ```
** (pcmanfm:6198): WARNING **: modules directory is not accessible
```only in the Openbox session.

Yes, still logged in the Openbox session :
```
** (pcmanfm:3347): WARNING **: modules directory is not accessible
```

I'm using it from the lxpanel.

Edit :
[http://sourceforge.net/p/pcmanfm/bugs/831/](http://sourceforge.net/p/pcmanfm/bugs/831/)
Looks there is a fix from 4 days ago.
And here of course [http://ubuntuforums.org/showthread.php?t=2217698](http://ubuntuforums.org/showthread.php?t=2217698) ;)

---

### Post by vasa1 on 2014-05-05
> **bapoumba said:**
> Yes, still logged in the Openbox session :
```
** (pcmanfm:3347): WARNING **: modules directory is not accessible
```

I'm using it from the lxpanel.

Edit :
[http://sourceforge.net/p/pcmanfm/bugs/831/](http://sourceforge.net/p/pcmanfm/bugs/831/)
Looks there is a fix from 4 days ago.
And here of course [http://ubuntuforums.org/showthread.php?t=2217698](http://ubuntuforums.org/showthread.php?t=2217698) ;)

Well, nice to know a patch has been accepted but it's intriguing that ~/.xsession-errors in the Lubuntu session is so "silent". I wonder if the Lubuntu devs have managed to suppress writing to that file during a Lubuntu session and that using the Openbox session shows what really goes on?

---

### Post by bapoumba on 2014-05-05
> **vasa1 said:**
> Well, nice to know a patch has been accepted but it's intriguing that ~/.xsession-errors in the Lubuntu session is so "silent". I wonder if the Lubuntu devs have managed to suppress writing to that file during a Lubuntu session and that using the Openbox session shows what really goes on?

I'm going to go back to the lubuntu session unless there are other tests you'd like me to do.
My Openbox session will need some tweaking around to be to my liking, I'll probably have a deeper look tomorrow.
I spent quite some time with the keyboard layout already :)

---

### Post by bapoumba on 2014-05-05
Bump for having a crash trying to add the panel to the autostart apps:
```
(openbox:2762): GLib-CRITICAL **: Source ID 20 was not found when attempting to remove it
```
With various numbers for source id.
Guess this is it : [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368)

Edit: I got stuck by apport. I thought I had cancelled the report but when logging out, I got welcomed with a blank screen. I could not restart LightDM from one of the virtual terminals, had to reboot.

---

### Post by vasa1 on 2014-05-05
@bapoumba, thanks for looking into things!

It's a relief to know it's not just me and that people on other systems have seen the "Source ID *nnn* was not found when attempting to remove it" line.

From all this I feel the .xsession-errors can be ignored if one wants to use the Openbox session (for whatever reason).

---

### Post by bapoumba on 2014-05-05
Hmm. [https://bugzilla.gnome.org/show_bug.cgi?id=721369](https://bugzilla.gnome.org/show_bug.cgi?id=721369)
If all the applications have to be reviewed, we may get them for quite a while..

---

### Post by vasa1 on 2014-05-06
> **bapoumba said:**
> Hmm. [https://bugzilla.gnome.org/show_bug.cgi?id=721369](https://bugzilla.gnome.org/show_bug.cgi?id=721369)
If all the applications have to be reviewed, we may get them for quite a while..
[s]I've got a small partial list of applications that don't (seem to) cause writing to *.xsession-errors*:
gcolor2
google-chrome
gpaint
leafpad
lxtask
lxterminal

For the others, I'm going to try appending **2>/dev/null** to my shortcuts in lubuntu-rc.xml and menu.xml.

Seems to work for Firefox and Seamonkey.[/s]

---

### Post by bapoumba on 2014-05-06
That is quite a bit of edits in there vasa :)

---

### Post by vasa1 on 2014-05-06
> **bapoumba said:**
> That is quite a bit of edits in there vasa :)
Yes :(

Things need more testing. I saw a Leafpad entry and *2>/dev/null* may not work in all cases.

---

