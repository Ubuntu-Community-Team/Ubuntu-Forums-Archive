---
title: "Firefox 1.0.7 update broke my Firefox"
date: 2005-09-23
forum: Desktop Environments
---

### Post by petrol on 2005-09-23
All,

I was just doing my duty in keeping up to date... I ran the firefox update to 1.0.7 and firefox no longer loads. I got an error :

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite ' /var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox


This error comes in the ubuntu software update and in Synaptic. Please Help!

Petrol

---

### Post by seaeric on 2005-09-23
Same here. I also tried apt-get on the command line and it gave me the same message.  Please someone post your fix when you figure it out.

Thanks

---

### Post by petrol on 2005-09-23
i wonder how many are not able to post because their browsers are broken too... :-#

---

### Post by Hairy_Palms on 2005-09-23
i wish opera could use mplayer plugins etc coz it is soo much better than firefox

---

### Post by Wide on 2005-09-23
Yep, got shotdown here also. ](*,)

---

### Post by debaser13 on 2005-09-23
Mine as well...had to install Konqueror to get online just to see if anyone has figured this out...I tried deleting:

/var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite ' /var/lib/mozilla-firefox/extensions.d/00classic

as well as the other file which comes up as error as root but it still no dice.

Any suggestions from those who are soooo much better at this stuff than myself? 

Or, to be honest, I am getting a little tired for Firefox.  Anything out there which anyone considers better?

-carl

---

### Post by jdmazz on 2005-09-23
Same here. At least I knew not to upgrade at work once my home one broke :)

---

### Post by debaser13 on 2005-09-23
Here is the thread that is addressing this problem...but, I tried the suggestions and they did not work for me...not sure what I am doing wrong.

[http://www.ubuntuforums.org/showthread.php?p=367285#post367285](http://www.ubuntuforums.org/showthread.php?p=367285#post367285)

---

### Post by minholi on 2005-09-23
Firefox is running here only by using 'sudo mozilla-firefox', it's a dangerous and not recommended way to use it, but for now I use this to download Opera 8.5 (static linked version).

---

### Post by seaeric on 2005-09-23
This seemed to work for me.

sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install

---

### Post by nubbe on 2005-09-23
Follow debaser13:s link, it worked for me
or do what seaeric suggested.
I did...
:)
First time I've had trbl with backports, I think

---

### Post by petrol on 2005-09-23
I tried the things in that post and they worked after i did:
killall firefox-bin

Petrol

---

### Post by treris on 2005-09-23
[QUOTE=petrol]All,

I was just doing my duty in keeping up to date... I ran the firefox update to 1.0.7 and firefox no longer loads. I got an error :

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite ' /var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox


This error comes in the ubuntu software update and in Synaptic. Please Help!

Petrol[/QUOTE]

try uninstalling version 1.0.6 of both the mozilla-firefox and then the firefox packages before installing firefox 1.0.7, that worked for me

---

### Post by debaser13 on 2005-09-23
And I ended up following the good ol' "Restart and Everything Will Work Out" method which, it did.  Of course, this was after I followed the commands on the link I provied above.  Regardless, looks like a few methods are working.  But, from now on, it looks like I will keep Konqueror on my app list for times like these.

Carl 

\\:D/

---

### Post by DeathOnJuice on 2005-09-23
Argh, the same thing happened to me! I tried marking mozilla-firefox for complete removal, installing it again, reinstalling the stuff it uninstalled (ubuntu-desktop and yelp), and restarting. I could install it, but not open it. So, I downloaded Mozilla and went to UbuntuForums (here) for some help. I tried one of the solutions, and I had to modify it slightly for it to work for me. Here's what I had to do (note that it's slightly different from what the other people did):

sudo apt-get update
sudo dpkg --purge firefox
sudo dpkg --purge firefox-gnome-support
sudo apt-get upgrade
ONLY DO THE FOLLOWING STEP IF ASKED (I didn't have to do it)
sudo apt-get -f install
killall firefox-bin

Note that while you probably won't have to do the second to last step, YOU MUST DO THE LAST STEP! Then, just open Firefox and be happy.

---

### Post by usererror on 2005-09-23
if the package is broken, installing firefox from a tar-ball is fairly easy.  if anyone wants instructions, i can post them. (it's one thing i do know how to do. :grin: )

---

### Post by sal on 2005-09-23
i followed the instruction here and got it to install.
the only hitch was that it killed my firefrox icon in the programs menu.
i just recreated the link and up and away it was running again.
my only question is i created the link pointing to
'/usr/lib/mozilla-firefox/firefox' but should i have pointed it to /usr/bin/firefox instead?
thanks.

---

### Post by bearbigears on 2005-09-23
had the same problem and followed seaeric advise and it worked thanks seaeric.

---

### Post by nbx909 on 2005-09-23
It broke firefox here too, so i tried to uninstall and then reinstall it and it didn't work.
So what should i do?
--edit--
NVM i saw what DeathOnJuice said and now it works

---

### Post by kleeman on 2005-09-23
No problems here at all. It might just be me but it looks like there has been a mild speedup as well.

---

### Post by Irony on 2005-09-23
Am I correct in saying that I should uninstall Firefox 1.0.6 before installing Firefox 1.0.7 - should I select *Removal* or *Complete Removal*;

[IMG]http://www.ironclub.net/ubuntu/firefox.png[/IMG]

Are these these the two items I should remove?

---

### Post by mlmurray on 2005-09-23
> **Irony]Am I correct in saying that I should uninstall Firefox 1.0.6 before installing Firefox 1.0.7 - should I select *Removal* or *Complete Removal* said:**
> http://www.ironclub.net/ubuntu/firefox.png[/IMG]

Are these these the two items I should remove?

I removed mozilla-firefox, and firefox.  I run Kubuntu, so I didn't have to remove mozilla-firefox-gnome-support.

Once that is done, then install mozilla-firefox and  mozilla-firefox-gnome-support.

Just "remove" should be fine (that's all I did).  If you do a "complete removal" you'll loose all your settings and probably your bookmarks, extensions and themes as well (I think).  Anyway, it doesn't seem that "complete removal" is necessary.

---

### Post by bob_c_b on 2005-09-23
[QUOTE=debaser13]Here is the thread that is addressing this problem...but, I tried the suggestions and they did not work for me...not sure what I am doing wrong.

[http://www.ubuntuforums.org/showthread.php?p=367285#post367285](http://www.ubuntuforums.org/showthread.php?p=367285#post367285)[/QUOTE]

This worked for me, but I had killed firefox-bin already. Of course the good part is it finally got me to install Epiphany again, more browsers=good.

---

### Post by anunn2001 on 2005-09-23
Sorry to hear about so many problems. The install went OK for me.

---

### Post by Benchrest on 2005-09-23
I have installed 1.0.7 with a few hitches. First I tried upgrading with both SUDO and SYNAPTIC.Both failed. Firefox would no longer start even with restarting the system. I then removed the upgrade 1.0.7 with SYNOPTIC and was surprised it removed 1.0.6 also. I then found reinstalling 1.0.6 was no longer an option which meant I was dead in the water without a browser. So I tried installing 1.0.7 with SYNOPTIC and the install went without errors. But Firefox would still not start. I shut down the system and restarted and now Firefox will start. I'm using it now.  \\:D/

---

### Post by antimatter on 2005-09-23
well heres what fixed it for me:
apt-get remove mozilla-firefox

that will also uninstall ubuntu-desktop and yelp for some reason

apt-get install mozilla-firefox
apt-get install ubuntu-desktop

and it all started working again....

---

### Post by Irony on 2005-09-24
Thanks everyone.

I did everything via synaptic;

*Removed (Removal rather than Complete Removal) mozilla-firefox, this informs me that it will remove gnome-support, yelp and ubuntu-desktop.*

Then re-installed each item individually;

[I]mozilla-firefox
mozilla-firefox-gnome-support
yelp
ubuntu-desktop[/I]

It all works and I now have Firefox 1.0.7

---

### Post by jahLux on 2005-09-24
Thanks much, I'd gone ahead and added Opera as well as Epiphany-browser, They're ok, but no match for Firefox!

---

### Post by imagine on 2005-09-24
[QUOTE=][/QUOTE]
 Installing both mozilla-firefox and mozilla-firefox-gnome-support with sudo dpkg --install --force-overwrite was enough for me. I did *not* have to uninstall firefox nor reboot Ubuntu.

When Synaptic stops the update with the error message "E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite [...]" close it, open a terminal and type:
```
cd /var/cache/apt/archives
sudo dpkg --install --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
sudo dpkg --install --force-overwrite mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
sudo apt-get install
killall firefox-bin
``` (stolen from sk545)
Start Firefox, check Help -> About. It should say 1.07.


Also a second Firefox-icon was added to the applicationsmenu. Not a big issue, but still it shows that this update to 1.07 wasn't tested very well.



Edit: Is there an administrator which can **sticky** this for some days? As I'm aware this bug affects everybody who tries to install the Firefox 1.07 update from the Ubuntu-security server and it renders Firefox unusable. And the browser is one the most important applications... I guess some users can't even access the forum anymore to find a solution.

---

### Post by Hairy_Palms on 2005-09-24
imo opera is the god of browsers, if theyd just open source it so that mplayer plugin etc would work they would truly be untouchable as it i s i use firefox for streaming opera for everything else.

---

### Post by logicaloperator on 2005-09-27
Whatever was broken must be fixed now because I just used sudo apt-get upgrade and firefox was upgraded to 1.0.7 - no problems whatsoever   :)

---

### Post by Duncan_Idaho on 2005-09-27
I had that problem, to fix it I uninstalled firefox and mozilla-firefox pakages with theri respective gnome-support, reboot, and then installed the mozilla-firefox
I did this 'cause reinstalling it didn't work :???:

---

### Post by GhostDawg on 2005-09-27
The other day I added some extensions to it, about three of them, and every since, it won't start.

I'm using Ubuntu Hoary and when I type firefox in cli, I get this message:

Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.


I see it listed when I type 'ps ax'

15501 pts/3    Sl    0:00 /usr/lib/mozilla-firefox/firefox-bin -a firefox

But it's not opening the browser. If I run it with sudo it will run. I've also tried changing permissions on my .mozilla/firefox folder without luck.

I ended up renaming my ~/.mozilla folder and reinstalled FF 1.0.7 and it works okay, but I can't add extensions or themes to it.

Any ideas/suggestions for adding them?

Thnx.

---

### Post by gushy on 2005-09-27
[QUOTE=seaeric]This seemed to work for me.

sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install[/QUOTE]

Worked for me, thanks. :D

---

### Post by Mustard on 2005-09-27
[QUOTE=GhostDawg]The other day I added some extensions to it, about three of them, and every since, it won't start.

I'm using Ubuntu Hoary and when I type firefox in cli, I get this message:

Extension System Warning: Failed to set up default extensions files probably because you do not have write privileges to this location. While you can run Firefox like this, it is recommended that you run it at least once with privileges that allow it to generate these initial files to improve start performance. Running from a disk image on MacOS X is not recommended.


I see it listed when I type 'ps ax'

15501 pts/3    Sl    0:00 /usr/lib/mozilla-firefox/firefox-bin -a firefox

But it's not opening the browser. If I run it with sudo it will run. I've also tried changing permissions on my .mozilla/firefox folder without luck.

I ended up renaming my ~/.mozilla folder and reinstalled FF 1.0.7 and it works okay, but I can't add extensions or themes to it.

Any ideas/suggestions for adding them?

Thnx.[/QUOTE]

What about the permissions for your chrome folder? That is where all the extensions and stuff go I think.  I have no idea whether its relevant.  I am more curious than anything else.

---

### Post by ceridwyn on 2005-09-28
[QUOTE=seaeric]This seemed to work for me.
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install[/QUOTE]
i also had to install a new browser so i could get to the forums and figure out how to fix the broken "auto update" of firefox. 
Many  many Thankyous  to all who posted helps! my Firefox is happy and all is great now!\\\\:D/

---

### Post by mchatel on 2005-09-29
I can also confirm, that I was able to install Firefox 1.0.7 just fine, using Synaptic Package Manager, with no problems.  I didn't do any of the extra steps mentioned above.  I simply got the "red" update notification, and told it to install new packages (including Firefox), and it worked right away.

If there was a problem, hopefully it was fixed.  Or maybe I was just lucky.

---

