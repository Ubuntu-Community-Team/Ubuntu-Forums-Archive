---
title: "Evolution stopped no online account"
date: 2018-02-03
forum: Desktop Environments
---

### Post by Jonners59 on 2018-02-03
I am running the latest 17;10 update after running software update.
i have been using for some year Evolution and have a number of google accounts set up on it via the app online accounts.  This allows not only email but also calender and contacts, sadly not notes/tasks to be synchronised.

The problem is that after the upgrade Evolution stopped synchronizing with the accounts so is unusable.  I search for online accounts but it is not in any menu.  In Synaptic it is listed as installed.  I have tried to uninstall and re install and complete uninstall and re install, but it makes no difference.  When i run in terminal it says /bin/online-accounts does not exist

Anyone help me please

---

### Post by #&amp;thj^% on 2018-02-05
Sorry late for the party.
Myself I stopped using Evolution and use my borwser's E-mail client.(Seamonkey)
This was fixed.(Suppositiously) Old Bug Report.:

```
apt policy gnome-online-accounts
```

I'm using version "3.26.2-1"
Not seeing it here on this install, but again I no longer use evolution.
To call it from the terminal try:

```
gnome-control-center online-accounts

```
Bug Description

> Impact
-----
Users will be unable to log in to a Google account using GNOME Online Account which is used by default in Ubuntu GNOME and Ubuntu Budgie.

Any other browser or service that uses webkit2gtk is similarly broken, such as the Epiphany browser.

The second issue fixed here is that any user who opted in to the new YouTube will only get a white screen when they attempt to visit YouTube. The new YouTube is still opt-in now but will eventually become the default for everyone.

Test Case
---------
1. Install the updated webkit2gtk on Ubuntu GNOME.
2. Restart your computer (this may be necessary because of LP: #1610944)
3. Log in. Open Settings>Online Accounts. Remove any Google accounts already configured. Add your Google account.
4. Install Evolution if it's not already installed and verify that your Gmail account loads.

Optional, because the beta is closed to new entrants:
5. Install epiphany-browser
6. Open the Web app (epiphany-browser) and log in to your Google account.
7. Visit [https://www.google.com/new](https://www.google.com/new) to make sure that your browser is set to use the "new YouTube."
8. If the new YouTube only shows a white screen, this part of the bug is not fixed.

Regression Potential
--------------------
The regression potential was limited by only cherry-picking the commits to fix these 2 high-profile issues. 2.16.2 is being rolled out to most distros now.

Other Info
----------
Fixed in 17.10 Alpha "artful" by updating to 2.16.2

Original Bug Report found here: [https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1687019](https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1687019)

Some have changed>> Going into Online Accounts settings and switching off Calendar in the "Use For" section will stop the password-entry dialogs from pestering you; the rest of your Google account connectivity will function normally. (Well... I don't know about Chat as I don't use it, so mine's always switched off.)

---

### Post by Jonners59 on 2018-02-06
> **1fallen said:**
> Sorry late for the party.
Myself I stopped using Evolution and use my borwser's E-mail client.(Seamonkey)
This was fixed.(Suppositiously) Old Bug Report.:

```
apt policy gnome-online-accounts
```

I'm using version "3.26.2-1"
Not seeing it here on this install, but again I no longer use evolution.
To call it from the terminal try:

```
gnome-control-center online-accounts

```
Bug Description



Original Bug Report found here: [https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1687019](https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1687019)

Some have changed>> Going into Online Accounts settings and  switching off Calendar in the "Use For" section will stop the  password-entry dialogs from pestering you; the rest of your Google  account connectivity will function normally. (Well... I don't know about  Chat as I don't use it, so mine's always switched off.)

OK  I have the same but it does not show in menu anywhere and when called  upusing your cmd I get a blank window and an error message in the  terminal...

[HTML]
** (gnome-control-center:9785): WARNING **: Invalid  categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings;  for panel gnome-background-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel; for  panel gnome-datetime-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel; for  panel gnome-info-panel.desktop

** (gnome-control-center:9785):  WARNING **: Invalid categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings;  for panel gnome-notifications-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings;  for panel gnome-online-accounts-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings;  for panel gnome-privacy-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings;  for panel gnome-region-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-SystemSettings;  for panel gnome-sharing-panel.desktop

**  (gnome-control-center:9785): WARNING **: Invalid categories  System;Settings;X-GNOME-Settings-Panel;X-GNOME-SystemSettings; for panel  gnome-user-accounts-panel.desktop[/HTML]

????????????????????  ANy ideas?

---

### Post by #&amp;thj^% on 2018-02-06
Just so I'm clear here you are running a Gnome DE? Right?
EDIT: Just seen in title of the thread XFCE.

I have found that if "**unity-control-center"** was installed, I had issues.(And that could be just on my end or system though)
There was another workaround for this by setting:
```
XDG_CURRENT_DESKTOP=GNOME
```
But i never used it due to fact that when you/I then run "gnome-control-center" from the command line you're just running unity-control-center instead. This isn't making gnome-control-center work, it's just running a different app. :(
I tried very hard to keep Unity to it's own install. (Installed on a _separate partition_ with **no **other DE's installed on that one.)

You won't see the unity version in non-Unity desktops because it has the line "OnlyShowIn=Unity;". 
I would either wait to see if this gets fixed soon or open a Bug Report.
Sorry for the bad news I thought I might be able to help here but I guess not.
One more Idea here you could try and install "**unity-control-center**" and use that.(If not already installed)

unity-control-center source package in Artful you will get these packages with the install.

```
libunity-control-center-dev: utilities to configure the GNOME desktop
libunity-control-center1: utilities to configure the GNOME desktop
libunity-control-center1-dbgsym: Debug symbols for libunity-control-center1
unity-control-center: utilities to configure the GNOME desktop
unity-control-center-dbgsym: Debug symbols for unity-control-center
unity-control-center-dev: utilities to configure the GNOME desktop
unity-control-center-faces: utilities to configure the GNOME desktop - faces images
```

Good Luck and Kind Regards :)

---

### Post by #&amp;thj^% on 2018-02-07
After more searching I've found, If I set XDG_CURRENT_DESKTOP=GNOME instead of XFCE and run gnome-control-center from the command line everything appears, although I get some warnings:-
```

** (gnome-control-center:3142): WARNING **: Ignoring launcher landscape-client-settings (missing desktop file)
** (gnome-control-center:3142): WARNING **: Ignoring launcher ubuntuone-installer (missing desktop file)
```

This part is not relavant to you.(XFCE) Unless you installed Unity control center already.;)
If I unset XDG_CURRENT_DESKTOP, then I can run unity-control-center from the command as well.

What I ended up doing was a bit hackish I'm afraid. My user has its own 'bin' directory which I like to keep at the top of the PATH, so I created an overriding shell script to set the XDG_CURRENT_DESKTOP variable and then call the system command thus:
Script: cat gnome-control-center
```

#!/bin/sh

# A frontend to the system 'gnome-control-center' to set the
# XDG_CURRENT_DESKTOP variable to GNOME. This ensures all icons appear.
# A bug has been logged for this issue.
# Only applies to xubuntu sessions

if [ "$DESKTOP_SESSION" = "xubuntu" ]
then
    export XDG_CURRENT_DESKTOP=GNOME
fi

/usr/bin/gnome-control-center

exit 0
```
You could also rename /usr/bin/gnome-control-center and then call that in an override /usr/bin/gnome-control-center script as above in /usr/bin I suppose, **_but I'd be a bit wary of this._**

---

### Post by Jonners59 on 2018-02-10
Thanks > **1fallen said:**
> 
I gave up in the end.  I stopped using Online Accounts.  Seems Evolution now is able to work out the box with gmail and its calander and contacts, I hope.  So reverted to that, but I do loose all the other features OLA gave me.  Thanks anyway.

Best
Jonners59

---

