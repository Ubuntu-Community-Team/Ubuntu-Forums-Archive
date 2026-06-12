---
title: "Steam running very slowly after restarting"
date: 2015-12-06
forum: Gaming &amp; Leisure
---

### Post by Aaron_Wilson on 2015-12-06
I have created a question on askubuntu with the full details: 

[http://askubuntu.com/q/706119/479215](http://askubuntu.com/q/706119/479215)

**The Short Story**

I recently installed Ubuntu and was able to use steam for several hours. However, at some point, I reloaded it and it ran extremely slowly. I flailed around looking for solutions and eventually just reinstalled Ubuntu (figuring I'd broken something I could not find).

I've reinstalled steam and it worked for another several hours. I restarted it and it now runs very slowly. However, I can't remember if this is the first time I restarted, but I'd guess that it was.

These details point me to an appcache problem that seems to be common, but I have tried those solutions to no avail.

[B]Current Text of My AskUbuntu question:

[/B]>   Steam was working earlier today. I apparently made a change that  affected the operation, but I can't recall exactly when it stopped  working. 
  The first thing I know that I changed before verifying it worked was  installing Tweak and the Arc theme. Immediately after this, Steam became  extremely sluggish (~60s to respond to input). I tried reinstalling,  and now all I get is an invisible window.
  I have purged (including deleting .steam) and reinstalled steam numerous times.
  **General Info:**
  
[LIST]
[*]Latest proprietary drivers 
[*]nvidia 650M running in SLI 
[/LIST]
  **Output:**
  [http://pastebin.com/7HMLHTFZ](http://pastebin.com/7HMLHTFZ)
  While the Refresh Rates are posting, I have an invisible window (size of the Steam login window).
  **What I've Tried:**
  
[LIST]
[*][http://askubuntu.com/a/689899/479215](http://askubuntu.com/a/689899/479215) 
[*][http://askubuntu.com/a/614458/479215](http://askubuntu.com/a/614458/479215) (Edit solution, had to do this to get it working earlier) 
[*][http://askubuntu.com/a/345144/479215](http://askubuntu.com/a/345144/479215) 
[*]steam reset 
[*]Tried both USC and steampowered.com versions. The USC appears to  download files which don't match the number of bytes it expects. Both  have the same problem. 
[*]Tried reinstalling the gtk engines as described in numerous places. 
[*]probably some other things I've forgotten 
[*]dpkg --configure -a then sudo apt-get clean 
[*]removed a font.conf file that was causing an error. Now I get a different error. 
[*]LC_ALL=C steam solution found in some places 
[*]reviewed /var/logs, found GTK errors regarding denied permissions on  ~/.local/share/recently-used.xbel. Changed owner/group to [me] after  finding root owner/group may not be correct. 
[/LIST]
  **Updates**
  I reinstalled ubuntu. After carefully setting up everything, steam once again worked. 
  However, it has stopped working. Here is a better list of what I know I've changed/done since it worked:
  
[LIST]
[*]Installed wine (did not do this last time) 
[*]Attempted to install steam through wine. Note, this requires closing the native version. 
[*]Installed Octave 
[*]Tested some options in Ubuntu Tweak 
[*]Installed Java 8 JDK 
[*]Ran Clementine 
[/LIST]
  I have not autoremoved or purged anything this time. Note that this mean that Steam still loads, but is just extremely sluggish.

Here is the current output: [http://pastebin.com/4BcD4z5j](http://pastebin.com/4BcD4z5j)

     


---

### Post by oldrocker99 on 2015-12-07
Try this:
```
sudo apt-get purge steam
```
Then go to [https://steampowered.com](https://steampowered.com) and download **steam-latest.deb**. Install it:
```
sudo dpkg -i steam_latest.deb
```

You may get an error due to missing libraries, so type this:
```
sudo apt-get -f install
```

See if that works, and post the results.

---

