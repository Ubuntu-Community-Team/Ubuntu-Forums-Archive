---
title: "How may I integrate thunderbird with indicator-messages to get mail notification"
date: 2010-12-01
forum: Desktop Environments
---

### Post by sefs on 2010-12-01
Hi all,

Pre-amble
---------
I currently use mail-notification to alert me to new email, it sits in the system tray.  When a new mail comes in it alerts me as such.  I DO NOT have to have thunderbird open or running to be notified.

What I need
-------------
I want to replace mail-notification with indicator messages.  I want the same functionality that I got with mail-notification.  That is, to have an icon sitting in the notification area that alerts me when new mail arrives.  I do not want to have thunderbird open for this to occur.

What I currently have.
----------------------
I have lib-notify installed.  I have the notify add-on installed in thunderbird, I have indicator-messages installed.
I have thunderbird.desktop in /usr/share/applications
I have a file called thunderbird that has one line which is the path to the desktop file above in /usr/share/indicators/messages/applications/

With this when i click on the icon in the notification area i DO see the listing for thunderbird, but the icon is not correct, it has a black bacground with a red circle in it with a slash.  When i click on this item thunderbird launches.

I do not recieve notificaion messages (i.e the letter icon does not turn green) unless i open thunderbird and check for messages manually.  This defeats the purpose of having a notification in the system tray.

Can anyone help me solve those two issues.

Additionally changes made to /usr/share/applicatons/thunderbird.desktop are not reflected in the indicator.

Thanks.

---

### Post by germanix on 2010-12-01
see if this "how to" helps

[http://ubuntuexplore.blogspot.com/2010/05/ubuntu-how-to-add-thunderbird-in.html](http://ubuntuexplore.blogspot.com/2010/05/ubuntu-how-to-add-thunderbird-in.html)

---

### Post by sefs on 2010-12-01
Thanks for responding.

Unfortunately this does not work as expected.

---

### Post by oldmankit on 2010-12-09
I've tested the howto: it just provides a link to thunderbird.  It doesn't monitor for new mail - I've tested it (using Ubuntu 10.10).  The OP was pretty clear about the specification.  I'm also looking for the same thing!

Any other ways to do this?

---

### Post by owiknowi on 2010-12-10
The following works for me:
remove Evolution and set Thunderbird as default mail application (Preferences/Preferred Applications).

Thunderbird should however be running (minimized because I always log in manually, no stored passwords).

---

### Post by Rodney9 on 2010-12-10
[http://ubuntuforums.org/showthread.php?t=1439519](http://ubuntuforums.org/showthread.php?t=1439519)

---

### Post by sefs on 2010-12-10
> **oldmankit said:**
> I've tested the howto: it just provides a link to thunderbird.  It doesn't monitor for new mail - I've tested it (using Ubuntu 10.10).  The OP was pretty clear about the specification.  I'm also looking for the same thing!

Any other ways to do this?

If you mean to have something that monitor for new email, when the email application of choice is close, then at this moment indicator-messages cannot do it.  There is talk I think of this functionality being built in at a later stage.  

I am however back to using mail-notification as it does what it does well.  Sit in the notification area and alerts when new mail arrives, without having to have the email application of choice open.

If we want to use indicator-messages for that we would have to wait and monitor the progress of its development until such time that it includes this functionality.

---

### Post by Krytarik on 2010-12-10
I'm using [Indicators for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/") , it works like a charm! 
Altough you don't get the notification-ballons when e.g. watching videos in fullscreen, but that's a common issue of notify-osd.

---

### Post by sefs on 2010-12-10
> **Krytarik said:**
> I'm using [Indicators for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/") , it works like a charm! 
Altough you don't get the notification-ballons when e.g. watching videos in fullscreen, but that's a common issue of notify-osd.

Do you have to have TB open for this to work in any form or fashion?

---

### Post by oldmankit on 2010-12-10
I've found a way of getting notifications through indicator-applet (in the little mail icon) without having to have thunderbird running.  Credit goes to [http://www.techgarten.com/extensions/thunderbird/integrate-messaging-applet-thunderbird-maverick-cloudsn/](http://www.techgarten.com/extensions/thunderbird/integrate-messaging-applet-thunderbird-maverick-cloudsn/)

Add the private repository as follows, update, and then install cloudsn

```
sudo add-apt-repository ppa:chuchiperriman/cloudsn && sudo apt-get update && sudo apt-get install cloudsn
```Set-up the details for your mail server; go into preferences and select 'indicate status with: indicator applet'.

In your account details, you can go to 'advanced' and tell it to execute command 'thunderbird'.

I had to log-out and log-in again before it integrated with the indicator-applet mail icon.

If anyone tests this please give feedback.  I tried a number of things to get this to work yesterday, and I might have forgotten one of the steps. I will probably make it a little how-to since so many people want this feature.

(I wasn't happy with mail-notification because it had such a large number of dependencies, and put a bunch of evolution stuff that I didn't want.)

---

### Post by Krytarik on 2010-12-10
> **sefs said:**
> Do you have to have TB open for this to work in any form or fashion?
Ok, one must have Thunderbird running, because it's simply an extension.
Not the way you wanted it, right?!

---

### Post by sefs on 2010-12-11
> **Krytarik said:**
> Ok, one must have Thunderbird running, because it's simply an extension.
Not the way you wanted it, right?!

Yes, my reckoning is if I have TB open, then I can already see that I have email.  This may be good for persons that run multiple desktops with TB open in one of them, but I'm a single desktop user.

---

### Post by Krytarik on 2010-12-11
> **sefs said:**
> Yes, my reckoning is if I have TB open, then I can already see that I have email.  This may be good for persons that run multiple desktops with TB open in one of them, but I'm a single desktop user.
So as I! I usually have Tb in the background or minimized, before using that extension I didn't recognized a new mail unless I checked directly in Tb. Now, when a mail arrives I get a notification-ballon (if not watching fullscreen-video, like I said) and the envelope in the indicator-applet (upper panel) gets green-colored.

---

### Post by sefs on 2010-12-11
> **oldmankit said:**
> I've found a way of getting notifications through indicator-applet (in the little mail icon) without having to have thunderbird running.  Credit goes to [http://www.techgarten.com/extensions/thunderbird/integrate-messaging-applet-thunderbird-maverick-cloudsn/](http://www.techgarten.com/extensions/thunderbird/integrate-messaging-applet-thunderbird-maverick-cloudsn/)

This sounds and looks good!  Will have to take it for a spin. Thank you for that.

---

### Post by Canned on 2011-01-31
> **Krytarik said:**
> I'm using [Indicators for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/") , it works like a charm! 
Altough you don't get the notification-ballons when e.g. watching videos in fullscreen, but that's a common issue of notify-osd.
Call me a security freak, but author of this extension has created only this one add-on and it's not verified by Mozilla... How can I be sure that by installing it I don't grand him access to my e-mail?

---

### Post by Krytarik on 2011-01-31
> **Canned said:**
> Call me a security freak, but author of this extension has created only this one add-on and it's not verified by Mozilla... How can I be sure that by installing it I don't grand him access to my e-mail?
By checking its source code.;-)
Tell me, if you find something suspicious.

---

### Post by Canned on 2011-02-01
If I had any clue about programming then I definitely would :)
I trusted that 24k downloads would pick up a security threat and installed it as well :)
But... With this plugin you still have to have TB on, right?
So what is it really helpful with, since you get a pop-up notification from TB itself anyway...
Did I miss on something?

---

### Post by oldmankit on 2011-02-01
> Did I miss on something?     Check out my post about cloudsn.  I can vouch for the fact the it gives me a little green you've got mail by the time I've logged into gnome - definitely before I start thunderbird.

---

### Post by danjaredg on 2011-05-11
You can try [ThunderUbuntu]("http://danjared.wordpress.com/proyectos/ubuntu-thunderbird/") Addon

[IMG]http://danjared.files.wordpress.com/2011/05/thunderubuntu.png[/IMG]

---

### Post by Krytarik on 2011-05-12
Updated instructions on how to install the add-on I previously mentioned:
```
sudo add-apt-repository ppa:ruben-verweij/thunderbird-indicator
sudo apt-get update
sudo apt-get install xul-ext-indicator 

```
[https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator](https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator)

The PPA only provides packages for Maverick and Natty. But you can safely install the Maverick deb-package manually if you are running Lucid, I did so.

Greetings.

---

### Post by Steeperton on 2011-05-12
> **Krytarik said:**
> I'm using [Indicators for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/") , it works like a charm! 
Altough you don't get the notification-ballons when e.g. watching videos in fullscreen, but that's a common issue of notify-osd.

The full-screen thing is something that annoyed me immensely! So I amended notify-osd. You can grab the updated version from: [https://launchpad.net/~avesummathat/+archive/ppa](https://launchpad.net/~avesummathat/+archive/ppa)

Hope this helps.

---

### Post by Krytarik on 2011-05-12
> **Steeperton said:**
> The full-screen thing is something that annoyed me immensely! So I amended notify-osd. You can grab the updated version from: [https://launchpad.net/~avesummathat/+archive/ppa]("https://launchpad.net/%7Eavesummathat/+archive/ppa")

Does that version also allow to modify the appearance/position of the Notify-OSD bubble, like these?:
[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26/](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26/)
[https://launchpad.net/~qwerty12/+archive/notifyosd](https://launchpad.net/~qwerty12/+archive/notifyosd)

---

### Post by Steeperton on 2011-05-17
> **Krytarik said:**
> Does that version also allow to modify the appearance/position of the Notify-OSD bubble, like these?:
[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26/](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26/)
[https://launchpad.net/~qwerty12/+archive/notifyosd](https://launchpad.net/~qwerty12/+archive/notifyosd)

No it doesn't. But there's been a couple of people asking for it, so I may look into doing so!

---

### Post by Krytarik on 2011-05-17
> **Steeperton said:**
> No it doesn't. But there's been a couple of people asking for it, so I may look into doing so!
That would be great! However, I'm afraid I won't benefit from it since you only build packages for the respective latest release, right!?

---

