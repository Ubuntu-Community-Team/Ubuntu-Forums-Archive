---
title: "Add RSS To Liferea From Chrome"
date: 2010-06-03
forum: Desktop Environments
---

### Post by jlward4th on 2010-06-03
How do I add RSS feeds from web pages in Chrome to Liferea?

---

### Post by Boondoklife on 2010-06-03
I know with firefox I used the command liferea-add-feed to add to the program, I would imagine it would be the same for chrome.

---

### Post by jlward4th on 2010-06-04
That is what I did in Firefox too.  But I can't figure out if there is any way to run that command from Chrome.  I installed the RSS Subscription Extension but it seems to only allow calling other URLs, not local apps.

---

### Post by ode on 2010-06-12
1. Install the ['RSS Subscriptions with FEED: Handler Support'](https://chrome.google.com/extensions/detail/ehojfdcmnajoklleckniaifaijfnkpbi) Chrome/Chromium extension.


2.

    2.1 Alt+F2--->gconf-editor

    2.2 In gconf-editor: Ctrl+F--->Search for 'feed'

    2.3 In the search box at the bottom of gconf-editor you will get some results (I got two.) Click on '/desktop/gnome/url-handlers/feed'.

    2.4 In the options box in the top right click on the 'command' key.

    2.5 Change the value to either 'liferea-add-feed "%s"' or 'akregator -a "%s"' depending on your preference. Press return to complete the edit.


3.

    3.1 Goto a webpage whose feed you wish to subscribe to.

    3.2 Now that you have installed the extension there will be an rss icon in the right of Chrome/Chromium's location bar. Click it.


    3.3 The browser will take you to a 'Subscribe to feed' page. In the dropdown box next to 'Subscribe to this feed using:' select 'Default Application'.

    3.4 Click the 'Subscribe Now' button. A warning box named 'External Protocol Request' will pop up. Press the 'Launch Application' button and confirm that the feed has been added to your reader.

    3.5 If the feed was added to your reader successfully you can click the 'Remember my choice for all links of this type.' checkbox in the 'External Protocol Request' box the next time you subscribe to a feed. Now the next time you click the rss button in the location bar then the 'Subscribe Now' button on the 'Subscribe to feed' page the feed should be added to your reader.

---

### Post by jlward4th on 2010-06-13
Thanks.  That seems to be getting me closer.  But I didn't have a feed item anywhere in gconf-editor.  I tried to add one with:
gconftool-2 --set --type=string /desktop/gnome/url-handlers/feed/command '/usr/bin/liferea-add-feed %s'

But that didn't seem to do the trick.

---

### Post by ode on 2010-06-13
Ah sorry, I assumed you'd have the key because I did, I'm on 10.04 of Ubuntu btw, which version are you on?

Feed also has two other keys in addition to command. 'enabled and needs_terminal.


Try:

'gconftool-2 --set --type=bool /desktop/gnome/url-handlers/feedfoocommand/enabled True'

'gconftool-2 --set --type=bool /desktop/gnome/url-handlers/feedfoocommand/needs_terminal False'


Hopefully turning 'enabled' on will fix it for you.

BTW the 'command' key has "" around the %s. Maybe you don't need this since there are no spaces in url's though.

---

### Post by jlward4th on 2010-06-13
Thanks!  This did the trick:
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/feed/enabled True

---

### Post by colin-m on 2010-06-22
Ode
Just to say thanks for the how-to add RSS to Liferea from Chrome. I had been trying to do this for the last week. Until I stumbled on the thread, I was beginning to think it wasn't possible!

---

### Post by Soarer on 2010-09-15
I'm trying to do this too.

When I click on the command key for the desktop feed, gconf-editor wont allow edits. It says:

```
Currently pairs and schemas can't be edited. This will be changed in a later version.
```

This is gconf version 2.30.0

I am also running 10.4. Ubuntu help says the schemas are in /etc/gconf/schemas but my system has no such directory.

I also tried to run gconf-editor with sudo, but the message is the same. 

Anyone else seen this please?

[EDIT] - I got it to work with all 3 of 'gconftool2' terminal commands. Thanks everyone.

---

### Post by BoHu on 2011-04-12
Doesn't work for me. Must be an XFCE thing.

---

### Post by jlward4th on 2011-09-28
I finally figured out a way to do this that works consistently for me.

Create a new file named ***~/.local/share/applications/liferea-add-feed.desktop*** containing:

```
[Desktop Entry]
Name=Liferea Feed Reader
GenericName=Feed Reader
Comment=Download and view feeds
Exec=liferea-add-feed %U
Icon=liferea
StartupNotify=true
Terminal=false
Type=Application
Categories=Network;News;
X-Ubuntu-Gettext-Domain=liferea
Version=0.9.4
```

Add a new line to the ***~/.local/share/applications/mimeapps.list*** file:

```
x-scheme-handler/feed=liferea-add-feed.desktop
```

---

### Post by lakitu on 2012-03-05
hey just wanted to say ode's method normally worked, but i kept getting "xdg-open [feed url here]" in Chrome followed by no result the last couple times - but in that case, jlward4th's way worked for me. thanks man/grrrl =P

hopefully this will be integrated in the future, somehow. 

thanks tho, both of you.

- a happier liferea/chrome/rss user

---

