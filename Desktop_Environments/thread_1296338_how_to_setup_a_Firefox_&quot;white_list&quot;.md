---
title: "how to setup a Firefox &quot;white list&quot;"
date: 2009-10-20
forum: Desktop Environments
---

### Post by boondocks on 2009-10-20
I have root access on a Ubuntu 9.04 Desktop.

How do I setup a firefox "white list" where:
[LIST]
[*]ONLY the web sites in that list can be visited.
[*]Access to all other sites is blocked.
[*]Only root can change this "white list".
[/LIST]

---

### Post by undecim on 2009-10-20
I don't think this is a feature that can be done specific to firefox (except with an add-on, but then the addon could be removed)

You might be able to do it system-wide though. The only way I know to do this (although I know there are other ways...) is through OpenDNS, which is a free internet service. That might also be handy if you want to keep the same whitelist set up for multiple machines.

The only downside to OpenDNS is that websites can still be accessed by IP address

---

### Post by undecim on 2009-10-20
Hmmm... take a look at this add-on: [https://addons.mozilla.org/en-US/firefox/addon/1803](https://addons.mozilla.org/en-US/firefox/addon/1803)

In the description, it says it can be set up to filter all internet traffic except for a white list.

It's not exactly what you want, but it does provide a password protected white list. (A root-only modifiable whitelist isn't something a simple addon can do)

This could easily be removed by deleting the addon from the .mozilla folder in your home directory (or removing the addon itself if the addon doesn't protect that), but if you only want to keep your kids off the websites they shouldn't be on, this should do well.

---

### Post by boondocks on 2009-10-20
Thanks.  I will take a look.

Here is what I need ...
There is a small office area.
It has a guest room with a Ubuntu Desktop.

I want the visitors to be able to access web sites like:
[LIST=1]
[*]Google
[*]Yahoo
[*]Our internal web site for appointments, schdules, etc.
[/LIST]

---

### Post by i.r.id10t on 2009-10-20
I'm doign this with a squid proxy running on localhost, blocking all, and then having the whitelist (*.edu, google.com).  Firefox is locked down with a read-only profile directory, the ubuntu desktop user is locked down using pessalus.  Works well.

---

### Post by undecim on 2009-10-20
> **i.r.id10t said:**
> I'm doign this with a squid proxy running on localhost, blocking all, and then having the whitelist (*.edu, google.com).  Firefox is locked down with a read-only profile directory, the ubuntu desktop user is locked down using pessalus.  Works well.

If you are using this for an internet kiosk only, that will be good. You may also want to use epiphany instead of firefox, because you can lock it down well with pessulus.

You should also disable desktop effects via System -> Preferences -> Appearance, and any keyboard shortcuts relating to window management (minimize, close, etc) via System -> Preferences -> Keyboard Shortcuts. Actually, I would disable all the shortcuts there, with the exception of maybe the volume control (if you even have speakers)

Also, to keep the Ctrl+Alt+backspace and Ctrl+Alt+F* keys from messing stuff up, lock down Xorg by adding these options to Xorg.conf in the Serverflags sections:
```
Option "DontVTSwitch"  "true"
Option "DontZap"  "true"
```I would also be concerned with data retention. You don't want users to remain logged into gMail when they leave their computers, or for your browser to remember what usernames were typed in. This should be configurable in epiphany (before you lock it down), but I'm not sure. Just in case, I would make the profile directory read only, and lock epiphany from changing any files at all (using AppArmor)

And one more thing: You should make sure that this box is physically secure. Often times, people will place a hardware keylogger in the back of a computer between the keyboard plug and computer, and come back later to get any passwords that were typed. Ideally, it would be in a ventilated, locked cabinet, and only unlocked for neccessary maintence

Speaking of maintence, you should probably enable automatic package updates without confirmation, via System -> Preferences -> Software Sources ("Updates" tab)

If you need help setting anything up (after all, there is a lot to set up here), make sure to post back

---

### Post by lovinglinux on 2009-10-20
I think you could achieve what you want with [moblock](http://moblock-deb.sourceforge.net/). Simply create a blocklist with the range 0.0.0.0-255.255.255.255, which would block th entire internet, then add the IP addresses of the allowed web sites to moblock's allow list.

Since you need root access to stop/start moblock or change the blocklists, the users wouldn't be able to bypass the filter.

Additionally, you could use [PublicFox](https://addons.mozilla.org/en-US/firefox/addon/3911) to lock down Firefox functionalities.

---

### Post by boondocks on 2009-10-21
These is all valuable information.
I am experimenting.

When using Pessulus, how do you disable the items in:
[LIST]
[*]The Places Menu like Home Folder, Desktop, Documents, etc.
[*]The System Menu like Help and Support, About GNOME, About Ubuntu.
[/LIST]

---

### Post by undecim on 2009-10-21
> **boondocks said:**
> These is all valuable information.
I am experimenting.

When using Pessulus, how do you disable the items in:
[LIST]
[*]The Places Menu like Home Folder, Desktop, Documents, etc.
[*]The System Menu like Help and Support, About GNOME, About Ubuntu.
[/LIST]


If you have set up epiphany as a kiosk as per the instructions in my last post, you shouldn't have to worry about disabling menu items (unless you want your guests to be able to use apps other than epiphany)

It might be best to forget gnome altogether and go with a lightweight window manager (to reduce system resource usage, and to prevent people from messing around with stuff if epiphany crashes)

Or maybe there is some way to start epiphany fullscreen without using a window manager? I'd have to experiment with that...

** opens VirtualBox **

---

### Post by boondocks on 2009-10-21
> **undecim said:**
> If you have set up epiphany as a kiosk as per the instructions in my last post, you shouldn't have to worry about disabling menu items (unless you want your guests to be able to use apps other than epiphany)
...
Or maybe there is some way to start epiphany fullscreen without using a window manager? I'd have to experiment with that...

Thank you for the suggestions.

Besides the Epiphany Web Browser, I would like to have the Calculator (gcalctool) available.
So these 2 icons on the desktop somewhere and the ability to switch between them - would be nice.

---

### Post by undecim on 2009-10-21
Maybe a combination of fluxbox (desktop environment) and idesk or fbdesk (for the launcher icons) then?

Fluxbox is some work to set up, especially if you are not used to editing config files manually. although I certainly wouldn't mind helping you out; I use FB a lot, so I can write the config. Also, you will need to do some work to keep your GTK theme settings in fluxbox; running GTK apps without a theme makes them look ugly

Seems to me that would be the best thing to do: squid with a whitelist, a Locked-Down Xorg.conf, a Locked-Down fluxbox, idesk, epiphany (locked down with pessulus), and gcalctool

With that setup, the only two things that a guest can do with that computer will be visiting websites you approve, and using the Calculator (or any other tools like that you wish to add.)

Maybe also lock down the guest user's home directory permissions, to prevent saving items from epiphany, except to a thumb drive.

---

### Post by boondocks on 2009-10-21
Actually, I have made quite a bit of progress.
I am still working with Gnome and Pessulus.
[LIST]
[*]Deleted the Top Panel from the Ubuntu Desktop.  No more Main Menu (Applications, Places, System).
[*]Put the Epiphany and Calculator icons on Desktop.
[*]Used Pessulus to enforce limitations on Epiphany.
[*]Locked down the Panels with Pessulus.
[*]The Bottom Panel could not be deleted.
[/LIST]
So all you see on the Desktop is:
[LIST]
[*]The 2 icons.
[*]A short and narrow Bottom Panel.
[/LIST]
But I can still right-click on the Desktop and that shows the menu with:
[INDENT]Create Folder
Create Launcher...
Create Document
Clean Up by Name
Keep Aligned
Change Desktop Background
[/INDENT]So how do I disable this Desktop right-click menu?

---

### Post by undecim on 2009-10-21
That is managed by nautilus. The only way I know to stop this is to tell nautilus not to draw a desktop, but that gets rid of your icons as well. You can replace them with idesk, or better yet, wbar.

You can try the .deb file here: [http://code.google.com/p/wbar/downloads/list](http://code.google.com/p/wbar/downloads/list)

There is also wbarconf, for graphical configuration of the launchers: [http://www.ihku.biz/wbarconf/](http://www.ihku.biz/wbarconf/)

Personally, I think that a desktop with nothing but your company logo and a Mac-ish launcher bar would look nice. You can add some more launchers to launch the web browser to different sites, like gmail, yahoo, etc. Just remember to get high enough resolution icons that they don't get blurred when stretched to launcher size.

I'm kind of worried about a couple things though: even with epiphany not storing any files, email cookies are still stored until the browser exits. You should leave a note somewhere on the machine (in a script as part of the launchers for the web browser icons, for example) warning people to close all browser windows when they are done.

---

### Post by boondocks on 2009-10-21
> **undecim said:**
> I'm kind of worried about a couple things though: even with epiphany not storing any files, email cookies are still stored until the browser exits. You should leave a note somewhere on the machine (in a script as part of the launchers for the web browser icons, for example) warning people to close all browser windows when they are done.
I understand your concerns.  We will setup a post-desktop-login script that will do an auto-logout if the desktop has no keyboard or mouse activity (like a screensaver).

---

### Post by undecim on 2009-10-21
To display a warning message before launching a browser, install gmessage, and put this in epiphany.sh in the guest user's home directory:
```
#!/bin/bash
if ps x | grep [e]piphany-browser; then
true
else
gmessage -title Warning -center -wrap -file ~/warning.txt
fi
epiphany-browser $@ &
```
then make it executable with "sudo chmod a+x epiphany.sh" and type a warning message and put it in warning.txt in the guest users home directory. Something about closing the browser when done to prevent other from logging into email accounts that were used, how [company name] cares about your privacy and security, etc...

That will show a warning message, as long as there is no epiphany window already open.

I'm working on a script that will kill epiphany when a user is idle (with a warning first, of course!), but I can't figure out how to get the number of seconds that a user has been idle in a way that I can compare it to another number in a bash script.

---

### Post by undecim on 2009-10-21
> **boondocks said:**
> I understand your concerns.  We will setup a post-desktop-login script that will do an auto-logout if the desktop has no keyboard or mouse activity (like a screensaver).(Posted my previous post before seeing this)

Yes, that should work well. you should make sure that user wont be able to choose an xterm session though. I think that rather an auto-logout, something to kill epiphany would be better. I would put it together myself, but like i said, I don't know how to get idle time in bash.

---

