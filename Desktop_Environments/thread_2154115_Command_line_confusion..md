---
title: "Command line confusion."
date: 2013-06-13
forum: Desktop Environments
---

### Post by jfbooth on 2013-06-13
Running Xubuntu 12.04 with XFCE 4.8.  There is an application "Web Browser" on the Applications Menu.  It appears to be the GOOGLE CHROME browser.  Due to hardware limitations, I have to start Chrome with a command line.  I see no way to do that ... right click on Web Browser from the menu simply runs Web Browser.

I separately downloaded and installed CHROME.  There is a Chrome icon on my desktop.  From that icon, a right click/properties allows me to create the needed command line.

I am ASSUMING I have Chrome installed TWICE (About on each shows same exact version) .. once as Web Browser and again as Chrome.  The OS came with Web Browser and I installed Chrome.  

Here is where it gets foggy.  If I edit properties for CHROME, I can create the necessary command line.  I dragged the Web Browser from the menu to the desktop ... creating a shortcut.  Right click on shortcut ... properties ... and it APPEARS I can edit a command line ... which I did, but it did not work.  Closer look shows vast differences between the two properties.  I have concluded that Web Browser is somehow linked to the MENU much differently than CHROME is linked to its desktop icon.

Fine ... so solution seems to be uninstall CHROME ... don't need the same browser twice.  Find out how to 'command line' Web Browser ... hence this post.

Only problem there is ..... I fear CHROME is installed OVER Web Browser somehow.  If I uninstall CHROME ... system is honked up pretty good.  I fear this because one time I preferred Xfe file manager over Thunar .. and after installing Xfe .. and uninstalling THUNAR ... that is what happened ... honked up pretty good.  I learned ... don't go uninstalling stuff without knowing what you are doing (beyond the obvious).

Soooo my questions are:

Can I safely uninstall CHROME?
If I can ..... how do I do a command line edit for Web Browser?

I figure this has to do more with XFCE than it does with merely an application question ... which is why I post in this forum.  Forgive me if I am out of place.

Thank you in advance.

---

### Post by Cheesemill on 2013-06-13
The default browser that comes with Xubuntu (called Web Browser in the menus) isn't Chrome, it's Chromium.

You should be able to edit the command that it's run with by editing its .desktop file in the /usr/share/applications directory.

---

### Post by slickymaster on 2013-06-13
> **Cheesemill said:**
> The default browser that comes with Xubuntu (called Web Browser in the menus) isn't Chrome, it's Chromium...

Sorry for contradicting you Cheesemill, but the default browser packed in Xubuntu is Firefox, not Chromium.

---

### Post by Toz on 2013-06-13
Xfce uses the exo-open set of commands for preferred applications. For Web Browser, for example, it uses the command:
```
exo-open --launch WebBrowser %u
```
The "preferred" applications are set in **SettingsManager -> Preferred Applications**. Here you can specify which applications are opened using the exo-open commands (Web Browser, Mail reader, File Manager, Terminal Emulator).

---

### Post by jfbooth on 2013-06-13
> **slickymaster said:**
> Sorry for contradicting you Cheesemill, but the default browser packed in Xubuntu is Firefox, not Chromium.

Uhmmm .. I am the least informed among us, but opening Web Browser and clicking on ABOUT gives (see attachment) ... (or is this because I set Chrome as default???)  Now more confused than ever :confused:

EDIT:
However, this is from the XUBUNTU 12.04 website:

> Xubuntu comes with the award-winning, extensible Firefox web browser and the light-weight yet feature-rich Abiword for all your word-processing needs. Abiword is compatible with popular word processing file formats.

but I have no recollection of ever seeing FF ... though I installed some time ago.  Catfish shows tons of FF files etc ... but no FF on a menu .. anywhere.

---

### Post by jfbooth on 2013-06-13
> **Toz said:**
> Xfce uses the exo-open set of commands for preferred applications. For Web Browser, for example, it uses the command:
```
exo-open --launch WebBrowser %u
```
The "preferred" applications are set in **SettingsManager -> Preferred Applications**. Here you can specify which applications are opened using the exo-open commands (Web Browser, Mail reader, File Manager, Terminal Emulator).


YEAH!!!  I sensed there was some big difference.  Sooooo, if I understand, I should set PREFERRED (back) to Web Browser and Uninstall CHROME, and then 'command line' Web Browser as needed.  How do I do that ... in Settings Manager?????  thank you.

EDIT:  So I went to SETTINGS MANAGER/PREFERRED applications and set preference for Web Browser FROM Chrome to Debian Simple.  Ran Web Browser from MENU and get the same exact version from ABOUT as for CHROME.

EDIT:  Debian Sensible, ... not Simple.

---

### Post by Toz on 2013-06-13
> **jfbooth said:**
> EDIT:  So I went to SETTINGS MANAGER/PREFERRED applications and set preference for Web Browser FROM Chrome to Debian Simple.  Ran Web Browser from MENU and get the same exact version from ABOUT as for CHROME.

Which browsers were listed there? Just Chrome and Debian Simple? Was firefox there or did you remove the software from your system?

Open a terminal window, type in the following command and post back the results:
```
apt-cache policy firefox | grep Installed
```

---

### Post by jfbooth on 2013-06-13
> **Toz said:**
> Which browsers were listed there? Just Chrome and Debian Simple? Was firefox there or did you remove the software from your system?

Open a terminal window, type in the following command and post back the results:
```
apt-cache policy firefox | grep Installed
```

Wow ... what a mess.  Synaptic Pkg Mgr shows FIREFOX not installed.  Preferred Applications/Web Browser shows  Debian Sensible Browser, Google Chrome, and OTHER.  I do not recall uninstalling FF ... but it would have been so long ago, probably I did.  I tend to dump s/w I don't use.  

I do remember installing a chrome DEB from [www.google.com/intl/en/chrome/browser/](www.google.com/intl/en/chrome/browser/)

Right now, if I click on (menu) Web Browser I get what appears to be the exact same thing as if I click on Chrome desktop icon.  In fact, they both point to the same place ... usr/bin/google-chrome.

At this point, I don't even know what Debian Sensible even looks like or where to find it.

To answer your question:

```
jb@jb-Compaq-PC:~$ apt-cache policy firefox | grep Installed
  Installed: (none)
```

I did find out more about exo-open ... here   [http://linux.die.net/man/1/exo-open](http://linux.die.net/man/1/exo-open) and how to do 'command line' but it doesn't tell me how to do that 'safely'   meaning other than a direct terminal command ... and I am not going to do that unless I can undo it ....like in an editor or GUI or SOMETHING.

---

### Post by Toz on 2013-06-13
Okay, so the question is: which browser do you want to run with the default "Web Browser" menu item and panel launcher?
- If it is firefox, you will need to install firefox then change the Web Browser entry in Preferred applications to Firefox.
- If it is the Chrome instance that you installed (via the deb you downloaded), select the "Other" option in "Preferred Applications" and type/paste in the command that you use to run it (as mentioned in your first post).

As for your issue with the File Manager:
- If you want to use Thunar, re-install thunar and select it from the Preferred Applications drop down for File Manager (Utilities tab).
- If you want to use Xfe, then select it from the drop-down (hopefully it shows up there).

---

### Post by jfbooth on 2013-06-13
> **Toz said:**
> Okay, so the question is: which browser do you want to run with the default "Web Browser" menu item and panel launcher?
- If it is firefox, you will need to install firefox then change the Web Browser entry in Preferred applications to Firefox.
- If it is the Chrome instance that you installed (via the deb you downloaded), select the "Other" option in "Preferred Applications" and type/paste in the command that you use to run it (as mentioned in your first post).

As for your issue with the File Manager:
- If you want to use Thunar, re-install thunar and select it from the Preferred Applications drop down for File Manager (Utilities tab).
- If you want to use Xfe, then select it from the drop-down (hopefully it shows up there).

Thank you, Sir for all your patience.  It boils down to this.  IF Web Browser was originally linked to CHROMIUM and FF was complementary, I would have uninstalled FF and used CHROMIUM.  I would THEN 'fix' Chromium through exo-open so I can attain the command line I need.

What it looks like, to me, is I uninstalled FF.  I installed CHROME (deb).  I have no idea what 'Debian Sensible' is or WAS.  If IT was Chrome or Chromium, then I would link Web Browser to Debian Sensible (Chrome or Chromium), ... fix command line .. and dump Chrome deb.

Sooo, would LOVE to know what the #Y@ Sensible IS.  When I set Web Browser to Sensible, I get CHROME but dunno if that is my CHROME deb or whatever Sensible is/was in the first place.  I MIGHT have set Sensible to point from whatever it WAS to Chrome deb.

Sorry .. I am major confused at this point.  If you agree, FF is not installed.  I should UNinstall Google CHROME.  Then .... see if Web Browser to Sensible brings up anything.  Depending on what it is, ... IF ANYTHING ... go from there .. with a command line edit through exo-open ...assuming it is indeed Chrome/Chromium.  If it fails (and is pointed to Debian Sensible), then I must have honked up Sensible .. WHATEVER it is.  I would rejoice if I knew what Sensible is suppoed to be in the first place.

The Thunar fiasco was corrected long ago.  I don't remember what it boiled down to, but at the moment, I have Thunar and Xfe installed.  I would like to only have Xfe ... as it is (now) my preferred ap for File Manager.  From your input, I gather I am free to uninstall Thunar ... but last time I did, .. it was a disaster.

Thank you again for your patience.  I await your reply.

---

### Post by Toz on 2013-06-13
Debian-sensible is another internal variable (not an actual browser) that gets resolved via the /usr/bin/sensible-browser script. It would appear that it uses the value stored in x-www-browser. More information about system alternatives and update-alternatives can be found [here]("http://manpages.ubuntu.com/manpages/raring/man8/update-alternatives.8.html") and [here]("http://askubuntu.com/questions/233190/what-exactly-does-update-alternatives-do").

You can view the list of www browser alternatives on your system with this command:
```
sudo update-alternatives --list x-www-browser
```

I know this is confusing. Perhaps we can simplify things. Which browser do you want to make your main browser? We can set up Xfce to make sure it starts regardless of the method you use to initiate it.

---

### Post by jfbooth on 2013-06-13
> **Toz said:**
> Debian-sensible is another internal variable (not an actual browser) that gets resolved via the /usr/bin/sensible-browser script. It would appear that it uses the value stored in x-www-browser. More information about system alternatives and update-alternatives can be found [here]("http://manpages.ubuntu.com/manpages/raring/man8/update-alternatives.8.html") and [here]("http://askubuntu.com/questions/233190/what-exactly-does-update-alternatives-do").

You can view the list of www browser alternatives on your system with this command:
```
sudo update-alternatives --list x-www-browser
```

I know this is confusing. Perhaps we can simplify things. Which browser do you want to make your main browser? We can set up Xfce to make sure it starts regardless of the method you use to initiate it.

```
jb@jb-Compaq-PC:~$ sudo update-alternatives --list x-www-browser
[sudo] password for jb: 
/usr/bin/google-chrome
```

AHAH!!  You are so kind and patient.  With this new info .. apparently this Xubuntu came with FF on it.  Probably, Web Browser pointed to it ... since there is no 'browser' named Debian Sensible.  I must have uninstalled FF and installed Chrome deb.  That matches the current evidence.

I have a Chrome icon on desktop.  I managed to properly 'command line' it.  I click on Web Browser in menu, which is pointed to Debian Sensible .... and I get CHROME  but running NONcommand line.  THAT'S because of exo-open!!  Therefore, if I am correct, and I think I am, all I need to do is delete the CHROME ICON from desktop, and apply command line parameter to WEB BROWSER.

exo-open --launch [category] [[parameter]...]    -------- exo-open -launch Web Browser --allow-outdated-plugins

and I should get Chrome with command line and no extra browser installations I don't use.  Dat's whut I wanted, Boss.

1.  Give your 'approval' ... and I will make the changes.
2.  I have Xfe set as my preferred File Manager.  Do you think I can uninstall THUNAR??  I remember now ... last time I did that, I SAW where Synaptics seemed to want to uninstall some dependencies that looked a LOT like stuff NOT related to Thunar ... and that is what (I think) created the chaos.  What do you think?

Thank you.  You are one of the Gods.

EDIT:  Thought I had it .... but cannot figure out WHERE/HOW to pass --allow-outdated-plugins to Web Browser or Debian Sensible  ... which ever one/ones it needs to pass to.  :redface:  HANG ON ... DON'T REPLY ... I will be right back.  I think it may be working.

Nope.  So close.  Web Browser from menu ... preferred to Debian Sensible or Google Chrome opens CHROME without command line.

CHROME from desktop ICON opens CHROME with command line parameters.

I need to pass **--allow-outdated-plugins** to Web Browser somehow.

Chrome ICON properties/launcher says **/opt/google/chrome/google-chrome %U --allow-outdated-plugins** in the command field.

If I create a shortcut on desktop for Web Browser, and edit its LAUNCHER .. the command shows **exo-open --launch WebBrowser %u**

---

### Post by Toz on 2013-06-13
> **jfbooth said:**
> 
Chrome ICON properties/launcher says **/opt/google/chrome/google-chrome %U --allow-outdated-plugins** in the command field.


Lets try the easy approach first. 

Create the file **/usr/local/bin/start_google**:
```
gksu leafpad /usr/local/bin/start_google
```
...copy/paste this code:
```
#!/bin/bash
/opt/google/chrome/google-chrome --allow-outdated-plugins
```
...then save the file.

Next, we have to make that file executable. Issue this command:
```
sudo chmod +x /usr/local/bin/start_google
```

And finally, in Settings Manager -> Preferred Applications, select Other for the Web Browser dropdown and enter in this command:
```
/usr/local/bin/start_google
```

Does this work?

---

### Post by jfbooth on 2013-06-13
> **Toz said:**
> Does this work?

perfectly.  I can only babble some kind of gratitude.  The Ubuntu forum moderators and supportive members are simply fantastic.  Thank you.

---

