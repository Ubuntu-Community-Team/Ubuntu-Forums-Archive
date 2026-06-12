---
title: "[HOWTO] Fix common Gnome 3 install issues in 11.04"
date: 2011-04-28
forum: Desktop Environments
---

### Post by slooksterpsv on 2011-04-28
**[COLOR="Red"]NEW!!![/COLOR] This guide isn't going to be updated anymore, as there is gNatty, and I've switched to Lubuntu. The reason? GDM kept crashing and issues kept coming up that reduced the overall functionality of my own computer.**

The PPA seems like it changes slightly to where things may break, if something does break, try to run: 
sudo apt-get install gnome-shell gnome-session
again, as it looks like a lot of the time gnome-shell and gnome-session aren't being installed.

**[Color="Red"]FIX for issue opening certain applications (like games)[/color]**

Do the following in terminal:

```

echo "PATH=\"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\"" | tee -a ~/.profile

```

Logout and log back in and that should fix the issue. NOTE: You have to do this for each user that logs into the system if they can't access games or that.

**FIX for .ICEauthority issue!**
There's another method besides this one, and it involves just installing the following:
```

sudo apt-get install gnome-session

```
This works!

**Installing Gnome 3.0**
Let's start by installing Gnome 3.0, NOTE THIS WILL REMOVE UNITY AND MAKE IT TO WHERE YOU CANNOT INSTALL UNITY!!! The only way to get Unity back is to remove the PPA and run a dist-upgrade on the system. (See further down)

Open a terminal and type in the following commands (do this by going to your applications area and searching for terminal):

```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell gnome-session
sudo apt-get -f install
sudo apt-get install gnome-shell
sudo apt-get install gnome-session

```

**NEW - The above has changed as issues occurred and didn't install gnome-shell**

Before we reboot, we do need to do a few more things to make sure it's running correctly, keep reading.

**Issues with strange themes**
You may have a strange theme and want the default Gnome 3 theme, here's what you need to do, now where we didn't reboot above (or if you did and are at the weird theme'ed gnome 3, open a terminal and follow along), in the terminal type in:
```

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
sudo apt-get install -f

```

Some users have reported needing to run sudo apt-get install -f due to failure to install some packages. If that doesn't work, go ahead and post and we'll see if we can help you out.

Now let's restart. For those of you having the common graphical glitch, this issue is caused by the gnome-accessibility-themes and by not having the gnome standard themes. Once you reboot you should be at the fresh interface of Gnome 3.

**Needs some tweaking! Window buttons, different themes, etc.**
Unfortunately, there's not a lot you can change initially, but we'll need to install another tool to help tweak some items, open a terminal again and install the following:
```

sudo apt-get install gnome-tweak-tool

```

Open the gnome-tweak-tool by pressing ALT+F2 and typing in: 
```

gnome-tweak-tool

```
then press Enter. Here we can change a few basic settings. Go under interface to change the Gtk+ Theme. If you find you don't like something, just change it back.

To apply the changes, either log out and log back in or press ALT+F2 and type in just r and press Enter, which will refresh the Window Manager.

If you want your regular buttons on the right hand side for the windows do the following, press ALT+F2 and type in: 
```

gconf-editor

```
Press Enter and navigate to:
```

/desktop/gnome/shell/windows

```
Change the button_layout to:
```

:minimize,maximize,close

```

After you do that, you do need to press ALT+F2, type r, press enter, and it'll fix that.

**Flickering, GAHHHHHHHH**
If you have flickering, tearing, etc. of the windows and HAVE installed the graphics drivers, you need to remove them. Unfortunately with some chipsets you will experience tearing with the graphic drivers - ATI for example.

**Other stuff?**
I'll update this guide as much as I can as I know there's a lot of questions about Gnome 3 and how to configure this or that or change settings. Try stuff out, experiment with the greatest DE in the world!

**How do I get Evolution 3.0**
So as a lot of you know, the Gnome 3.0 PPA above DOES NOT include Evolution 3.0, well here's a simple way of getting it from another PPA. So open the terminal again and type in the following:

```

sudo apt-add-repository ppa:danilo/evolution
sudo apt-get update
sudo apt-get dist-upgrade

```

It is a SLOW PPA so give it time. When that's done, just restart Evolution for the 3.0 goodness. The menu's are a lot better than 2.32, and fitted for smaller screen resolutions.

**Tips & Tricks! I want to have fun!**
Ok let's get out some tips and tricks, have 2 separate windows open on one application, like 2 separate firefox windows (not tabs) and press ALT+TAB and while holding down ALT press Tab until you get to the firefox icon and press the down arrow key. Voila! You see all the separate windows in Live Previews.

Press the Super key (windows logo key) then start typing in the name of an application. Voila! You don't need the mouse to get to your apps.

What else... hmmm... click on the circle with the little person in it, there's a way to find some accessibility settings.

Click at the top where it says todays date and time, it pops down a cool calendar that integrates with Evolution 3.0

Click on the application name in the top left, it has a quit menu so if you can't figure out how to quit an app or close a window, you can do it that way.

If you get stuck in a window that has no close button, try pressing the escape key.

When someone sends you an im, you can click on it at the bottom middle and reply if using Empathy.

If you press the activities button and go to the bottom right-hand side you should see a list of your current tray icons such as empathy chats. In the activities menu if you get an IM you can reply to it there.

**I want my Unity back!**

On page 9, [M4570D0N] stated that the following should work.

To remove Gnome 3 and reinstall Unity, do the following in a terminal:

```

sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade

```

I have not tested this personally, but it sounds like it works. So let me know if it doesn't and I'll remove this section.

If you have any more let me know. I know I haven't added who gave what fixes for what, but I'll try to update that here. If you added something and don't see your alias, PM me.

---

### Post by ctaborda on 2011-04-28
Man this is awesome!! Thanks!! You fixed all the issues I was having.

---

### Post by Visceral Monkey on 2011-04-28
Something else to consider. Gnome 3 in Ubuntu isn't feature complete, it's missing a lot of base Gnome 3 stuff that you'll see in SuSE and Fedora. Nothing *huge* but there is stuff missing, so it might seem "bare" in places. I know this is why I reluctantly moved over to Fedora for the time being. A lot of the fixes listed here are for problems unique to the unfinished Gnome 3 PPA for Ubuntu, not Gnome 3 itself. Great thread though.

---

### Post by morgue on 2011-04-29
Great post.

---

### Post by lucasart on 2011-04-29
> **morgue said:**
> Great post.

Yeah, this one should be made a sticky post !
I don't know how posts are made sticky though. Perhaps it has to be communicated to an admin on this forum.

---

### Post by slooksterpsv on 2011-04-29
> **lucasart said:**
> Yeah, this one should be made a sticky post !
I don't know how posts are made sticky though. Perhaps it has to be communicated to an admin on this forum.

Probably, I think if there's lots of questions on the subject (same questions) and you let an admin know they stick it? I dunno, need an admin to direct me on info on how to sticky items ;) I must've missed it when going through the rules.

---

### Post by pony-tail on 2011-04-29
Most excellent - Unity gone ! - For good on my machines .

---

### Post by neopium on 2011-04-29
> **Visceral Monkey said:**
> Something else to consider. Gnome 3 in Ubuntu isn't feature complete, it's missing a lot of base Gnome 3 stuff that you'll see in SuSE and Fedora. Nothing *huge* but there is stuff missing, so it might seem "bare" in places. I know this is why I reluctantly moved over to Fedora for the time being. A lot of the fixes listed here are for problems unique to the unfinished Gnome 3 PPA for Ubuntu, not Gnome 3 itself. Great thread though.

I have one question related to these missing functions. How in Gnome 3 can I access the old Ubuntu System Preferences and Adminisatrtion menus? When upgrading to Natty, it broke my keyboard layout and I can't find how to access the keyboard layout GUI settings.

---

### Post by lisati on 2011-04-29
Another thing to consider: HOWTOs usually go in [Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100"). (Don't forget to read the [sticky]("http://ubuntuforums.org/showthread.php?t=677396"))

---

### Post by cbowman57 on 2011-04-29
> **neopium said:**
> I have one question related to these missing functions. How in Gnome 3 can I access the old Ubuntu System Preferences and Adminisatrtion menus? When upgrading to Natty, it broke my keyboard layout and I can't find how to access the keyboard layout GUI settings.

A picture is worth 1,000 words.

---

### Post by neopium on 2011-04-29
> **cbowman57 said:**
> A picture is worth 1,000 words.

Thanks Chuck, but if you go in the keyboard item, there is nothing to configure the layout (see the screen capture, in French, sorry about that).

I finally found my way with the command line, but its really not as easy as the user interface.

Another question regarding the tutorial. I followed it, but it seems that Evolution has not been updated. It is still at version 2.32 and not 3 according to the About dialog... And it is sometimes very very slow... How do I upgrade it?

---

### Post by slooksterpsv on 2011-04-29
You'd have to install it manually it looks like the PPA doesn't have Evolution 3.0, I thought it was.

Also, lisati (I think that's the admins name) thank you for telling me about the Tutorials and Tips section, I completely forgot about it.

---

### Post by neopium on 2011-04-29
> **slooksterpsv said:**
> You'd have to install it manually it looks like the PPA doesn't have Evolution 3.0, I thought it was.

Ouch...
I downloaded the source code, but the ./configure command failed because it did not find some Gnome3 related libraries that are only available in version 2.32 and not 3...

---

### Post by cbowman57 on 2011-04-29
> **neopium said:**
> Thanks Chuck, but if you go in the keyboard item, there is nothing to configure the layout (see the screen capture, in French, sorry about that).

I finally found my way with the command line, but its really not as easy as the user interface.


I'm sorry I don't know French.  Glad you got it figured out with the command line, I read layout but for some reason thought you blew up a couple shortcuts.  My bad.

Don't have anything to offer on the Evolution problem since I usually uninstall it. :(

---

### Post by neopium on 2011-04-29
> **cbowman57 said:**
> Don't have anything to offer on the Evolution problem since I usually uninstall it. :(

What email client do you use? I was very disapointed by Thunderbird and switched to Evolution, but now, with Gnome 3, its memory footprint expodes in a few seconds (I just deleted two messages and evolution took 1.6 Gb of RAM)...

I guess Ubuntu is not ready for Gnome 3... Maybe I will have to switch to Fedora...

---

### Post by neopium on 2011-04-29
> **cbowman57 said:**
> I'm sorry I don't know French.  Glad you got it figured out with the command line, I read layout but for some reason thought you blew up a couple shortcuts.  My bad.

The screenshot has only two tabs saying "General settings" and "shortcuts", no layout there.

---

### Post by cbowman57 on 2011-04-29
> **neopium said:**
> What email client do you use? I was very disapointed by Thunderbird and switched to Evolution, but now, with Gnome 3, its memory footprint expodes in a few seconds (I just deleted two messages and evolution took 1.6 Gb of RAM)...

I guess Ubuntu is not ready for Gnome 3... Maybe I will have to switch to Fedora...

This may sound funny but I've grown fond of using Gmail instead of dedicated email software.

Not sure what Fedora offers that gnome 3 on Ubuntu doesn't.  I'm starting to archive some notes on what I've been doing to mine, check out this link.

[http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?uc=1]("http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?uc=1")

---

### Post by neopium on 2011-04-29
> **cbowman57 said:**
> This may sound funny but I've grown fond of using Gmail instead of dedicated email software.

Not sure what Fedora offers that gnome 3 on Ubuntu doesn't.  I'm starting to archive some notes on what I've been doing to mine, check out this link.

[https://www.facebook.com/note.php?note_id=213440325351139]("https://www.facebook.com/note.php?note_id=213440325351139")

I can't read your link, I'm not on facebook :D

Fedora will support Gnome officially in the next release due by th end of the month, while Ubuntu will not support it before october...

---

### Post by cbowman57 on 2011-04-29
Sorry about that, I saved it to a .pdf and changed the link, hopefully it is accessible to everyone.

---

### Post by neopium on 2011-04-29
> **cbowman57 said:**
> Sorry about that, I saved it to a .pdf and changed the link, hopefully it is accessible to everyone.

Thanks

---

### Post by Visceral Monkey on 2011-04-29
> **neopium said:**
> I can't read your link, I'm not on facebook :D

Fedora will support Gnome officially in the next release due by th end of the month, while Ubuntu will not support it before october...

Fedora fully supports Gnome 3 in the current Fedora 15 beta. It's 100% working and feature complete. I switched to Fedora when I saw the Ubuntu Gnome 3 ppa falling further and further behind on updates and functionality. It's a little different, but Fedora does have some things going for it. The biggest complaint I had was the default fonts which SUCK. Installed the better font hinter and then the Ubuntu fonts and it's good to go. Gnome 3 is awesome, after trying both it and Unity there really is no comparison.

As a side note, SuSE also has full Gnome 3 support and software installation is even easier on SuSE than Fedora. Really hard to choose between the two.

If you're more interested in Gnome 3 than the Distro it's running on, Ubuntu really isn't where you need to be right now, sadly. There is a sizable number of people switching to Fedora right now from Ubuntu which is the main reason I choose Fedora over SuSE.

---

### Post by cbowman57 on 2011-04-29
Visceral Monkey, I have considered that, and I try out different distros all the time but I've just become too accustomed to Ubuntu.

Might be old age creeping up on me. :)

However, I might just have to install Fedora to compare it to what I'm using now.  I know that most of the info I've gleaned on using & tweaking gnome 3 has come from Fedora users.  Thanks.

---

### Post by Durden on 2011-04-29
My biggest complaint with Fedora is that it's rpm based, and thus slow to install. However, once things are installed and functional you won't have to deal with it often. The fedora community is a bit smaller too, harder to get questions answered.

Currently the Fedora 15 beta will not install on my machine so I haven't had the chance to switch, I may do so though when I can.

---

### Post by slooksterpsv on 2011-04-29
> **Durden said:**
> My biggest complaint with Fedora is that it's rpm based, and thus slow to install. However, once things are installed and functional you won't have to deal with it often. The fedora community is a bit smaller too, harder to get questions answered.

Currently the Fedora 15 beta will not install on my machine so I haven't had the chance to switch, I may do so though when I can.

Like installing Apache, could not figure out how to do that, a few google searches turned out I had to install httpd, ok I know that's a related service but the overall product is apache, not httpd, so label it as so, haha.

I'll see if I can get more info on for getting Evolution 3 up and going.

EDIT:

Trying this PPA, if it works I'll include instructions on the first page:
[https://launchpad.net/~danilo/+archive/evolution](https://launchpad.net/~danilo/+archive/evolution)
So that'd be: ppa:daniolo/evolution

---

### Post by slooksterpsv on 2011-04-29
Evolution 3.0 added on how to install

---

### Post by grappler on 2011-04-29
Running Natty I followed the instructions to the letter and got

$ gksudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


As to email clients - try Zimbra - have to compile from source but works really well. 

[http://www.zimbra.com/downloads/zd-downloads.html](http://www.zimbra.com/downloads/zd-downloads.html)

---

### Post by Blakefreak on 2011-04-30
If ever there was a version of a main distrobution that would forever kill Linux as an alternative to windows... THIS WOULD BE IT.

I have adored Ubuntu for many years now... Until now.

The worst version of Ubuntu to date... Can't wait to see how they make Linux less palatible in 11.10.

---

### Post by lvalen18 on 2011-04-30
If I use this method would it be like regularly installing the ppa for gnome3 etc? If that made sense

I used Ubuntu Tweak and added the gnome3 ppa and installed it... At the login screen it looks gnome3 ish with the black bar at top but the themes is the one that gnome falls back on when there isn't another installed or crashes... Then when i attempt to login it gives me a gnome shell error that it failed to load/start the same with Ubuntu Classic... Only way to get it to login is to revert back to gnome2 with ppa-purge.. 

Same thing happen running the beta... Is there a hardware requirement that im missing? or just software bug

---Forget it... My crackpot laptop doesn't support OpenGL 1.4+ only has Direct3D 8/Open GL 1.3 ... Time for a new laptop no wounder---

---

### Post by neopium on 2011-04-30
> **slooksterpsv said:**
> Evolution 3.0 added on how to install

Thanks, it works like a charm. And I got rid of the memory leak I had with Evolution 2.32.

The user interface of evolution 3 is also more classy. Thanks a lot.

---

### Post by dawbomb on 2011-04-30
> **slooksterpsv said:**
> **Installing Gnome 3.0**
**Flickering, GAHHHHHHHH**
If you have flickering, tearing, etc. of the windows and HAVE installed the graphics drivers, you need to remove them. Unfortunately with some chipsets you will experience tearing with the graphic drivers - ATI for example.


If I remove the drivers, then won't I have no hardware acceleration?

Great post, thanks!

---

### Post by Mosabama on 2011-04-30
Thanks .. but it would be great if you write a tutorial about how to install gnome3 without effecting unity, I heard that compiling gnome3 from source would install gnome3 separately and it wouldnt effect unity at all.

thanks.

---

### Post by Martin Marshalek on 2011-04-30
Currently, that is not possible. Unity depends on Gnome 2.32 libraries right now so updating those libraries (required to run Gnome 3) would break Unity. It will be possible in 11.10 though, as Unity will be upgraded to use gnome 3 libraries without requiring gnome-shell.

---

### Post by slooksterpsv on 2011-04-30
> **grappler said:**
> Running Natty I followed the instructions to the letter and got

$ gksudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


As to email clients - try Zimbra - have to compile from source but works really well. 

[http://www.zimbra.com/downloads/zd-downloads.html](http://www.zimbra.com/downloads/zd-downloads.html)

Did you add the PPA for Gnome 3? If you didn't then that's why you're getting the error, you need to have the PPA Added in order to get gnome-shell.

Zimbra, they have a Linux binary that I've used. I've used it, but where it's an Ajax interface, meh, I like the hard-coded stuff.

> **dawbomb said:**
> If I remove the drivers, then won't I have no hardware acceleration?

Great post, thanks!

You should still have the open-source drivers installed/available. I just know with my ATI Radeon the drivers from ATI do not work, nor does the fglrx in the repos.

---

### Post by lasombra on 2011-04-30
I'm running Ubuntu Natty and installed Gnome-Shell from ppa. Unfortunately Alt-Tab is not working. Any clue how to fix this?

I've also installed installed the extensions but I get:
GLib-GIO-ERROR: Settings schema 'org.gnome.shell.extension.auto-move-windows' not installed
how to I create the missing schema?

---

### Post by akand074 on 2011-04-30
This is great. I can't wait until a fully functional Gnome 3 for Ubuntu is available.

---

### Post by slooksterpsv on 2011-04-30
> **lasombra said:**
> I'm running Ubuntu Natty and installed Gnome-Shell from ppa. Unfortunately Alt-Tab is not working. Any clue how to fix this?

I've also installed installed the extensions but I get:
GLib-GIO-ERROR: Settings schema 'org.gnome.shell.extension.auto-move-windows' not installed
how to I create the missing schema?

Do you have Sticky Keys on or Bouncy Keys? If so disable them.

Did it work after the initial installation of Gnome 3.0? Is it pressing down another key? When you're trying to ALT+TAB are you in the Activity view area or desktop view?

I didn't know there were extensions for Gnome 3.0 I'll have to look that up.

--
I think I'm going to screenshot some cool features of Gnome 3.0 and post them on the first page so if people want to see what's so special about the coolest DE ever, they can.

---

### Post by lasombra on 2011-04-30
> **slooksterpsv said:**
> Do you have Sticky Keys on or Bouncy Keys? If so disable them.
No Sticky or Bouncy Keys on.

> **slooksterpsv said:**
> Did it work after the initial installation of Gnome 3.0? Is it pressing down another key? When you're trying to ALT+TAB are you in the Activity view area or desktop view?

In Desktop view. no it never worked

> **slooksterpsv said:**
> 
I didn't know there were extensions for Gnome 3.0 I'll have to look that up.
[https://live.gnome.org/GnomeShell/Extensions](https://live.gnome.org/GnomeShell/Extensions)

---

### Post by slooksterpsv on 2011-04-30
Do this (READ ALL OF THIS FIRST):
Press ALT+F2, type in:
```

lg

```
Press return, click on the extensions area, is anything listed there?

To close the window press CTRL+ESC.

If you press ALT+TAB do you switch between current application windows? I see that's an extension.

EDIT:

Does regular tab and regular like ALT+F2 work?

EDIT 2:

Click on Activities (or press Super) and type in Keyboard, click on Keyboard, not Keyboard Input Method. Then click on Shortcuts -> Window Management and make sure that:
Move between windows, usi... is set to ALT+TAB

---

### Post by grappler on 2011-04-30
> 

**Re: [HOWTO] Fix common Gnome 3 install issues in 11.04**
              Quote:
                                                                      Originally Posted by **grappler**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10741990#post10741990")                 
                 [I]Running Natty I followed the instructions to the letter and got

$ gksudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


As to email clients - try Zimbra - have to compile from source but works really well. 

[http://www.zimbra.com/downloads/zd-downloads.html](http://www.zimbra.com/downloads/zd-downloads.html)[/I]
                                 
Did you add the PPA for Gnome 3? If you didn't then that's why  you're getting the error, you need to have the PPA Added in order to get  gnome-shell.


As I said  running from Natty,   and in a bash shell, I followed the instructions to the letter. That included the first instruction, namely, 

gksudo add-apt-repository ppa:gnome3-team/gnome3

I have tried a couple of  other ways  to install gnome3 but they all inevitably break unity (as expected) and when I try to login to the gnome3 desktop a blank purple screen appears  with no response from any key combination except the CTRL-ALT-F2 switch to a virtual console. As a result I have to switch to KDE to have a barely useable machine before using ppa-purge to eliminate gnome3 and go back to unity.

---

### Post by iveshoot on 2011-05-01
> **neopium said:**
> I have one question related to these missing functions. How in Gnome 3 can I access the old Ubuntu System Preferences and Adminisatrtion menus? When upgrading to Natty, it broke my keyboard layout and I can't find how to access the keyboard layout GUI settings.

Hi, not sure whether the following is what you want.

"System Settings"-->"Region and Language" --> Layouts.

For those who would like to enable the usual key sequences to kill X

Under the Layouts --> Options


It seems the options has be recategorized in GNOME3.

---

### Post by lilifiz on 2011-05-01
thanks dude!.... will give it a try ;-)

---

### Post by lasombra on 2011-05-01
What to do, if the session does not start at all? I'm a little confused on how ubuntu stores the session settings.

If I login using the gnome-shell session, it only starts empathy, but nothing else. Also no borders are visible. I have to start in recovery console and enter 
```
gnome-shell --replace&
gnome-session
```

---

### Post by lasombra on 2011-05-01
> **slooksterpsv said:**
> Do this (READ ALL OF THIS FIRST):
Press ALT+F2, type in:
```

lg

```
Press return, click on the extensions area, is anything listed there?

To close the window press CTRL+ESC.

If you press ALT+TAB do you switch between current application windows? I see that's an extension.

EDIT:

Does regular tab and regular like ALT+F2 work?

EDIT 2:

Click on Activities (or press Super) and type in Keyboard, click on Keyboard, not Keyboard Input Method. Then click on Shortcuts -> Window Management and make sure that:
Move between windows, usi... is set to ALT+TAB

All done, still not working.

---

### Post by -unseen- on 2011-05-01
Hi guys, I installed gnome3 from the ppa like the initial post suggests and so far it is working quite well. There are only two minor things I can't sort out so far.

First: is it possible to change the login settings so that the gnome-shell session is the default one (and maybe autologin to the gnome-shell session)?

Second: the network manager applet menu looks like it has no theme, everything else looks fine though ...

any suggestions? thanks, love gnome 3 so far, btw :)

---

### Post by Charlski on 2011-05-01
I could'nt get these codes (the last two) to work with the gksudo so I used sudo. But now I broke my ICEauthority file hahaha. I understand I have to use gksudo, but when I tried and it asked me to continue [Y/n] and typed Y nothing would happen... what should I do ?? anyone got a clue ?


```
gksudo add-apt-repository ppa:gnome3-team/gnome3
gksudo apt-get update
gksudo apt-get dist-upgrade
gksudo apt-get install gnome-shell
```

---

### Post by davy_crockett on 2011-05-01
Hi,
I followed the instructions installing gnome3 shell from the console until reaching the step where I should run gnome-tweak-tool. But I could not because I can't log in the graphical environment.

I get the error 
"Could not update ICEauthority file /home/<user>/.ICEauthority"

from all 4 accounts currently available on the computer. I searched the threads that mention this error and followed the instructions (chown, chmod) without success (the same error continues to happen). I removed the .ICEauthority file n one of the accounts to see if it solved the problem bu it did not. I crated a fresh dummy user (using adduser) but even from this new account I get the same error.

I ran out of ideas :-) so, 
if someone could help I would be grateful.

This may help, the contents of .xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=all_ALL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
The files that contain your preference settings are currently in use.

You might be logged in to a session from another computer, and the other login session is using your preference settings files.

You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.

Do you want to continue? Continue (y/n)?Failed to create secure directory: Permission denied

---

### Post by scottie_z on 2011-05-01
> **davy_crockett said:**
> Hi,

I get the error 
"Could not update ICEauthority file /home/<user>/.ICEauthority"

from all 4 accounts currently available on the computer. 

Ahh -- me too!  I just installed a few hours ago and get the same error.  Did something recently break in the PPA?  If anyone finds the solution we will be grateful.

---

### Post by itmanvn on 2011-05-01
> **scottie_z said:**
> Ahh -- me too!  I just installed a few hours ago and get the same error.  Did something recently break in the PPA?  If anyone finds the solution we will be grateful.

same here, tried to boot into recovery mode and chown chmod entire mu home directory with no luck

---

### Post by slooksterpsv on 2011-05-01
I'll check, I'll change it from gksudo to sudo or that. I know gksudo is easier for some, I used sudo to, so I'll change that.

If you get errors with .ICEauthority try this:

```

sudo chown *username*:*username* .ICEauthority

```

Where username is your username, so if I had a username joe, but the fullname was Joe Swanson, I'd change username to joe in the above.

---

### Post by itmanvn on 2011-05-02
> **slooksterpsv said:**
> I'll check, I'll change it from gksudo to sudo or that. I know gksudo is easier for some, I used sudo to, so I'll change that.

If you get errors with .ICEauthority try this:

```

sudo chown *username*:*username* .ICEauthority

```

Where username is your username, so if I had a username joe, but the fullname was Joe Swanson, I'd change username to joe in the above.

tried chown but no luck

---

### Post by slooksterpsv on 2011-05-02
> **itmanvn said:**
> tried chown but no luck

So yeah I just installed on a VM and yeah it's broke. Dang it =(, that makes me sad.

I even tried removing .ICEauthority, doesn't help.

---

### Post by magneze on 2011-05-02
I have exactly the same error. It's not a permissions problem, I get the same error in .xsession-errors. Seems like it's broken. :(

---

### Post by slooksterpsv on 2011-05-02
> **magneze said:**
> I have exactly the same error. It's not a permissions problem, I get the same error in .xsession-errors. Seems like it's broken. :(

I've read using another WM fixes the issue, so like installing LXDE or that. Then choosing Gnome Shell; dunno though, I'm going to see if I can try it.

EDIT:

I installed LXDE logged in, installed lxdm selected that as the default DM logged out of LXDE and logged into Gnome Shell, so probably just installing LXDE and logging in to lxde the logging out will fix the issue.

---

### Post by neopium on 2011-05-02
> **iveshoot said:**
> Hi, not sure whether the following is what you want.

"System Settings"-->"Region and Language" --> Layouts.

For those who would like to enable the usual key sequences to kill X

Under the Layouts --> Options


It seems the options has be recategorized in GNOME3.

Great, thanks, that's exactly what I was looking for.

---

### Post by matt_symes on 2011-05-02
Hi

> Seems like it's broken

Just to let you know, i am running Fedora 15 at the moment and Gnome 3 seems pretty stable. If there are problems under Ubuntu maybe a change of Distro is the way to go.

Maybe i should not say this but at the moment i prefer it to Unity. *runs for cover*

Kind regards

---

### Post by neopium on 2011-05-02
Hi everyone,

I am still very happy with Gnome 3, but I have found a new very annoying problem: in Netbeans 7, since I installed Gnome 3, the menus and contextual menus are not accessible or very hard to access (the selected menu is not the one under the mouse, etc.). Has anyone had the problem? Has anyone used Netbeans on Gnome 3 on other distributions and does the problem also exists there? (Just to know if it is a Netbeans problem or a Gnome problem)

---

### Post by mordecai83 on 2011-05-02
Hi all,

Love gnome 3, at the moment a lot better than unity. However encountered a few problems: 

When installing a game from software center, ppa or just trying to run gbrainy i get: 

The command could not be located because '/usr/games' is not included in the PATH environment variable

I can run the games by accessing them via the terminal with the whole path, e.g.: usr/games/gbrainy

Has anyone encountered this too, is there a fix?

Furthermore i run a laptop of which the battery is almost dead. I get a "batttery might be broken notification everytime i login. I used to be able to remove that by editing gnome-power-settings in gconf-editor. However the value doesn't seem to be there anymore. Tried searching for it to no avail. Any suggestions?

---

### Post by slooksterpsv on 2011-05-02
> **mordecai83 said:**
> Hi all,

Love gnome 3, at the moment a lot better than unity. However encountered a few problems: 

When installing a game from software center, ppa or just trying to run gbrainy i get: 

The command could not be located because '/usr/games' is not included in the PATH environment variable

I can run the games by accessing them via the terminal with the whole path, e.g.: usr/games/gbrainy

Has anyone encountered this too, is there a fix?

Furthermore i run a laptop of which the battery is almost dead. I get a "batttery might be broken notification everytime i login. I used to be able to remove that by editing gnome-power-settings in gconf-editor. However the value doesn't seem to be there anymore. Tried searching for it to no avail. Any suggestions?

As for the PATH issue, you can do the following, in your .bashrc file add the line:

PATH=$PATH:/usr/games

Or run the following command:

echo "PATH=\$PATH:/usr/games" | sudo tee -a ~/.bashrc

Or you can modify: /etc/init.d/rc.local
and change PATH=... to:

PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/games

---

### Post by mordecai83 on 2011-05-02
> **slooksterpsv said:**
> As for the PATH issue, you can do the following, in your .bashrc file add the line:

PATH=$PATH:/usr/games

Or run the following command:

echo "PATH=\$PATH:/usr/games" | sudo tee -a ~/.bashrc

Or you can modify: /etc/init.d/rc.local
and change PATH=... to:

PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/games

Tanks for the quick reply, however none of these seem to work. Weird problem, has anyone else encountered this?

---

### Post by buster2209 on 2011-05-02
> **matt_symes said:**
> HiJust to let you know, i am running Fedora 15 at the moment and Gnome 3 seems pretty stable. If there are problems under Ubuntu maybe a change of Distro is the way to go.

Maybe i should not say this but at the moment i prefer it to Unity. *runs for cover*

Kind regards

Compared to Gnome3, Unity sucks.

According to [this]("http://www.omgubuntu.co.uk/2011/04/gnome3-packages-begin-trickling-into-ubuntu-11-10/"), gnome3 will be available in the Repos with 11.10 that *wont* break Unity so if we are all patient, we don't have to move distros.

Given the issues we are all having with Gnome3 right now, in 6 months I guess a lot of the bugs will be fixed and it'll be an absolutely cracking UI!

Until then, I think maybe Gnome2 will be best for those who want some stability.

But I like Gnome3 so I guess I will tinker with it until 11.10 comes out... lol

On another note, is there yet any support for applets in the panel in Gnome3 or something that will be an equivalent as I miss my applets!

---

### Post by Terad on 2011-05-02
Thanks for the HOWTO! Worked great :D
The only odd thing now is that I have nearly every program listed twice in the application section. Is this a bug due to the installation of LXDE or something else?

---

### Post by philnice on 2011-05-02
> **buster2209 said:**
> Compared to Gnome3, Unity sucks.

According to [this]("http://www.omgubuntu.co.uk/2011/04/gnome3-packages-begin-trickling-into-ubuntu-11-10/"), gnome3 will be available in the Repos with 11.10 that *wont* break Unity so if we are all patient, we don't have to move distros.

Given the issues we are all having with Gnome3 right now, in 6 months I guess a lot of the bugs will be fixed and it'll be an absolutely cracking UI!

Until then, I think maybe Gnome2 will be best for those who want some stability.

But I like Gnome3 so I guess I will tinker with it until 11.10 comes out... lol

On another note, is there yet any support for applets in the panel in Gnome3 or something that will be an equivalent as I miss my applets!
Hopefully, we don't have to wait until 11.10 is released: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

---

### Post by Stackmouse on 2011-05-02
> I installed LXDE logged in, installed lxdm selected that as the default DM logged out of LXDE and logged into Gnome Shell, so probably just installing LXDE and logging in to lxde the logging out will fix the issue. 

I used the same method to fix the .ICEauthority issue, but I'm curious why it was issue in the first place. If someone has any pointers on possible reasons, please share :)

(...so, +1 on the "fix")

---

### Post by x1um1n on 2011-05-02
Hey folks, any idea how to force the display to stay awake?  I've always had my desktop set to never sleep as I watch films on there from time to time.  1 hour really doesn't cut it..

I've tried looking in both GConf and DConf and can't find the key, but it could be well hidden.

There used to be an applet in Gnome 2.x that gave you quick access to the power settings, think it was called inhibit, but I can't find anything similar for 3.0..

---

### Post by siblog on 2011-05-02
> **-unseen- said:**
> Second: the network manager applet menu looks like it has no theme, everything else looks fine though ...

The Network Manager Applet icon/menu also an issue for me. Has anyone figured out a fix for this?

---

### Post by thinrhino on 2011-05-02
> **slooksterpsv said:**
> 
EDIT:

I installed LXDE logged in, installed lxdm selected that as the default DM logged out of LXDE and logged into Gnome Shell, so probably just installing LXDE and logging in to lxde the logging out will fix the issue.

I faced the same issue, but installing gnome-session solved the issue. I did not have to install LXDE or LXDM.

---

### Post by buster2209 on 2011-05-02
> **philnice said:**
> Hopefully, we don't have to wait until 11.10 is released: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

Thanks for the link!

---

### Post by bcarlowise on 2011-05-02
The instructions from slooksterpsv worked like a charm, thanks!

---

### Post by slooksterpsv on 2011-05-02
> **thinrhino said:**
> I faced the same issue, but installing gnome-session solved the issue. I did not have to install LXDE or LXDM.

Installing gnome-session works? I'll have to try that, cause that'd be better than doing LXDE, but mine already have gnome-session installed. Weird... I'll try it and see what happens. 

I like the LXDE that way in-case you can't get to a DE you still have a fallback option. Just weird weird issues with Gnome 3 though. Thanks for the tip =D if it works I'll post that as an alternative to LXDE =D

---

### Post by WG- on 2011-05-02
Atm I'm installing gnome3 I have the error to. I was gonne do the fix but I'll try this first. I also readed that removing LXDE will make sure that the error returns, so I have some feedback.

---

### Post by cbowman57 on 2011-05-02
> **philnice said:**
> Hopefully, we don't have to wait until 11.10 is released: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

Just tried this out, installation went without a hitch.

---

### Post by WG- on 2011-05-02
> **WG- said:**
> Atm I'm installing gnome3 I have the error to. I was gonne do the fix but I'll try this first. I also readed that removing LXDE will make sure that the error returns, so I have some feedback.

I confirm. I installed gnome-session and removed LXDE and I still can login etc... no ICEauthority error. Maybe someone should confirm it now without installing LXDE at all...

---

### Post by WG- on 2011-05-02
> **cbowman57 said:**
> Just tried this out, installation went without a hitch.
Hooray!!!

\\:D/

---

### Post by philnice on 2011-05-02
> **cbowman57 said:**
> Just tried this out, installation went without a hitch.
That's great! have you had gnome 3 installed before you try UGR? Did you have to roll back to unity interface and then install it? And finally, what graphics card you use and also drivers? Thanks.

---

### Post by cbowman57 on 2011-05-02
> **philnice said:**
> That's great! have you had gnome 3 installed before you try UGR? Did you have to roll back to unity interface and then install it? And finally, what graphics card you use and also drivers? Thanks.

Yes, I had gnome 3 running before I tried UGR.  I did the UGR installation on another partition following their instructions to the letter, so it was installed on a fresh natty installation.  I didn't try installing it over my existing gnome 3 installation.

For graphics card I've just got an Nvidia 9500GT, 270.41 drivers.

---

### Post by philnice on 2011-05-02
> **cbowman57 said:**
> Yes, I had gnome 3 running before I tried UGR.  I did the UGR installation on another partition following their instructions to the letter, so it was installed on a fresh natty installation.  I didn't try installing it over my existing gnome 3 installation.

For graphics card I've just got an Nvidia 9500GT, 270.41 drivers.
Thanks a lot. Nvidia got better luck with everything, until natty deliver some updates to fix these issues. Just a question: I need to keep my current stuff installed upon unity, and i did a distro upgrade in the first place. How would i go if i want to reinstall it without losing anything?

---

### Post by cbowman57 on 2011-05-02
> **philnice said:**
> Thanks a lot. Nvidia got better luck with everything, until natty deliver some updates to fix these issues. Just a question: I need to keep my current stuff installed upon unity, and i did a distro upgrade in the first place. How would i go if i want to reinstall it without losing anything?

I'd like to say that you can just re-install without formatting and everything should be fine, but I'm not positive.  Make sure you have a backup before trying it.

---

### Post by buster2209 on 2011-05-02
Just tried the UGR method and all went without a hitch.

Gnome3 was very laggy until I installed the 270 NVidia driver.

No need for gnome-session or LXDE.

Awesome!

---

### Post by buster2209 on 2011-05-02
ALT+F2 brings up a HUD-esque like terminal.

It's pretty cool!

---

### Post by cbowman57 on 2011-05-02
Synapse really rounds it out, and you can add awn if you want a dock/panel.  Here are a couple shots, one is showing the theme selector extension in operation.

I saw on a blog somewhere today that someone is running a gnome-panel placed on the bottom with this shell.  I expect that for those missing the traditional panel there will probably be some how-to on that within a few days.

---

### Post by buster2209 on 2011-05-02
Missing the 'force quit' applet?

Hit Alt+F2 and type 'xkill' then left click the window you want to force close or right click to cancel.

---

### Post by grappler on 2011-05-03
I've done some research on why this proposed method of installation fails to work on my laptop (Thinkpad T-410). 

I reinstalled gnome3 as in the first post here  from an essentially fresh install of natty - with lxde added. 

Again when I logged in to gnome3 a blank purple screen came up with no panels/buttons etc on it. On retrying several times I found that the following lines appeared in the syslog in a consistent way for each attempt. 

May  3 13:56:19 bill-T410 kernel: [   45.299060] compiz[1796]: segfault at 200000001 ip 0000000200000001 sp 00007fff6cde12f8 error 14 in libcommands.so[7f97cbd78000+15000]
May  3 13:56:20 bill-T410 kernel: [   46.246497] compiz[1906]: segfault at 200000001 ip 0000000200000001 sp 00007fff469d8618 error 14 in libcommands.so[7fce8e9db000+15000]
May  3 13:56:20 bill-T410 gnome-session[1656]: WARNING: App 'compiz-1.desktop' respawning too quickly
May  3 13:56:20 bill-T410 gnome-session[1656]: WARNING: Error on restarting session managed app: Component 'compiz-1.desktop' crashing too quickly

There appears to be nothing else that might cause the problem. I had thought that gnome-shell did not use compiz? Perhaps there is something in my config that calls for compiz - but I've deleted the standard gnome config files each time.

---

### Post by magneze on 2011-05-03
Is there any way around the ICEauthority problem without installing LXDE. I have no network to download packages. Can't seem to connect to my wireless.:(

---

### Post by WG- on 2011-05-03
> **magneze said:**
> Is there any way around the ICEauthority problem without installing LXDE. I have no network to download packages. Can't seem to connect to my wireless.:(

Guess not, can't you use the cable from your router to temporary connect to the internet?

---

### Post by magneze on 2011-05-03
Not easily at all. :(

---

### Post by Grozzy on 2011-05-03
> **grappler said:**
> I've done some research on why this proposed method of installation fails to work on my laptop (Thinkpad T-410). 

I reinstalled gnome3 as in the first post here  from an essentially fresh install of natty - with lxde added. 

Again when I logged in to gnome3 a blank purple screen came up with no panels/buttons etc on it. On retrying several times I found that the following lines appeared in the syslog in a consistent way for each attempt. 

May  3 13:56:19 bill-T410 kernel: [   45.299060] compiz[1796]: segfault at 200000001 ip 0000000200000001 sp 00007fff6cde12f8 error 14 in libcommands.so[7f97cbd78000+15000]
May  3 13:56:20 bill-T410 kernel: [   46.246497] compiz[1906]: segfault at 200000001 ip 0000000200000001 sp 00007fff469d8618 error 14 in libcommands.so[7fce8e9db000+15000]
May  3 13:56:20 bill-T410 gnome-session[1656]: WARNING: App 'compiz-1.desktop' respawning too quickly
May  3 13:56:20 bill-T410 gnome-session[1656]: WARNING: Error on restarting session managed app: Component 'compiz-1.desktop' crashing too quickly

There appears to be nothing else that might cause the problem. I had thought that gnome-shell did not use compiz? Perhaps there is something in my config that calls for compiz - but I've deleted the standard gnome config files each time.
I've experienced a similar problem, and it turned out that the solution was to add the command "gnome-shell --replace" to run at login. Do so by creating a new file in ~/.config/autostart/GnomeShell.desktop. I did copy the content of another file in the same directory and just modified the newly created one.

---

### Post by bcarlowise on 2011-05-03
Does anyone else have problems with Gnome3 not changing the background? Mine seems stuck on a color gradient and will not change no matter what I select as a background via the system settings.

---

### Post by magneze on 2011-05-03
I ended up reinstalling using the following commands:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell **gnome-session**
```

Note the extra bit in bold. This seems to work fine - update the first post!!

---

### Post by slooksterpsv on 2011-05-03
> **magneze said:**
> I ended up reinstalling using the following commands:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell **gnome-session**
```

Note the extra bit in bold. This seems to work fine - update the first post!!

I will, gnome-session, it looks like, is a failed compile on the Gnome 3 PPA if you look at the packages. So I'm not sure if it's installing a 2.xx or if it is installing 3.0.x I'll update that cause it won't hurt it either way.

---

### Post by M4570D0N on 2011-05-03
I'm really enjoying Gnome 3. I've got the AlternateTab, windowNavigator, Alternative Status Menu, Dock, User Themes, and the GNOME Shell ThemeSelector shell extensions enabled and working without any issues. The only one that gave me any issue at all was installing the user theme extension. All the others were immediately enabled and working after installing gnome-shell-extensions. 

Pretty much any issue or question I've had so far has been answered over at Web Upd8. I highly recommend anyone with a problem or question read the articles/walk-throughs over there (as well as the comments for additional info). 

all gnome-shell related articles can be found here:
[http://www.webupd8.org/search/label/gnome%20shell?max-results=10](http://www.webupd8.org/search/label/gnome%20shell?max-results=10)

Also, I'm a little confused by something in the OP. It says that installing gnome3/gnome-shell via the Gnome3 PPA breaks unity and you have to reinstall your system to get it back. That sounds a bit misleading to me. I get that you cant log in to the Unity desktop after installing gnome 3, but all you have to do is purge the gnome3 PPA
```
sudo ppa-purge ppa:gnome3-team/gnome3
```
and it restores everything back to how it was before you installed gnome3. I'm also not sure why it says to use.
```
sudo apt-get dist-upgrade
```

I did not use "dist-upgrade" and it works just fine here.

For info/install on the GNOME Shell ThemeSelector, as well as quick reference to installing gnome shell or the extensions via JHbuild (git) or the PPA, check out this article:
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)


My only complaint with gnome3 is that Nautilus Elementary is gone. I really dont know why it's additional functionality is not standard for the default Nautilus in Ubuntu. Particularly for gnome3, it would seem that since gnome3 uses Mutter/Clutter an extension like ClutterView would be easy enough to have for gnome3. Anyone seen any info on NE coming to gnome3 anytime soon (or ever)? If not, will Marlin have the extra features available in NE?

---

### Post by Stackmouse on 2011-05-03
> **magneze said:**
> Is there any way around the ICEauthority problem without installing LXDE. I have no network to download packages. Can't seem to connect to my wireless.:(

[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

I had to get the packages first on a working system (dualboot), moved the .debs to the Gnome3 system, then booted to the Gnome3 login window, ctrl+alt+f1 to switch to console, and then installed the .deps with apt-get from there.

There might be a more easy solution, but this didn't take more than fifteen minutes or so (and I'm still somewhat of a noob)

---

### Post by magneze on 2011-05-03
> **Stackmouse said:**
> [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

I had to get the packages first on a working system (dualboot), moved the .debs to the Gnome3 system, then booted to the Gnome3 login window, ctrl+alt+f1 to switch to console, and then installed the .deps with apt-get from there.

There might be a more easy solution, but this didn't take more than fifteen minutes or so (and I'm still somewhat of a noob)Thanks, that's very useful. I've already reinstalled though (see previous post). Seems that gnome-session is the better package to install than lxde. Unless you actually want LXDE that is. :D

---

### Post by philnice on 2011-05-03
> **cbowman57 said:**
> I'd like to say that you can just re-install without formatting and everything should be fine, but I'm not positive.  Make sure you have a backup before trying it.
All right i'll do it this way then. Thanks a lot.

---

### Post by Stackmouse on 2011-05-03
> **magneze said:**
> Thanks, that's very useful. I've already reinstalled though (see previous post). Seems that gnome-session is the better package to install than lxde. Unless you actually want LXDE that is. :D

Oops, missed that one. :) Well, hope that saves someone the trouble of reinstalling. :D

---

### Post by 3abdo3asal on 2011-05-03
Hey everybody ..
im using 11.04 desktop on netbook it rocks anyway 
is gnome 3 better then unity that much I want to try it but , does it need high graphics and is there any big problems that happend with u ,
Thankxx Really greateat os in the world & Community tooo...:popcorn::):):)

---

### Post by slooksterpsv on 2011-05-03
Technically I can't verify that it breaks the system to where you have to reformat, but Unity won't be available (unless you remove the PPA and reinstall the Unity packages). I'll update the verbage, and include a section for reverting the changes made by Gnome 3 in case anyone wants to revert to Unity.

When I find some time I'll test it out.

---

### Post by RJ12 on 2011-05-03
It seems like that it now automatically uninstalls that accessibility package by itself. Also, has anyone noticed their login screen only displaying "other"?

---

### Post by cbowman57 on 2011-05-03
> Also, has anyone noticed their login screen only displaying "other"?

No, not on any I've done.  Might want to purge & re-install gdm if you run into trouble from that.

---

### Post by philnice on 2011-05-03
> **RJ12 said:**
> It seems like that it now automatically uninstalls that accessibility package by itself. Also, has anyone noticed their login screen only displaying "other"?
It happens to me, only on boot. Then everytime i'm log in and out, i can see the normal shell, until the next shutdown.

---

### Post by slooksterpsv on 2011-05-03
> **RJ12 said:**
> It seems like that it now automatically uninstalls that accessibility package by itself. Also, has anyone noticed their login screen only displaying "other"?

Yes I've had that happen, I rebooted into Safe Mode did dpkg-reconfigure gdm and rebooted and it cleared up mine.

---

### Post by Xantheil on 2011-05-04
I have a little problem..

Most of the applications (Banshee, firefox-till I removed it) appear twice, one with a low resolution icons (resulting in blurriness) and once with a normal size icon.
I thought it had something to do with something, until I realized Chrome shows only once ;)

Thanks

---

### Post by Terad on 2011-05-04
> **Xantheil said:**
> I have a little problem..

Most of the applications (Banshee, firefox-till I removed it) appear twice, one with a low resolution icons (resulting in blurriness) and once with a normal size icon.
I thought it had something to do with something, until I realized Chrome shows only once ;)

Thanks
I had the same problem, fixed it unintentionally by installing gnome-session and removing lxde + autoremove afterwards.

---

### Post by -unseen- on 2011-05-04
Hi, I have been playing around with this the last couple days, and came up with a different solution to installing natty+gnome3.

I didn't really like the idea of installing gnome2 plus compiz plus unity and so on and then removing all that (or more partly remove it) and than installing gnome3. So here is what I did:

I used the alternate cd to install a command line system and than added xorg and gnome 3 manually. That left me with a totally clean system, only gnome3 (and some ubuntu dependencies like ubuntuone, but that can be removed as well)... now I can start adding all my favorite apps, nice :)

For all who are interested, here are the steps necessary to make this work (no guaranties, this worked for me on a test machine, it doesn't necessarily mean it works for everyone or every pc). It is more the notes I took for myself to remember the steps if I ever have to do it again.

- use alternate cd to install a command line system (F4 in the installer)

-after reboot Ctrl+Alt+F1

sudo aptitude update
sudo aptitude upgrade

sudo aptitude install python-software-properties (this includes add-apt-repository)

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:danilo/evolution (if you like to have evolution 3, include this repo here, it will prevent installing old libs and upgrading them later)

sudo aptitude update

sudo aptitude install xorg

sudo aptitude install gnome-session

sudo aptitude install gdm

sudo aptitude install gnome-terminal network-manager gnome-tweak-tool gnome-themes-ubuntu ubunut-mono evolution

- reboot

sudo vi /usr/share/xsessions/gnome.desktop
- change "Name=Ubuntu" to "Name=Gnome3" or something you like, its what the default session is called in gdm (without "")
- change "Exec=gnome-session --session=ubuntu" to "Exec=gnome-session --session=gnome" (without "")

- if wired connections are not managed by network manager:
sudo vi /etc/network/interfaces
- comment out anything with eth0 (# are comments)

- in gnome tweak tool: interface -> icon theme -> ubuntu-mono-dark
- in gnome tweak tool: windows -> action on title bar middle-click -> minimize
- in gnome tweak tool: shell -> arrangement of buttons on the titlebar -> minimize and close

That's it, have fun. If someone is using video drivers like the "nvidia-current", probably after installing xorg is a good point to install them... My machine has an older ATI card and is using the xserver-xorg-video-ati driver, so I didn't have to do that step.

Everything works very well so far.

:guitar:

---

### Post by mercurycc on 2011-05-04
Apparently after upgrading gnome-session-bin today my Gnome 3 broke.

Time to try something new.

---

### Post by cbowman57 on 2011-05-04
> **mercurycc said:**
> Apparently after upgrading gnome-session-bin today my Gnome 3 broke.

Time to try something new.

From the logon screen, open the recovery console.

From the recovery console open synaptic, 'sudo synaptic'
Click on "Upgrade All"
Mark selected files for upgrade.
Apply, then reboot, selecting "Ubuntu GNOME .." whatever it is, login as per usual.

Haven't tried yet but it's possible this upgrade fixed the autologin bug, it definitely changed /usr/share/xsessions/gnome.desktop so if you'd edited it you might want to edit again.

* Did not fix autologin.

---

### Post by philnice on 2011-05-04
> **mercurycc said:**
> Apparently after upgrading gnome-session-bin today my Gnome 3 broke.

Time to try something new.
How you did upgrade it?
I was just looking in synaptic and noticed some strange things:
gnome - session and gnome - session - bin packages are both under version 3.0.0.
The description for the gnome - session package says: "This package contains a session that can be started from a display
manager such as GDM. It will load all necessary applications for a
full-featured user session.

The session manager also features the ability to save a running session
an restore it later."
Underneath, i can see a gnome3 - session package which is not installed, version is 2.32.1, and here's the description: "This package contains a session that can be started from a display
manager such as GDM. It will load all necessary applications for a
full-featured user session.

The session manager also features the ability to save a running session
an restore it later.

This version is configured to start the **GNOME 3 desktop**, based on the
**GNOME shell**. 
If i try to  install gnome3 - session, i get a notice that gnome - session and **ubuntu** - **desktop **packages, are about to removed. Strange?

---

### Post by kagedin on 2011-05-04
Hey guys, so I followed the instructions in the first post and it all went pretty smoothly, however when I rebooted and logged in to the "Ubuntu Gnome Shell" it didn't look right. Everything seems to work fine, however, the bar up top is all strange looking, the icons in the bar are all messed up, and some of the text in the application list is messed up. I followed the instructions of removing the accessibility theme and then installing the standard theme, however it didn't change anything. I attached a screenshot of my desktop so you guys can see how it looks. 

Like I said, everything seems to work fine, it just looks messed up, anyone else have this problem or know how to fix it? Would a simple uninstall/reinstall work? Thanks for your time and help guys.

---

### Post by RJ12 on 2011-05-04
> **kagedin said:**
> Hey guys, so I followed the instructions in the first post and it all went pretty smoothly, however when I rebooted and logged in to the "Ubuntu Gnome Shell" it didn't look right. Everything seems to work fine, however, the bar up top is all strange looking, the icons in the bar are all messed up, and some of the text in the application list is messed up. I followed the instructions of removing the accessibility theme and then installing the standard theme, however it didn't change anything. I attached a screenshot of my desktop so you guys can see how it looks. 

Like I said, everything seems to work fine, it just looks messed up, anyone else have this problem or know how to fix it? Would a simple uninstall/reinstall work? Thanks for your time and help guys.

Are you by chance running any restricted drivers? I heard GNOME 3 isn't working well with them

---

### Post by kagedin on 2011-05-04
> **RJ12 said:**
> Are you by chance running any restricted drivers? I heard GNOME 3 isn't working well with them

Yes actually, I'm running ATI restricted drivers. I also have ATI Catalyst Control Center installed, so should I disable them and uninstall CCC?

---

### Post by RJ12 on 2011-05-04
> **kagedin said:**
> Yes actually, I'm running ATI restricted drivers.

You need to disable those, that should fix the issues your having.

---

### Post by kagedin on 2011-05-04
So strange issue. After trying to disable the restricted drivers via "Additional Drivers" and the clicking "Remove" an error message popped up, I don't remember what it said, but after it said the drivers were still in use, so I figured I would reboot and try again. However, after rebooting, Ubuntu will no longer boot up.

---

### Post by cbowman57 on 2011-05-04
[Link to Natty Gnome 3.0 64-bit custom distro torrent]("http://linuxtracker.org/index.php?page=torrent-details&id=19b739de888cd8f1b12816e3a191abc45f40710d")

I debated on this for a couple days, finally decided to make a custom distro already loaded with gnome shell. Read the README, be prepared to figure some things out on your own and through this forum.

It's ugly out of the box but the extensions & gnome-tweak-tool are already installed.  If you don't have an Nvidia card you will probably need to logon in failsafe mode (not sure about that).  The README contains links to the work-in-progress Gnome shell theme selector.

Frankly I think it looks & acts just like the Fedora & Suse gnome 3.0 distros, without having to abandon Ubuntu.

* My connection is slow so it will take some time for this to spread, in the mean time please be patient.

---

### Post by 23dornot23d on 2011-05-04
Will it run as a live CD /DVD too ?

Downloading it now to try it out ....

Thank you ....  ;) ..... 

( This may resolve a lot of problems people are having getting the Themes to work etc ..... and may be a good place to start from as people will then be using the same PPA's and files  )

---

### Post by cbowman57 on 2011-05-04
> **23dornot23d said:**
> Will it run as a live CD /DVD too ?

Yes, but it will require some tweaking to make it look decent.  If you use a USB drive with a persistence file you can probably have a pretty nice live environment within a few minutes.  Gnome tweak tool is our friend. :)

---

### Post by 23dornot23d on 2011-05-04
ok cheers .... will try it ty ...... at the moment its saying 2 peers and a 4 hour download ..... 1.07 Gig
but maybe the more of us that keep it up and alive on the torrent - once downloaded then the time may go down.

---

### Post by cbowman57 on 2011-05-04
> **23dornot23d said:**
> 
( This may resolve a lot of problems people are having getting the Themes to work etc ..... and may be a good place to start from as people will then be using the same PPA's and files  )

That's what I was hoping for, a base line experience.  

Just want to warn people, this is not a finished distro with millions of hours of beta testing.  I am making the assumption that anyone who checks it out knows what to expect, this is basically a generic backup of my system created with Remastersys.

ps. trying to spare as much bandwidth as possible for this initial upload, it's slow, I blame Clearwire, sorry.

---

### Post by 23dornot23d on 2011-05-04
That is not a problem I will let it chug away while I work .....   120 Meg downloaded so far.

Could you do me a favour and do a screen shot similar to this one below showing what versions of the Files you have ....

I just want to do a comparison .... because we already seem to have a good working system
for Gnome-Shell ...... [HERE IS MY SCREENSHOT]("http://img857.imageshack.us/img857/4076/screenshot19b.png") ..... would like to know what if any files
need updating ...... and what PPA's you have to the relative files you used ...... 

I realize that Gnome3-Session is indicated as needing a update .....  but I will do this later on
as it wants to remove Gnome-Session when I choose it ......

---

### Post by cbowman57 on 2011-05-04
Here are the screenshots of synaptic.

---

### Post by 23dornot23d on 2011-05-04
Good - from what I can see we seem to running similar setups and using the same files
pulled in from the same PPA's by the looks of it   .... that's good to know - looking again
some of mine need updating.  ty ;)  so will definitely use the downloaded ISO as a start point
for a new system.  
( 409 Meg downloaded - 3 Peers now )

---

### Post by jbicha on 2011-05-05
Hi, I just wanted to let you know that the new gnome-session I got uploaded today to the Gnome3 PPA will allow you to log in to Ubuntu (Unity) or Ubuntu Classic in addition to Gnome Shell. You can read a little more about the fixes at my personal [blog]("http://jeremy.bicha.net/2011/05/05/improvements-to-gnome-3-ppa-5-5/").

If you want to use Ubuntu Classic, you'll need to be sure to install gnome-session-fallback. We don't depend on this as Gnome Panel won't be in the default 11.10 install (but will be in the repositories) and part of the point of the PPA is as a testing ground for 11.10 development.

Also, some of your problems are because you are not installing things correctly. gksu or gksudo are only for GUI commands, not for command-line stuff. So *gksu gedit *is correct but it's *sudo add-apt-repository* and *sudo mv file* and *sudo apt-get upgrade*.

---

### Post by jbicha on 2011-05-05
By the way, gnome3-session is a broken package. Don't install it and remove it if you already have it installed. You don't need it as everything you need to login is already in gnome-session or gnome-shell.

---

### Post by 23dornot23d on 2011-05-05
@jbicha Thanks for the information on gnome3-session  .... have now downloaded the ISO from Cbowman .... and there are 6 peers now on it ..... 

I will also leave it up and running as long as I can - time to try it out .... will put it on another machine now.

This is a screenshot of GNOME3 / GNOME shell running on my system and its brilliant so far .....
[SCREENSHOT]("http://img153.imageshack.us/img153/6418/screenshot20r.png") ...... good burnt the ISO onto a DVD  ..... will go load it on the Desktop machine now and let you know how well it runs .....

_______________________________________________________

**[COLOR=Red](ONLY testing the ISO here ....maybe we should have a separate thread for testing the ISO out)[/COLOR]**

DESKTOP m/c .... Good news is that it loaded in ok upto the custom screen ...... then it stopped ...... on the desktop m/c
[IMG]http://img713.imageshack.us/img713/6056/startscreen.jpg[/IMG]
I can get to a terminal though .....  
_____________________________________________

Then tried it on my old laptop ...... which is only 32 bit ...... 
I have a feeling this may be a 64 bit ISO ..... not sure though ..... but on the laptop it would not load live.

_____________________________________________

Then tried it on my Acer Aspire Z7730 ..... with dual monitor ...... no luck ..... yet 

______________________________________________

[COLOR=Red][B]Has anybody else got it running ...... can I force it from the terminal .... not sure how to get by the custom screen in live mode . 
( These are just my first attempts at running it live - still got options left - 
installing it onto a flash drive or trying to get it working from the terminal  )

[COLOR=Black]Was there a way in remastersys to get it to log into the desktop automatically ........
[/COLOR][/B][/COLOR]
I am sure that would have been ok for me and it should have then gone straight into the desktop.

---

### Post by Dronar on 2011-05-05
When I log in to gnome3 (and gnome2 with the new patch) the GUI freezes.
The mouse cursor is still works, but the GUI just dies 1-2 seconds after login.

I've done some googling, and I think this is related to some issue with the nVidia drivers, some people have gotten it working (slowly) with the nouveau drivers. 

I'm on a GeForce 7300 Go.

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> Then tried it on my old laptop ...... which is only 32 bit ...... 
I have a feeling this may be a 64 bit ISO ..... not sure though ..... but on the laptop it would not load live.

_____________________________________________

Then tried it on my Acer Aspire Z7730 ..... with dual monitor ...... no luck ..... yet 

______________________________________________

[COLOR=Red][B]Has anybody else got it running ...... can I force it from the terminal .... not sure how to get by the custom screen in live mode . 
( These are just my first attempts at running it live - still got options left - 
installing it onto a flash drive or trying to get it working from the terminal  )

[COLOR=Black]Was there a way in remastersys to get it to log into the desktop automatically ........
[/COLOR][/B][/COLOR]
I am sure that would have been ok for me and it should have then gone straight into the desktop.

Yeah, it is 64-bit, didn't even think about a 32-bit version, should have made it clear in the comments, sorry about that.

To get past the logon screen you should be able to click on the box end enter "custom" as user, leave pw empty, then logon.

---

### Post by 23dornot23d on 2011-05-05
Ok had to kill off the gdm display greeter in HTOP ....

Easiest way is to kill this one and it restarts the greeter up ....... 
ALT + CTRL + F7 to get back to your greeter .... LOGIN screen ......

[IMG]http://img815.imageshack.us/img815/1958/killi.jpg[/IMG]

as it would not let me into the greeter box to select anything ... its looking good now though ... ty 



Then it all worked ok

[IMG]http://img19.imageshack.us/img19/4828/screenshot4xq.png[/IMG]


Just for information .....

Picked up my network and display ..... no problems ..... 

( not sure why it hung at the greeter though - see if others get the same problem - may be my system will add a screenshot showing settings and computer I am using )


What I did to get in before I forget

1 .... ctrl+alt+f1 (to go into a terminal)
2 .... sudo passwd (so I could get in as root to work)
3 .... apt-get update (to get the download listings up to date - realised here it was 64 bit - but thanks for confirming it)
4 .... apt-get install lxde ( just wanted a desktop to get into - but did not use this - but am adding it here in case it did something to change things - just to be precise on the steps I took )
5 .... apt-get install htop
6 .... htop ( look at the system see if I can stop the greeter )
7 .... after stopping the gdm greeter - it seemed to restart properly

[IMG]http://img199.imageshack.us/img199/5871/dsci0675f.jpg[/IMG]


Then just clicked Unlock - no password needed ......

My system - just in case it hung at login due to some problem with my hardware .... seems ok now though
I want to install it ..... 

[IMG]http://img199.imageshack.us/img199/9296/screenshot5ow.png[/IMG]

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> Ok had to kill off the gdm display greeter in htop ....

as it would not let me into the greeter box to select anything ... its looking good now though ... ty 



Then it all worked ok

[IMG]http://img19.imageshack.us/img19/4828/screenshot4xq.png[/IMG]

I updated the original post to identify it as 64-bit, & the description at linuxtracker as well.

How exactly did you use htop to kill the greeter?  Somebody else might want that bit of info.
(You beat my question)  thanks for explaining how you did it.

---

### Post by cbowman57 on 2011-05-05
Ok, now you can load load gnome-tweak-tool and adjust the GTK & icon themes.  Re-install the theme selector (the per-user portion) & complete or undo the "Activities" text or logo mod so that it displays something (or nothing if that's your preference).

Ubuntu-tweak, synapse & awn are already preloaded, not sure what else I've got on there.  It's probably shaping up nicely already.

---

### Post by 23dornot23d on 2011-05-05
Your welcome .... 

I was wondering if you were to do a new one at some point .....

Whether you could add lxde and htop ...... as they are only small .... this could be really useful if people encounter problems  .... ( I like options  )

Do you have some details on how you used remastersys too ..... as when I tried it the
ISO file was too big ..... that I created ..... :confused:

Ok will try some of the customization once I have it permanent ty ...

THEMES is there (but no themes are available yet to select)
AWN is on 
GIMP is also on I am glad to see too

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> Your welcome .... 

I was wondering if you do a new one at some point .....

Wether you could add lxde and htop ...... as they are only small .... this could be really useful if people encounter problems  .... ( I like options  )

Do you have some details on how you used remastersys too ..... as when I tried it the
ISO file was too big ..... that I created ..... :confused:

Ok will try some of the customization once I have it permanent ty ...

THEMES is there (but no themes are available yet to select)
AWN is on 
GIMP is also on I am glad to see too

In remastersys I used the dist option, not the backup option.  My entire installation takes up just over 4 Gb, probably because I keep Downloads & Music on a separate partition & mount/bind them in fstab.

I don't use evolution so a lot of that is missing, if anyone wants it they will need to re-install it.

---

### Post by 23dornot23d on 2011-05-05
Cheers for the info - 

Trying to do a (backup) - but will try the (dist) 

[IMG]http://img88.imageshack.us/img88/415/remaster.jpg[/IMG]

basically to see why its hanging for me at the login .....
I like trying to solve problems - so its as good a challenge as any at this moment in time

Ok created one now and its come in at 3.8Gig ..... perfect ...... 

Thank you once again ..... (will let you know if its a problem with remastersys or my system shortly.)




 As far as I see now Gnome Shell and Unity are in close competition which to me is a good thing.

(I would really like to see LXDE and Gnome-Shell as the way forward though knowing now that they will run together on a 7 year old machine speaks volumes to me  ..... LXDE then could be eventually dropped at a later date once Gnome-Shell has all the functionality to cover all the extra things that the panels can do at this moment in time ...)

Hope that once the ISO works so the problems left will be become easier to sort out as we will all be
able to sit on top of the same foundations - solutions for the people with problems should become
easier to solve without having to guess which files have been loaded from which PPA's.

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> Cheers for the info - 

I am trying to do a (backup) - but will try the (dist) basically to see why its hanging for me at the login .....
I like trying to solve problems - so its as good a challenge as any at this moment in time and as far as I see now Gnome Shelll and Unity are in close competition which to me is a good thing.

(I would really like to see LXDE and Gnome-Shell as the way forward though knowing now that they will run together on a 7 year old machine speaks volumes to me  ..... LXDE then could be eventually dropped at a later date once Gnome-Shell has all the functionality to cover all the extra things that the panels can do at this moment in time ...)



I'm no programmer but I have a patch from Carlos over on geekconnection.com to build a gnome-panel that will run on gnome-shell.  If someone wants to compile it & make it available through the ppa that would be a cool.

---

### Post by 23dornot23d on 2011-05-05
> 
I'm no programmer but I have a patch from Carlos over on  geekconnection.com to build a gnome-panel that will run on gnome-shell.   If someone wants to compile it & make it available through the ppa  that would be a cool.
Neither am I ..... 
I just like doing 3D ....... hope someone else picks up on this , could be good if its highlighted on the UGR on launchpad.
thats if they want to go that way of course ..... 

I know Kansasnoob looked at having Lxde with Gnome-Shell at one point and thats what struck me as a good idea too ..... 

But to add the options in Gnome Shell to have its own panels to turn on and off would be great in my mind ......

---

### Post by cbowman57 on 2011-05-05
[QUOTE=23dornot23d;10773657
But to add the options in Gnome Shell to have its own panels to turn on and off would be great in my mind ......[/QUOTE]

This is the blog entry [http://carlosgc.linups.org/gnome/gnome-panel-dock]("http://carlosgc.linups.org/gnome/gnome-panel-dock")

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> Cheers for the info - 

Trying to do a (backup) - but will try the (dist) 

[IMG]http://img88.imageshack.us/img88/415/remaster.jpg[/IMG]

basically to see why its hanging for me at the login .....
I like trying to solve problems - so its as good a challenge as any at this moment in time

Ok created one now and its come in at 3.8Gig ..... perfect ...... 



Good way to keep an installable backup.

---

### Post by cbowman57 on 2011-05-05
> **23dornot23d said:**
> 
**[COLOR=Red](ONLY testing the ISO here ....maybe we should have a separate thread for testing the ISO out)[/COLOR]**


Good idea. [Link to thread for discussing this ISO]("http://ubuntuforums.org/showthread.php?t=1750450")

---

### Post by aigle on 2011-05-06
I installed Gnome 3 in ubuntu 11.04 fresh install. After that I rebooted and tried to login gnome shell but I can,t. Each time I get this message:
> could not update ICEauthority 
 file /home/shahbaz/.ICEauthority
 
I tried:

 sudo apt-get install gnome-session

 It says:

> unable to locate package session

Can anyone help?

Thanks

---

### Post by layr on 2011-05-06
```

sudo apt-get dist-upgrade
```resulted finally in:[B]
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session_3.0.1-0ubuntu1~build1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]Edit: running```

sudo apt-get -f install
```
fixed this issue.

---

### Post by cbowman57 on 2011-05-06
Try sudo apt-get -f install

then sudo apt-get dist-upgrade

Not certain, just a shot in the dark.

---

### Post by zka on 2011-05-06
Since upgrading, I have a weird problem with fonts. Gnome terminal, firefox etc have a strange font that hurts the eyes in a way i can't describe. Tried changing the fonts in several ways but it just isn't working. Had the same problem with unity after the upgrade, and the problem still persisted after the upgrade to gnome3.

Anyone who can give some information as to why my installation got screwed ?

---

### Post by cbowman57 on 2011-05-06
Did you look over font settings with gnome-tweak-tool?

Sounds like it might be a hinting & antialiasing problem.

---

### Post by zka on 2011-05-06
> **cbowman57 said:**
> Did you look over font settings with gnome-tweak-tool?

Sounds like it might be a hinting & antialiasing problem.

Yes, I did play with fonts settings with the gnome-tweak. Tried different aa and hinting.. still nothing.

The thing is, even if i change the font to something else, the font used in the terminal, applications such as firefox is still the same.

---

### Post by cbowman57 on 2011-05-06
> **zka said:**
> Yes, I did play with fonts settings with the gnome-tweak. Tried different aa and hinting.. still nothing.

The thing is, even if i change the font to something else, the font used in the terminal, applications such as firefox is still the same.

Strange, I can't think of anything more to check.

Maybe re-install your fonts?

---

### Post by grappler on 2011-05-06
Thanks slooksterpsv - your method gave me the clue to solve my problem. Instead of making a new file in ~/.config/autostart  as you suggested, I deleted compiz-1.desktop from that folder. Then on rebooting gnome3 worked. Since this is in the userspace it was not deleted with the fresh install, and was not one of the config files I had thought to delete before.

---

### Post by ZekeGraal on 2011-05-06
Still not good for newer users, since extra stuff had to be tweaked on your part. The ppa broke all of my sessions, so I just dropped back to my 11.04 beta 2.. Can't wait until this is fully functional though! :D

---

### Post by cbowman57 on 2011-05-06
> **jbicha said:**
> Hi, I just wanted to let you know that the new gnome-session I got uploaded today to the Gnome3 PPA will allow you to log in to Ubuntu (Unity) or Ubuntu Classic in addition to Gnome Shell. You can read a little more about the fixes at my personal [blog]("http://jeremy.bicha.net/2011/05/05/improvements-to-gnome-3-ppa-5-5/").



Thanks for everything you're doing.

---

### Post by philnice on 2011-05-07
How things going here? - I've tried to install ugr-desktop-g3 earlier on a fresh natty install but gave me an error. The package wasn't there. I'll stay with plain old gnome for a while cause, i need a break! I use the open source ati drivers now, which don't work at all with unity, but the reason i got them was to run gnome3 anyway.

---

### Post by chazdg24 on 2011-05-08
I actually installed Gnome 3 with distorted graphics. I remembered that Gnome 3 has issues with the ATI CCC and drivers. So I unistalled both and rebooted to a black screen. I then rebooted into the Recovery Console and was able to install the Generic video driver. I rebooted again and had a decent looking Gnome 3. I rebooted one more time and then...

a black screen. Ubuntu will not load, so I rebooted and ran various diagnostic tests in Recovery Console to no avail. Every time I reboot, I get a blank screen.

Any ideas how I should proceed to fix this?  Thanks in advance for any help.

---

### Post by chazdg24 on 2011-05-08
Well I reconfigured the video card to the generic version and now am able to boot into Gnome 3.  Only problem, I the hard drive fan will not power down on my desktop (at least I think it is the hard drive fan).

I booted into Windows 7 and the fan stopped spinning once the Welcome screen popped up.  Any ideas how to proceed with this problem?  I would open the case, but I am disabled and will be unable to pull that off.  Any help is appreciated.

---

### Post by bulldog on 2011-05-08
> **chazdg24 said:**
> Well I reconfigured the video card to the generic version and now am able to boot into Gnome 3.  Only problem, I the hard drive fan will not power down on my desktop (at least I think it is the hard drive fan).

I booted into Windows 7 and the fan stopped spinning once the Welcome screen popped up.  Any ideas how to proceed with this problem?  I would open the case, but I am disabled and will be unable to pull that off.  Any help is appreciated.

I don't think it's your hard drive fan who's making the noise.
Hard drives do not come with a fan by default afaik.

Is it possible that the fan from your video card is making the noise?

---

### Post by 23dornot23d on 2011-05-08
> **bulldog said:**
> I don't think it's your hard drive fan who's making the noise.
Hard drives do not come with a fan by default afaik.

Is it possible that the fan from your video card is making the noise?


I have a feeling this may be true too as a while back my temperature was high on the 
Nvidia Card ..... look in Applications >> Administration >> Nvidia Server Settings

open it up and keep a check on the Thermal reading ..... there is also a Powermizer

[IMG]http://img546.imageshack.us/img546/1772/nvidia1.jpg[/IMG]


Check the Thermal readings ..... mine is usually constant at 58 C its a laptop though ... yours should be much lower.

[IMG]http://img36.imageshack.us/img36/5222/nvidia2n.jpg[/IMG]


Try to work out when it happens too - mine was playing flash games - scrabble in firefox
was ok in Google Chrome though .....


Of course if its not a Nvidia card then most of this is not relative to your situation ....

But its best noting when the fan is running the hardest and what you have running ..

Also do you have all the latest updates .

and what kernel do you use .... in a terminal type .....

uname -a

---

### Post by -unseen- on 2011-05-08
Does suspend and resume work for you guys? For me it seems to suspend fine, but when resuming, the desktop is messed up (gfx, like wrong colors etc.) and its unresponsive.

---

### Post by chazdg24 on 2011-05-08
> **bulldog said:**
> I don't think it's your hard drive fan who's making the noise.
Hard drives do not come with a fan by default afaik.

Is it possible that the fan from your video card is making the noise?

Yes, you are correct (a dumb conclusion on my part).  I think it is an  ATI driver issue again.  As soon as I log in to Ubuntu the fan kicks in.  I guess the question is - what is the correct driver for and  ATI 5800 Video Card?

BTW, Gnome 3 is nice, not great, but a better choice than Unity.

---

### Post by kelvin spratt on 2011-05-08
Just to let you Know Arch moved to Gnome3 last week and its much more stable than fedora there are a lot of hacks on the Arch forums. It is so easy to customise the Gnome Shell transparency etc. As with Arch you learn the command line way 1st the the tools appear after

---

### Post by slooksterpsv on 2011-05-08
> **chazdg24 said:**
> Yes, you are correct (a dumb conclusion on my part).  I think it is an  ATI driver issue again.  As soon as I log in to Ubuntu the fan kicks in.  I guess the question is - what is the correct driver for and  ATI 5800 Video Card?

BTW, Gnome 3 is nice, not great, but a better choice than Unity.

My computer only has an HD 4200, but the AMD Drivers fail to work for me. I stick with the Open Source ones (installed by default). I've switched to Kubuntu due to stability issues with Gnome 3. And in Kubuntu I'm able to use the Proprietary AMD Drivers.

So yeah. I'll read through see if I can update the OP with content that you guys have provided for fixes and that.

---

### Post by slooksterpsv on 2011-05-08
> **-unseen- said:**
> Does suspend and resume work for you guys? For me it seems to suspend fine, but when resuming, the desktop is messed up (gfx, like wrong colors etc.) and its unresponsive.

Suspend was hit or miss. If I had a media player open, it wouldn't resume, if I didn't, it would sometimes come back.

---

### Post by philnice on 2011-05-08
Based on my last (yesterday) experience with gnome 3 and natty, the ati driver works good and fast, better than it does with unity, until i'll launch mixxx software (which is essential for me). Then it will brake, and even reisub won't work sometimes. On the other hand fglrx, will work with mixxx, but firefox is so slow that it becomes useless. Guess i need to combine parts from both drivers, to make it work for my old system!
The good thing is, i succeed to make an iso of my ubuntu 10.10 installation with remastersys, so now i can play with no worries.
Edit: One last thing. Another version of ubuntu gnome remix is out since last night. But when i tried,  ugr-desktop-g3 package wasn't in the repos as it should so i ended up with a broken shell. So if you guys wanna try this out, make sure you have a backup first.

---

### Post by chazdg24 on 2011-05-08
> **slooksterpsv said:**
> My computer only has an HD 4200, but the AMD Drivers fail to work for me. I stick with the Open Source ones (installed by default). I've switched to Kubuntu due to stability issues with Gnome 3. And in Kubuntu I'm able to use the Proprietary AMD Drivers.

I tried Kubuntu but did't care for it.  I haven't used KDE since Mandrake 9.3.  As far as Ubuntu goes, i just can't use Unity and was hoping that Gnome 3 would work out.  I think it might be time to check out and try a new distro.  

Thanks for the help.

---

### Post by pablotdl on 2011-05-09
Hi, I installed gnome3 on a fresh natty install and I'm having the following issues:

- Cannot set the background image: The background setting shows the image I chose, but it's not drawn on the desktop
- Icon theme does not change: I installed Faenza icons, but when I select them with gnome-tweak-tool nothing changes
- Ugly windows: Some applications, like firefox 4, display the menus an tabs as tf they don't recognize a theme at all (like plain old gtk).

Any ideas what can be the problem? I already removed gnome-accessibility-themes and installed gnome-themes-standard.

Thanks in advance.

---

### Post by M4570D0N on 2011-05-09
WARNING:
If you are using Gnome 3 from the gnome3-team PPA, the latest update for gnome-settings-daemon is borked. 

DO NOT INSTALL THIS UPGRADE.

The version in question is: 3.0.1-0ubuntu1**~build3**. 

After installing this upgrade, gnome-settings-daemon will crash with a segmentation default. No user settings will work (this includes fonts, gtk3 themes, gnome shell themes, background wallpaper, keyboard shortcuts, etc.).

If you already installed it, downgrade back to 3.0.1-0ubuntu1**~build2**:
```
sudo dpkg --force-downgrade -i '/var/cache/apt/archives/gnome-settings-daemon_3.0.1-0ubuntu1~build2_amd64.deb'
```

Fortunately, it looks like the devs are aware and there is a ~build3.1 on the way, that will hopefully fix this.

---

### Post by M4570D0N on 2011-05-09
> **pablotdl said:**
> Hi, I installed gnome3 on a fresh natty install and I'm having the following issues:

- Cannot set the background image: The background setting shows the image I chose, but it's not drawn on the desktop
- Icon theme does not change: I installed Faenza icons, but when I select them with gnome-tweak-tool nothing changes
- Ugly windows: Some applications, like firefox 4, display the menus an tabs as tf they don't recognize a theme at all (like plain old gtk).

Any ideas what can be the problem? I already removed gnome-accessibility-themes and installed gnome-themes-standard.

Thanks in advance.

See the post I just made after yours. It's a problem with gnome-settings-daemon. 

...Actually. As I was writing this reply, it looks like ~build3.1 is out. Try upgrading that package and rebooting and see if it resolves the issue.

---

### Post by slooksterpsv on 2011-05-09
> **chazdg24 said:**
> I tried Kubuntu but did't care for it.  I haven't used KDE since Mandrake 9.3.  As far as Ubuntu goes, i just can't use Unity and was hoping that Gnome 3 would work out.  I think it might be time to check out and try a new distro.  

Thanks for the help.

I have the same issue, KDE 4 has not been good KDE release, in my opinion. Now KDE 3 was amazing. So I'm switching to Mint, 11 is still going to be Gnome 2.32, not sure where 12 is heading but by that time either they'll stick with Gnome 2.32, Gnome 3 will be stable, they'll be able to make Gnome 3 Mint-ified, or Gnome 3 will function like Gnome 2.32.

The 3 main issues I have with Unity are:
1. Window Bar when maximized (I don't like it on the panel)
2. File Menu is at the top on the panel (really makes it tough using those programs where you're back and forth in those menus)
3. Lack of Customization

I sure hope Shuttleworth knows what he's doing.

---

### Post by philnice on 2011-05-09
I'm gonna try gnome 3 on ubuntu 10.10 later. I thought about switching to another distro too, but maverick really does the thing for me anyway.

---

### Post by pablotdl on 2011-05-09
> **M4570D0N said:**
> See the post I just made after yours. It's a problem with gnome-settings-daemon. 

...Actually. As I was writing this reply, it looks like ~build3.1 is out. Try upgrading that package and rebooting and see if it resolves the issue.
Thanks! upgrading gnome-settings-daemon to build3.1 fixed all my issues.

---

### Post by pablotdl on 2011-05-09
After a new restart, it's not picking up the correct icon theme or fonts. It fell back to the hicolor theme, and I don't know which font it's using but it's not the Ubuntu I configured.

I checked gconf-editor and the values seem to be right, any ideas what can be messing this up?

---

### Post by ZekeGraal on 2011-05-09
I tried Fedora 15 today to look at gnome 3. Everything has gone bad for me lol: I installed grub 1 over ubuntu's 2, ran a ton of updates, and my b43 wireless does not work, and I can't find support on it anywhere. That's what I get for being curious.. lol I'm coming back ubuntu!! :lolflag:

---

### Post by cbowman57 on 2011-05-09
> **ZekeGraal said:**
> I tried Fedora 15 today to look at gnome 3. Everything has gone bad for me lol: I installed grub 1 over ubuntu's 2, ran a ton of updates, and my b43 wireless does not work, and I can't find support on it anywhere. That's what I get for being curious.. lol I'm coming back ubuntu!! :lolflag:

You can still use gnome 3 on Ubuntu.

---

### Post by Synthetic Sam on 2011-05-09
> **cbowman57 said:**
> You can still use gnome 3 on Ubuntu.
Having tried both, it runs a lot more smoothly in Fedora 15.  But the package management always brings me crawling back...

---

### Post by cbowman57 on 2011-05-09
> **Synthetic Sam said:**
> Having tried both, it runs a lot more smoothly in Fedora 15.  But the package management always brings me crawling back...

I tried Suse for comparison and my system runs the Ubuntu version just as well, and no learning curve trying to learn a new distro.  I messed with Fedora too, but preferred Suse. :)

---

### Post by philnice on 2011-05-09
I just installed gnome 3 on ubuntu 10.10, and it works great! panel, windows, indicators, applications, everything. :)

---

### Post by cbowman57 on 2011-05-09
> **philnice said:**
> I just installed gnome 3 on ubuntu 10.10, and it works great! panel, windows, indicators, applications, everything. :)

What repos & recipe did you use?

---

### Post by philnice on 2011-05-09
> **cbowman57 said:**
> What repos & recipe did you use?
ppa:gnome3-team/gnome3
sudo apt-get install gnome3-session. The only indicator i can't get onto panel is the popper for incoming messages. I'll see what i can i do. And the login shell works as it should, with just the gnome3 session added.

---

### Post by gwoodruff on 2011-05-09
Hello all, I am trying to solve multiple issues with my 64x natty install using gnome3 ppa( official ppa from gnome3). I have this setup on two machines, one is a fresh install the other is a upgrade. They both have most of these issues. Here they are:

1) Nautilus will not launch from the favorites bar. It does launch from a shortcut on the desktop. It will not run from the terminal unless I am root.

2) Number lock is disabled at startup (enabled in my bios). I used to be able to enable after nattty had started, I no longer can, though num lock light is lit - number keypad does not work!
* Update keypad now works, only when num lock is off!

3) I have set gnome3 set to let nautilus draw the background and desktop, I get a white screen at boot until Nautilus is launched then I get a background and some desktop icons(no computer or network icons). If I plug in a usb drive the icon appears on my desktop, when I select it I loose the background and have to select it again. No PC, Network, or trash icons ever.
* update - The desktop background is being displayed at boot now. I am still missing my Computer, Home, Network icons even though they are set to be displayed by gconf-editor.


4) Wireless randomly will drop the connection, have to reconnect, sometimes it will, sometimes I have to reboot.

I have Fedora installed on a 2nd hard drive on the machine with a clean install and the only similarity is it displays the default desktop until I launch Nautilus, then my background and desktop are displayed with all of the icons. From there on out Fedora has none of these issues. I have used Ubuntu Gnome and XFCE as my only os since 6.0 and have never had this many problems. Both machines would not run the gdm because of Nvidia issues after the upgrade and clean install. I DO NOT want to give up on Ubuntu as I tell all my friends and family to use it. Can anyone help me sort these issues out?
** I have been booting into Fedora and so far the only big issue I have not solved is getting my usb wifi to work (Realtek 8192su). *update got wifi working in Fedora! I would still rather use Natty with gnome3 but am still seeing alot of issues. Gary

---

### Post by cbowman57 on 2011-05-09
> **philnice said:**
> ppa:gnome3-team/gnome3
sudo apt-get install gnome3-session. The only indicator i can't get onto panel is the popper for incoming messages. I'll see what i can i do. And the login shell works as it should, with just the gnome3 session added.

Thanks, I might play with that when I get some time.

---

### Post by philnice on 2011-05-09
> **cbowman57 said:**
> Thanks, I might play with that when I get some time.
Np, i think it would be a good start point for a 32 bit custom iso. Speaking of which, i'm gonna launch remastersys now to see how it goes with that.

---

### Post by cbowman57 on 2011-05-09
> **philnice said:**
> Np, i think it would be a good start point for a 32 bit custom iso. Speaking of which, i'm gonna launch remastersys now to see how it goes with that.

Speaking of a custom iso 

[[COLOR="Indigo"]gNatty Gnome i686 v1 Live thread & link to torrent[/COLOR].]("http://ubuntuforums.org/showthread.php?p=10793858#post10793858")

---

### Post by lamb123 on 2011-05-10
okay I followed the 1st post in this thread. during dist-upgrade I got 1 "system error" message to which I clicked cancel. (it completed tho)

next during "sudo apt-get install gnome-shell gnome-session" I get following error right from the start:

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.0.0) but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
               Depends: gjs but it is not going to be installed
               Depends: libgjs0b (>= 0.7.11) but it is not going to be installed
               Depends: libmutter0 (>= 3.0.0) but it is not going to be installed
               Depends: gnome-icon-theme-symbolic (>= 2.91) but it is not going to be installed
               Depends: gnome-themes-standard (>= 2.91) but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not going to be installed
               Depends: gir1.2-polkit-1.0 but it is not going to be installed
               Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
               Depends: mesa-utils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```what to doooo

---

### Post by jbicha on 2011-05-10
> **gwoodruff said:**
> 
1) Nautilus will not launch from the favorites bar. It does launch from a shortcut on the desktop. It will not run from the terminal unless I am root.

3) I have set gnome3 set to let nautilus draw the background and desktop


#1 and #3 are related. If you have Gnome display the desktop icons, then many Nautilus shortcuts won't work. I reported [this]("https://bugzilla.gnome.org/show_bug.cgi?id=649063") and it is now fixed in the development version of Nautilus. We'll have to see about getting a patch for the PPA since it was decided today to keep the Gnome 3 PPA at version 3.0.* instead of switching to the developmental 3.1.*.

A workaround is to run ```
nautilus .
``` from your terminal. Please do not use a root file manager unless you are doing root stuff!

---

### Post by scpxi on 2011-05-11
> **gwoodruff said:**
> 

1) Nautilus will not launch from the favorites bar. It does launch from a shortcut on the desktop. It will not run from the terminal unless I am root.



I'm not sure if this is the same prob that I have but if you enabled 
"Have file manager handle the desktop" in gnome-tweak-tool the same thing happens so I just turned it off for now, you wont have desktop icons but nautilus should launch on your fav menu without root

---

### Post by gwoodruff on 2011-05-11
The only issues I have left is Nautilus not launching from the favorites bar, and no computer, network, or home icons on the desktop when file manager is set to handle the desktop. All else functions ok. I will note that I have Fedora on the same PC (diff hard drive) with the same settings and it does launch Nautilus from favorites and does display home, network, and computer icons on the desktop. Fedora just feels slower to respond on my PC and Ubuntu has better community support (thank you all)! I believe these last few bugs will get worked out and we will even end up with weather notification on a panel again.

---

### Post by philnice on 2011-05-11
Guys, you might want to check this out as well: [http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

---

### Post by GeekGirl1 on 2011-05-11
> **lamb123 said:**
> okay I followed the 1st post in this thread. during dist-upgrade I got 1 "system error" message to which I clicked cancel. (it completed tho)

next during "sudo apt-get install gnome-shell gnome-session" I get following error right from the start:

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.0.0) but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
               Depends: gjs but it is not going to be installed
               Depends: libgjs0b (>= 0.7.11) but it is not going to be installed
               Depends: libmutter0 (>= 3.0.0) but it is not going to be installed
               Depends: gnome-icon-theme-symbolic (>= 2.91) but it is not going to be installed
               Depends: gnome-themes-standard (>= 2.91) but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not going to be installed
               Depends: gir1.2-polkit-1.0 but it is not going to be installed
               Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
               Depends: mesa-utils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```what to dooooI got the same error, except I followed the advice:

```
apt-get -f install
```

After it ran, I repeated the first post instructions and everything completed.

---

### Post by jbicha on 2011-05-12
gwoodruff, Ok, nautilus is fixed now in the PPA so it should open normally even when desktop icons are shown.

---

### Post by gwoodruff on 2011-05-12
Thank you jbicha! Nautilus does launch from the favorites bar now. Any ideas why the computer, home and Network icons are missing from the desktop?
Thanks, Gary

---

### Post by 23dornot23d on 2011-05-12
Try the DISTRO ....... everything is already set up for you ..... and its all up to date 
at the moment ........  its in development too  ( but what isn't at the moment  ? )

Step 1
[COLOR=Red]**[LINK]("http://ubuntuforums.org/showthread.php?t=1754198")**[/COLOR]

or try this ...... its not always going to work ..... but if it does ..... you are in 7th heaven.

step 2
[COLOR=Red]**[LINK]("http://ubuntuforums.org/showpost.php?p=10798534&postcount=61")**[/COLOR]

if Step 2 fails go to step 1 ..........

or continue battling with the problems ...... 

I found that the 
gir1.2-mutter-3.0



Wants or needs to be installed first to stop dependency problems ......

But if you like banging your head against a wall continue as you are then

at some point come back to this .....

Does not bother me one way or another what you do ..... !!!!

But I do like to see happy LINUX users ..... ;)

( jhbuild went through all 41 packages without a glitch from this DVD as a base too - )

---

### Post by scpxi on 2011-05-12
> **gwoodruff said:**
> Thank you jbicha! Nautilus does launch from the favorites bar now. Any ideas why the computer, home and Network icons are missing from the desktop?
Thanks, Gary

in the gconf-editor the schema for enabling/disabling the icons as well as others are missing in 
/apps/nautilus/desktop

---

### Post by gwoodruff on 2011-05-12
The Icons are displayed in Fedora 15, If it works there should not be too difficult to get them to work in Ubuntu. I have downloaded the 23dornot23d I did download and burn, will not boot live or install, says medium error, Do you have a hash for the 64b ver?
Gary

---

### Post by 23dornot23d on 2011-05-12
This is the Link to the 64 bit version ..... 

It was the first one created ..... and you need to
use HTOP as root  to stop the greeter - if you use this one ........ [[COLOR=Red]**LINK 64 Bit Gnome-Shell**[/COLOR]]("http://linuxtracker.org/index.php?page=torrent-details&id=19b739de888cd8f1b12816e3a191abc45f40710d")

The 32 Bit one has a error on the session but that was all .....
( its just a case of clicking to continue .... once you encounter it )

 it runs well and installs to the hard drive ok  ...... [[COLOR=Red]**Link 32 Bit Gnome-Shell**[/COLOR]]("https://www.4shared.com/file/S4quZcoK/gNatty_Gnome_i686_v1_Live.html")

We can also run LXDE - UNITY - and CLASSIC from it too

[IMG]http://img135.imageshack.us/img135/3503/screenshot7g.png[/IMG]

---

### Post by elcalamar on 2011-05-13
Hello there,
I hope the amazing people here can give me a hand/confirm a few things. 
I am a novice user that got over my head... I do not have dual boot, only Ubuntu 11.04, and I managed to wreck my log-in screen. I can see the user, but there is no session available and when I attempt to log in (any user) I see the following error message: Could not update ICEAuthority file /home/user/.ICEAuthority

I simply don't have access to any GUI. 

I've tried deleting or restoring ICEAuthority following other users to no avail. The problem (as I learnt in this forum) is not there, but with my Gnome-shell and Unity install. 

So, in order to hopefully fix my computer without having to wipe it...

1.I should connect my laptop to a router and use the recovery terminal that says superuser with network option?
 
I have tried to figure out how can I connect to the internet with wireless, but I get the information of the network on the screen but can't find a command or way to enter the passkey.
Any help here and confirmation that if I use a LAN connection I should have Internet would be great.

2. IF I am successful at connecting to the network so I have internet... What is the best way to recover? Should I use:
sudo ppa-purge ppa:gnome3-team/gnome3
And then re-install?

Thanks a lot for your help. I am truly scared of what I've done to my system...

---

### Post by gwoodruff on 2011-05-14
23dornot23d, I tried the 32 and 64 bit both. The 32 bit had multiple problems from no screens found to unable to find my profile. The 64 bit had the ICEAuthority problem, once fixed said it could not run the shell at first logon. I logged out and it ran fine at 2nd loggin. Still no Computer, Network or Home icons at desktop. I do not see much difference between Natty with shell and this iso? I have the Natty release working fine with the exception of the missing icons and it seems to be stable and everything works so far. What does your release have that is not in the Natty release with the gnome shell ppa? I am not opposed to going through all the downloading and setup of my fav programs again if there is some significant advantage.
Gary

---

### Post by 23dornot23d on 2011-05-14
If you already have a working system of Gnome3/Gnome-Shell then the updates you
can get out of the repositories ..... can bring you up to date with what is currently
there.

The Dvd's can produce a quick way for some people to get fully up and running ...... 
they work better with Nvidia Graphics cards .... 

(We recently found that out but some people are finding that ATI and Intel are ok too)
 
Its less hassle than compiling it all .... or using mixtures of the PPA's in the repositories .... 
of which their are 3 .... and I saw many problems before this with the things you mention.

UGR
RICOTZ
TEAM GNOME   

A week has passed now .... so the originals are a week out of date now - but still gave
a good base to start from once running .....

The UGR disk is meant to come out on the 18th of this Month .... so you may find that 
will be better for you ..... 

The links to the two available in my signature were put there 4 days ago ..... as I believe they are useful links.

if you use the packs that CBowman has so kindly provided .... you will find that a lot
more has been added ..... and working from the Dvd's will put you in a better position to
use them ..... if you follow the thread that applies to your own situation.

More people seem to be using the 32 bit ..... the 64 bit is almost ready to burn tonight.
We wanted to check and try to avoid what happened last time with the 64 bit as it locks at login
for some people - (The 64 bit -V2 is in progress and does not show this problem now).

If yours looks like this  [LINK]("http://ubuntuforums.org/showpost.php?p=10813097&postcount=353") ( and you have themes and extensions) or if you follow the thread further through .... 
to the latest update ..... which is in the pack that goes with the original install of the 32 bit system ......

[IMG]http://img809.imageshack.us/img809/218/1gs.jpg[/IMG]


We have been working for more solutions now for around 4 days ..... but a lot is happening mainly on the 32 bit one .

---

### Post by rigel4 on 2011-05-14
> **buster2209 said:**
> Compared to Gnome3, Unity sucks.

According to [this]("http://www.omgubuntu.co.uk/2011/04/gnome3-packages-begin-trickling-into-ubuntu-11-10/"), gnome3 will be available in the Repos with 11.10 that *wont* break Unity so if we are all patient, we don't have to move distros.

Given the issues we are all having with Gnome3 right now, in 6 months I guess a lot of the bugs will be fixed and it'll be an absolutely cracking UI!

Until then, I think maybe Gnome2 will be best for those who want some stability.

But I like Gnome3 so I guess I will tinker with it until 11.10 comes out... lol

On another note, is there yet any support for applets in the panel in Gnome3 or something that will be an equivalent as I miss my applets!

Great thread everyone. the post I have quoted seems the most sensible.I tried to install Gnome 3 and ended with a reinstall lol. Seems that waiting six months is the best way to go for me anyway. Presently I just log in with the classic option and use the current Gnome version. 
I look forward to October though.

Again you guys knowledge is awesome, nothing but respect.

---

### Post by elcalamar on 2011-05-14
> **rigel4 said:**
> Great thread everyone. the post I have quoted seems the most sensible.I tried to install Gnome 3 and ended with a reinstall lol. Seems that waiting six months is the best way to go for me anyway. Presently I just log in with the classic option and use the current Gnome version. 
I look forward to October though.

Again you guys knowledge is awesome, nothing but respect.

I agree. I also ended up reinstalling, and will put up with Unity until Gnome3 is stable. The 10 or so days that I was able to use Gnome-shell, it is far superior (IMHO) to Unity.

Looking forward to future developments.

---

### Post by slooksterpsv on 2011-05-14
> **elcalamar said:**
> I agree. I also ended up reinstalling, and will put up with Unity until Gnome3 is stable. The 10 or so days that I was able to use Gnome-shell, it is far superior (IMHO) to Unity.

Looking forward to future developments.

I'm with Unity, now that I fixed a few issues - like Global Menu, Overlay Scrollbars, etc. - there's a great guide on how to do that and make some nice modifications. Now it feels like Ubuntu with a dock-type deal (Unity) and lack of a customizable panel (the top). So yeah... it's working well =D. I really like it now.

---

### Post by Dobbie03 on 2011-05-15
So if I am using solely Gnome-Shell, is it safe for me to remove any Unity related programs?  If so is there an easy way to get rid of it all?

---

### Post by bmbaker on 2011-05-15
> **Dobbie03 said:**
> So if I am using solely Gnome-Shell, is it safe for me to remove any Unity related programs?  If so is there an easy way to get rid of it all?
well i removed compz which also removed unity and ubuntu-desktop and I have no problems so far!

---

### Post by Gnorrogh on 2011-05-15
> **slooksterpsv said:**
> 
To remove Gnome 3 and reinstall Unity, do the following in a terminal:

```

sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade

```

I have not tested this personally, but it sounds like it works. So let me know if it doesn't and I'll remove this section.


Tested, and confirmed working. :guitar:

---

### Post by macozz on 2011-05-15
I got the impression that the UGR with Gnome3 is better integrate. However, I already have the gnome-shell installed. There is any problem in to install the UGR-desktop-g3 on the top of the previous gnome-shell?
Thanks!

---

### Post by philnice on 2011-05-15
> **macozz said:**
> I got the impression that the UGR with Gnome3 is better integrate. However, I already have the gnome-shell installed. There is any problem in to install the UGR-desktop-g3 on the top of the previous gnome-shell?
Thanks!
You should better install ugr on a fresh natty installation, as they suggest on their website.

---

### Post by macozz on 2011-05-15
Yes, I read that. However to do a fresh install is a problem for me now. In any case, previous versions of the UGR can be installed at any moment. I notice that installing the UGR-desktop-g3 requires compiz... which is interesting because compiz is not required for Gnome 3.

---

### Post by philnice on 2011-05-15
> **macozz said:**
> Yes, I read that. However to do a fresh install is a problem for me now. In any case, previous versions of the UGR can be installed at any moment. I notice that installing the UGR-desktop-g3 requires compiz... which is interesting because compiz is not required for Gnome 3.
As far as i know, compiz should be removed while you upgrading your distro. Now, since you can't do a fresh install, you should use ppa-purge, and clean up after that to start over.
Again, some problems may occur, or maybe not, so make a backup at least.

---

### Post by Dobbie03 on 2011-05-16
> **bmbaker said:**
> well i removed compz which also removed unity and ubuntu-desktop and I have no problems so far!

Can you access Fallback Mode?

Also how is the best way to completely remove compiz and unity?

---

### Post by philnice on 2011-05-16
> **Dobbie03 said:**
> Can you access Fallback Mode?

Also how is the best way to completely remove compiz and unity?
sudo apt-get purge unity
sudo apt-get purge compiz
sudo apt-get autoremove
-if anything has left.

---

### Post by Dobbie03 on 2011-05-16
> **philnice said:**
> sudo apt-get purge unity
sudo apt-get purge compiz
sudo apt-get autoremove
-if anything has left.

Thanks Mr Nice :D

---

### Post by philnice on 2011-05-16
> **Dobbie03 said:**
> Thanks Mr Nice :D
You're welcome. :) Don't forget to **backup** first.
Another thing. You'll do that after gnome3 is installed. Otherwise, you're gonna end without a desktop enviroment.

---

### Post by Dobbie03 on 2011-05-16
Goes without saying.  Thanks again.

---

### Post by Dobbie03 on 2011-05-16
For some reason Fallback mode won't work, is anyone else having this issue?
I installed Gnome Shell using the UGR Repo.

---

### Post by cbowman57 on 2011-05-16
> **Dobbie03 said:**
> For some reason Fallback mode won't work, is anyone else having this issue?
I installed Gnome Shell using the UGR Repo.

Look in synaptic and see if it installed gnome-session-fallback.  UGR is a bit of a moving target right now, it's possible that package hadn't hit their ppa at the time you installed it.  ugr-desktop-g3 just had an update this afternoon, for example, and there are 3 packages waiting to upgrade but apparently there is a package dependency that hasn't caught up yet.

---

### Post by Dobbie03 on 2011-05-16
> **cbowman57 said:**
> Look in synaptic and see if it installed gnome-session-fallback.  UGR is a bit of a moving target right now, it's possible that package hadn't hit their ppa at the time you installed it.  ugr-desktop-g3 just had an update this afternoon, for example, and there are 3 packages waiting to upgrade but apparently there is a package dependency that hasn't caught up yet.

Yes its installed.  Should I have an option at login to choose the fallback mode?

---

### Post by cbowman57 on 2011-05-16
> **Dobbie03 said:**
> Yes its installed.  Should I have an option at login to choose the fallback mode?

No, it will only use fallback mode if a) the video does not support the shell or b) you set it to default to fallback mode with gnome-tweak-tool (or manually editing it but I don't know the procedure)

---

### Post by Dobbie03 on 2011-05-16
> **cbowman57 said:**
> No, it will only use fallback mode if a) the video does not support the shell or b) you set it to default to fallback mode with gnome-tweak-tool (or manually editing it but I don't know the procedure)

I have chosen the fallback mode to start using the option under System Settings, Gnome Shell still loads.

---

### Post by cbowman57 on 2011-05-16
> **Dobbie03 said:**
> I have chosen the fallback mode to start using the option under System Settings, Gnome Shell still loads.

My bad, you are correct, it's under system settings > system info > graphics.  Mine worked when I tried it that way a couple days ago.

---

### Post by philnice on 2011-05-16
> **Dobbie03 said:**
> I have chosen the fallback mode to start using the option under System Settings, Gnome Shell still loads.
Yes, that never worked for me either, probably a bug. I'm searching for a way to fallback from the terminal. I'll let you know if i find something.

---

### Post by Dobbie03 on 2011-05-17
> **philnice said:**
> Yes, that never worked for me either, probably a bug. I'm searching for a way to fallback from the terminal. I'll let you know if i find something.

That would be really appreciated!! Thanks!

---

### Post by aka TRAP on 2011-05-17
If some of the above suggestions don't work for people, you can try the following as it worked for me.

When I tried to install Gnome 3, I restarted my laptop, but it didn't give me the option to log into it, and everything failed.  So I tried running in Recovery Mode and re-typed "sudo apt-get install gnome-shell" and "sudo apt-get install gnome-shell", in that order.  Then restarted my laptop again.  If has been stated before, my apologies.  I'm just excited to figure out something on my own in Linux for once :D

& If anyone has any way to fix my issues, please tell me.  When I click on my username, you know how you get the drop-down and you can log out, switch users, etc?  Well, I tried to click "System Settings", and it didn't work.  I also can't change the time settings.  Anyone have a fix for this?

EDIT: nvm, it fixed itself.

---

### Post by Dobbie03 on 2011-05-17
> **aka TRAP said:**
> If some of the above suggestions don't work for people, you can try the following as it worked for me.

When I tried to install Gnome 3, I restarted my laptop, but it didn't give me the option to log into it, and everything failed.  So I tried running in Recovery Mode and re-typed "sudo apt-get install gnome-shell" and "sudo apt-get install gnome-shell", in that order.  Then restarted my laptop again.  If has been stated before, my apologies.  I'm just excited to figure out something on my own in Linux for once :D

& If anyone has any way to fix my issues, please tell me.  When I click on my username, you know how you get the drop-down and you can log out, switch users, etc?  Well, I tried to click "System Settings", and it didn't work.  I also can't change the time settings.  Anyone have a fix for this?

EDIT: nvm, it fixed itself.

Hold the alt key and the Power Off button shows up.

---

### Post by slooksterpsv on 2011-05-17
Quick Item: 
I just went through my guide again rebooted, tried to log in and Gnome-Shell wasn't there. It didn't install gnome-shell, even though I told it to, so I had to do sudo apt-get install gnome-shell - twice to make sure it was installed, same with gnome-session. I'll update the guide.

---

### Post by bmbaker on 2011-05-17
I just was trying out gnome tweak for changing the gtk-3 themes and i get this with everything except the default adwaita gtk-3 anyone got any ideas why this is happening?
 I tried re-installing mutter but no joy!

---

### Post by bmbaker on 2011-05-17
has anyone managed to get the systemMonitor extension working ?
i keep getting gtop missing !

---

### Post by koug44 on 2011-05-17
> **bmbaker said:**
> I just was trying out gnome tweak for changing the gtk-3 themes and i get this with everything except the default adwaita gtk-3 anyone got any ideas why this is happening?
 I tried re-installing mutter but no joy!

It seems I've got the same issue. For me, it means that gnome-settings is kinda broken

---

### Post by gwoodruff on 2011-05-17
I used the gnome3 repository ```
sudo add-apt-repository ppa:gnome3-team/gnome3
``` And have a stable gnome3 desktop. I have used tweak-advanced-settings to allow Nautilus to display the desktop and after the last round of updates I have all of the desktop icons and everything works as it should. I have evolution 3.0 from danilo's repository all works great. I am very happy with gnome3 so far and it will only get better as time progresses. Thanks to all that work so hard at giving us options!

---

### Post by macozz on 2011-05-17
[QUOTE.... I have evolution 3.0 from danilo's repository all works great. I am very happy with gnome3 so far and it will only get better as time progresses. Thanks to all that work so hard at giving us options![/QUOTE]

Hi gwoodruff,
I installed the Evolution 3.0.1 from the same repo, but I am having troubles with it. It insist in download duplicate messages and after the first time, it stops downloading mail from my GMail account.... Do you experienced something similar?

Thanks!

---

### Post by philnice on 2011-05-17
> **macozz said:**
> [QUOTE.... I have evolution 3.0 from danilo's repository all works great. I am very happy with gnome3 so far and it will only get better as time progresses. Thanks to all that work so hard at giving us options!

Hi gwoodruff,
I installed the Evolution 3.0.1 from the same repo, but I am having troubles with it. It insist in download duplicate messages and after the first time, it stops downloading mail from my GMail account.... Do you experienced something similar?

Thanks![/QUOTE]
Hi, i have also tried the updated evolution with no problems. I think you should purge the current installation and re-install. Something might have happened during the upgrade.

---

### Post by macozz on 2011-05-17
I am doing this right now....

---

### Post by philnice on 2011-05-17
> **macozz said:**
> I am doing this right now....
Ok I think in your case, you should use ppa-purge to remove it properly.

---

### Post by slooksterpsv on 2011-05-17
Ok so for the Gnome-Shell-Extension systemMonitor, I tried modifying it to see if I could get it to work and I get the same error about:

Unable to construct boxed type glibtop_cpu as it contains no zero-arg constructor.

So when trying to create it all I can figure is the constructor requires x amount of arguments, and doesn't have a 0 constructor argument. The thing is, I looked through the code for glibtop_cpu and couldn't find any constructors C wise, so I dunno if there's another area I could look and find out what's going on. Other than that it seems to all work if you just comment out the box.add((Cpu_Indicator()).actor)
line, it only gives you mem but yeah.

I'll work on it and post updates if I get it to work.

Also, if you use that extension, be sure to log out, go to a terminal and remove it as the CPU jacks up to 100% (both cores), due to it failing.

EDIT: ** NEW INFO **
The issue lines are the following:
```

this._prev = new GTop.glibtop_cpu;
GTop.glibtop_get_cpu(this._prev);

```

Calling "new GTop.glibtop_cpu" needs a constructor, I can't find one. Also if you try to pass like (0) or (0,0) it still says it can't find a zero arg constructor.

Now calling it like this:

```

this._prev = GTop.glibtop_cpu;
GTop.glibtop_get_cpu(this._prev);

```

Fails because it can't use a dynamic allocation of the CPU.

So I dunno how to fix it, still working on it.

---

### Post by macozz on 2011-05-17
> **philnice said:**
> Ok I think in your case, you should use ppa-purge to remove it properly.

Well, it seems that a full remove (not purging the ppa) fixed the problem... Probably I had a mix of Evolution 2.xx and 3.0 packages... Still some issues with the server in my university, that refuse to send my mail through it, but they goes through GMail...

Cheers

---

### Post by jbicha on 2011-05-17
Gnome Shell extensions are a bit disorganized at the moment. If you download from git, some of the extensions may actually be for the 3.1 version of Gnome Shell and may not work with the 3.0 version in the PPA. So the extensions repository isn't very usable yet, but it's a wonder in some ways it exists at all with how certain other parts of the Gnome 3 desktop are locking down (System Settings, for one).

---

### Post by cbowman57 on 2011-05-17
> **jbicha said:**
> Gnome Shell extensions are a bit disorganized at the moment. If you download from git, some of the extensions may actually be for the 3.1 version of Gnome Shell and may not work with the 3.0 version in the PPA. So the extensions repository isn't very usable yet, but it's a wonder in some ways it exists at all with how certain other parts of the Gnome 3 desktop are locking down (System Settings, for one).

Can't speak for all of them but it's usually just a simple edit to adjust the version number in the metadata.json

---

### Post by philnice on 2011-05-17
> **macozz said:**
> Probably I had a mix of Evolution 2.xx and 3.0 packages.
Exactly what i thought. Glad you solve it.

---

### Post by pikamoku on 2011-05-18
> **jbicha said:**
> Gnome Shell extensions are a bit disorganized at the moment. If you download from git, some of the extensions may actually be for the 3.1 version of Gnome Shell and may not work with the 3.0 version in the PPA. So the extensions repository isn't very usable yet, but it's a wonder in some ways it exists at all with how certain other parts of the Gnome 3 desktop are locking down (System Settings, for one).

so far we have gnome-shell from gnome3-PPA(3.0)  and extensions (some for 3.1) from GIT repository, any chance of gnome3 team to include in the PPA some/any of the extensions?

I'm quite pleased with gnome-shell but I gave up to install any extension on 64bit laptop, cant even make work properly the user-theme extension

---

### Post by cbowman57 on 2011-05-18
> **pikamoku said:**
> so far we have gnome-shell from gnome3-PPA(3.0)  and extensions (some for 3.1) from GIT repository, any chance of gnome3 team to include in the PPA some/any of the extensions?

I'm quite pleased with gnome-shell but I gave up to install any extension on 64bit laptop, cant even make work properly the user-theme extension

This should fix you up.

[Link to gnome-shell-extensions-user-theme converted from .rpm to .deb]("http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gnome-shell-extensions-user-theme^_3.0.0-6.6^_all.deb")

---

### Post by slooksterpsv on 2011-05-18
> **pikamoku said:**
> so far we have gnome-shell from gnome3-PPA(3.0)  and extensions (some for 3.1) from GIT repository, any chance of gnome3 team to include in the PPA some/any of the extensions?

I'm quite pleased with gnome-shell but I gave up to install any extension on 64bit laptop, cant even make work properly the user-theme extension

You can hit up the gnome-team, contact someone on the PPA and see.

64-bit here too, didn't care for the extensions just yet. I don't like how you program them/test them out. Not very functional just yet.

---

### Post by pikamoku on 2011-05-18
> **slooksterpsv said:**
> ......

64-bit here too, didn't care for the extensions just yet. ....
 +1 but some of them could be useful

thanks **cbowman57**, I'll take a look at that ;)

---

### Post by cbowman57 on 2011-05-18
> **pikamoku said:**
> +1 but some of them could be useful

thanks **cbowman57**, I'll take a look at that ;)

If you install it with software center it will complain but it does work.  Gdebi will pop it in without complaint.

---

### Post by Dobbie03 on 2011-05-18
Does everyone else's network connections look as ugly as mine?
[http://i.imgur.com/NqYAQ.jpg](http://i.imgur.com/NqYAQ.jpg)

---

### Post by slooksterpsv on 2011-05-18
> **Dobbie03 said:**
> Does everyone else's network connections look as ugly as mine?
[http://i.imgur.com/NqYAQ.jpg](http://i.imgur.com/NqYAQ.jpg)

Yes mine does =D I kind of like the Black on White for that, seems more crucial to know what's in there.

---

### Post by bmbaker on 2011-05-18
if you add the testing ppa and the staging ppa [https://launchpad.net/~ricotz]("https://launchpad.net/%7Ericotz") you'll get an update for the network manager, just remember though it experimental, though i have it wking fine on my laptop.

---

### Post by ojdon on 2011-05-18
Everything is working for me, it's absolutely beautiful on my Viewpad 10. The only issue I'm having is that it refuses to automatically login no matter what options I set. So I have to grab a USB Keyboard in order to type my password in since the virtual keyboard "Florence" only starts **after** I log in.

Any help?

---

### Post by pikamoku on 2011-05-18
I was asking myself the same thing, how to auto-log on startup screen?

thanks cbowman57, your script (.deb) works fine ;)

---

### Post by ZekeGraal on 2011-05-18
Seeing this was updated, I will go for this again. Running 11.04.

```
sudo add-apt-repository ppa:gnome3-team/gnome3 sudo apt-get update sudo apt-get dist-upgrade sudo apt-get install gnome-shell gnome-session sudo apt-get -f install sudo apt-get install gnome-shell sudo apt-get install gnome-session
```and
```
sudo apt-get remove gnome-accessibility-themes sudo apt-get install gnome-themes-standard sudo apt-get install -f
```
These *should* work, correct? I just figured I'd ask because I don't feel like installing natty again, (after breaking it before), lol

---

### Post by cbowman57 on 2011-05-18
> **pikamoku said:**
> I was asking myself the same thing, how to auto-log on startup screen?

thanks cbowman57, your script (.deb) works fine ;)

Excellent, then you have some theme support now?  ;)

---

### Post by ojdon on 2011-05-18
When I installed Gnome-Shell last night, I never ran: 
>  sudo apt-get install gnome-session
Should I still do this even though everything seems fine.

Doubt that would resolve my problem about not being able to log in?

---

### Post by slooksterpsv on 2011-05-18
> **ojdon said:**
> When I installed Gnome-Shell last night, I never ran: 

Should I still do this even though everything seems fine.

Doubt that would resolve my problem about not being able to log in?

It will resolve your issue to login, but if everythings working just fine it's installed.

Last time I did a reformat and install (2 days ago) I had to do: sudo apt-get install gnome-session - 2 times before it installed, same with gnome-shell.

Dunno why, but I did.

---

### Post by ojdon on 2011-05-18
Hmmm... It's still not wanting to log in. That's the last issue I have. =\

---

### Post by philnice on 2011-05-18
> **ZekeGraal said:**
> Seeing this was updated, I will go for this again. Running 11.04.

```
sudo add-apt-repository ppa:gnome3-team/gnome3 sudo apt-get update sudo apt-get dist-upgrade sudo apt-get install gnome-shell gnome-session sudo apt-get -f install sudo apt-get install gnome-shell sudo apt-get install gnome-session
```and
```
sudo apt-get remove gnome-accessibility-themes sudo apt-get install gnome-themes-standard sudo apt-get install -f
```
These *should* work, correct? I just figured I'd ask because I don't feel like installing natty again, (after breaking it before), lol
Yes they should work. Terminal is your best friend there to watch the upgrade procedure, and take action whenever is needed.
Also, you could install your experimental copy on a separate partition to avoid risking your main system or, use tools like remastersys to clone your system so you can go back at any time without pain.

---

### Post by ZekeGraal on 2011-05-18
> **philnice said:**
> 
Also, you could** install your experimental copy on a separate partition** to avoid risking your main system or, use tools like remastersys to clone your system so you can go back at any time without pain.
I think I'll do that, I have my live sd card right here :D

---

### Post by philnice on 2011-05-18
> **ZekeGraal said:**
> I think I'll do that, I have my live sd card right here :D
Smart thinking, enjoy testing! ;)

---

### Post by Dobbie03 on 2011-05-19
> **bmbaker said:**
> if you add the testing ppa and the staging ppa [https://launchpad.net/~ricotz]("https://launchpad.net/%7Ericotz") you'll get an update for the network manager, just remember though it experimental, though i have it wking fine on my laptop.

Will that mess up the official Gnome3 and UGR PPA though?

---

### Post by bmbaker on 2011-05-19
> **Dobbie03 said:**
> Will that mess up the official Gnome3 and UGR PPA though?
it won't mess up the the gnome3 ppa and from what i have understood it shouldn't mess up UGr either.

another solution is to add the testing ppa and do update dist-upgrade and then manually add wpasupplicant deb

[HTML] https://launchpad.net/~ricotz/+archive/staging/+files/wpasupplicant_0.7.3-3%7E11.04%7Ericotz0_i386.deb[/HTML]

---

### Post by Dobbie03 on 2011-05-19
> **bmbaker said:**
> it won't mess up the the gnome3 ppa and from what i have understood it shouldn't mess up UGr either.

another solution is to add the testing ppa and do update dist-upgrade and then manually add wpasupplicant deb

[HTML] https://launchpad.net/~ricotz/+archive/staging/+files/wpasupplicant_0.7.3-3%7E11.04%7Ericotz0_i386.deb[/HTML]

Just in case this does mess up my system is this reversible?

---

### Post by slooksterpsv on 2011-05-19
> **Dobbie03 said:**
> Just in case this does mess up my system is this reversible?

You can always reverse it by removing the PPA and doing:

sudo apt-get dist-upgrade

It'll revert back to the packages like Unity or that.

---

### Post by cbowman57 on 2011-05-19
Don't overlook our friend, Clonezilla. :)

---

### Post by slooksterpsv on 2011-05-19
Anyone having an issue with opening some applications you install such as games should run this command (under each user account that logs into the computer):

```

echo "PATH=\"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\"" | tee -a ~/.profile

```

EDIT: Added on Post #1

---

### Post by copernic2006 on 2011-05-19
> **bmbaker said:**
> I just was trying out gnome tweak for changing the gtk-3 themes and i get this with everything except the default adwaita gtk-3 anyone got any ideas why this is happening?
 I tried re-installing mutter but no joy!
([http://ubuntuforums.org/showpost.php?p=10826455&postcount=217](http://ubuntuforums.org/showpost.php?p=10826455&postcount=217))

Good evening
I have the same problem with themes gtk3, Have you solved the problem?
Thank you for your help.

---

### Post by cbowman57 on 2011-05-19
> **copernic2006 said:**
> Good evening
I have the same problem with themes gtk3, Have you solved the problem?
Thank you for your help.

I haven't, but if you're just wanting a dark GTK3 theme, Adwaita has one, you just have to rename gtk-dark.css to gtk.css

---

### Post by copernic2006 on 2011-05-19
Thank a Lot :D
That's exactly what I want: A dark theme

---

### Post by cbowman57 on 2011-05-19
> **copernic2006 said:**
> Thank a Lot :D
That's exactly what I want: A dark theme

Yeah, that's Atolm shell, Adwaita dark GTK3, iNdentured-outine metacity, Aw0ken icon theme.

---

### Post by copernic2006 on 2011-05-19
I love this theme, I'm not ready to let go ;)

---

### Post by ojdon on 2011-05-19
I still want to log in automatically. :(

---

### Post by macozz on 2011-05-19
Some one knows how to get the Empathy integration with Gnome3? I have seen screenshots in which the notifications and messages popup from the bottom of the screen, but that do not occur here.
Any ideas?

Cheers!

---

### Post by 23dornot23d on 2011-05-19
You can still log in automatically .... 

Menu >>> Administration  >>> Users and Groups .... 
( you need to be enter root password when asked )

Choose Automatic login .....  for the user ..... then you have to re-boot.

if you are using gdm ....

---

### Post by ojdon on 2011-05-19
I've tried that but it doesn't seem to work for some reason... =\

---

### Post by cbowman57 on 2011-05-19
> **macozz said:**
> Some one knows how to get the Empathy integration with Gnome3? I have seen screenshots in which the notifications and messages popup from the bottom of the screen, but that do not occur here.
Any ideas?

Cheers!

Do you have empathy set for notifications in preferences > general?

---

### Post by cbowman57 on 2011-05-19
> **23dornot23d said:**
> You can still log in automatically .... 

Menu >>> Administration  >>> Users and Groups .... 
( you need to be enter root password when asked )

Choose Automatic login .....  for the user ..... then you have to re-boot.

if you are using gdm ....

Yeah, never worked for me either.

---

### Post by Dobbie03 on 2011-05-20
> **slooksterpsv said:**
> You can always reverse it by removing the PPA and doing:

sudo apt-get dist-upgrade

It'll revert back to the packages like Unity or that.

Thanks!

---

### Post by Xantheil on 2011-05-20
Reinstalling gnome 3 now..

I loved it, when I had it, but I was really tired to people telling me that I'll love Unity if I try it for a month with a open mind. And yet, here I am!

Anyway, I was wondering. Is there any way to install other applications which have been ported to gtk-3? (There are some, right?) I believe Rhythumbox is gtk-3, and so must be some other applications. So, How Do I Install Them? (even if I have ton compile oO)

---

### Post by macozz on 2011-05-20
> **cbowman57 said:**
> Do you have empathy set for notifications in preferences > general?

Yes, I do that, but nothing happens...

---

### Post by cbowman57 on 2011-05-20
> **macozz said:**
> Yes, I do that, but nothing happens...

And the Notification tab in preferences is set to Enable bubble notifications?  If so then it's a bug somewhere.  I know I had a period yesterday between updates where I was getting NotifyOSD type bubbles instead of the bottom panel, but an update cured it here.

---

### Post by Dobbie03 on 2011-05-20
I just installed the Gnome Shell extensions and restarted GS with alt-f2 then "r".

GS crashed and asked me to log out, now the only user option I have to log in with is "other".  The login dialog box has my user at the top but if I enter my details it just hangs and wont log in.

Anyone else encountered this?  What can I do?

---

### Post by cbowman57 on 2011-05-20
> **Dobbie03 said:**
> I just installed the Gnome Shell extensions and restarted GS with alt-f2 then "r".

GS crashed and asked me to log out, now the only user option I have to log in with is "other".  The login dialog box has my user at the top but if I enter my details it just hangs and wont log in.

Anyone else encountered this?  What can I do?

Login through the recovery console, navigate (I just bring up nautilus) to your extensions, compress the extensions directory by directory, then delete the directories.  Log back in and extract/test each extension until you find the one that is problematic.  Repairing/editing the extensions is something for another post. :)

---

### Post by macozz on 2011-05-20
> **cbowman57 said:**
> And the Notification tab in preferences is set to Enable bubble notifications?  If so then it's a bug somewhere.  I know I had a period yesterday between updates where I was getting NotifyOSD type bubbles instead of the bottom panel, but an update cured it here.

Yes, this was set to enable bubbles... I had a large upgrade today. Let's see if fix this.

Thanks!

---

### Post by jjcv on 2011-05-20
> **Dobbie03 said:**
> I just installed the Gnome Shell extensions and restarted GS with alt-f2 then "r".

GS crashed and asked me to log out, now the only user option I have to log in with is "other".  The login dialog box has my user at the top but if I enter my details it just hangs and wont log in.

Anyone else encountered this?  What can I do?

I have this most of the time.  What I do when the login freezes is do an Ctrl-Alt-F1, login and then do "sudo /etc/init.d/gdm restart"

This will restart GDM and usually allow you in.  I notice that GDM thinks I am already logged in when I do this.

Hope this helps.

---

### Post by omskates on 2011-05-21
I had installed xubuntu 11.04 for the explicit reason of installing Gnome3 with as few conflicts as possible.  After Xubuntu install and full update I did add ppa and only installed gnome-shell without dist-upgrade.  No issues until update manager requested a dist-upgrade and then I had the launching new apps issue as mentioned in this thread & added to page 1.  The 'echo fix' on page one resolved it.  Thankyou:D

---

### Post by afraca on 2011-05-22
Hi guys, 

Because of a bcm4311 wifi bug in the kernel included in Natty I upgraded 10.10, which went suprisingly well. After thoroughly reading this topic I thought I'd give it a shot, which didn't went so well. Everything installed fine (with some apt-get -f install ) , but GDM just gives me the finger. GDM offers me only "other" , and when I give my username and password it hangs. I installed no extensions whatsoever. The suggestion to restart GDM by jjcv didn't help. Suggestions?

---

### Post by philnice on 2011-05-22
> **afraca said:**
> Hi guys, 

Because of a bcm4311 wifi bug in the kernel included in Natty I upgraded 10.10, which went suprisingly well. After thoroughly reading this topic I thought I'd give it a shot, which didn't went so well. Everything installed fine (with some apt-get -f install ) , but GDM just gives me the finger. GDM offers me only "other" , and when I give my username and password it hangs. I installed no extensions whatsoever. The suggestion to restart GDM by jjcv didn't help. Suggestions?
Try sudo dpkg-reconfigure gdm and then reboot.

---

### Post by afraca on 2011-05-22
Thanks for the quick reply philnice, but too bad it didn't make any difference.

---

### Post by philnice on 2011-05-22
> **afraca said:**
> Thanks for the quick reply philnice, but too bad it didn't make any difference.
I assume you don't have any other display manager installed to try. 
Since we tried anything else, perhaps open synaptic and remove gdm and then re-install, would help..? Can't think of anything else right now sorry.

---

### Post by rezonatix3 on 2011-05-22
Has anyone got [autologin](http://ubuntuforums.org/showthread.php?t=1745454) to work yet?

---

### Post by maverick280857 on 2011-05-22
A few notes for those doing a fresh install of Natty, and trying to install Gnome3. When you start Natty for the first time, you are likely to get an error message stating that you don't have the hardware required for Unity.

1. If you have an NVIDIA/ATI graphics card, there are accelerated drivers available. Install them and reboot the system into Unity. **Get Unity to work first**. The accelerated drivers are available from Administration-->Additional Drivers. On my system, before these drivers were installed I was unable to switch to console mode using Ctrl+Alt+F1. I needed the console mode for step 2 (see below).

2. Next, install the NVIDIA (or ATI) drivers from the manufacturer (this is optional -- I prefer to use NVIDIA drivers for my GTX 295 and GT435M because I use CUDA, and the default drivers don't have support for CUDA). Reboot your computer. Hopefully you should see Unity work.

3. *Now*, follow the instructions in the first post of this thread.

---

### Post by slooksterpsv on 2011-05-22
> **maverick280857 said:**
> A few notes for those doing a fresh install of Natty, and trying to install Gnome3. When you start Natty for the first time, you are likely to get an error message stating that you don't have the hardware required for Unity.

1. If you have an NVIDIA/ATI graphics card, there are accelerated drivers available. Install them and reboot the system into Unity. **Get Unity to work first**. The accelerated drivers are available from Administration-->Additional Drivers. On my system, before these drivers were installed I was unable to switch to console mode using Ctrl+Alt+F1. I needed the console mode for step 2 (see below).

2. Next, install the NVIDIA (or ATI) drivers from the manufacturer (this is optional -- I prefer to use NVIDIA drivers for my GTX 295 and GT435M because I use CUDA, and the default drivers don't have support for CUDA). Reboot your computer. Hopefully you should see Unity work.

3. *Now*, follow the instructions in the first post of this thread.

You have NVidia, I'd like to see if someone can do this with ATI cause when I tried with my Radeon HD 4200, I rebooted into Gnome 3 (previously having Unity and the ATI Drivers) it was all glitched and artifacted. I was able to fix a piece (not all of it) by enabling Tearing in the ATI Catalyst Configuration. But it was still too glitchy.

If someone can verify that this works for them (need 2 people for nvidia, and 2 people for ati) I'll update it on the first page.

---

### Post by philnice on 2011-05-23
> **slooksterpsv said:**
> You have NVidia, I'd like to see if someone can do this with ATI cause when I tried with my Radeon HD 4200, I rebooted into Gnome 3 (previously having Unity and the ATI Drivers) it was all glitched and artifacted. I was able to fix a piece (not all of it) by enabling Tearing in the ATI Catalyst Configuration. But it was still too glitchy.

If someone can verify that this works for them (need 2 people for nvidia, and 2 people for ati) I'll update it on the first page.
Unfortunately, ATI seems to fail big time on unity and gnome 3 at the moment. I can only verify the problems you mentioned and even some more, which got me back using maverick.
But, i want to see too, other entries from ATI users, positive or, negative, to have a big picture of it although, i'm quite sure of what the result should be...

---

### Post by maverick280857 on 2011-05-23
> **philnice said:**
> Unfortunately, ATI seems to fail big time on unity and gnome 3 at the moment. I can only verify the problems you mentioned and even some more, which got me back using maverick.
But, i want to see too, other entries from ATI users, positive or, negative, to have a big picture of it although, i'm quite sure of what the result should be...

I realise I may have jumped the gun generalising to ATI. But for NVIDIA cards, I am (now) quite sure that it is better to install the additional drivers, the proprietary drivers in that order and get Unity to work before Gnome3.

---

### Post by philnice on 2011-05-23
> **maverick280857 said:**
> I realise I may have jumped the gun generalising to ATI. But for NVIDIA cards, I am (now) quite sure that it is better to install the additional drivers, the proprietary drivers in that order and get Unity to work before Gnome3.
Yea Ati got many problems. There are enough threads in here at the moment mentioning this. Time will show about that.
Nvidia, just doing good.

---

### Post by ZekeGraal on 2011-05-23
Just installed today, I love it. Thanks for the awesome guide! :D

Edit: It's running great! I'm on a netbook too: Acer Aspire One D250 w/ Intel Atom Processor @ 1.60GHz and 2.0 GiB of ram. (The ram is a chip I bought, I doubt it would run as smoothly on the stock 1 GiB one, lol)

---

### Post by dane1986 on 2011-05-23
Hi I have installed a fresh ubuntu 11.04 using the  guidelines in this thread. Installed updates and third party drivers (nVidia graphics card) without any problems. 

Using the guidelines in this thread I have installed gnome 3, however now the option at login is 'other', and the same as the previous posts with this problem it just hangs when I try to login. I have tried all the suggested fixes;
$ sudo dpkg-reconfigure gdm
$ sudo /etc/init.d/gdm restart
purging and reinstalling gdm and gnome power manager, and upgrading packages in synaptic, but still to no luck.

Does anyone have any more ideas as to what may be wrong with my system? Thanks, Dane.

---

### Post by maverick280857 on 2011-05-24
> **dane1986 said:**
> Hi I have installed a fresh ubuntu 11.04 using the  guidelines in this thread. Installed updates and third party drivers (nVidia graphics card) without any problems. 

Using the guidelines in this thread I have installed gnome 3, however now the option at login is 'other', and the same as the previous posts with this problem it just hangs when I try to login. I have tried all the suggested fixes;
$ sudo dpkg-reconfigure gdm
$ sudo /etc/init.d/gdm restart
purging and reinstalling gdm and gnome power manager, and upgrading packages in synaptic, but still to no luck.

Does anyone have any more ideas as to what may be wrong with my system? Thanks, Dane.

Did you reboot after installing the third party nvidia drivers, *before* installing gnome3? Did Unity work? Or were you at least able to log into X Windows using gdm?

---

### Post by dane1986 on 2011-05-24
Yes I did reboot after installing the nVidia drivers and Unity started without any problems. I then ran the system update rebooted and then installed gnome 3. Dane.

---

### Post by dane1986 on 2011-05-24
I should also add that I have installed 11.04 with gnome 3 sucessfully about 1 month ago now, using the same procedure. So it is capable of running on my system. Dane.

---

### Post by maverick280857 on 2011-05-24
> **dane1986 said:**
> I should also add that I have installed 11.04 with gnome 3 sucessfully about 1 month ago now, using the same procedure. So it is capable of running on my system. Dane.

So are you re-installing it now?

---

### Post by dane1986 on 2011-05-24
Yes, I have been trying to reinstall it. I've tried 4 times, and it is the same result each time, as above. So now I'm trying to resolve the problem as a fresh install doesn't seem to solve it. Dane

---

### Post by maverick280857 on 2011-05-24
> **dane1986 said:**
> Yes, I have been trying to reinstall it. I've tried 4 times, and it is the same result each time, as above. So now I'm trying to resolve the problem as a fresh install doesn't seem to solve it. Dane

Doing a fresh install is the best. This is what I would suggest:

**Step 1**. Install Ubuntu cleanly after formatting your drive (don't choose to 'keep' the old ubuntu). 

**Step 2**. Run

```
sudo apt-get update
sudo apt-get upgrade

```

right after install.

**Step 3** (**OPTIONAL**): Get rid of network manager, and use wicd -- this is to deal with the possibility of losing network access in one of the intermediate steps below, if network-manager crashes, and also to maintain a link in the text mode which you'll likely need.

```

sudo apt-get install wicd wicd-gtk
sudo apt-get remove network manager
sudo reboot

```

(Don't get rid of network-manager first! Otherwise, you won't be able to get wicd).

**Step 4**. Install the 'additional drivers' that Ubuntu allows you to get for the nvidia card you have. Reboot. You should be able to boot into Unity now. If not, post here -- something else is wrong with  your configuration.

**Step 5**. Now, follow the steps in the very first post of this thread, which is here: [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1). Pay special attention to the installation of gnome-shell and gnome-session - the post has been updated to deal with some problems people were facing.

In short, don't be in a hurry to install Gnome3 on your system. Don't do it right after you install Natty. First even out the corners and get things to work.

If something gets screwed up in the process, you should boot from your Ubuntu Live CD/DVD and follow the procedure below to mount your existing linux installation, and repair it

**Step 1**: Boot from the Live CD/DVD and select 'Try Ubuntu'.

**Step 2**: Connect to the wireless/wired network if necessary (i.e. if you think you'll have to download updates or other stuff).

**Step 3**: Start the gparted partition manager **only** to figure out which drive your linux installation is on. Close gparted.  I am going to assume that it is /dev/sda5 in whatever follows. 

**Step 4**: Launch a terminal window and type the following commands to mount your existing linux installation

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

```

Now change root to the mounted system (so that / now refers to *your* linux installation and not the live cd).

```
sudo chroot /mnt
```

This effectively starts a new shell session inside your freshly mounted linux installation. Note that everything you do now will affect your linux installation and will be permanent!

**Step 5**: Perform repair tasks (whatever you need to do).

**Step 6**: Exit the shell started in step 4 using

```
exit
```

**Step 7**: Unmount everything using

```

sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt

```

(The last command should be issued only after everything else has been unmounted).

**Step 8**: Hopefully everything has been fixed now, so you should reboot using

```
sudo reboot
```

(and of course, remove the Live CD/DVD).

---

### Post by dane1986 on 2011-05-24
Thank you very much for the post, I may have to wait a few days so I can do it all in one go. I will let you know how I go. Thanks, Dane.

---

### Post by maverick280857 on 2011-05-24
> **dane1986 said:**
> Thank you very much for the post, I may have to wait a few days so I can do it all in one go. I will let you know how I go. Thanks, Dane.

Most of my post pertains to the 'rescue act' which hopefully you *won't* have to do. For a fresh install, you can ignore that.

Anyway I hope it works...I am re-installing Ubuntu on my desktop (which has a GTX 295) and will make a note of any deviations I am forced to make, to get Gnome 3 to work.

---

### Post by amites on 2011-05-24
Tried installing gnome 3 yesterday was able to install and see that the new interface borrows heavily from Mac OSX :P

that said I ran into a new kind of problem that I haven't seen documented anywhere

the windows would not refresh until I switched to a different active window

ie: I would open a terminal window and a chromium browser window
I would type something into terminal - the window would appear to be frozen until I switched the active window to the chromium window at which point it would update the terminal window once - so if I were to run an apt-get install
I would have to switch windows several times to see the progress
this happened with all programs that I tried running

everything else ran smoothly - could pull up the new menu rather quickly

since I made the mistake of installing this on my primary laptop I ended up re-installing 11.04 and run Gnome 2 (Ubuntu classic) for the time being

for reference:
HP Elitebook 8740w
2.6 Intel Dual Core i7
4GB DDR3 RAM
Nvidia Quadro w/ 1GB 


this one had me stumped though it seemed like a config issue?

---

### Post by 23dornot23d on 2011-05-24
> 
Tried installing gnome 3 yesterday was able to install and see that the new interface borrows heavily from Mac OSX :razz:


Can you post a screenshot of what it looks like please ......

---

### Post by cbowman57 on 2011-05-24
Sounds like a video driver issue, or possibly a version mismatch.

---

### Post by mercurycc on 2011-05-25
After all the failures and pain trying to get rid of Unity and replace it with GNOME 3 in Ubuntu, I gave up.  The best way to get a great GNOME 3 desktop is to switch your distribution to Fedora.  Fedora 15 has native GNOME 3 support.

Trust me.  Fedora isn't that much more difficult to use.

---

### Post by maverick280857 on 2011-05-25
> **mercurycc said:**
> The best way to get a great GNOME 3 desktop is to switch your distribution to Fedora.  Fedora 15 has native GNOME 3 support.

Well, that sort of kills the fun of configuring Gnome 3 yourself ;-). I think most of us here who got it to work managed only after 2 or 3 attempts, so its definitely not perfect.

Before Maverick Meerkat, I used Fedora as my primary distribution. I don't have any reason why I switched to Ubuntu other than the fact that I prefer to install everything from the ground-up by hand and Ubuntu comes very light weight. Anyway, this is relatively trivial.

---

### Post by Dronar on 2011-05-25
> **amites said:**
> Tried installing gnome 3 yesterday was able to install and see that the new interface borrows heavily from Mac OSX :P

that said I ran into a new kind of problem that I haven't seen documented anywhere

the windows would not refresh until I switched to a different active window

ie: I would open a terminal window and a chromium browser window
I would type something into terminal - the window would appear to be frozen until I switched the active window to the chromium window at which point it would update the terminal window once - so if I were to run an apt-get install
I would have to switch windows several times to see the progress
this happened with all programs that I tried running

everything else ran smoothly - could pull up the new menu rather quickly

since I made the mistake of installing this on my primary laptop I ended up re-installing 11.04 and run Gnome 2 (Ubuntu classic) for the time being

for reference:
HP Elitebook 8740w
2.6 Intel Dual Core i7
4GB DDR3 RAM
Nvidia Quadro w/ 1GB 


this one had me stumped though it seemed like a config issue?


I had the exact same problem earlier, now it's worse... When I login the GUI just freezes. The mouse cursor is still active, but everything else is stopped.
I've heard rumors that this is related to the nVidia-drivers but I am not 100% sure yet.

I'm actually running xfce now just to be able to use my laptop :/

---

### Post by 23dornot23d on 2011-05-25
> **Dronar said:**
> I had the exact same problem earlier, now it's worse... When I login the GUI just freezes. The mouse cursor is still active, but everything else is stopped.
I've heard rumors that this is related to the nVidia-drivers but I am not 100% sure yet.

I'm actually running xfce now just to be able to use my laptop :/

Which graphics card do you have and what laptop is it please ?

---

### Post by cbowman57 on 2011-05-25
> **23dornot23d said:**
> Which graphics card do you have and what laptop is it please ?

Saw something in passing, maybe you know something about it, it is called Beehive I think.  Does something for laptops that have both intel & nvidia graphics.  You know anything about that?

---

### Post by 23dornot23d on 2011-05-25
> **cbowman57 said:**
> Saw something in passing, maybe you know something about it, it is called Beehive I think.  Does something for laptops that have both intel & nvidia graphics.  You know anything about that?

Not seen that one ...... but there was a video on graphics switching ..... when laptops had
the dual graphics cards in them ..... Intel / Nvidia ..... seems there are a few people having 
problems with the computer being able to switch cards (there is a launchpad bug open on this too) ..... 

Someone wrote a program to make sure that for Linux .... the USER has the choice .... 
rather than the computer deciding which graphics card to use .......

Will see if I can find it ....

---

### Post by cbowman57 on 2011-05-25
I don't use a laptop but I wonder if that would solve the problem for some people.

---

### Post by 23dornot23d on 2011-05-25
Found this  **[LINK]("http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html")** ..... after you mentioned beehive .... its bumblebee

---

### Post by cbowman57 on 2011-05-25
Maybe it will help somebody out.

---

### Post by karmila on 2011-05-25
Is there any tutorial for installing gnome-shell and gtk-3 theme?

I found some but i don't know which one is updated and safe metode.

Edit: Nevermind, got it :D

---

### Post by bmbaker on 2011-05-25
has anyone been having problems with the gtk3 themes ?
see screenshots, most of them seem to have gone really funny looking !!!

---

### Post by cbowman57 on 2011-05-25
> **bmbaker said:**
> has anyone been having problems with the gtk3 themes ?
see screenshots, most of them seem to have gone really funny looking !!!

Yes, that has been a problem for a couple weeks now.  Not a fix, but if you want a dark gtk3 theme Adwaita actually has one built in, just rename gtk-dark.css to gtk.css

---

### Post by bmbaker on 2011-05-25
> **cbowman57 said:**
> Yes, that has been a problem for a couple weeks now.  Not a fix, but if you want a dark gtk3 theme Adwaita actually has one built in, just rename gtk-dark.css to gtk.css
nice :-)
thought it was just me !!
on another note, after yesterdays updates, you can now log into unity without any crashes, was just testing it and it seems ok.
of course i am sticking with gnome-shell but its nice to have another option :-)

---

### Post by bmbaker on 2011-05-25
another artist has made a nice theme:-)
[http://ubuntuforums.org/showthread.php?t=1767287&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1767287&highlight=gnome-shell)

---

### Post by cbowman57 on 2011-05-25
> **bmbaker said:**
> nice :-)
thought it was just me !!
on another note, after yesterdays updates, you can now log into unity without any crashes, was just testing it and it seems ok.
of course i am sticking with gnome-shell but its nice to have another option :-)

Yes, options are nice. :)

---

### Post by 23dornot23d on 2011-05-25
This thread may help ..... [**LINK**]("http://ubuntuforums.org/showthread.php?t=1754198&page=78") ....  just in case people wonder where it went ...... :confused:

( luckily the administrators left the **[COLOR=Red]problems[/COLOR]** here ..... but the one thing that can get people to start from a common
base with very few problems they moved ....... sometimes you have to ask the question .... why is that then .... ? )

Its good to sort problems out that we have bypassed ..... fills our days with endless repeats of things already solved .....

Keep moving things out of here ... please ...... why is this page in desktop environments ..... 

UNITY is the one ....... not Gnome-Shell ..... as Gnome-Shell .......  is another OS apparently ......

Where is Sef when you need her - this one has had 27,000 views ..... is it not about time to move it ....

The other one was only realised after 11,000 views that it was in the wrong place ....... oh well ....

Problems are one thing solutions are another .......

---

### Post by cbowman57 on 2011-05-25
> **23dornot23d said:**
> 

UNITY is the one ....... not Gnome-Shell ..... as Gnome-Shell .......  is another OS apparently ......

Apparently :lol:

---

### Post by magneze on 2011-05-26
```
Preparing to replace gnome-session 3.0.1-0ubuntu1~build2 (using .../gnome-session_3.0.2-0ubuntu3~natty1_all.deb) ...
Unpacking replacement gnome-session ...
dpkg: error processing /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/xsessions/gnome-shell.desktop', which is also in package gnome-shell 3.0.1-0ubuntu1~build1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Anyone else been getting this error recently?

---

### Post by maverick280857 on 2011-05-26
> **magneze said:**
> ```
Preparing to replace gnome-session 3.0.1-0ubuntu1~build2 (using .../gnome-session_3.0.2-0ubuntu3~natty1_all.deb) ...
Unpacking replacement gnome-session ...
dpkg: error processing /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/xsessions/gnome-shell.desktop', which is also in package gnome-shell 3.0.1-0ubuntu1~build1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Anyone else been getting this error recently?

While trying to install and subsequently uninstall libxmu6 for NVIDIA CUDA on my desktop (the 2nd system I use Ubuntu 11.04 on) I think I got this error, and some updates seemed to have wiped out gnome3 altogether. Now I cannot boot into anything other than a console. This is the 4th time I am going to have to do a fresh install of Ubuntu 11.04.

By the way, it seems if you have a crashed gnome3 installation, re-installing it on top of the old one using the info mentioned on the first thread, does not solve the problem. Or am I wrong?

---

### Post by bmbaker on 2011-05-26
> **maverick280857 said:**
> While trying to install and subsequently uninstall libxmu6 for NVIDIA CUDA on my desktop (the 2nd system I use Ubuntu 11.04 on) I think I got this error, and some updates seemed to have wiped out gnome3 altogether. Now I cannot boot into anything other than a console. This is the 4th time I am going to have to do a fresh install of Ubuntu 11.04.

By the way, it seems if you have a crashed gnome3 installation, re-installing it on top of the old one using the info mentioned on the first thread, does not solve the problem. Or am I wrong?

try this it should wk just fine :-)
```

sudo dpkg -i /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
```

and if you haven't already added it add the **ppa:ricotz/testing **

---

### Post by maverick280857 on 2011-05-26
> **bmbaker said:**
> try this it should wk just fine :-)
```

sudo dpkg -i /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
```

Thanks, I am going to try this now.

[QUOTE=bmbaker]and if you haven't already added it add the **ppa:ricotz/testing **[/QUOTE]

What is this for?

---

### Post by magneze on 2011-05-26
I fixed it using:

sudo apt-get -f dist-upgrade

---

### Post by maverick280857 on 2011-05-26
> **maverick280857 said:**
> Thanks, I am going to try this now.

This didn't help me. Apparently the libraries for cuda damaged gnome3 and nvidia-current irreparably. Funny, because the same configuration works just fine on my laptop.

---

### Post by bmbaker on 2011-05-26
> **maverick280857 said:**
> This didn't help me. Apparently the libraries for cuda damaged gnome3 and nvidia-current irreparably. Funny, because the same configuration works just fine on my laptop.
ya it sometimes happens that the graphics divers cause problems !
one of the post i was reading was saying that it is better to set everything up so it wking well in ubuntu classic first and then install the gnome-shell stuff!
I am sure that once the gnome-shell is fully integrated with ubuntu 11.10 that alot of these issues will disappear :-) 
In the mean time perhaps you should do a ppa-purge and log into classic and go from there !!

---

### Post by maverick280857 on 2011-05-26
> **bmbaker said:**
> one of the post i was reading was saying that it is better to set everything up so it wking well in ubuntu classic first and then install the gnome-shell stuff!

Haha, I think I said that [here]("http://ubuntuforums.org/showpost.php?p=10855699&postcount=291").

I should point out that I have two systems running Gnome3, one being a laptop and the other a desktop. The laptop is what I am using right now, and Gnome3 has been working very nicely for several days with CUDA support. The desktop is basically my test bed for now, and somehow I managed to screw up the CUDA installation when one of the in-built SDK files was not compiling due to missing libraries (an all too often problem with CUDA these days). So, it wasn't Gnome3 but one of the CUDA related library downgrades which did the damage.

Anyway, I just find it easier to do a fresh install when the graphics drivers really get mangled badly..

---

### Post by cbowman57 on 2011-05-26
> **bmbaker said:**
> try this it should wk just fine :-)
```

sudo dpkg -i /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
```

and if you haven't already added it add the **ppa:ricotz/testing **

So that worked for you?  Good, I forgot to add that I went in via synaptic & upgraded gnome-shell first, by itself, then the mass update.  Glad it worked. :)

---

### Post by maverick280857 on 2011-05-26
> **cbowman57 said:**
> So that worked for you?  Good, I forgot to add that I went in via synaptic & upgraded gnome-shell first, by itself, then the mass update.  Glad it worked. :)

If this was meant to 'fix' something that got messed up in gnome3/gnome-shell, it didn't work for me. But then my problem probably wasn't supposed to be fixed by this command.

PS -- Some things like ubuntu-restricted-extras, etc. work best if installed via the command line.

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> If this was meant to 'fix' something that got messed up in gnome3/gnome-shell, it didn't work for me. But then my problem probably wasn't supposed to be fixed by this command.

PS -- Some things like ubuntu-restricted-extras, etc. work best if installed via the command line.

I don't know what problem you were having, it was directed to bmbaker & a problem he was having the other day.

---

### Post by bmbaker on 2011-05-26
> **maverick280857 said:**
> Haha, I think I said that [here]("http://ubuntuforums.org/showpost.php?p=10855699&postcount=291").

I should point out that I have two systems running Gnome3, one being a laptop and the other a desktop. The laptop is what I am using right now, and Gnome3 has been working very nicely for several days with CUDA support. The desktop is basically my test bed for now, and somehow I managed to screw up the CUDA installation when one of the in-built SDK files was not compiling due to missing libraries (an all too often problem with CUDA these days). So, it wasn't Gnome3 but one of the CUDA related library downgrades which did the damage.

Anyway, I just find it easier to do a fresh install when the graphics drivers really get mangled badly..

hmmm that could well be it :-) :-)

---

### Post by yrral86 on 2011-05-26
> **magneze said:**
> I fixed it using:

sudo apt-get -f dist-upgrade

Thanks, this did it for me.

---

### Post by JCSalomon on 2011-05-26
The package [FONT="Courier New"]gnome-icon-theme-extras[/FONT] have a dependency not only on [FONT="Courier New"]gnome-icon-theme >= 3.0[/FONT], but also on [FONT="Courier New"]gnome-icon-theme < 2.92[/FONT], making it impossible to install.

Also, my shiny new Gnome 3 session dissapeared from the list of available sessions after an update yesterday.  I’ll be re-installing [FONT="Courier New"]gnome-session[/FONT] and [FONT="Courier New"]gnome-shell[/FONT] to see if that helps any.

---

### Post by cbowman57 on 2011-05-26
> **JCSalomon said:**
> The package [FONT="Courier New"]gnome-icon-theme-extras[/FONT] have a dependency not only on [FONT="Courier New"]gnome-icon-theme >= 3.0[/FONT], but also on [FONT="Courier New"]gnome-icon-theme < 2.92[/FONT], making it impossible to install.

Also, my shiny new Gnome 3 session dissapeared from the list of available sessions after an update yesterday.  I’ll be re-installing [FONT="Courier New"]gnome-session[/FONT] and [FONT="Courier New"]gnome-shell[/FONT] to see if that helps any.

Did you already check to see if it was just renamed Gnome?  That's what happened here.

---

### Post by JCSalomon on 2011-05-26
> **cbowman57 said:**
> [QUOTE=JCSalomon;10866727]Also, my shiny new Gnome 3 session dissapeared from the list of available sessions after an update yesterday.Did you already check to see if it was just renamed Gnome?  That's what happened here.[/QUOTE]No, “Gnome” just shows what I believe is called “Gnome Classic”.> **JCSalomon said:**
> I’ll be re-installing [FONT="Courier New"]gnome-session[/FONT] and [FONT="Courier New"]gnome-shell[/FONT] to see if that helps any.And that helped not very much at all. :(

---

### Post by dane1986 on 2011-05-26
Hi I have followed the steps in post #291 to install gnome 3 and have encountered a different problem. Everything went well until I rebooted, and I get a desktop which is a mix of unity and gnome 3! Attached are some screen shots, it is a working desktop I can log in and out etc without any problems, the styles are a mix between the two desktops and the graphics seem to have a refresh problem (can be seen in the last picture). I have installed the two available nVidia graphics drivers and neither of them fix this problem. My only thought might be that unity has not been completely removed. Does anyone have any suggestions for a fix to this problem? Thanks, Dane.

---

### Post by maverick280857 on 2011-05-27
> **dane1986 said:**
> Everything went well until I rebooted, and I get a desktop which is a mix of unity and gnome 3! 

This is just Unity. Not Gnome Shell.

What are the options you see for the login-session on the drop down menu at the graphical log-in screen? If you pick Gnome, you should be taken to the Gnome Shell, and if you pick Ubuntu (which seems to be the default option on the first run), you'll be taken to Unity.

After you installed the restricted drivers and first round of updates **before** adding the Gnome3 ppa, did you reboot the system?

---

### Post by shafiee01 on 2011-05-27
Hi,
i have installed gnome3 on my natty and it was ok till i update it and after update:
after i login, gnome-shell doesnt start and if i statrt it manully with typing "gnome-shell --replace" in a terminal it works!!
then i tried to fix this by modifying Xsession files such as gnome.desktop and ...
sometimes it works and sometimes not!!
and sometime gnome 3 start but with out default them and with ugly appearance.
i am really tired of this...
and i dont want to reinstall it.
thanks

---

### Post by Dobbie03 on 2011-05-27
I just added the ricotz ppa and restarted GS and now I have horrible pink borders around all the buttons etc, how do I correct that?

---

### Post by bmbaker on 2011-05-27
> **Dobbie03 said:**
> I just added the ricotz ppa and restarted GS and now I have horrible pink borders around all the buttons etc, how do I correct that?
use the gnome tweak tool and set your interface to adwaita and choose your gtk3 theme from the windows tab.
then alt->f2-> r

there does seem to some sort of bug! but this works!

---

### Post by Dobbie03 on 2011-05-27
> **bmbaker said:**
> use the gnome tweak tool and set your interface to adwaita and choose your gtk3 theme from the windows tab.
then alt->f2-> r

there does seem to some sort of bug! but this works!

Sweet, that worked perfectly.  Now one last thing, how do I get my external hard drives to mount at login?

---

### Post by slooksterpsv on 2011-05-27
> **Dobbie03 said:**
> Sweet, that worked perfectly.  Now one last thing, how do I get my external hard drives to mount at login?

Add them to your FSTAB via pysdm found in the repos. Prob is you'll need to have them connected everytime you boot. Otherwise you could edit .profile and add the mount commands yourself.

---

### Post by maverick280857 on 2011-05-28
> **slooksterpsv said:**
> Add them to your FSTAB via pysdm found in the repos. Prob is you'll need to have them connected everytime you boot. Otherwise you could edit .profile and add the mount commands yourself.

The mount command returns an error message if a device is not present.

```

mount: can't find /dev/blah in /etc/fstab or /etc/mtab

```

It should be possible to exception-handle this, to make it work if the device(s) is(are) not connected at boot.

---

### Post by IanW on 2011-05-28
> **maverick280857 said:**
> The mount command returns an error message if a device is not present.

```

mount: can't find /dev/blah in /etc/fstab or /etc/mtab

```

It should be possible to exception-handle this, to make it work if the device(s) is(are) not connected at boot.

Try setting "nofail" as an option in /etc/fstab.

---

### Post by Dobbie03 on 2011-05-28
Thanks guys but in this situation I have no idea what I am doing, could someone give me some pointers please?

---

### Post by maverick280857 on 2011-05-28
> **Dobbie03 said:**
> Thanks guys but in this situation I have no idea what I am doing, could someone give me some pointers please?

You seem to want all your external drives to boot up when you log in, by themselves. To do this you need to add a line for each device you want to mount, in /etc/fstab. For a description of this file, what it contains and how you can edit it, click [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").

Plug in all your external drives, and from a terminal, post the output of

```
df
```

---

### Post by karmila on 2011-05-28
I'm using 3 ppas gnome3 related now:
1. gnome-3 ppa
2. ricotz ppa
3. ugr ppa

My problems so far:
1. I can not right click on desktop. Is this default behaviour?
2. I can not delete files on nautilus. Need to right-click and choose "move to Trash" to delete.
3. Whenever I press super button / go to activities my gnome-shell theme back to default.
4. Title bar won't use my selected gtk-3 theme. It keeps use adwaita theme but other parts is respect gtk-3 theme i used.
5. After last updates my network manager is broken. but luckily my mobile broadband has dialer for linux so I can use it easily, no need go to command line and setup wvdial.

Anyone know how to fix any of that problems?

---

### Post by karmila on 2011-05-28
Okay, the first problem is solved.
I only need to turn on "Have File Manager handle the desktop" from tweak-tool.

Still looking for other fix...

---

### Post by veroslav on 2011-05-28
I have the same problem regarding the broken network manager :(
I've just installed Gnome 3 according to the steps in the first post, but now I can't access my wireless Internet connection.
Also, the network manager looks weird, gnome-2-ish.

Does anybody has a clue of what might be the cause?

Also, I saw in one of the older posts that one should replace the network manager with something called like wcid or so, I didn't do this step, could this explain why my wireless is broken at the moment?

Other than that, Gnome 3 works fine, even though some of the graphical artifacts, such as menus, still have Clearlooks-look to them.

Thanks.

Kind Regards,
Veroslav

---

### Post by bmbaker on 2011-05-28
for all those that are still having problems with updates, esp the network manager stuff you need to have the testing ppa enabled :-)

```
sudo add-apt-repository ppa:ricotz/testing
```

after the update log out and log back in again and you will have this ..........

---

### Post by bmbaker on 2011-05-28
oh ya almost forgot! you can now get the gnome-extensions from the testing ppa :-)

---

### Post by veroslav on 2011-05-28
Hi,

I am trying to add the PPA through LIve CD, because I do not have access to the wireless at the moment. I am following the instructions on how to mount the Gnome 3 partition in Live CD but unfortunately when I run the above command, I get the following error:


root@ubuntu:/# sudo add-apt-repository ppa:ricotz/testing
sudo: unable to resolve host ubuntu
Error reading [https://launchpad.net/api/1.0/~ricotz/+archive/testing:]("https://launchpad.net/api/1.0/%7Ericotz/+archive/testing:") <urlopen error [Errno -2] Name or service not known>
root@ubuntu:/#

Do you know what might be the case?

Thanks.

Veoslav

---

### Post by cbowman57 on 2011-05-28
> **karmila said:**
> Okay, the first problem is solved.
I only need to turn on "Have File Manager handle the desktop" from tweak-tool.

Still looking for other fix...

File deletion is a nautilus option you set in preferences.

Do you have these network-manager files available in synaptic?  If so try and install those even if they have to be forced.

---

### Post by veroslav on 2011-05-28
Ok, I managed to resolve the wireless internet connection not being found, however, after I added and successfully installed the updates from ppa:ricotz/testing, even though I've got the new looking network manager, all of the options are invalid:

Wired invalid
Wireless invalid
Network Settings

When I open the Network Settings above, I get an error message that says:

The system network services are not compatible with this version

I also notice that there are two more packages left, available to install from ppa:ricotz/testing, but I can't select these in the Update Manager. The two packages are:

network managment framework (daemon and userspace tools)
network managment framework (GNOME frontend)

Does anybody knows what the cause is? Please, other than this small issue, everything works and looks so good! :)

Kind Regards,
Veroslav

---

### Post by cbowman57 on 2011-05-28
> **veroslav said:**
> Ok, I managed to resolve the wireless internet connection not being found, however, after I added and successfully installed the updates from ppa:ricotz/testing, even though I've got the new looking network manager, all of the options are invalid:

Wired invalid
Wireless invalid
Network Settings

When I open the Network Settings above, I get an error message that says:

The system network services are not compatible with this version

I also notice that there are two more packages left, available to install from ppa:ricotz/testing, but I can't select these in the Update Manager. The two packages are:

network managment framework (daemon and userspace tools)
network managment framework (GNOME frontend)

Does anybody knows what the cause is? Please, other than this small issue, everything works and looks so good! :)

Kind Regards,
Veroslav

These are the dependencies as shown in synaptic, you may also have to be sure and have the ubuntu proposed updates selected.

---

### Post by bmbaker on 2011-05-28
log into synaptic and try installing them from there and then do a full reboot :-9 should fix everything bicely :-)

---

### Post by veroslav on 2011-05-28
Thank you for your fast reply.

When looking in Synaptic, I notice that these two packages are already marked as installed, but also marked with a "gold star". What does this means?

When I right-click on them, I can choose "Mark for upgrade", is this something that might fix it? As I mentioned, I did install every package it offered me to install from the test PPA, these two are the only ones left.

Could you please tell me what the proposed respository contains?

Thanks again.

/Veroslav

---

### Post by veroslav on 2011-05-28
Hi bmbaker,

thank you for you reply. As I mentioned in my previous post, they do appear to have been installed, but are marked with a "golden star".

I can choose to upgrade them, however, do not know if this is right or not.

Thanks.

/Veroslav

---

### Post by cbowman57 on 2011-05-28
> **veroslav said:**
> Thank you for your fast reply.

When looking in Synaptic, I notice that these two packages are already marked as installed, but also marked with a "gold star". What does this means?

When I right-click on them, I can choose "Mark for upgrade", is this something that might fix it? As I mentioned, I did install every package it offered me to install from the test PPA, these two are the only ones left.

Could you please tell me what the proposed respository contains?

Thanks again.

/Veroslav

If it shows that you can mark them for upgrade, upgrade them.

I don't see gold stars here but that might be due to different icon themes.

Proposed repository are the files going into natty but not in main repo (consider them testing but stable for the most part)

You might also want to do a sudo apt-get dist-upgrade every once in awhile and see what shows up, be very careful before you select **Y**/n? though, sometimes it removes things, when in doubt, say no & ask.

---

### Post by veroslav on 2011-05-28
Thank you very much [cbowman57]("http://ubuntuforums.org/member.php?u=1089002"), it is working as a charm now! :)

Now, I've installed some extensions from the test PPA as well, but so far I haven't gotten them to work (logged out and restarted), so I will have a little play with that now.

But so far so good!

/Veroslav

---

### Post by veroslav on 2011-05-28
Actually, I take that back. It appears that the only extension not working, of all I've installed, is "Alternative Status Menu Extension". It shows as installed in Synaptic but looking for it in Gnome Tweak, shows it as available but the option is disabled and I cant turn it on.

/Veroslav

---

### Post by cbowman57 on 2011-05-28
> **veroslav said:**
> Thank you very much [cbowman57]("http://ubuntuforums.org/member.php?u=1089002"), it is working as a charm now! :)

Now, I've installed some extensions from the test PPA as well, but so far I haven't gotten them to work (logged out and restarted), so I will have a little play with that now.

But so far so good!

/Veroslav

Excellent!  Those extensions are just the most basic, if you do some searching there are some very cool ones available. Webupd8 is doing a good job covering those. :)

---

### Post by bmbaker on 2011-05-28
> **cbowman57 said:**
> excellent!  Those extensions are just the most basic, if you do some searching there are some very cool ones available. Webupd8 is doing a good job covering those. :)

:-)

---

### Post by Dobbie03 on 2011-05-28
> **maverick280857 said:**
> You seem to want all your external drives to boot up when you log in, by themselves. To do this you need to add a line for each device you want to mount, in /etc/fstab. For a description of this file, what it contains and how you can edit it, click [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").

Plug in all your external drives, and from a terminal, post the output of

```
df
```

Ok here is the output of "df"

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            304440640  12176200 276799736   5% /
none                   1602120       764   1601356   1% /dev
none                   1609820      3124   1606696   1% /dev/shm
none                   1609820        88   1609732   1% /var/run
none                   1609820         0   1609820   0% /var/lock
/dev/sdc1            488383484 149537940 338845544  31% /media/Music

```

Also does anyone know how to enable the delete key to delete rather than having to right click the files.

---

### Post by veroslav on 2011-05-28
I have now played a while with my new Gnome 3 installation, and these are the few outstanding issues, if somebody could help me out with those (see attached images for the screenshots).

1. The menus in nautilus have strange look, both background and foreground colors are wrong (see nautilus.png)

2. Some of the applications have completely different look than the default look of the gnome shell, for instance Totem (see totem.png)

3. Some of the applications look to have Clearlooks theme applied to them, for instance Banshee (see banshee.png)

4. I am still unable to enable "Alternative status menu extension", I tried un- and re-installing but it didn't work (see tweak.png)

Anybody can help me solve these?

Thank you in advance!

/Veroslav

---

### Post by cbowman57 on 2011-05-28
> **veroslav said:**
> I have now played a while with my new Gnome 3 installation, and these are the few outstanding issues, if somebody could help me out with those (see attached images for the screenshots).

1. The menus in nautilus have strange look, both background and foreground colors are wrong (see nautilus.png)

2. Some of the applications have completely different look than the default look of the gnome shell, for instance Totem (see totem.png)

3. Some of the applications look to have Clearlooks theme applied to them, for instance Banshee (see banshee.png)

4. I am still unable to enable "Alternative status menu extension", I tried un- and re-installing but it didn't work (see tweak.png)

Anybody can help me solve these?

Thank you in advance!

/Veroslav

Can't address all your questions but some apps still use gtk2 which probably accounts for visual differences you are seeing.

Try editing the metadata.json in your alt-status extension folder and make the version either 3.0 or make it match your shell version.  Not positive that will fix it but it's where I would start looking.

---

### Post by veroslav on 2011-05-28
Hi,

thank you for your reply. Unfortunately, changing the Gnome version for the extension in question did not resolve the issue.

But it is ok, these are not the major issues, I will have another go tomorrow, when I am not as tired as I am now.

One last question: is it normal for some applications not to use gtk3 but gtk2 instead? How does it look on your computer if I may ask?

Thanks again.

/Veroslav

---

### Post by cbowman57 on 2011-05-28
> **veroslav said:**
> Hi,

thank you for your reply. Unfortunately, changing the Gnome version for the extension in question did not resolve the issue.

But it is ok, these are not the major issues, I will have another go tomorrow, when I am not as tired as I am now.

One last question: is it normal for some applications not to use gtk3 but gtk2 instead? How does it look on your computer if I may ask?

Thanks again.

/Veroslav

You might want to try another alt-status extension, I've run across at least one that didn't work for me.

Not certain how common the gtk issue is, this is what mine looks like now with gmusicbrowser opened up.

---

### Post by karmila on 2011-05-28
> **bmbaker said:**
> for all those that are still having problems with updates, esp the network manager stuff you need to have the testing ppa enabled :-)

```
sudo add-apt-repository ppa:ricotz/testing
```after the update log out and log back in again and you will have this ..........

> **cbowman57 said:**
> File deletion is a nautilus option you set in preferences.

Do you have these network-manager files available in synaptic?  If so try and install those even if they have to be forced.

Thanks cbowman & bmbaker, network-manager problem is fixed now :D
I become love gnome-shell more and more.

Now for file deletion issue, which part from preference I should enable so I can remove file with delete button?
I didn't see any option related with that on behaviour tab.

---

### Post by JCSalomon on 2011-05-28
> **shafiee01 said:**
> after i login, gnome-shell doesnt start and if i statrt it manully with typing "gnome-shell --replace" in a terminal it works!!I had the same issue; and the same thing helps.  Also, no idea how to bring gnome-shell back on startup.

I note, though, that since I have that terminal I have some logging statements:

[FONT="Courier New"]JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat May 28 2011 22:26:53 GMT-0400 (EDT)[/FONT]

---

### Post by cbowman57 on 2011-05-29
> **karmila said:**
> Thanks cbowman & bmbaker, network-manager problem is fixed now :D
I become love gnome-shell more and more.

Now for file deletion issue, which part from preference I should enable so I can remove file with delete button?
I didn't see any option related with that on behaviour tab.

It's under Trash.

---

### Post by ojdon on 2011-05-29
GDM is still my only problem. It just refuses to Automatically login even though It worked before I installed Gnome-Shell from the Gnome3-Team PPA. The Automatic Login option under the Users menu is on, but still no luck. =\ 

An work-around I thought of was to display Florence, the Virtual Keyboard at login using this guide. But it seems that it can't find the files (Guessing they've moved in this version of GDM?) 

So maybe I could use something to replace GDM? Something faster maybe? I tried to install "SLIM" but that broke my installation. :( Maybe I didn't install it correctly...

Any help guys? :)

---

### Post by macozz on 2011-05-29
Almos all is running fine now with Gnome-shell in Natty. The only little thing that is not working is the bubble notification of Epiphany appearing in the bottom of the screen. Actually it do not appears there!I made some Google search but I did not found nothing. Any ideas why this is happens? Someone is experiencing this?
Thanks!

---

### Post by karmila on 2011-05-29
> **cbowman57 said:**
> It's under Trash.

Thanks but that is not fix the issue. I don't understand why :confused:

Nice dark theme :D

I have problem with most of themes I installed. They have pinky lines, lol.
Any known issue about this?

---

### Post by cbowman57 on 2011-05-29
> **karmila said:**
> Thanks but that is not fix the issue. I don't understand why :confused: 

Is the choice displayed & not working or just not there at all?

> Nice dark theme :D

Shell theme Atolm (modified), gtk3 theme Adwaita dark, metacity theme Atolm, icon set Aw0ken.

> I have problem with most of themes I installed. They have pinky lines, lol.
Any known issue about this?

Known issue, changed a few weeks ago with an update, some say it was gnome-shell itself, not certain.  I just avoid the themes that do it for now.

---

### Post by ojdon on 2011-05-29
Is anyone using a different login manager than gdm?

---

### Post by cbowman57 on 2011-05-29
> **ojdon said:**
> Is anyone using a different login manager than gdm?

I've stuck with gdm, but have also used lxdm & slim with this install.  Matter of fact I used lxdm for my live iso because of a gdm display problem.

Also know that kdm will work, pulls in most of KDE with it though.

---

### Post by ojdon on 2011-05-29
Right, since I tried installing Slim before simply using:
> sudo apt-get install slim

Then selecting it as my default login manager when the menu pops up while it installs, I restarted only to find a blank screen. =\ I'm just after a login manager which I can either automatically login or display an on screen keyboard like Florence.

---

### Post by cbowman57 on 2011-05-29
> **ojdon said:**
> Right, since I tried installing Slim before simply using:


Then selecting it as my default login manager when the menu pops up while it installs, I restarted only to find a blank screen. =\ I'm just after a login manager which I can either automatically login or display an on screen keyboard like Florence.

Wish I could offer a suggestion that works, I've been looking for a solution to this too (for weeks).

I did manage to get semi-functionality a couple weeks ago by going into User and Groups and setting my account to NOT ask for password at login, but after an update Users & Groups is still visible but doesn't work (at least not from the shell, might be possible from fallback mode, haven't tried that).  The downside to that is that I got prompted for keyring passwords about 2-3 times after I hit the desktop, but that may suit your needs??  If you manage to make that change I suppose you could set your keyring PW to <blank> (unsafe storage) to eliminate that prompt also.

Let me know what you find if you manage to access it.

---

### Post by ojdon on 2011-05-29
Also, come across another problem, anyone know how to make password fields like text fields or whatever the option was in the all Visual Assistance. It's useful for when using Virtual Keyboards.

---

### Post by karmila on 2011-05-29
> **cbowman57 said:**
> Is the choice displayed & not working or just not there at all?

Yes, it's there.
I see the 2nd option "Include a delete..." will add delete option at context menu which will delete files permanently (bypass the trash bin).
But that was not help with my unworking delete button (I tested the keyboard and the button works with unity)

> **cbowman57 said:**
> Known issue, changed a few weeks ago with an update, some say it was gnome-shell itself, not certain.  I just avoid the themes that do it for now.

Thanks for the info, i will try some fresh themes. Maybe it is issue with old packaged themes.

---

### Post by cbowman57 on 2011-05-30
> **karmila said:**
> Yes, it's there.
I see the 2nd option "Include a delete..." will add delete option at context menu which will delete files permanently (bypass the trash bin).
But that was not help with my unworking delete button (I tested the keyboard and the button works with unity)



Thanks for the info, i will try some fresh themes. Maybe it is issue with old packaged themes.

Yeah, you can only delete via the mouse, the delete key doesn't do it.  That what you mean?

---

### Post by slooksterpsv on 2011-05-31
> **cbowman57 said:**
> Yeah, you can only delete via the mouse, the delete key doesn't do it.  That what you mean?

CTRL+Delete does and CTRL+SHIFT+Delete permanently deletes it.

---

### Post by cbowman57 on 2011-05-31
> **slooksterpsv said:**
> CTRL+Delete does and CTRL+SHIFT+Delete permanently deletes it.

True, haven't used those in awhile. :)

---

### Post by cbowman57 on 2011-05-31
> **ojdon said:**
> Right, since I tried installing Slim before simply using:


Then selecting it as my default login manager when the menu pops up while it installs, I restarted only to find a blank screen. =\ I'm just after a login manager which I can either **automatically login** or display an on screen keyboard like Florence.

You have two auto login choices, force a downgrade to the 2.32 gdm (which works), or start over with oneiric, it runs well but is highly unstable right now.

---

### Post by Dronar on 2011-06-01
> **23dornot23d said:**
> Which graphics card do you have and what laptop is it please ?

Sorry, my internet broke down, haven't been able to respond :/

I have a dell D620 with a Nvidia 7300 Go graphics card

---

### Post by pikamoku on 2011-06-01
> **slooksterpsv said:**
> CTRL+Delete does and CTRL+SHIFT+Delete permanently deletes it.

thanks, but .... wtf? :confused: is this for security reasons? why dont just use the "Supr" o "Del" button? (without crtl)

---

### Post by karmila on 2011-06-01
> **cbowman57 said:**
> Yeah, you can only delete via the mouse, the delete key doesn't do it.  That what you mean?

Yes, it is.

> **slooksterpsv said:**
> CTRL+Delete does and CTRL+SHIFT+Delete permanently deletes it.

We need Ctrl button now for deleting files :confused:

Thanks, I finally know how...

---

### Post by daniel4m on 2011-06-01
After a fresh installation of LM11, I added Gnome 3 from ppa. Now I have Gnome 3.0.2(Fallback session) & the following issues:

- eog editor is so slow(system use nouveau graphic driver). EOG is not a slow with a small images,
 but is extremely slow with large images (i see broken images)[SOLVED - proprietary driver 173 installed]

- Gnome System Monitor work very well but need 2-5 sec to exit(which is not a case in Gnome 2.3)

- Mint application 'Desktop Settings' seem to have no effect on the Gnome 3

- Exit and logout(mintMenu) buttons not work  

Does anyone have the following problems?

---

### Post by DarkTide on 2011-06-04
If some of the above suggestions don't work for people, you can try the following as it worked for me.

When I tried to install Gnome 3, I restarted my laptop, but it didn't  give me the option to log into it, and everything failed.  So I tried  running in Recovery Mode and re-typed "sudo apt-get install gnome-shell"  and "sudo apt-get install gnome-shell", in that order.  Then restarted  my laptop again.  If has been stated before, my apologies.  I'm just  excited to figure out something on my own in Linux for once

---

### Post by ojdon on 2011-06-04
> **cbowman57 said:**
> You have two auto login choices, force a downgrade to the 2.32 gdm (which works), or start over with oneiric, it runs well but is highly unstable right now.

Shame Alpha 1 is far too unstable at the moment (I installed gnome-shell but whenever I log in and press the Applications menu it just crashes and I have to log out. So until 11.10 is stable... How do I downgrade to GDM 2.32?

Thanks!

---

### Post by cbowman57 on 2011-06-04
> **ojdon said:**
> Shame Alpha 1 is far too unstable at the moment (I installed gnome-shell but whenever I log in and press the Applications menu it just crashes and I have to log out. So until 11.10 is stable... How do I downgrade to GDM 2.32?

Thanks!

Using synaptic it's just a matter of selecting your gdm (highlight it), click package on the menu, then force, you'll get a window pop up, select a previous version and install.  From the same menu you will want to lock the version so any more updates won't overwrite your version.

---

### Post by bmbaker on 2011-06-04
> **ojdon said:**
> Shame Alpha 1 is far too unstable at the moment (I installed gnome-shell but whenever I log in and press the Applications menu it just crashes and I have to log out. So until 11.10 is stable... How do I downgrade to GDM 2.32?

Thanks!
ya there is a fix for this :-)
[http://ubuntuforums.org/showthread.php?t=1775049](http://ubuntuforums.org/showthread.php?t=1775049)
i installed and have running gnome-shell in Oneiri, took a bit of wk and i also manually upgraded GDM and gnome-tweak-tool and added the ricotz testing ppa :)
wks fine and is noticably faster than natty :-)

---

### Post by bmbaker on 2011-06-04
> **cbowman57 said:**
> Using synaptic it's just a matter of selecting your gdm (highlight it), click package on the menu, then force, you'll get a window pop up, select a previous version and install.  From the same menu you will want to lock the version so any more updates won't overwrite your version.

I really like what you have for a theme :-) which one are u using?

---

### Post by cbowman57 on 2011-06-04
> **bmbaker said:**
> I really like what you have for a theme :-) which one are u using?

A slightly modified Atolm for the shell & Atolm-gtk3 for the windows.  To get it without the pink lines make sure you aren't using ricotz gnome-themes-standard (if you have his ppa turned on). I've gotten in the habit of just using his ppa to fix select problems. He has warned us that some of his packages are a bit unstable.

---

### Post by maverick280857 on 2011-06-04
> **daniel4m said:**
> After a fresh installation of LM11, I added Gnome 3 from ppa. Now I have Gnome 3.0.2(Fallback session) & the following issues:

- eog editor is so slow(system use nouveau graphic driver). EOG is not a slow with a small images,
 but is extremely slow with large images (i see broken images)[SOLVED - proprietary driver 173 installed]

- Gnome System Monitor work very well but need 2-5 sec to exit(which is not a case in Gnome 2.3)

- Mint application 'Desktop Settings' seem to have no effect on the Gnome 3

- Exit and logout(mintMenu) buttons not work  

Does anyone have the following problems?

Best to start a thread separately. What is your system configuration? Do you have a nvidia graphics card? If yes, use 'Additional Drivers' (System -> Administration -> Additional Drivers) from the repository, to install the so called 'restricted' drivers for your nvidia card.

PS -- Best to use drivers from [www.nvidia.com](www.nvidia.com) instead, if you don't mind updating them manually. (Good to know you've solved this :-)).

Use 'gnome-tweak-tool' as outlined in the first post of this thread, to change gnome settings. For under the hood stuff, use the command line interface (CLI) and look up the man page for 'gsettings':

```
man gsettings
```

Applications like ubuntu-tweak don't yet have support for the Gnome Shell.

What is mintMenu? Are you able to use the default Gnome3 logout button?

---

### Post by sandy_ on 2011-06-04
I am attempting to create a ubuntu live cd with gnome 3 pre-installed and no unity. I followed the steps at [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) to create a basic live cd and now I want to add GNOME 3 to it rather than getting Unity by installing ubuntu-desktop. Will the procedure mentioned in this thread work ?

---

### Post by maverick280857 on 2011-06-04
> **sandy_ said:**
> I am attempting to create a ubuntu live cd with gnome 3 pre-installed and no unity. I followed the steps at [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) to create a basic live cd and now I want to add GNOME 3 to it rather than getting Unity by installing ubuntu-desktop. Will the procedure mentioned in this thread work ?

Post #1 of this thread contains the procedure to install Gnome 3 on a functional Natty machine.

Check out the gnatty thread by Charles Bowman here: [http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198). This is what you're looking for.

---

### Post by sandy_ on 2011-06-05
Thanks... That solved it...

---

### Post by ojdon on 2011-06-05
> **cbowman57 said:**
> Using synaptic it's just a matter of selecting your gdm (highlight it), click package on the menu, then force, you'll get a window pop up, select a previous version and install.  From the same menu you will want to lock the version so any more updates won't overwrite your version.

Ah thank you so much for this solution! I now have a fully functional Tablet OS! :D 

Though, not to sure if this is related but now ever program listed in gnome-session-properties seems to load quite a few seconds after Gnome-Shell loads like Florence, the virtual keyboard or Network Manager. Any idea on how to speed things up? :confused:

---

### Post by cbowman57 on 2011-06-05
> **ojdon said:**
> Ah thank you so much for this solution! I now have a fully functional Tablet OS! :D 

Though, not to sure if this is related but now ever program listed in gnome-session-properties seems to load quite a few seconds after Gnome-Shell loads like Florence, the virtual keyboard or Network Manager. Any idea on how to speed things up? :confused:

Try this, not sure if it will work but it doesn't hurt to try.  In your /etc/environments file add this line: 

```
export CLUTTER_VBLANK=none
```

Let me know if it does something.  It is supposed to speed things up, though I have no experience with tablets.

---

### Post by ojdon on 2011-06-05
Unfortunately that didn't seem to work, here is my bootchart though:

[http://dl.dropbox.com/u/6773567/Viewpad-natty-20110604-2.png]("http://dl.dropbox.com/u/6773567/Viewpad-natty-20110604-2.png")

Not too sure if that's going to help find what my problem is though. Gnome-Shell is usable in 15 seconds, yet Bootchart states that it doesn't finish booting after 52 seconds. Strange...

---

### Post by Visceral Monkey on 2011-06-05
Has *anyone* from the gnome 3 team or ATI fixed the fglrx issues that prevents the official ATI driver from being used without graphic corruption? The open source driver sucks and I can't use Gnome 3 until this issues gets resolved..

---

### Post by rpk94 on 2011-06-12
A friend of mine can apparently can use gnome 3 AND unity on his machine when he followed the commands given by you in your post. Will this hold true to every machine? and basically, how is this possible?

---

### Post by ZekeGraal on 2011-06-15
> **rpk94 said:**
> A friend of mine can apparently can use gnome 3 AND unity on his machine when he followed the commands given by you in your post. Will this hold true to every machine? and basically, how is this possible?
I've looked around and there is nothing on this from what I've seen. Slooksterpsv said he wouldn't be updating this anymore, and I don't see Unity working side by side with it anyway. I myself am reverting back to GNOME 2 for speed and compatibly issues. If you keep looking you may be able to find something, good luck. :D

---

### Post by bulldog on 2011-06-15
> **ZekeGraal said:**
> I've looked around and there is nothing on this from what I've seen. Slooksterpsv said he wouldn't be updating this anymore, and I don't see Unity working side by side with it anyway. I myself am reverting back to GNOME 2 for speed and compatibly issues. If you keep looking you may be able to find something, good luck. :D

FYI,I have a x64 and a i686 install WITH a working Gnome-Shell AND a working Unity.
There's a fallback mode which is working too.

Take a look at this tread,there are downloads available and cbowman57 is thinking about a new release which would be even better.

[http://ubuntuforums.org/showthread.php?p=10942707#post10942707](http://ubuntuforums.org/showthread.php?p=10942707#post10942707)

---

### Post by cbowman57 on 2011-06-15
@bulldog; yep, plan to lead v3 with a 64-bit version first if I can figure a couple more things out.

---

### Post by ZekeGraal on 2011-06-15
> **bulldog said:**
> FYI,I have a x64 and a i686 install WITH a working Gnome-Shell AND a working Unity.
There's a fallback mode which is working too.

Take a look at this tread,there are downloads available and cbowman57 is thinking about a new release which would be even better.

[http://ubuntuforums.org/showthread.php?p=10942707#post10942707](http://ubuntuforums.org/showthread.php?p=10942707#post10942707)
I will look into this, thanks! :D

---

### Post by Dobbie03 on 2011-06-16
This may have already been asked and answered, but does anyone know how to automount external hard drives at login with gnome3?

---

### Post by bulldog on 2011-06-16
> **Dobbie03 said:**
> This may have already been asked and answered, but does anyone know how to automount external hard drives at login with gnome3?

I have a 2TB external hdd,when I turn it on,it's visible in nautilus.
Just click on it and it's mounted,at least it works this way on my machine.
Why would you have automount at login?

---

### Post by Dobbie03 on 2011-06-17
Because it is easier than opening Nautilus to mount it.

---

### Post by cbowman57 on 2011-06-17
> **Dobbie03 said:**
> This may have already been asked and answered, but does anyone know how to automount external hard drives at login with gnome3?

Have you already tried just adding it to fstab?  If it has a uuid it should be possible if it's always connected.  If you want an app that might make it easy try installing pysdm but I'm not sure if it's still being maintained & compatible with 11.04.

---

### Post by 23dornot23d on 2011-06-17
Boot up from it .... then you will have no problem ..... as it has no choice ....
it has to mount .... and your main sda drive will automatically mount too this way.

---

### Post by skibler on 2011-07-03
I have been using gnome3 for well over a month without major issue.

Recently, the system on my laptop has decided that it no longer wants to use the faenza icon theme. 

The icon theme is installed properly, and it is set correctly in gnome-tweak-tool, but the system is still using the standard "gnome" icons. I have even changed the key in gconf to Faenza-Darkest (it was "gnome"), and reloaded, but that makes no difference.

Has anyone else had this issue? Any ideas?

---

### Post by pritam_par on 2011-08-06
This will help 
[http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.htm]("http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html")l

---

### Post by isaacj87 on 2011-08-07
I apologize if this has been answered. This thread has become quite long.

Is there a way to get Gnome3's gnome-power-manager working?

---

### Post by pratpor on 2011-08-26
i will be glad if i could get some common shortcuts for gnome 3.........
plz help me.....
and is there any way in which i can assign shortcut keys to applications like we can do in windows

---

### Post by jbicha on 2011-08-26
[http://library.gnome.org/users/gnome-help/stable/shell-keyboard-shortcuts.html.en](http://library.gnome.org/users/gnome-help/stable/shell-keyboard-shortcuts.html.en)

You can change keyboard shortcuts with System Settings>Keyboard.

---

### Post by skibler on 2011-08-26
> **pratpor said:**
> i will be glad if i could get some common shortcuts for gnome 3.........
plz help me.....
and is there any way in which i can assign shortcut keys to applications like we can do in windows

[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)


> **isaacj87 said:**
> I apologize if this has been answered. This thread has become quite long.

Is there a way to get Gnome3's gnome-power-manager working?

What doesn't work for you? It works on both my laptops, but when I try to run it on my desktop:

```

patrick@gnubuntu:~$ gnome-power-manager 

(gnome-power-manager:4163): GLib-WARNING **: XDG_RUNTIME_DIR variable not set.  Falling back to XDG cache dir.
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:4163): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:4163): Gtk-WARNING **: Failed to load type module: (null)

patrick@gnubuntu:~$

```

---

### Post by pandeylavakesh on 2011-09-12
> **slooksterpsv said:**
> **[COLOR=red]NEW!!![/COLOR] This guide isn't going to be updated anymore, as there is gNatty, and I've switched to Lubuntu. The reason? GDM kept crashing and issues kept coming up that reduced the overall functionality of my own computer.**
 
The PPA seems like it changes slightly to where things may break, if something does break, try to run: 
sudo apt-get install gnome-shell gnome-session
again, as it looks like a lot of the time gnome-shell and gnome-session aren't being installed.
 
**[COLOR=red]FIX for issue opening certain applications (like games)[/COLOR]**
 
Do the following in terminal:
 
```

echo "PATH=\"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\"" | tee -a ~/.profile

```
 
Logout and log back in and that should fix the issue. NOTE: You have to do this for each user that logs into the system if they can't access games or that.
 
**FIX for .ICEauthority issue!**
There's another method besides this one, and it involves just installing the following:
```

sudo apt-get install gnome-session

```
This works!
 
**Installing Gnome 3.0**
Let's start by installing Gnome 3.0, NOTE THIS WILL REMOVE UNITY AND MAKE IT TO WHERE YOU CANNOT INSTALL UNITY!!! The only way to get Unity back is to remove the PPA and run a dist-upgrade on the system. (See further down)
 
Open a terminal and type in the following commands (do this by going to your applications area and searching for terminal):
 
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell gnome-session
sudo apt-get -f install
sudo apt-get install gnome-shell
sudo apt-get install gnome-session

```
 
**NEW - The above has changed as issues occurred and didn't install gnome-shell**
 
Before we reboot, we do need to do a few more things to make sure it's running correctly, keep reading.
 
**Issues with strange themes**
You may have a strange theme and want the default Gnome 3 theme, here's what you need to do, now where we didn't reboot above (or if you did and are at the weird theme'ed gnome 3, open a terminal and follow along), in the terminal type in:
```

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
sudo apt-get install -f

```
 
Some users have reported needing to run sudo apt-get install -f due to failure to install some packages. If that doesn't work, go ahead and post and we'll see if we can help you out.
 
Now let's restart. For those of you having the common graphical glitch, this issue is caused by the gnome-accessibility-themes and by not having the gnome standard themes. Once you reboot you should be at the fresh interface of Gnome 3.
 
**Needs some tweaking! Window buttons, different themes, etc.**
Unfortunately, there's not a lot you can change initially, but we'll need to install another tool to help tweak some items, open a terminal again and install the following:
```

sudo apt-get install gnome-tweak-tool

```
 
Open the gnome-tweak-tool by pressing ALT+F2 and typing in: 
```

gnome-tweak-tool

```
then press Enter. Here we can change a few basic settings. Go under interface to change the Gtk+ Theme. If you find you don't like something, just change it back.
 
To apply the changes, either log out and log back in or press ALT+F2 and type in just r and press Enter, which will refresh the Window Manager.
 
If you want your regular buttons on the right hand side for the windows do the following, press ALT+F2 and type in: 
```

gconf-editor

```
Press Enter and navigate to:
```

/desktop/gnome/shell/windows

```
Change the button_layout to:
```

:minimize,maximize,close

```
 
After you do that, you do need to press ALT+F2, type r, press enter, and it'll fix that.
 
**Flickering, GAHHHHHHHH**
If you have flickering, tearing, etc. of the windows and HAVE installed the graphics drivers, you need to remove them. Unfortunately with some chipsets you will experience tearing with the graphic drivers - ATI for example.
 
**Other stuff?**
I'll update this guide as much as I can as I know there's a lot of questions about Gnome 3 and how to configure this or that or change settings. Try stuff out, experiment with the greatest DE in the world!
 
**How do I get Evolution 3.0**
So as a lot of you know, the Gnome 3.0 PPA above DOES NOT include Evolution 3.0, well here's a simple way of getting it from another PPA. So open the terminal again and type in the following:
 
```

sudo apt-add-repository ppa:danilo/evolution
sudo apt-get update
sudo apt-get dist-upgrade

```
 
It is a SLOW PPA so give it time. When that's done, just restart Evolution for the 3.0 goodness. The menu's are a lot better than 2.32, and fitted for smaller screen resolutions.
 
**Tips & Tricks! I want to have fun!**
Ok let's get out some tips and tricks, have 2 separate windows open on one application, like 2 separate firefox windows (not tabs) and press ALT+TAB and while holding down ALT press Tab until you get to the firefox icon and press the down arrow key. Voila! You see all the separate windows in Live Previews.
 
Press the Super key (windows logo key) then start typing in the name of an application. Voila! You don't need the mouse to get to your apps.
 
What else... hmmm... click on the circle with the little person in it, there's a way to find some accessibility settings.
 
Click at the top where it says todays date and time, it pops down a cool calendar that integrates with Evolution 3.0
 
Click on the application name in the top left, it has a quit menu so if you can't figure out how to quit an app or close a window, you can do it that way.
 
If you get stuck in a window that has no close button, try pressing the escape key.
 
When someone sends you an im, you can click on it at the bottom middle and reply if using Empathy.
 
If you press the activities button and go to the bottom right-hand side you should see a list of your current tray icons such as empathy chats. In the activities menu if you get an IM you can reply to it there.
 
**I want my Unity back!**
 
On page 9, [M4570D0N] stated that the following should work.
 
To remove Gnome 3 and reinstall Unity, do the following in a terminal:
 
```

sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade

```
 
I have not tested this personally, but it sounds like it works. So let me know if it doesn't and I'll remove this section.
 
If you have any more let me know. I know I haven't added who gave what fixes for what, but I'll try to update that here. If you added something and don't see your alias, PM me.
 
hey buddy .. today i followed this procedure and m not able to see anything on my desktop. Its completely a blank screen. What should I do now?? I have lost my Unity desktop and its customization .. so can u please tell me how can i get back my previous desktop without affecting its customization ? or do i need to do a fresh install ? i really frustrated ..

---

### Post by ale.junuzovic on 2011-09-13
Can anyone using ATI/fglrx driver confirm this is working?

---

### Post by jdbausch on 2011-09-21
thanks for a great post.  quick question (searching did not find the answer for me)

at the login screen, I see usernames, but no user icons - is there some way to make those show?

obviously this is not a big deal, just curious.

---

### Post by itzfritz on 2011-10-03
> **skibler said:**
> I have been using gnome3 for well over a month without major issue.

Recently, the system on my laptop has decided that it no longer wants to use the faenza icon theme. 

The icon theme is installed properly, and it is set correctly in gnome-tweak-tool, but the system is still using the standard "gnome" icons. I have even changed the key in gconf to Faenza-Darkest (it was "gnome"), and reloaded, but that makes no difference.

Has anyone else had this issue? Any ideas?

How did you get the faenza gtk2 theme working in gnome3?

---

### Post by jamesringhof on 2012-01-11
Man. Unity is dead. Thanks Guys. Put Unity Back Into The WM without Unity (did that make sense?)

James:p:p

---

