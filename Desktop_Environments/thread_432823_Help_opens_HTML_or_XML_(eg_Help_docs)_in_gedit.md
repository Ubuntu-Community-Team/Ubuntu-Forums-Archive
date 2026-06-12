---
title: "Help opens HTML or XML (eg: Help docs) in gedit"
date: 2007-05-04
forum: Desktop Environments
---

### Post by haz2a on 2007-05-04
Since upgrading Dapper to Edgy a week ago, I have not been able to read HTML or XML help docs in yelp.  

If I go: Help > Ubuntu Help Centre > Desktop - yelp opens the 'Desktop' help categories OK. 
If I then click on Desktop User Guide (an XML file) - it opens in gedit! 
The same thing happens if I go to any HTML or XML file - they all open in gedit. 
Man Pages and GNU Info Pages all open OK in yelp.  

If I open an XML file in yelp from the command line I get the following errors:- 

$ yelp file:///usr/share/djvu/languages.xml 
I/O error : Permission denied 
I/O error : Permission denied 
I/O error : Permission denied 
I/O error : Permission denied 
I/O error : Permission denied 
I/O error : Permission denied 
I/O error : Permission denied 
(and the terminal hangs)  

Yelp opens with the Ubuntu Help Centre top page, but opens the languages.xml file in gedit again.  

I don't know if this might have been the cause, but in Dapper I had installed Firefox 2 from the Mozilla download, leaving Ffx 1.5 from Ubuntu installed too, as recommended, for apps needing gecko. I didn't remove Ffx 2 before upgrading (via 'update-manager -C') but the original installation from the Moz download has disappeared from /opt. Ffx 2 seems to work fine.  

I have tried completely removing Firefox (which also removes yelp + others) and reinstalling them, but it makes no difference. 
I created a new user and the same thing happens there.  

One other problem (just in case its related) is that I can no longer browse icons in nautilus as an ordinary user - no images are shown for the icons. It doesn't seem to be a simple permissions issue - its the same even when the icons are in my home dir and I am the owner of them. I have to run nautilus as root to see the icons.   

I'm not sure where to go from here - any suggestions appreciated.  
Thanks  
Haz.

---

### Post by DonS on 2007-05-04
Sounds like you're file associations (mime types) are screwed up.  Try reinstalling gnome-mime-data (or other packages relating to 'mime').

Other than that, I don't really know, sorry.

---

### Post by haz2a on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/nautilus/+bug/19101](https://bugs.launchpad.net/nautilus/+bug/19101)  [https://bugs.launchpad.net/ubuntu/+source/planner/+bug/41772](https://bugs.launchpad.net/ubuntu/+source/planner/+bug/41772)  [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/91636](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/91636) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Thanks for that suggestion Don - it set me off in the right direction and I finally found the solution. Yelp problem was indeed connected with the icon display/browsing issue, and caused by a Gnome 'security feature' to warn when it thinks the filename extension is inconsistent with its MIME type. Some of the MIME data or configs were corrupt.

Key signs of this corruption are messages like "No application suitable for automatic installation is available for handling this kind of file" and "The filename "xxx.xxx" indicates that this file is of type "yyy". The contents of the file indicate that the file is of type "zzz"".

It did not seem to be necessary to move/rename
~/.local/share/applications/mimeinfo.cache as suggested elsewhere

I believe the following steps fixed the problems:-

1. sudo update-mime-database /usr/share/mime

2. sudo dpkg-reconfigure shared-mime-info

3. $ killall gnome-panel
    $ killall nautilus

Haz

---

