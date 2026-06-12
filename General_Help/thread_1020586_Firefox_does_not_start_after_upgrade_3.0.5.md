---
title: "Firefox does not start after upgrade 3.0.5"
date: 2008-12-24
forum: General Help
---

### Post by 1script on 2008-12-24
Hi All,

Firefox forced an upgrade on me two days ago and it is no longer able to start. A small bar "Starting Firefox Web Browser" comes up on the taskbar for 10 seconds or so and then nothing else happens. I checked system logs, there is nothing in there that has anything to do with Firefox (or has timestamp of my attempts to start it). Starting 'firefox' in terminal returns nothing.
I had to dust off my old Windows laptop to post this. Very embarrasing :redface:

System: Release 8.10(intrepid)
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1


Looking for any help I can get.

P.S. What's an alternative browser I can install to at least post here from the same PC so I can copy/paste any logs/messages?

---

### Post by taurus on 2008-12-24
Did you by any chance install a bunch of add-on before you upgraded to the latest version of firefox from the repos?

Opera is another option.

[http://www.opera.com/browser/](http://www.opera.com/browser/)

---

### Post by 1script on 2008-12-24
No, no addons whatsoever. I just reinstalled it, too. It worked for one session, I shut the PC down. Then turned it back up and it does no longer work again.

---

### Post by thisperishedmin on 2008-12-24
can you launch from terminal?

(alt+f2 > gnome-terminal) and then "firefox" ?

---

### Post by TeXtonyx on 2008-12-24
> **1script said:**
> Hi All,

Firefox forced an upgrade on me two days ago and it is no longer able to start. A small bar "Starting Firefox Web Browser" comes up on the taskbar for 10 seconds or so and then nothing else happens. I checked system logs, there is nothing in there that has anything to do with Firefox (or has timestamp of my attempts to start it). Starting 'firefox' in terminal returns nothing.
I had to dust off my old Windows laptop to post this. Very embarrasing :redface:

System: Release 8.10(intrepid)
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1

Looking for any help I can get.

P.S. What's an alternative browser I can install to at least post here from the same PC so I can copy/paste any logs/messages?

---------------------------------------------
Firefox
"Tools>Options>Advanced>Update

Where it says "When updates to Firefox are found" select "Ask me 
what I want to do." 

TeX: I think the thing to do is prevent it. Some of the updates
make older add-ons incompatible, from 3.03 to 3.04 for instance.

What I'm going to do is look for the older version that worked
and uninstall the new Firefox and replace it with the old.
To be safe I'm gonna unhook from the internet so that no update
can happen while I'm changing the settings in Tools.

[http://www.oldapps.com/firefox.htm](http://www.oldapps.com/firefox.htm)
This looks like older versions of Firefox for Windows.

[http://mac.oldapps.com/firefox.php](http://mac.oldapps.com/firefox.php) .dmg for Mac.

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/)

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.4/linux-i686/en-US/firefox-3.0.4.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.4/linux-i686/en-US/firefox-3.0.4.tar.bz2)

taurus
November 15th, 2008, 04:46 PM
You don't build firefox. You download it, unpack it, and then run it. 
Therefore, you might want to move your firefox-3.0.4.tar.bz2 to /opt

sudo mv firefox-3.0.4.tar.bz2 /opt
cd /opt
sudo tar xvjf firefox-3.0.4.tar.bz2
cd firefox
./firefox

--------------------------------------

"Do that and delete the old FF program folder after you
uninstall and before you install the new (old) version.

To be safe, I would create a new profile for the new
installation because older versions of FF might not like
profiles modified by the newer versions of FF."

TeX: First I'm going to try reinstalling the old version over
the new (3.05) version. If that doesn't work then I'll delete
the new one and reinstall the old one. Better save Bookmarks.

---

### Post by 1script on 2008-12-24
> **thisperishedmin said:**
> can you launch from terminal?

(alt+f2 > gnome-terminal) and then "firefox" ?

Nope, nothing at all happens.

---

### Post by fooman on 2008-12-24
i would try deleting the hidden mozilla configuration files....first back up your favorites/bookmarks

next, open your home folder (places > home folder) and in the toolbar, click "view"...then put a check next to "show hidden files"

find the .mozilla folder,  right click on it and choose "move to trash"

try to open firefox again and see if it works.

hope that helps.

---

### Post by 1script on 2008-12-25
Sorry, guys. I had to drop out of this discussion because the PC simply would not start at all after I went for a simple reboot. Had to re-install GRUB before I could bring the PC up again. 

Firefox started fine for the first time. I worked on the PC for couple hours, then shut it down. 

Today I turned it back on and lo and behold Firefox does not start again.  

Deleted the ~/.mozilla 

Made no difference. 

So, to recap: 
#1 starting 'firefox' in terminal generates no message, no window comes up.

#2 There are no messages anywhere in the log files that pertain to Firefox (as shown by System Log)

#3 'firefox', 'ubufox', 'firefox-3.0', 'firefox-3.0-branding', 'firefox-3.0-gnome-support' are all installed, all version 3.0.5. Everythign was re-installed (including purge) at least twice by now

#4 Starting Firefox in a usual way through the icon creates a taskbar item that says "Starting Firefox Web Browser" and then it disappears and nothing else happens

#5 Firefox settings have been deleted: rm -rf ~/.mozilla

#6 WTF?



Typing this on Opera which actually turned out to be not so bad at all. Still want Firefox back though, so any suggestion would be greatly appreciated.

---

### Post by TeXtonyx on 2008-12-25
Purge firefox. Install an earlier version that worked. Turn off 
automatic updates.
I think something else is wrong with your computer and FF is a symptom.

---

### Post by fslezak on 2008-12-25
Try to install Epiphany. It is a very good web browser that I have.
Hope you like it!

Code:
> sudo apt-get install epiphany-browser

P.S. This is a replacement for Firefox. Make sure to set it your default browser.

---

