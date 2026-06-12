---
title: "ubuntu/gnome as userfriendly as possible"
date: 2005-06-15
forum: Desktop Environments
---

### Post by phen on 2005-06-15
hello all!

i am planning to load ubuntu on my mother's computer. She is what i would call "worst case computer user". I am planning to:
- remove the two standart panels and replace them by a single one with as little confusing information as possible
- remove desktop switching (she would be lost....) 
- biiig desktop starters for her three programs: email, browser and ooffice writer.
- modify the gnome menu to show only the most needed things.

after tweaking, linux would have following advantages besides gnome's ease of use:

-system would be safe from unwanted configuration by mom
-system would be safe from 99% of internet adware,spyware,virusses etc


now i have a question: is there a way to boot into X without user login? i know, thats kind of unsecure and therefore not really what linux is for. but i really believe, that gnome is able to be much more userfriendly than windows with a little tweaking. And autologin would be important imho. 



other ideas are welcome, too!


have a nice day :-)
cheers, kai

---

### Post by Knome_fan on 2005-06-15
AFAIK you can configure gdm to autologin a user. Just open gdmsetup and it should be on the first tab.

---

### Post by lukasmaci on 2005-06-15
[http://ubuntuguide.org/#automaticlogingnome](http://ubuntuguide.org/#automaticlogingnome) :-)

---

### Post by desdinova on 2005-06-15
Install Splashy as well - so she doesn't have to see the text mode boot up which could cause concern.

---

### Post by phen on 2005-06-15
thanks for your answers! a splashscreen is a good idea. something looking friendly :-)

---

### Post by Knome_fan on 2005-06-15
Just an idea, but you should probably also take a look at using abiword instead of openoffice, as it is simpler imho.

Also evolution might be overkill and something like balsa (though I haven't tried it in a long time), might be better suited.

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=Knome_fan]Just an idea, but you should probably also take a look at using abiword instead of openoffice, as it is simpler imho.

Also evolution might be overkill and something like balsa (though I haven't tried it in a long time), might be better suited.[/QUOTE]
 Evolution may be an overkill, but I consider its interface to simple enough. Last time I tried, balsa had problems of its own...

---

### Post by g14 on 2005-06-15
turn off spatial mode in nautilus: Open up gconf-editor and browse to /apps/nautilus/preferences/ and check always_use_browser

Under the different keys under /apps/nautilus, you should check the ones to put the computer, home directory, and trash icons on the desktop. Then you should rename them to more windows friendly names like home to my documents.

Change it from one panel to 2 panels and then lock all of the icons so she doesn't mess it up and not understand how to fix it. Here is an example:
[Screenshot of a linux desktop for my parents](http://www.digitalprognosis.com/pics/Screenshot.png) 

That shows ubuntu linux with the redhat bluecurve icon theme with a clearlooks window and metacity theme.

Here is additional software I installed for them:
Inkscape - vector graphics for creating flyers and banners
evince - the best linux pdf / postscript reader and is much faster than adobe acrobat reader for linux
samba - so that you can share files with windows hosts
firestarter - for easy firewall configuration
netapplet - a gnome panel applet from suse that allows easy switching between different networks.

Adblock, foxytunes, cute menu, extensions for firefox. You can import this list into adblock for some pretty nice default adblocking. This is my personal list:
[http://www.digitalprognosis.com/opensource/adblock.txt](http://www.digitalprognosis.com/opensource/adblock.txt)

OPTIMIZE, OPTIMIZE, OPTIMIZE!!!
[http://www.linuxjournal.com/article/8308](http://www.linuxjournal.com/article/8308)
[http://www.linuxjournal.com/article/8317](http://www.linuxjournal.com/article/8317)
[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)
[http://forevergeek.com/open_source/make_firefox_faster.php](http://forevergeek.com/open_source/make_firefox_faster.php)
[http://www.newsforge.com/article.pl?sid=03/10/07/1943256](http://www.newsforge.com/article.pl?sid=03/10/07/1943256)
[http://desktoplinux.com/news/NS8224596155.html](http://desktoplinux.com/news/NS8224596155.html)

Edit /etc/sudoers using sudo visudo and change the very last ALL in the file to:
NOPASSWD:ALL

You can start firestarter with gnome-session-daemon by adding sudo /usr/bin/firestarter to your session by going to System -> Preferences -> Session

I am currently on a windows computer typing this up so some of it might be incorrect but this + some basic linux hardening will make a very usable linux desktop. And yes, the screenshot IS ubuntu

---

### Post by desdinova on 2005-06-15
The problem I see is removing the password for sudo goes against hardening - I find the best way is then to ditch firestarter and setup shorewall - which starts as a service and doesn't need root permissions to start.

---

### Post by g14 on 2005-06-16
/usr/bin/firestarter is simply a configuration interface and only required if you like to see what processes are acessing the network, what events and being blocked, and need to change your firewall policy. So you know, firestarter starts as a daemon on system boot similar to shorewall. Correct me if I'm wrong, but doesn't shorewall use webmin or a webserver for configuration? This is unnecessary as I see it.

Also, adding the NOPASSWD option to sudo accomplishes a few things while only sacrificing local security. If he wants to enable autologin, local security is very obviously not a problem. This will allow the user to install / remove software, update the system, and configure samba sharing without needing to enter a password. Different configurations are appropriate for different situations. A home desktop user shouldn't have to worry about much of anything and requiring them to enter a password for everything will force the password to be less secure. I guess you could say that allowing sudo with no password will increase security if remote access (ssh, nfs, telnet) means were enabled.

---

### Post by phen on 2005-06-21
Hello!

thanks again for your answers. i realized some of your suggestions. others will follow. for now i made up a really clean and simple looking desktop. I changed all program names (e.g. "Firefox" to "Internetbrowser", K3B to "Burn CD"), The Adblocker will follow, a splashscreen will follow.

I changed from Evolution to thunderbird, mainly because my father is using it. Balsa was looking interesting, too. we will see. G14, some of your tips i will use for myself :-)

anyway, thanks again to all!

---

### Post by tristan on 2005-06-21
I made an extremely simple and easy gnome desktop for guest users on my computer. 

* Non scary splashy boot process
* Single gnome panel on the bottom
* Panel launcher icons for dialin (gnome ppp), firefox, Beep Music Player, openoffice2 and logout. All with user friendly names.
* The guest home directory folder icon on the desktop
* No gnome menus, pager, update icons or anything else confusing
* No configuration options available

The user logs in, clicks on the icons to get online (which is what 99% of people want to do) and clicks on a button to logout.

If they want to achieve anything more they can come and get me!

I always figure the less options you give people, the less trouble they can get themselves into! I've had no complaints form anyone using my computer. Sure, it doesn't look like windows but it's very easy to figure out what to do.

---

### Post by Alexander Kirillov on 2005-06-22
[QUOTE=phen]Hello!

thanks again for your answers. i realized some of your suggestions. others will follow. for now i made up a really clean and simple looking desktop. I changed all program names (e.g. "Firefox" to "Internetbrowser", K3B to "Burn CD"), The Adblocker will follow, a splashscreen will follow.

I changed from Evolution to thunderbird, mainly because my father is using it. Balsa was looking interesting, too. we will see. G14, some of your tips i will use for myself :-)

anyway, thanks again to all![/QUOTE]
 I think this thread would make a very nice howto. Are you willing to write it up and post in howtos forum?

---

### Post by phen on 2005-06-22
I am willing to! but imho it is not yet enough for a howto document. I just removed some gnome-panel applets and used ubuntuguide for the rest. As soon as the adblocking splashscreen etc comes, it might be worth to write an article. What do you think?

Kai

---

### Post by Alexander Kirillov on 2005-06-22
[QUOTE=phen]I am willing to! but imho it is not yet enough for a howto document. I just removed some gnome-panel applets and used ubuntuguide for the rest. As soon as the adblocking splashscreen etc comes, it might be worth to write an article. What do you think?

Kai[/QUOTE]
 Well, you can start a thread on the forum - other sill add to it. This is the beauty of the forum - even howtos can be created step-by-step, in little increments, rather than all at once. 

But indeed, if you paln on imeplemnting more of the suggestions here (splashscreen, etc) it may make sense to wait until this is done.

---

### Post by kiwibird on 2005-06-22
Wow, guess I'm not alone in trying to make a user-friendly guest/parent login. I guess it's pretty obvious though that these Simple-projects are going to become more and more popular as Linux spreads to a wider audience. 

I've got a setup that is pretty simple and clean-looking, got 5 icons for the most used folders and icons for the net and all, but I need to fix the menus (and the few menu-editor programs I found just made matters worse, so I guess that means doing it by hand..agh). [Here](http://folk.uio.no/kevinu/Skjermdump-guest.png)'s a screenshot. 

I guess I should make program icons bigger, but I need to somehow turn off the emblems on those folder icons - anyone know of a quick way to do that? 

And is there a way to have the guest user be totally password-free? (As in, they type/select "guest" at the happy friendly login screen and enter and they're in, while other users need to enter username and password.)

I've also wondered how understandable that life-buoy icon really is... I mean, when I first saw that, I thought it must be some weird internet-software, I didn't think of "Help".

---

### Post by phen on 2005-06-23
try smeg! i like it. the installation is possible via synaptic. ubuntuguide describes it, too.

---

