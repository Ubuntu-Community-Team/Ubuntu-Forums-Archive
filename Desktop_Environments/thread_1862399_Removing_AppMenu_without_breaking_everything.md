---
title: "Removing AppMenu without breaking everything"
date: 2011-10-16
forum: Desktop Environments
---

### Post by BazookaAce on 2011-10-16
Hi, i really hate the app menu in 11.10 and since i'm using Gnome-Shell i want to remove it. But can i saftely remove it without breaking anything? And can i still use desktop icons if i remove it, since if i activate desktop icons now, i'll get the appmenu under "Activities".

Thanks in advance.

Edit: According to webupd8 it's easy to remove it:

[http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)

But according to AskUbuntu it's not possible:

"there is no known fix other than to disable Nautilus drawing the desktop:"

[http://askubuntu.com/questions/65705/how-to-remove-global-menu-from-gnome-shell](http://askubuntu.com/questions/65705/how-to-remove-global-menu-from-gnome-shell)

What do you guys think?

Edit 2: This method didn't work

sudo su
echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy

I can remove appmenu, but then it will remove ubuntu-desktop, and that's the last thing i want.

---

### Post by Pithikos on 2011-10-16
I disabled it and didn't have any problems. Not problems due to that, but still struggling with other crap. In the worst case you can just reinstall it so no worries ;)

---

### Post by mc4man on 2011-10-16
You can remove all the packages shown in the screen with no issue, though likely you could leave indicator-appmenu if you wish

ubuntu-desktop is a meta package, doesn't matter if you remove
Only value down the road is if you choose to upgrade from 11.10 to 12.04, then you should re-install before doing so

Edit: just to note - When I use Gs the appmenu isn't a factor - could be related to the theme you are using & or trans on top panel

---

### Post by BazookaAce on 2011-10-16
I can't see the appmenu now, but when i enable desktop icons from the gnome tweak tool, it shows up under the statusbar. But i'll try to remove it and hope for the best. I'm sure it'll work fine, but with my luck..... :p

I'll report back.

---

### Post by BazookaAce on 2011-10-16
I'm back. It didn't work...

Here's some screenshots. One with desktop icons enabled, and one when it's disabled.

Desktop icons disabled: (statusbar is transparent without the menu)

[IMG]http://img810.imageshack.us/img810/9291/noappmenu.png[/IMG]

Desktop icons enabled: (another statusbar behind GS statusbar with menu)

[IMG]http://img834.imageshack.us/img834/4167/withappmenu.png[/IMG]

---

### Post by mixim on 2011-10-16
> **mc4man said:**
> You can remove all the packages shown in the screen with no issue, though likely you could leave indicator-appmenu if you wish
panel

Didn't work for me =/...

Still a stupid appmenu behind the gnome-shell menu.

Solutions??

---

### Post by mc4man on 2011-10-16
> **mixim said:**
> Didn't work for me =/...

Still a stupid appmenu behind the gnome-shell menu.

Solutions??
Both of your issues are the trans panel being used - search it out

---

### Post by BazookaAce on 2011-10-16
But... it *must* be possible to remove the whole f@cking bar! Come on geniuses! Do i have to call Mark Shuttleworth myself?

---

### Post by mixim on 2011-10-16
> **mc4man said:**
> Both of your issues are the trans panel being used - search it out

What is the trans panel?

Do u mean that nautilus is handling the desktop? Because i have disabled that now, and it works.. but yea would be nice to have my icons on the desktop though.

---

### Post by BazookaAce on 2011-10-16
Yeah, that's the whole point of this thread :p

---

### Post by mc4man on 2011-10-17
@ BazookaAce 	
I haven't spent much time in Gs - with the vanilla default Gs that menu doesn't show up (obviously because the panel is opaque
If you can tell me what to do to get the panel you show in screen I'd be interested in seeing if there is a workaround

---

### Post by BazookaAce on 2011-10-17
The GS theme i'm using is called "Faience" and can be downloaded here: 

[http://tiheum.deviantart.com/art/Gnome-Shell-Faience-255097456](http://tiheum.deviantart.com/art/Gnome-Shell-Faience-255097456)

---

### Post by mc4man on 2011-10-17
At least here with the above linked theme got rid of that menu by removing the indicator-application package in addition to the ones mentioned before - from synaptic
> Completely removed the following packages:
appmenu-gtk
appmenu-gtk3
appmenu-qt
indicator-appmenu
indicator-application
If you aren't going to use unity then don't see much use for them, if there is you always can re-install

---

### Post by BazookaAce on 2011-10-17
**Oh**
**my**
**god..**

I can't win. It's *still* there! I even rebooted! I give up! I think i might install Win95 just so i don't have to live in the same house as "it"!

[IMG]http://globalcitizenblog.com/wp-content/uploads/globalcitizen/crazyface.jpg[/IMG]

---

### Post by mc4man on 2011-10-17
while I'm sure you removed all of those packages, (also don't have the firefox & thunderbird ones installed here either), did you do a log out or even a restart?
Edit: see you rebooted, got me, goes away here..?

I did this on a temp user I set, don't think that's a factor, could check on my 'real' user (unity

re-edit; - same thing on my real user login - no menu with the trans panel  
previously I had also removed these, but don't think a factor
gir1.2-panelapplet-4.0
gnome-applets-data
gnome-panel-data
libpanel-applet-4-0
python-gmenu

---

### Post by BazookaAce on 2011-10-17
Hmmm, i'll take a look at it tomorrow. Thanks for sticking around :)

---

### Post by BazookaAce on 2011-10-18
Ok, i'm back. I removed these: 

gir1.2-panelapplet-4.0
gnome-applets-data
gnome-panel-data
libpanel-applet-4-0
python-gmenu

But no luck! I've even rebooted, and nothing. It's still there. 

Well, i think it's time to face the fact that i'm defeated by the all mighty Ubuntu. Thank you all for the help!

---

### Post by mc4man on 2011-10-18
Well - if you're headed to a new of  <something>, then maybe try 11.10 1 more time (if inclined

If so - 
before doing anything after the install remove those packages, then go about installing Gs, ect.
good luck in any event...

Edit - 
maybe try this on current install - open up your home folder > .config/dconf & delete the user file inside
Note that this will remove all your settings changed from default

do a log out/in & reset stuff

---

### Post by BazookaAce on 2011-10-18
Oh, i'm not going anywhere :p I just have to face the fact that i "can't" use desktop icons, but i've gotten used to it now so no biggie :)

---

### Post by mc4man on 2011-10-18
> **BazookaAce said:**
> Oh, i'm not going anywhere :p I just have to face the fact that i "can't" use desktop icons, but i've gotten used to it now so no biggie :)
Well that's good, you may end up without the shadow menu at some point because of .. who knows

I think curiosity would cause me  to create a temp new user, log into & change the theme, if for nothing else to see if it was something in my local settings/files/whatnot.

---

### Post by djchandler on 2011-11-01
This may not be exactly what you want, but I've managed to almost get (I think) what you seem to be after. I can't get gnome shell to work correctly at all, so I'm running Unity with the AppMenu disabled and have enabled desktop icons using gnome-tweak. To get this to this point, I set the theme to all the default (Adwaita, gnome icons) settings.

I'm a GIMP user, so I too am uncomfortable with the AppMenu setup in Unity.

But I believe that if you are truly dedicated to using Gnome-Shell, then perhaps you should consider using Debian or some other distribution.

Canonical does not seem to be interested in supporting any desktop other than Unity. They only seem to care about getting new users. Everybody else who's been part of the Ubuntu community for the past several years that doesn't want to use Unity may need to use something else.

I've been using Ubuntu since the release of 6.06. I'm looking at Debian and Fedora (again). I started out with Red Hat about 10 years ago. Perhaps that's what I'll go back to, at least the free (Fedora) distribution.

Alternatively, I would also give a hard look at using a distribution that is committed to and fully supports KDE, like PC-Linux.

---

### Post by BazookaAce on 2011-11-01
Thanks, but "i" fixed it by installing an update (not sure which) from the "proposed repo" (you can enable it by going to the source manager), so after the update it works as it should! :)

---

### Post by BigCityCat on 2011-11-01
I don't think I can be much help here but I had removed all of those packages and I had nautilus controlling the desktop and the damn thing was gone. Then I made the mistake of installing the app from webupd8 that changes LightDm background image and the damn panel reappeared and would not go away. Luckily I screwed something else up and had to reinstall. I did everything the same except install the program that changes the login screen and everything is good.

---

