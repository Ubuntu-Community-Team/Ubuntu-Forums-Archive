---
title: "Using ctwm under Jaunty Jackalope"
date: 2009-06-17
forum: Desktop Environments
---

### Post by wacky_keyboards on 2009-06-17
Hello,

I've installed Jaunty Jackalope, and pulled down ctwm using aptitude.  I would like to make ctwm my preferred window manager.  I don't really mind (yet) how I get to it, as long as I do!

I found a trick that was posted elsewhere, wherein I add a new file under /usr/share/xsessions/ to create a new session option.  I copied the gnome.desktop file to a new one, called ctwm.desktop, and just changed "gnome" to "ctwm."  More specifically, here is what's in ctwm.desktop:

     [Desktop Entry]
     # NOTE:  this is a modified copy of the file, "gnome.session."
     Encoding=UTF-8
     Name=CTWM
     Comment=This session logs you into CTWM
     Exec=/usr/bin/ctwm
     # no icon yet, only the top three are currently used
     Icon=
     Type=Application
     X-Ubuntu-Gettext-Domain=CTWM-session

I was then able to log out, and (in the log in window) select CTWM as one of my sessions.  I logged in, and CTWM came up.  BUT, my .xinitrc file was not followed.  (I was able to put my own .ctwmrc file into my home directory, and it was followed, so I was partially successful.)

Can anyone help me?  I have a large set of scripts set up from the Good Old X days that are based on starting X clients through .xinitrc (which also launches CTWM, by the way, although for my testing purposes I'm using a .xinitrc file that contains one line, "xterm -geometry 80x24+100+100").  Am I even doing this correctly?

Thanks!

Oh, and I tried the /etc/inittab trick to try to obtain a text console login so that I can directly launch X with either xinit or startx, but that seems ignored under Jaunty Jackalope (the /etc/inittab file does not even exist with the Ubuntu installation anymore).

---

### Post by XanTrax on 2009-06-17
If you can select CTWM from the drop down list of available X Sessions at the GDM login screen, you can set it as default from there.  

1.) Restart
2.) Get to the login screen
3.) Select CTWM as your session
4.) Select to make it default
5.) It'll log you in
6.) Next time you start up, you should be prompted with CTWM version of their login prompt

---

### Post by wacky_keyboards on 2009-06-17
XanTrax, thanks for the reply!

I tried what you suggested, but while it did make CTWM my default session manager, it did not change the Ubuntu login screen in any way.  (I just didn't need to explicitly select CTWM anymore.)  I tried logging out and logging back in, as well as rebooting my computer.  In both cases, while CTWM was the default manager, I was still being presented with the Ubuntu login screen to log in.

More importantly, my .xinitrc file was not run as far as I can tell.  CTWM came up, but the xterm (which is the only thing invoked in my .xinitrc file) did not appear.

---

### Post by XanTrax on 2009-06-18
You can try what this guy suggests:

[http://ubuntuforums.org/showthread.php?t=349517](http://ubuntuforums.org/showthread.php?t=349517)

"Bum", GUI application for removing applications that load at boot.  You can remove the login screen and replace it with the console screen or change it out for another script that autoloads the CTWM login prompt (whatever that may be).

---

### Post by wacky_keyboards on 2009-06-18
Thanks, XanTrax!  Actually, I used a different method (see below).  However, your link was useful in that it enabled me to UNDO what I did.  B-)

My solution was to disable the GDM (aka "Graphical Login Manager" under Services -- see below).  This meant that I would be presented with a text-based console login when Ubuntu boots up.  Thus, I log in and manually start X (using xinit, which then reads my .xinitrc file which contains invocations for lots of X applications and my preferred window manager, CTWM).  Problem solved!

I used a suggestion from

[http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etcinittab-506281/](http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etcinittab-506281/)

The way this is accomplished is to use the Services administration application.  You access this using System (taskbar menu) -> Administration -> Services.  (Note, some of these names may be different on your Ubuntu.  I've noticed how these option names sometimes change between Ubuntu distributions.)  Click on the "Unlock" button and give your password so that you can make changes, then scroll down to "Graphical Login Manager (gdm)" (or whatever it may be called on your Ubuntu) and click on it.  You'll be presented with a dialog box asking to confirm.  MAKE SURE THAT EVERYTHING ELSE IS CLOSED/SHUT DOWN because the moment you confirm YOUR X SESSION DIES!  (That was my surprise.  B-)

The only thing left to check was how to restart it, since there are times when I want to use the Ubuntu services without having to Google what the command-line invocation is.  That was provided by XanTrax's link,

[http://ubuntuforums.org/showthread.php?t=349517](http://ubuntuforums.org/showthread.php?t=349517)

To wit, I just needed to restart the GDM, which was accomplished using:

sudo /etc/init.d/gdm start

Now all I need to do is figure out how Ubuntu does all this other stuff (like connecting to a wireless network if nm-applet is not running) ....

---

### Post by XanTrax on 2009-06-19
Congrats :), learn something new everyday.

For the networking stuff, you can look into modifying/editing the /etc/network/interfaces file that will allow you to set static information for each device individually.

So, if your computer is usually home, you can use that file to autoconnect to you with a static IP specifying the ESSID and password (if there is one) and you wont have to worry about anything after login.

---

### Post by wacky_keyboards on 2009-06-21
XanTrax:  I'm not sure what you mean about modifying/editing the /etc/network/interfaces file.  Mine only contains the following:

auto lo
iface lo inet loopback

So, for example, I wouldn't know what entry to add to autoconnect in the scenario that your described.

(Of course, I have a new problem:  my wireless network access has stopped working for no reason that I've yet been able to puzzle out.  I've not changed any access passwords, my MAC filtering on the router hasn't been changed, and I *was* previously able to connect as I had been using aptitude to download packages.  Argh, always one more problem that SHOULDN'T BE!)

---

### Post by wacky_keyboards on 2009-06-21
Actually, scratch my bitching about loss of wireless access in my previous post.  I had brilliantly managed to disable my wireless card using a Fn-based key combination and hadn't noticed it.  It can be mighty hard to protect against one's own stupidity.  B-)

---

### Post by XanTrax on 2009-06-22
haha, good to hear you got your wireless up and working.

What I was talking about was that you had said you had no access to wireless without nm-applet running (which is Gnome), or at least, thats how you made it sound.

What I was suggesting was editing the /etc/network/interfaces file and set it up so you have a static IP and it autoconnects so you do not have to worry about nm-applet which is NetworkManager applet (I personally hate NetworkManager).

You can find plenty of materials online that tell you how to edit it so that it can autoconnect to a wireless network with a specific ESSID and password/passphrase.

---

### Post by wacky_keyboards on 2009-06-23
XanTrax:  you are quite correct.  I am using nm-applet (which, as you noted, is Gnome) to obtain wireless (and wired) access.  I don't mind it, except that since I am not using all of the Gnome desktop then I have to enter in wireless pass codes all the time.  Either NetworkManager is not configured to save my pass codes, or it has no access to the ones I've already entered (and re-entered).  (I'm going to post about this in a new thread, since we've strayed considerably from the original subject of this thread.)

I'm not sure what you suggest would work better for my situation.  I have 3 kinds of network connection scenarios:  wired/DHCP, wireless, and dial-up (through a USB modem).  In Ye Good Olde Days, when I was using Red Hat, their distribution came with a GUI called redhat-network-manager, or something like that, and you could configure wired connections through that and click-and-activate through the GUI (which I prefer, rather than being automatically connected).  It didn't handle wireless so well, so through a lot of googling I eventually cobbled together a script that made use of various modules (ndiswrapper being the big one -- NOTE: I was using a PCMCIA wireless card at the time, whereas on my current laptop the wireless card is built-in) and commands (e.g. "ifconfig wlan0" and "iwlist wlan0").

I'll dust off the script and see if it works so that I don't need NetworkManager anymore for wireless, but I'm not sure what I'd use for the wired/DHCP and modem connections.  Do you have specific suggestions for /etc/network/interfaces (or a URL)?

However, this will not end my dependency on Gnome, or at least Gnome's panel (gnome-panel), because I can't get my keyboard settings to work any other way.  (By default, X's keyboard repeat delay and rate are too slow for me, and "kbdrate" doesn't fix it.)

Thanks!

---

