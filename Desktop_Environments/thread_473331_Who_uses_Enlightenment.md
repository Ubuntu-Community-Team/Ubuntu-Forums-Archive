---
title: "Who uses Enlightenment"
date: 2007-06-13
forum: Desktop Environments
---

### Post by Perfex on 2007-06-13
Just curious how many of us are using e17.. and if you want to share you experiences, tweaks, etc 

I am very happy with e17.. my only beef is the not being able to use the gnome network manager.. though for most other things I made a link to the control center under accessories and for file management i have been using .

To get my wifi working I boot in to an gnome session ,connect, log off, and into e17, I tried some standalone wifi managers, but they seem to not work well for me, there is also this [http://watchwolf.fr/index.php?post/2007/04/01/%5BEnigma%5D-You-can-configure-your-wired-network](http://watchwolf.fr/index.php?post/2007/04/01/%5BEnigma%5D-You-can-configure-your-wired-network)
but it complains of not having etk dependencies when I try to install, which I figure would be installed.. im at a loss there .

---

### Post by smartboyathome on 2007-06-14
I am thinking of trying it out after I finish making a LiveCD for my custom FVWM-Crystal install. I had the same problem in FVWM-Crystal, but I got around it by using WICD, you should try it out too. ;)

---

### Post by Perfex on 2007-06-14
excellent .Wicd works better then network-manager.. :D

[Enlightenment - ubuntu ]("http://ubuntuforums.org/showthread.php?t=319336&highlight=enlightenment")

---

### Post by trippinnik on 2007-06-14
I keep testing it out as it progresses, but there's a few things that keep me from using it full time yet.  Can't use the keyboard to sleep my laptop, when I run ktorrent it just disappears and the Wifi utility it uses doesn't let me setup my WPA password so I can't connect.  I think if I had a desktop system (especially a low end one) I'd use it though.  Hopefully it stablizes soon, because I went in an customized my application icons to the animated ones but then an update wiped them out.

---

### Post by Perfex on 2007-06-14
My laptop is not the fastest out there.. that was the initial choice...
have not installed on my desktop yet.. will soon.. just mainly for the eye candy heh

Some of the things I used to work around issues so far - vlc player if you maximize it .. well lets just say ctrl,alt,backspace ;).... I am using xine movie player now.. works just as good..


by the way that wifi utility in e17 doesnt do anything really but monitor.. as was just suggested wicd works ;)

---

### Post by watchwolf on 2007-06-15
> **Perfex said:**
> Just curious how many of us are using e17.. and if you want to share you experiences, tweaks, etc 

I am very happy with e17.. my only beef is the not being able to use the gnome network manager.. though for most other things I made a link to the control center under accessories and for file management i have been using .

To get my wifi working I boot in to an gnome session ,connect, log off, and into e17, I tried some standalone wifi managers, but they seem to not work well for me, there is also this [http://watchwolf.fr/index.php?post/2007/04/01/%5BEnigma%5D-You-can-configure-your-wired-network](http://watchwolf.fr/index.php?post/2007/04/01/%5BEnigma%5D-You-can-configure-your-wired-network)
but it complains of not having etk dependencies when I try to install, which I figure would be installed.. im at a loss there .

I can help you about Exalt, I m the developper.

You installed E17 with easy_e17.sh ? You have e17 in /opt/e17 ? If yes you need to add /ope/e17/lib/pkgconfig in the pkgconfig path. That's why it don't find ETK.

The procedure to install Exalt is:
```
cvs -z3 -d:pserver:anonymous@cvs.exalt.berlios.de:/cvsroot/exalt co exalt
cd exalt/libexalt
./autogen.sh
make
sudo make install
cd ../exalt
./autogen.sh
make
sudo make install
```

---

### Post by Mlehliw on 2007-06-15
I think it looks great and has awesome potential but at the moment it is still a little too buggy for me. When I last compiled from CVS a month ago I had problems configuring my mouse buttons. From what I remember remapping any key seemed to be a big hassle. The kicker was horribly buggy whenever I tried to put in new apps. I'll probably try it again in a couple weeks to see if anything has changed, but until then I'll stick with one of the major DE's.

Also I couldn't use conky without giving it a "window." That can probably be fixed but mainly I just use e17 to play with features.

---

### Post by Brimmy on 2007-06-19
> **watchwolf said:**
> I can help you about Exalt, I m the developper.

You installed E17 with easy_e17.sh ? You have e17 in /opt/e17 ? If yes you need to add /ope/e17/lib/pkgconfig in the pkgconfig path. That's why it don't find ETK.

The procedure to install Exalt is:
```
cvs -z3 -d:pserver:anonymous@cvs.exalt.berlios.de:/cvsroot/exalt co exalt
cd exalt/libexalt
./autogen.sh
make
sudo make install
cd ../exalt
./autogen.sh
make
sudo make install
```

I get this

cvs [checkout aborted]: connect to cvs.exalt.berlios.de(195.37.77.137):2401 failed: Connection refused

---

### Post by firstlife on 2007-06-19
It's worked great for me. I even put it on a 600mhz pentium 3, and it did just fine. A few crashes here and there, but overall great. Was even able to run the "about" window with the moving background, and slide windows from desktop to desktop.

---

### Post by AJB2K3 on 2007-06-20
I am but i dont like its control pannel, IMHO is absolutly revolting but it is a nice fast system on my test hardware.

---

### Post by Brimmy on 2007-06-27
Getting this error now

./autogen.sh 
Running aclocal...
configure.in:16: warning: macro `AM_ENABLE_SHARED' not found in library
configure.in:17: warning: macro `AM_PROG_LIBTOOL' not found in library
Running autoheader...
Running autoconf...
configure.in:16: error: possibly undefined macro: AM_ENABLE_SHARED
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:17: error: possibly undefined macro: AM_PROG_LIBTOOL


help!!

---

### Post by Brimmy on 2007-06-27
> **Brimmy said:**
> Getting this error now

./autogen.sh 
Running aclocal...
configure.in:16: warning: macro `AM_ENABLE_SHARED' not found in library
configure.in:17: warning: macro `AM_PROG_LIBTOOL' not found in library
Running autoheader...
Running autoconf...
configure.in:16: error: possibly undefined macro: AM_ENABLE_SHARED
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:17: error: possibly undefined macro: AM_PROG_LIBTOOL


help!!


installed libtool   fixed it but now i get this


991FZ81% cd ../exalt 
991FZ81% ./autogen.sh 
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in:82: required file `./config.rpath' not found
po/Makefile.am:6: addsuffix .mo,$(ALL_LINGUAS: non-POSIX variable name
po/Makefile.am:6: (probably a GNU make extension)
po/Makefile.am:8: addsuffix .po,$(ALL_LINGUAS: non-POSIX variable name
po/Makefile.am:8: (probably a GNU make extension)
po/Makefile.am:10: `%'-style pattern rules are a GNU make extension



downgraded to automake1.9

---

### Post by Brimmy on 2007-06-27
Getting a new error message

sudo exalt
wifi_set_current_essid(): essid() is not a correct essid!
exalt_eth_load_ip(): ioctl (SIOCGIFADDR): Cannot assign requested address
exalt_eth_load_netmask(): ioctl (SIOCGIFNETMASK): Cannot assign requested address
exalt_eth_save_load_byeth(): the card is a wireless card ! 
wifi_set_current_essid(): essid() is not a correct essid!
exalt_wifi_scan_stop(): no scan launch !
wifi_set_current_essid(): essid() is not a correct essid!
*** stack smashing detected ***: exalt terminated
zsh: abort (core dumped)  sudo exalt

---

### Post by Perfex on 2007-06-27
I started using wicd give it a try ;) (attached)

---

### Post by gspearing on 2007-07-05
> **Perfex said:**
> I started using wicd give it a try ;) (attached)

I just wanted to say many many thanks for posting this. I have also now installed wicd (1.27 I think). Quite simply what this has enabled me to do on the laptop is run Entrance and run straight into E17 with wireless as a startup application. I don't have to login to Gnome, use network manager, logout, and then login to Enlightenment. 

Quite brilliant! :D

---

### Post by zero244 on 2007-07-05
I used E17 for a while and thought it was cool. 
It worked very well. The only problem I ran into was the font size in some windows was just too small to use.
I was able to get some of the font sizes bigger, but some menu items would not except larger font sizes.
Apparently some menu's are hardwired to a certain font size.
Maybe there is a way to deal with that problem.

---

### Post by Perfex on 2007-07-05
Hmm not sure what that problem is, more details or a screenshot?
Whats resolution are you using?

---

### Post by gspearing on 2007-07-06
Interesting.

Now that I am logging straight into Enlightenment using Entrance the font size of applications is slightly too big. To fix it  I load the Gnome Control Center and load the Font tool. Simply by loading the tool it corrects the application font sizes!

How can I ensure that Enlightenment application font sizes (eg Firefox) are correct without having to load the Gnome font tool? Is there a control somewhere to do that?

---

### Post by gspearing on 2007-07-06
> **gspearing said:**
> How can I ensure that Enlightenment application font sizes (eg Firefox) are correct without having to load the Gnome font tool? Is there a control somewhere to do that?

Fixed it. Created a blank .gtkrc-2.0 in my home directory.

File content:

gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Mist"
gtk-icon-theme-name = "Mist"


That seems to work nicely.

---

### Post by TravMan63 on 2007-07-28
I remember looking at enlightenment 2 yrs ago thinking it would be fun to try...it looked great then
1st use was on a Knoppix DVD - it's matured much since then.

I've just started on e17; I'm sure I have much to learn about it...

Here are my short/fragmented/noob observations:

Merged the sources list from elive to ubuntu to install.  Did most over of install over ssh.

I've used for a couple of days. It seems to run well.  It looks 'pretty'.  (I've used one of the dark themes).
Installing one of the moving backgrounds - did nothing.

Firefox - data entry points (search box, address bar etc) are all too dark.

I've used fluxbox in the past (DSL) - it's like 'fluxbox on steroids'.

Things I need to do to make it more use able - add installed programs to the menu.  (the 'update menu command' worked in elive ok)
Fix/edit icons.
No success in getting entrance to work.
I added a 'home folder' to the 'dock', but that crashed the wm.
The sounds that are on the elive distro/live cd - are not working yet.  Maybe that's good.

Not real fond of the control panel design - it's 'neat', but - it can't be moved on the screen.  Change the overall shape of it/color to match theme and it would be better.

Wireless continues to work fine. (It didn't work at all on the elive cd)

I miss having a clock/date panel, as well as a static menu area (if you applications are full screen - you can switch desktops to access the menu and see the clock/date).  Adding gnome panel to the elive distro didn't work - haven't tried it on Ubuntu yet...

The install I have on Ubuntu has more options (in the user config panel?) than the elive gem cd.

TM

---

### Post by Happy_Man on 2007-07-28
I swear, I would absolutely LOVE to use E. If only it all worked......

For example, when I installed it today..... I could only use the default theme, because if I tried to use another one, all my menu text would disappear.

Last time I tried (About two months ago), it wouldn't let me change the wallpaper without segfaulting. 

The day the bugs are ironed out, I will be an E convert. Until then...... *sigh*

---

### Post by worldwithoutgurus on 2007-07-29
"I could only use the default theme, because if I tried to use another one, all my menu text would disappear."

This has nothing to do with ' E'. Use the source code for a fully functional  E17 desktop environment.

---

### Post by Mstrk242 on 2007-08-02
I am having the same problem with the menu text disappearing when I switch themes.  Also I'm using entrance, and when you go to select session menu (the pop-up on the left side) it's the same issue.  It does function, because if I click on empty spaces it will change it (depending on where I click)

Any idea how to fix this?  (I'm rather new to this, so if you'd be so kind as to give me instructions to follow I'd appreciate it)

---

### Post by sirrahn on 2007-08-03
Yep, I'm having the problem with the menus being blank also. I'm just trying to find a way of getting  back to the default!

Until E is packaged so that it just works for users it basically isn't ready for me. I try to use it but don't have the time to attempt to find fixes for the long list of problems so keep getting forced back to Gnome.

I wish the developers had a slightly different attitude towards its development - i.e. making some of the core features stable for users (eg the menus) rather than feeling they have to complete every possible feature (eg desktop icons) before anything is made stable. I imagine the basics could be considered pretty stable by now if they took this approach.

Actually does anyone know how to get back to the default theme - without being able to see any text in the menus?

---

### Post by Jhongy on 2007-08-03
Played around with the elive CD for the whole day a few days ago.

I was very impressed at how stable it was, out of the box -- everything 'just worked' -- including wifi & screen resolution (better than feisty in that regard)... BUT...

meh.

My biggest gripes:
-- Lots of icons in the launcher, but no tooltips (to be fair, my Gnome panels don't give tooltips for launchers either).
-- Open windows can completely occlude the launcher and application switcher
-- Control panel: Very cool for a game, but not so sure about its utility for an OS.
-- Very pretty -- especially the click/right-click menus in the dark theme. But not my cup of tea. Reminded me of old 2D PC games a bit. Much prefer a crisper, cleaner look, with 3D accelerated effects. (I think some of the good emerald themes, with nice transparent glows, are better). The twinkling stars weren't as cool as I expected.

elive is an incredibly solid preview of E17, but although Ubuntu took more setting up to "perfect" it, I was glad to get back home :-)

Based on my experience with elive, I don't plan on installing E17 as an alternative window manager yet.

---

### Post by Virgofenix on 2007-08-03
> **sirrahn said:**
> Yep, I'm having the problem with the menus being blank also. I'm just trying to find a way of getting  back to the default!

Actually does anyone know how to get back to the default theme - without being able to see any text in the menus?

And I thought I was the only one have this problem. Please help me in my thread:[http://ubuntuforums.org/showthread.php?t=516377](http://ubuntuforums.org/showthread.php?t=516377)

How do you get back to default?

---

### Post by Happy_Man on 2007-08-03
> **Virgofenix said:**
> And I thought I was the only one have this problem. Please help me in my thread:[http://ubuntuforums.org/showthread.php?t=516377](http://ubuntuforums.org/showthread.php?t=516377)

How do you get back to default?
Well, I kinda knew where on the menus the settings dialogs were (the clicking works, even if you can't see the text), so I guessed and eventually got it back.

---

### Post by Mstrk242 on 2007-08-03
What I did to get back to default was rename the entire .e directory in your home directory.  I renamed it to .e.old.  Then rebooted, and it re-created everything.  I just then copied all the binary configs (UGGG binary configs) that I had changed (the non theme ones.  I had made a lot of shelves, so I copied those configs over) and i got back to default.

Now, anytime I make a change, i copy my .e directory to .e.good in my home directory.  This way if I make a change that messes things up, I can just put my old config back.

I don't really care about the themes myself, I can live without those.   The only reason I'm trying to fix this issue is I like to use entrance, it's pretty.  But when when you hit the button to select your session manager (if you want something other than default) it's the same as the menu's on a non default theme, they're blank.

---

### Post by sirrahn on 2007-08-04
Thanks Mstrk242, after I posted I has a suspicion that might be the way to do it. Probably good to start again anyway. Its a pity some of these basis things don't work with a bit more reliability.

---

### Post by Virgofenix on 2007-08-04
<3 Mstrk242

---

### Post by TravMan63 on 2007-08-05
In reply to: Perfex...

> Some of the things I used to work around issues so far - vlc player if you maximize it .. well lets just say ctrl,alt,backspace .... I am using xine movie player now.. works just as good..

VLC is indeed a bit 'quirky' - sometimes it responds to 'f' to go out of fullscreen, sometimes not.  Seems to play better in Ubuntu...

I've used both xine and mplayer - and noticed sync problems with the audio (wmv files) - vlc is mucho better.

Another workaround for VLC....
fullscreen it - then bring the vlc controls to the front (usually alt tab) - 

(try ddesk - but again quirky (won't restore desktop - control alt 2 and wait....) and only works in e16) -- 

drag the control for VLC to a different desktop...

go back and view - switch to the other (desktop) to stop it...

try doing that with an open office impress session and it gets fun - but can be done - used a remote clicker to go between VLC and Impress - just n and p for next or previous video.  Guess I could have set that up for VLC too... hmmm

Also have Ubuntu on same machine - and Ubuntu is much more laggy on video (unless I crank the res down to say 800x600 (2Ghz 1GB Dell C840)...

---

### Post by Mstrk242 on 2007-08-07
It appears they've fixed the bug with the themes.  I did an update a few minutes ago (just apt-get, just had to add the repositories manually), and now all the themes work.  Entrance is working as well.   For all those that were having the same problem as me, update it.

---

### Post by Linuturk on 2007-09-06
I'm using e16 from the repos right now. Some of the applets are buggy, but once you get used to using e, it is hard to go back.

---

### Post by Peacepunk on 2007-09-20
I am a fanatic for a while now... love it, in whatever guise you take it:

the e16 version as available in ubuntu is great but outdated, epplets are buggy indeed, but on my laptop, a sub-tiny 1.3kg 10.1'widescreen thingy it's just the awesomest thing around, ultimate presentation tool to carry with you: beamer connects with xinerama, multimedia keys mapped for xmms, slide & transparency, unobfuscated desktop... drawbacks are: the 16.7 "ubuntu" version prevent you from co-installing e17 (fixed in e16.8), beware of e16menuedit2 (better to edit the config files by hand) & don't launch too many eppelts they tend to reproduce themselves freely!

e17 is running on my openSUSE dektop in RPM from january 2007 form, available in pacman repositories - it just works, rocks, and for a pre-alpha release it's been my tool of choice for many months now. everything is there, sound, deskshot, keybindings, individual window memory of every parameters,... the full monty, used on a real "production" machine for my everyday work

The "mature-est" version of e17, if you don't like CVS, is to be found on fedora 7 in the "didier" repositories; usually refreshed once a month, they don't offer as much features (where's the sound applet ç§µ$ù@# ?? ) but is definitely stable & has more native E apps than the SuSE rpm, being more recent.

I even toyed around a full CVS on a Slackware11 testebed, complete with entrance login manager, that's where you can feel these e people are working for real, and things do broke up by sometimes. Non-slack geeky fanatics could turn on to Gentoo as well where a lot of support is available.

And, last, eliveCD is probably the easiest way to get you a glimpse of e, being the sleek-mean-lean 16 or the jaw-dropping 17.

Enjoy. Go for it, especially if you find gnome tasteless, kde bulky & wanna see where xfce should go.

---

### Post by Blind Tiger on 2007-09-29
I've been customizing an install of e17 through alternating sessions of Gnome and E17.  The only error I have thus far is related to the language module -- there is a file path error or missing link.  It doesn't affect usability or performance though.  

My only two gripes are (1) the default file manager, and (2) a few missing menu icons.  For example, when selecting the "file" option from the main menu, it opens a simple window without a tree or side panel, and each successive double click opens yet another window.  Regarding the menu icons, I would like to add a launcher to the ibar for /home or "computer" but their are no available icons for those items, therefore a blank space is all you get.

I'm assuming there is a way to configure the window actions of the default file manager, but I have not found it yet.  I also think I can choose the option to use the gnome icons for all cases which may solve the icon issue.  But ideally I am hoping to find a module or extension to install that activates a robust file manager with complete icon sets for applications and utilities or other menu items.

---

### Post by Rupertronco on 2007-09-29
I just finished compiling and installing e17 on my laptop, thanks for giving me something to do while I'm stuck in this ruddy airport.

Eclair is being a pain for me, it installed just fine after I built all of the dependencies but it seems to be lacking functionality. 

The environment as a whole is a nice, fresh look. I installed the milky theme and it's spectacular. I think they might be trying too hard to add too many effects and it might lose some of its elegance. It has just enough effects right now to keep it simple and clean. 

They shouldn't be trying to compete with compiz and should keep emphasis on a moderate amount of effects and maintaining simplicity.

edit: ah ha! amarok works just fine! 

This is a perfect environment for everyday use. I usually use fluxbox when I'm going for pure speed, and gnome/compiz-fusion for eye candy.

---

### Post by Peacepunk on 2007-10-16
@ Blind Tiger:

I agree with you on the file manager, it's PITA. I had a conversation with Cartsen on the E mailing list, and that's just how HE likes it... And it's also the default for Nautilus in Fedora7... I can't get to it still, and when I need to move things or to open a lot of stuff I just use the split-pane feature of Konqueror which is my filebrowser of choice in e17.

A word of warning: e16 for sure, e17 maybe: if you want to use Nautilus you _have_ to issue the following command: 

nautilus --no-desktop 

otherwise you'll end up with your usual gnome layer & you wont be able to click & drop menus from anywhere as  featured in E.

You sure can configure any app to appear with any icon, starting option & such from the iBar applet, 

Cheers. E Rocks.

---

### Post by uwe_a on 2007-11-19
hello, i havnt read the whole thread but i was trying to install exalt, and was facing lot of problems, done many things, but i think what solved the problem of compiling exalt was 

#apt-get install e17-devel-extras

hope it helps somebody

---

### Post by smartboyathome on 2007-11-19
I am having no problems with e17, even after changing my theme. Have any of you who are having the blanking problem activated the bling module, by chance? If so, that is what is causing the blanking.

---

### Post by Zipster90 on 2007-11-19
I just downloaded it today during class and took it for a test drive. I thought it was really neat. I don't think I'll use it full-time for a while, but I'll still have fun tinkering with it.

---

### Post by lamegaptop on 2007-11-23
Thought I'd alert you to an easy way to try E17.... the gOS repos.

I did this -

 [http://ubuntuforums.org/showthread.php?t=602640&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=602640&highlight=enlightenment)

and it works. All I have is E17, none of the green stuff, but it works well. I get the occasional fault "this is really bad" sometimes, for example when I right click on a file on the desktop. I'd have to work on the networkmanager issue before I was to use it full time on my laptop. Fun to play with!

---

### Post by smartboyathome on 2007-11-26
There is another easy way to install e17, via this package:
[http://ruialeixopais.planetaclix.pt/linux/e17/](http://ruialeixopais.planetaclix.pt/linux/e17/)
It installs the latest Enlightenment for you (from CVS), and it comes without all the software you may not use.

---

### Post by NaplesBill on 2008-01-15
I solved the wireless problem by running a terminal session(after logging in to E17) and typing:

> sudo nm-applet

This allows it to connect using networkmanager and you can close the terminal window once it's connected.  It will also close the applet but it stays connected until the next boot.

** UPDATE **

I created a script to run:
> gksudo nm-applet

I then added the script as a menu item and added it to the startup applications.  I removed networkmanager from the startup applications.  I also placed the script application at the top of the startup list. Now I get prompted for the sudo password as soon as I login.  The tray icon is working perfectly.  Anyone know how to pass-through the sudo password?

---

### Post by molom on 2008-01-16
For anyone that is interested... Linux Mint E17 should be release January 2008 (This month). For anymore info - [http://linuxminte17.wordpress.com/](http://linuxminte17.wordpress.com/)

Cheers,
molom

---

### Post by Rui Pais on 2008-01-16
> **NaplesBill said:**
> ...

I created a script to run:


I then added the script as a menu item and added it to the startup applications.  I removed networkmanager from the startup applications.  I also placed the script application at the top of the startup list. Now I get prompted for the sudo password as soon as I login.  The tray icon is working perfectly.  Anyone know how to pass-through the sudo password?

Hi, try from a terminal:
```
sudo visudo
```
and add a line at the end:
```
<your_username> ALL=NOPASSWD: /full/path/to/nm-applet
```
replace *<your_username>* by your username and don't put the full path for nm-applet just to be sure it works without problems.
Save and exit (Ctrl+'X' and 'Y' to accept save)

Don't remember if a simple login make changes effective or it requires a reboot...

btw, what are you using as tray for icons?

---

### Post by NaplesBill on 2008-01-16
I'm going to try that now.  I used OpenGEU to install E17 and it includes a XFCE panel for the Gnome applets and Gnome systray items.  I understand that the next release of OpenGEU will eliminate the need for the XFCE panel.  Do you know of a better way?

*** UPDATE ***

It is now working without the password prompt.  Here is the VISUDO line that it took to get this working:
<user_id> ALL=NOPASSWD: ALL

I thought I had it working with the specific bin file but I kept getting a 0:0 connection refused error.  There must be another bin that needs permission.

Thank you very much for pointing me in the right direction!

---

### Post by Rui Pais on 2008-01-16
> **NaplesBill said:**
> I'm going to try that now.  I used OpenGEU to install E17 and it includes a XFCE panel for the Gnome applets and Gnome systray items.  I understand that the next release of OpenGEU will eliminate the need for the XFCE panel.  Do you know of a better way?

*** UPDATE ***

It is now working without the password prompt.  Here is the VISUDO line that it took to get this working:
<user_id> ALL=NOPASSWD: ALL

I thought I had it working with the specific bin file but I kept getting a 0:0 connection refused error.  There must be another bin that needs permission.

Thank you very much for pointing me in the right direction!

Hi again.
Sorry that it didn't work completely... That way with 'ALL' works, of course, but it skips the confirmation of password of all commands; not a good option (in security terms).

I made a quick search and found that it seems to be a not so easy answer as i thought. Here a full thread on the subject:
[http://ubuntuforums.org/showthread.php?t=187874&page=18](http://ubuntuforums.org/showthread.php?t=187874&page=18)
i didn't read it all, maybe it contains some tips you like.


About OpenGEU (i didn't noted yet it name had changed) implementation with xfce panels... well is far from elegant, and bring the annoying problem of the close of the session, that it's only "solved" by some equally dirty hack directly on code... don't know which solution the OPenGEU devs are implementing.

I personally don't use a systray, but i suggest stalonetray as an alternative independent app. But it didn't  work well with screenshot modules or when user set different wallpapers per desktop...

---

### Post by NaplesBill on 2008-01-16
> **Rui Pais said:**
> Hi again.
Sorry that it didn't work completely... That way with 'ALL' works, of course, but it skips the confirmation of password of all commands; not a good option (in security terms).

I made a quick search and found that it seems to be a not so easy answer as i thought. Here a full thread on the subject:
[http://ubuntuforums.org/showthread.php?t=187874&page=18](http://ubuntuforums.org/showthread.php?t=187874&page=18)
i didn't read it all, maybe it contains some tips you like.


About OpenGEU (i didn't noted yet it name had changed) implementation with xfce panels... well is far from elegant, and bring the annoying problem of the close of the session, that it's only "solved" by some equally dirty hack directly on code... don't know which solution the OPenGEU devs are implementing.

I personally don't use a systray, but i suggest stalonetray as an alternative independent app. But it didn't  work well with screenshot modules or when user set different wallpapers per desktop...
Well, I was just experimenting anyway but I don't like the reduction in security either.  For now, I just switched to WICD and I'm using the wlan module on the E17 dock.  It just works!

I installed the stalonetray but I'm not too impressed.  I also think the app menu system on E17 is pretty limited.  Why allow me to add applications without providing an easy way to delete them.

---

### Post by Rui Pais on 2008-01-16
> **NaplesBill said:**
> Well, I was just experimenting anyway but I don't like the reduction in security either.  For now, I just switched to WICD and I'm using the wlan module on the E17 dock.  It just works!

Yes, i have heard always good things of WICD.

> I installed the stalonetray but I'm not too impressed.  I also think the app menu system on E17 is pretty limited.  Why allow me to add applications without providing an easy way to delete them.

You can easily delete/change/edit Favorite menus from:
Main menu > Configuration > Configuration Panel > Menus > Favorite Menus

The Applications menus, are independent of e17. They are just the standard implementation of menus of freedesktop.org. It's not easy to edit (same as in gnome or xfce, that use them too) 
I do it from Gnome menus editor alacarte. I don't think that e17 now have one of they own...

---

### Post by NaplesBill on 2008-01-16
> **Rui Pais said:**
> Yes, i have heard always good things of WICD.



You can easily delete/change/edit Favorite menus from:
Main menu > Configuration > Configuration Panel > Menus > Favorite Menus

The Applications menus, are independent of e17. They are just the standard implementation of menus of freedesktop.org. It's not easy to edit (same as in gnome or xfce, that use them too) 
I do it from Gnome menus editor alacarte. I don't think that e17 now have one of they own...

I appreciate your help once again.  BTW, I don't have any icons for the drive partitions on my desktop.  Any ideas why and how can I add them?  If I plug in a usb drive I don't get an icon either, just the shortcut itself.

---

### Post by Rui Pais on 2008-01-16
> **NaplesBill said:**
> I appreciate your help once again.  BTW, I don't have any icons for the drive partitions on my desktop.  Any ideas why and how can I add them?  If I plug in a usb drive I don't get an icon either, just the shortcut itself.

umm... if it makes the link but not assign an icon, that sounds a theme problem.
what theme do you use? Have you check with the default from e17 (bling/golding)? or others from get-e.org? (the old ones, listed as outdated, should still work with openGEU)

---

### Post by NaplesBill on 2008-01-16
I've tried many themes but no icons?  They are set to use the "default" icon from the theme.

---

### Post by Rui Pais on 2008-01-17
> **NaplesBill said:**
> I've tried many themes but no icons?  They are set to use the "default" icon from the theme.

Hi, sorry this late answer... i was researching :)

The icons system of e17 it's a confusion (from old edj files to the slow semi-implementation of icons seen by .desktop files... well thats pre-alpha stuff)

Right now icons of e17 internal file manager and menus are controlled by:
Configuration > Configuration Panel > Appearance > Icon Theme 
(requires a Enlightenment > Restart from menu to take effect)

You can choose there which icon set use, from the ones you got on /usr/share/icons and ~/.icons. Just pick one that you like and have that icon implemented. 

Note that change theme will reflect too on icons of Main Applications. If you prefer to use your present theme and don't want changes you can add an icon for removable devices on the icon theme folder .../devices/ named drive-removable-media.png or gnome-removable-media.png (not sure)

hth

---

### Post by nlogax on 2008-01-21
> **NaplesBill said:**
> I solved the wireless problem by running a terminal session(after logging in to E17) and typing:



This allows it to connect using networkmanager and you can close the terminal window once it's connected.  It will also close the applet but it stays connected until the next boot.

I would highly recommend using WICD instead of NM-Applet - it is much more stable and seems to be less resource-intensive also.

There's a WICD tutorial [here](http://ubuntuforums.org/showthread.php?t=587010).

---

### Post by Cloudy on 2008-02-24
How do I install themes? I installed the themes to ~/.enlightenment/themes/[name of theme]/ and restarted Enlightenment, but I've had no luck in finding the themes I installed.

---

### Post by Rui Pais on 2008-02-24
> **Cloudy said:**
> How do I install themes? I installed the themes to ~/.enlightenment/themes/[name of theme]/ and restarted Enlightenment, but I've had no luck in finding the themes I installed.

Themes should go to:
~/.e/e/themes/
to change/choose themes:
Configuration > Themes

---

### Post by Nameless_one on 2008-02-24
Does anyone else find too mouse-driven for their taste? 

I only tried it for a couple of days some time ago (although I know I tried e17, not an earlier version), and I remember I had a few complaints, but mainly that. Do you think I just didn't give it as much time as it deserved?

---

### Post by molom on 2008-02-24
I want to use e17 and that is why I'm waiting eagerly for Maryan Linux and the OZOS Iso. Elive 1.0 is poor, I bet 2.0 is going to be REALLY good. I don't like OpenGEU (Just my opinion, but it is a very good e17 distro). I've used e17, but e17 has even gotten better recently. I was going crazy at how cool it was when I was using the dunnewind e17 build and when I open an app or window my cursor automatically moves swiftly to the window without me moving the mouse.

Cheers,
molom

---

### Post by psycosmyth on 2008-03-08
I'm using the development 1.6 of Elive right now. It is beautiful. It is not as buggy on my box but it did not load the right module for xserver, I had to use failsafe. I wish I could install this but there is no installer.
I am impressed at the Eteam's efforts. I am thinking of installing Kiwi and then E17. Any suggestions.
I am using PclinuxOS right now but I feel frisky:)

---

### Post by earlycj5 on 2008-03-08
> **Nameless_one said:**
> Does anyone else find too mouse-driven for their taste? 



No, I use keyboard shortcuts and the application launcher module myself.

---

