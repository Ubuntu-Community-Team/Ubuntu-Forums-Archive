---
title: "Runewin - Runescape Linux Client"
date: 2009-11-22
forum: Gaming &amp; Leisure
---

### Post by Triggerhapp on 2009-11-22
----- **[Ubuntu installer]("http://bazaar.launchpad.net/%7Erunewin-team/runewin/trunk/download/triggerhapp%40desky-20120123144904-plvtdv6eo5ksvna4/runewininstaller.sh-20120123144858-hw23ess1vxhz84yu-1/RunewinInstaller.sh")** -----

**What is Runewin ?**

Runewin is a Client to the popular MMORPG Runescape, written in Python and using Mozilla libraries for Webpage viewing. Runewin has a plugin system that allows extra features to be added and has a built-in IRC client, which is simple, and yet scriptable. All Plugins, Sourcecode, Images and other files are released under the GPLv3 license

**Jagex is particular about 3rd Party Apps, Does Runewin conform to the rules?**

[http://runewin.wikidot.com/jagexrules](http://runewin.wikidot.com/jagexrules)
To my knowledge, Runewin follows all the Runescape rules regarding 3rd part Applications. Also, as the current developer of this code, I intend to keep it within these rules.

**I don't want any fancy features, I just want to play Runescape!**

Then Runewin probably Isn't for you.

**Any Screenshots?**
Screenshot 1 : Desktop mode, Playerstats plugin, config window, IRC and the RS front page
[[IMG]http://img69.imageshack.us/img69/7494/screenshot1s.th.png[/IMG]]("http://img69.imageshack.us/my.php?image=screenshot1s.png")

Screenshot 2 : Desktop mode, Edgeville bank in RS, Notepad plugin, IRC again
[[IMG]http://img687.imageshack.us/img687/8884/screenshot2m.th.png[/IMG]]("http://img687.imageshack.us/my.php?image=screenshot2m.png")

Screenshot 3 : Paned mode, RS Login, Playerstats plugin and IRC again
[[IMG]http://img694.imageshack.us/img694/8621/screenshot3zo.th.png[/IMG]]("http://img694.imageshack.us/my.php?image=screenshot3zo.png")

Just a small handful of screenshots.

**Info, Howto's and Links**

If you've got this far, why not give it a go and see if Runewin is for you.

[http://runewin.wikidot.com/](http://runewin.wikidot.com/)



The Wiki contains Information and Installers

Feel free to Post replies with problems, questions, comments, or whatever.

[SIZE=2]Obvious Note : I am in no way affiliated with Jagex or Runescape[/SIZE]

---

### Post by Vadi on 2009-11-22
bad link

---

### Post by Triggerhapp on 2009-11-22
Lol thanks : missed that on my proof read

---

### Post by Vadi on 2009-11-22
Still broken!

But found a [PPA]("https://launchpad.net/~runewin-team/+archive/ppa"), going to give it a try.

---

### Post by doorknob60 on 2009-11-22
Under Arch.

```
austin@austin-desktop ~/Compiled apps/runewin
 % ./runewin
Finding Plugins
runeinfo.calcs
runeinfo.calcs.extra
runeinfo.fastaccess
runeinfo.forums
runeinfo.gewatch
runeinfo.irctest
runeinfo.notepad
runeinfo.playerstats
runeinfo.test
--- Done Finding Plugins
[1]    2516 segmentation fault  ./runewin
austin@austin-desktop ~/Compiled apps/runewin
 %

```

And how the hell do you uninstall it? I ran setup.py but there's no way to uninstall, that's one of my biggest pet peeves when compiling software...

---

### Post by Triggerhapp on 2009-11-23
Not sure why it didnt fix the links when I edited. Just double checked them now.

And yeah, I don't use arch, but I do my own install from source, and distutils in python for some strange reason doesn't give an uninstall option.

Edit : Just read up a bit more, try using checkinstall to make temporary package which can be uninstalled using normal package managers

My advise is stick to packages where possible, until I find a reliable fix.

I'm also not sure what it could be segfaulting for, but I'm placing my bet on Mozembed not playing nice...

---

### Post by Triggerhapp on 2009-11-23
> **Vadi said:**
> Still broken!

But found a [PPA]("https://launchpad.net/~runewin-team/+archive/ppa"), going to give it a try.

That's the one, I update that whenever I commit

---

### Post by simplygar on 2009-11-23
Been using RuneWin for about a week now, loving what you've managed so far. Being an avid RS fan/nerd I'm finding the layout refreshing and the tools actually useful! It's possibly comparable to the old dog which CAN be taught new tricks. Be interesting to see what you manage after the initial development stages. Keep up the good work.

---

### Post by doorknob60 on 2009-11-23
Does anyone have a screenshot? Since I can't use it, I'd at least like to see what it's like :) Also, right now I'm gonna try to extract the deb file and see if that works rather than getting the source. EDIT: Nope, still doesn't work. Oh well, I'll try it maybe in a month, maybe something will have updated and fixed itself (easy to test, since I can't uninstall it...)

EDIT: Just tried it in a Ubuntu Vbox I had, and it's very nice. I suggest trying to get it to work on Arch. I'm gonna be brutally honest here, I hate developers that pretend Ubuntu is the only important distro, and I hate programs that only work on certain distros. One example I can think of off the top of my head is Adobe AIR. Good luck getting that working on anything other than Ubuntu, Fedora, or OpenSUSE (The installer actually fails saying you're using an unsupported distro). Actually, I think Python is to blame in this case though. What version of Python do you use for this in Ubuntu? Arch uses 2.6.

---

### Post by Triggerhapp on 2009-11-24
```

triggerhapp@triggtop:~$ python --version
Python 2.6.4

```

I understand your frustration, and I don't believe Ubuntu is the only important Distro, It's merely that I have not had enough chance, nor experience with many other Distros to test it on them, and Runewin currently lacks enough userbase of other distros (Gar is using Xubuntu, I use Ubuntu, not much incompatibility is likely to occur there)

Sorry I hadn't thought of screenshots before, Probably would make sense to include some.

I'm still interested in that Segfault, what Mozemebed version have you got, and which firefox?

---

### Post by Triggerhapp on 2009-11-24
Screenshot 1 : Desktop mode, Playerstats plugin, config window, IRC and the RS front page
[[IMG]http://img69.imageshack.us/img69/7494/screenshot1s.th.png[/IMG]](http://img69.imageshack.us/my.php?image=screenshot1s.png)

Screenshot 2 : Desktop mode, Edgeville bank in RS, Notepad plugin, IRC again
[[IMG]http://img687.imageshack.us/img687/8884/screenshot2m.th.png[/IMG]](http://img687.imageshack.us/my.php?image=screenshot2m.png)

Screenshot 3 : Paned mode, RS Login, Playerstats plugin and IRC again
[[IMG]http://img694.imageshack.us/img694/8621/screenshot3zo.th.png[/IMG]](http://img694.imageshack.us/my.php?image=screenshot3zo.png)

Just a small handful of screenshots.

---

### Post by Vadi on 2009-11-24
Submit news to linuxgames.com

---

### Post by MaximB on 2009-11-24
I never tried Runescape - but doesn't it already have a Linux client being java based and all ?

---

### Post by Triggerhapp on 2009-11-24
> **MaximB said:**
> I never tried Runescape - but doesn't it already have a Linux client being java based and all ?

Yes, this is where explaining becomes a bit more awkward, If you do not know much about Runescape.

Runescape is a very full game, if you're a member or if you're new to Free to Play, and Windows users have the option of using programs like SwiftKit, which has a handful of helpful features like Level Calculators, IRC and other scripts.

Runewin is a Client in this sense, it is not a replacement for going to [www.runescape.com](www.runescape.com) and clicking play, It's a replacement for SwiftKit and its ilk for those who want the extra functionality

---

### Post by Triggerhapp on 2009-11-24
> **doorknob60 said:**
> ...I suggest trying to get it to work on Arch..

I've only just got my Arch Vbox to show Xserver, that was a strange toy. Got Runewin up and installed, and getting the same segfault (I'm not suprised by that)


Working out the problem now should be fun :)

```

#!/usr/bin/python

import gtk
import gtkmozembed

w=gtk.Window()
m=gtkmozembed.MozEmbed()

w.add(m)
w.show_all()
gtk.main()

```

This Segfaults too.. I think we're missing something vital, rather than it being something wrong with Runewin

---

### Post by Triggerhapp on 2009-11-24
AHA!

```
export LD_LIBRARY_PATH="/usr/lib/xulrunner-1.9.1:$LD_LIBRARY_PATH"
export MOZILLA_HOME="/usr/lib/xulrunner-1.9.1"
export MOZILLA_FIVE_HOME="/usr/lib/xulrunner-1.9.1"
```

Now the test app and Runewin seem to work fine :)

---

### Post by Triggerhapp on 2009-11-26
Working out a few bugs as I speak

---

### Post by Triggerhapp on 2009-12-09
Updated with a few bug fixes, for those of you interested.

---

### Post by rasmus91 on 2010-05-04
Is this still being updated?

---

### Post by Triggerhapp on 2010-05-04
Not often enough! I keep meaning to put time aside to see if it's all still in shape

---

### Post by blazemore on 2010-05-04
I don't understand how everyone is able to play Runescape when I am not.  
I installed Ubuntu 10.04 32 bit. 
I have an Ati card. 
 
I  installed the graphics card drivers through Hardware Drivers tool. 
I  installed sun-java6-jdk package (provides jre and plugin) from the  Partner repository. 
 
Yet I can only get safe mode. 
Standard  mode says no, and HD just goes white.

---

### Post by Triggerhapp on 2010-05-04
"Standard Detail" is DirectX (therefore, Windows Only) and HD depends on your graphic card, and I have no idea about ATI cards, never owned one.

---

### Post by louis--taylor on 2010-05-04
This looks great! I am trying it out now :)

---

### Post by blazemore on 2010-05-05
I'm interested in working on this.
People please can you report bugs and I'll try and fix.
I'll email the patches on Launchpad, you can merge them yourself.

---

### Post by Triggerhapp on 2010-05-05
I'll be glad to have the help with this!

Currently I don't know of any bugs in the program (unless we count wish lists, and even then it's not much) But feel free to put forward ideas for improving it!

---

### Post by Triggerhapp on 2010-05-05
Scratch that, Icedtea java seems to cause it errors, and I still have that stupid dependency on Mozembed. Working on this a little now.

---

### Post by blazemore on 2010-05-06
> **Triggerhapp said:**
> Scratch that, Icedtea java seems to cause it errors, and I still have that stupid dependency on Mozembed. Working on this a little now.
Can't you use Webkit?

---

### Post by Triggerhapp on 2010-05-06
I can and that's what I was in the process of moving to last time I did work on it, sadly at that time it became apparent that Java didnt want to work AT ALL in webkit for me, so I gave it time. As it stands now, It semi-works but keeps throwing fits about RS's adverts which cause the whole thing to hang for minutes at a time.

---

### Post by Triggerhapp on 2010-05-12
Did an update, moved it most of it over to Webkit, and fixed up a few loose ends

---

### Post by HHx66 on 2010-05-12
You do know that, as far as I remember, I don't know if Jagex changed it or not so correct me if I am wrong, but using non-official clients with Runescape violates the TOS right? Just a warning in case thats still around to players.

---

### Post by Triggerhapp on 2010-05-12
[http://runewin.wikidot.com/jagexrules](http://runewin.wikidot.com/jagexrules)

The way Runewin is coded fits these rules 100%

---

### Post by HHx66 on 2010-05-12
Alright, I just making sure people didn't get in trouble over nothing, I just knew from a while back they cracked down on that, but that was back when I still played.

---

### Post by Triggerhapp on 2010-05-12
I'm aware of the situation, even made a note of it in the front page before ;)

I was, and am, very careful of the rules, since I am a fairly high level player and have no intention of getting banned.

---

### Post by Triggerhapp on 2010-05-26
doing some more porting to webkit, think i've removed the moz dependency totally in trunk

---

### Post by kingdogbert on 2010-07-28
Similar to blazemore, I'm trying to get hardware acceleration out of my Thinkpad and ATi card. It doesn't work in Firefox and it doesn't work in the official RS client (running under Wine); I only get safe mode.

I tried you're client, but the game doesn't pop up. All I get is one tiny little notepad/player-stat window:

[[IMG]http://img530.imageshack.us/img530/8711/screenshotku.png[/IMG]]("http://img530.imageshack.us/img530/8711/screenshotku.png")

There are only the two tabs shown (notepad and player stats) even if I make the window larger

The terminal output:
```

dean@fermi:~$ runewin
{'menu': '1', 'set': '1', 'x': '0', 'y': '0', 'w': '800', 'h': '550', 'skin': 'desktop', 'plugins': {'playerstats': '1', 'setup': '0', 'calcs': '0', 'calcs.extra': '0', 'threadwatch': '0', 'test': '0', 'notepad': '1', 'forum': '1'}, 'notepad': {'data': 'This is a persistant notepad. all changes in here will be kept.'}, 'irc': {'nick': 'unknown', 'ident': 'unknown', 'realname': 'unknown', 'autoroom': '#linuxrs', 'password': 'unknown', 'server': 'irc.swiftirc.net', 'port': '6667', 'serverpassword': ''}}
Finding Plugins
runeinfo.calcs
runeinfo.calcs.extra
runeinfo.eggtimer
runeinfo.fastaccess
runeinfo.forums
runeinfo.gewatch
runeinfo.irc
runeinfo.irc.test
runeinfo.notepad
runeinfo.playerstats
runeinfo.test
--- Done Finding Plugins
Starting
Using desktop
Done Setting up RS Window
Starting notepad
Starting playerstats
Done Setting up Plugins
** (runewin:6051): DEBUG: NP_Initialize
** (runewin:6051): DEBUG: NP_Initialize succeeded
** (runewin:6051): DEBUG: NP_Initialize
** (runewin:6051): DEBUG: NP_Initialize succeeded
** (runewin:6051): DEBUG: NP_Initialize
** (runewin:6051): DEBUG: NP_Initialize succeeded
** (runewin:6051): DEBUG: NP_Initialize
** (runewin:6051): DEBUG: NP_Initialize succeeded
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-4ubuntu3)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)

```

Any idea why I'm not getting a game window? Thanks

---

### Post by Triggerhapp on 2010-07-28
You're set to "Desktop" mode in your config, which means the game window appears over the top of your files on your desktop, but underneath every window you have open. Note that using "Show Desktop" currently also hides the RS window, and you're often left with no way to re-show it.

---

### Post by kingdogbert on 2010-07-28
Ok, I got it now. First I looked for some command-line options for the display mode, then I tried to find a config file, before randomly getting the game window to pop up and finding the settings menu, lol.

To anyone who has the same problem as me, make sur eyou don't have any applications maximized when you launch the client.

---

### Post by Simdog1 on 2010-07-30
how can i download it?

---

### Post by Simdog1 on 2010-07-31
nvm got it but i keep thinking its runescape its notihing like the rsps that ive played its like more coded you should trying making a rsps mainly for pking thats compatible with linux and windows ill show u an example [http://www.youtube.com/watch?v=yIC4-aeY00A](http://www.youtube.com/watch?v=yIC4-aeY00A)

---

### Post by Triggerhapp on 2010-07-31
> **Simdog1 said:**
> nvm got it but i keep thinking its runescape its notihing like the rsps that ive played its like more coded you should trying making a rsps mainly for pking thats compatible with linux and windows ill show u an example [http://www.youtube.com/watch?v=yIC4-aeY00A](http://www.youtube.com/watch?v=yIC4-aeY00A)

RSPS's are against jagex rules. This is a client to THE official Runescape game. It abides by their rules, and is an accepted alternative to SwiftKit.

---

### Post by RonB123123 on 2010-08-20
Is this client still in development? I've been making random runescape apps such as [here](http://ronak.comxa.com/runescape) and I'd like to help. I checked out Metis but that java client is outdated and seems to hang on loading worlds. Hope this one is up to date. :)

---

### Post by doorknob60 on 2010-08-20
I just made an AUR package for it, this was one of the easiest AUR packages I've made in a long time (thank god, my last one was a nightmare lol): [http://aur.archlinux.org/packages.php?ID=40072](http://aur.archlinux.org/packages.php?ID=40072)

---

### Post by Triggerhapp on 2010-08-20
> **RonB123123 said:**
> Is this client still in development? I've been making random runescape apps such as [here](http://ronak.comxa.com/runescape) and I'd like to help. I checked out Metis but that java client is outdated and seems to hang on loading worlds. Hope this one is up to date. :)

It's up to date, And I tweak it when I see a fix is needed. I've run out of inspiration right now on things to add, but I intend to keep this in perfect condition for a long time yet.

Please feel free to join the runewin-team on launchpad!

> **doorknob60 said:**
> I just made an AUR package for it, this was one of the easiest AUR packages I've made in a long time (thank god, my last one was a nightmare lol): [http://aur.archlinux.org/packages.php?ID=40072](http://aur.archlinux.org/packages.php?ID=40072)

Thanks for helping maintain Runewin :D
If theres anything I can do to make the job easier please give me a buzz, I'm happy people besides me are finally using it ;P

---

### Post by RonB123123 on 2010-08-20
Hi Triggerhapp,

I just installed RuneWin for Ubuntu 10.04 Lucid Lynx and discovered that the panels disappearing also affect my distro and not just Fedora's distro. When I first started RuneWin, I ran it from the command line by typing in "runewin" and noticed only the Player Stats and Notepad were displayed and my panels disappeared. 

I killed the notepad/stats window, checked my system monitor (all processes tied to runewin weren't running), so I ran the program again, this time from Applications > Internet > RuneWin and this time it displayed the Main window, again removing my panels. I reloaded my panels by running "pkill gnome-panel"

What was really strange was that the panels (top and bottom) were invisible but they were still usable. If I clicked on the top left, it would have a drop down list of my applications, same with the panel on the bottom, I could change desktops and scroll through windows but the panels would be completely transparent.

Now, my main window was loading the RS applet but died suddenly. Is there a debug or error log that RuneWin outputs?

---

### Post by Triggerhapp on 2010-08-20
Runewin will output to a CLI if run from one...

The problem appears to be the Runewin window mode chosen, edit the file ~/.runewin (gedit/vi etc) and change the skin... something like...

> # Config for Rune Window
menu = 0
set = 1
x = 0
y = 0
w = 800
h = 550
skin = windowed 

the default "desktop" skin is a nicer appeal, but appears to have a bug I've never encountered before from Runewin (and I always use desktop mode)

Give me a shout on how windowed treats you, and remember that the key-combo Alt-M opens the menu (or hides it again)

---

### Post by Triggerhapp on 2010-08-20
bug fix pushed to bzr and packaged :)

Enjoy

---

### Post by doorknob60 on 2010-08-20
> **Triggerhapp said:**
> 
Thanks for helping maintain Runewin :D
If theres anything I can do to make the job easier please give me a buzz, I'm happy people besides me are finally using it ;P
Nah, it's a very simple package to make. Literally all I have to do is check it out from bzr and run this: python setup.py install --root=$pkgdir/ --optimize=1 Couldn't possibly be any easier :) Good job, I look forward to future progress on this program :) It's given me problems in the past (like when it sefaulted along time ago, and when I was mad that it wouldn't uninstall lol), but it works great now :)

[OFF TOPIC]You should see what a mess another package I'm maintaining has become:
```

build() {
install -d $pkgdir/usr/bin
install -d $pkgdir/usr/share/applications
install -d $pkgdir/usr/share/damnvid
wget http://damnvid.googlecode.com/svn/trunk/build-deb/damnvid -O $srcdir/damnvid/build-deb/damnvid
cp $srcdir/build-required-files.py $srcdir/damnvid/build-any/
cd $srcdir/damnvid
python -OO build-any/build-required-files.py
for files in `cat required-files.txt | grep -v ' '`
do
cp --parents "$files" "$pkgdir/usr/share/damnvid/"
done
IFS=$'\n'
for files in `cat required-files.txt | grep ' '`
do
cp "`echo "$files" | cut -d' ' -f1`" "$pkgdir`echo "$files" | cut -d' ' -f2`"
done
}
```
Oh man...at least it works now though so I'm done editing that :)

---

### Post by Triggerhapp on 2010-08-20
hah I aimed for simple to compile to save myself the headache of packaging...

I think right now I need inspiration for new plugins, or changes to allow better plugins. I use this daily to play Runescape, but cant think of much else I wish to add.

---

### Post by RonB123123 on 2010-08-26
TriggerHapp, there's a lot you could add. I'd say build up the plugin system and look at SwiftKit, add each of SwiftKit's features in a plugin form so the users can pick and choose what they want. :)

Some ideas could be...

- multiple compare statistics (more than 2 users compare)
- calculators (maybe generate items/images/exp from an XML page.. autoupdate XML from a website for updates)
- IRC
- maybe have your own high score page for all the people who use Runewin
- last fm/shoutcast/radio/pandora plugin
- screenshot tools
- maybe be able to choose a web rendering engine, like mozilla, so you can install adblock to remove runescape ads w/o jagex knowing
- a plugin for private servers ([http://www.moparscape.org/smf](http://www.moparscape.org/smf))
- item database/monster database
- a usermade list of usernames to keep track of (maybe like a clan to keep track who's the best of the best in the clan)
- price guide
- maybe something that watches item trends and suggests the best time to buy/sell an item for profit

[http://www.rs-tiko.com](http://www.rs-tiko.com) is also an interesting client

just a few ideas :)

~Ron

---

### Post by Triggerhapp on 2010-08-27
> **RonB123123 said:**
> TriggerHapp, there's a lot you could add. I'd say build up the plugin system and look at SwiftKit, add each of SwiftKit's features in a plugin form so the users can pick and choose what they want. :)

I've said it in every place, Runewin isn't meant to be an all-supplying package, I wish for people to get involved and add whatever they need.


> - multiple compare statistics (more than 2 users compare)

Cute, so a front end to the highscores on the website?

> - calculators (maybe generate items/images/exp from an XML page.. autoupdate XML from a website for updates)

Already got a calc going, needs work but it's there

> - IRC

Done

> - maybe have your own high score page for all the people who use Runewin

Hard to do this since runewin doesn't harvest names (or even passwords) for any reason, also easy to circumvent and extremely pointless


> - last fm/shoutcast/radio/pandora plugin

Its not a music player?

> - screenshot tools

I rather firmly believe this is the job of the WM. at any rate, if people disagree, it's one small script away for them

> - maybe be able to choose a web rendering engine, like mozilla, so you can install adblock to remove runescape ads w/o jagex knowing

This sounds cute, but I've found mozilla impossible to use for Https, sometimes even java... as for mozilla plugins? I've not seen hide nor hair of them in the mozilla plugin api

> - a plugin for private servers ([http://www.moparscape.org/smf](http://www.moparscape.org/smf))

Doing so would break runescape guidelines on 3rd party clients, I have no wish to EVER associate with private servers

> - item database/monster database

Semi-in-the-works along with the currently unfinished calc

> - a usermade list of usernames to keep track of (maybe like a clan to keep track who's the best of the best in the clan)

So like a wrapper for runescape highscores?

> - price guide

The GE? Still working on a price checker in the calc

> - maybe something that watches item trends and suggests the best time to buy/sell an item for profit

I have no care, nor expertise in trade manipulation to gain money, I wont know where to start suggesting to others how to do it, let alone writing a script to do it.

> [http://www.rs-tiko.com](http://www.rs-tiko.com) is also an interesting client

just a few ideas :)

Thanks for the ideas, but I simply feel you didnt bother to find out much about the reason this client was made, or its vision.

---

### Post by MakotoTheKnight on 2010-08-27
This is definitely an interesting little project here.  If I could use it, I would definitely be giving some tips to you, especially for a bit of polish here and there.  But alas, I cannot.

Good work so far though Triggerhapp, and I wish you much success. :)

---

### Post by Triggerhapp on 2010-08-28
Thankyou again Makoto :)

It's nice to have your input, even though you must for your own reasons not use this. It's a shame, I suspect you would rather like this... I know I'm stuck on it.

I'm running through a few ideas for new additions with my house mate. :D

Edit : I'm interested in your sig, you're a student programmer? what language are students programmed in?

---

### Post by Alateriel on 2011-03-03
I can't get it to work.  I launch the application and it all it does is flash the homepage and close.

Below is the message when executing from a terminal.

```
alateriel@alateriel-A770M-A:~$ runewin
{'menu': '1', 'set': '1', 'x': '0', 'y': '0', 'w': '800', 'h': '550',  'skin': 'desktop', 'plugins': {'playerstats': '1', 'setup': '0',  'calcs': '0', 'calcs.extra': '0', 'threadwatch': '0', 'test': '0',  'notepad': '1', 'forum': '1'}, 'notepad': {'data': 'This is a persistant  notepad. all changes in here will be kept.'}, 'irc': {'nick':  'unknown', 'ident': 'unknown', 'realname': 'unknown', 'autoroom':  '#linuxrs', 'password': 'unknown', 'server': 'irc.swiftirc.net', 'port':  '6667', 'serverpassword': ''}}
Finding Plugins
runeinfo.calcs
runeinfo.calcs.extra
runeinfo.eggtimer
runeinfo.fastaccess
runeinfo.forums
runeinfo.gewatch
runeinfo.irc
runeinfo.irc.test
runeinfo.notepad
runeinfo.playerstats
runeinfo.test
--- Done Finding Plugins
Starting
Using desktop
Done Setting up RS Window
Starting notepad
Starting playerstats
Done Setting up Plugins
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.5) (6b20-1.9.5-0ubuntu1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
/usr/bin/runewin:255: Warning: g_hash_table_foreach: assertion `hash_table != NULL' failed
  gtk.main()
/usr/bin/runewin:255: Warning: g_hash_table_insert_internal: assertion `hash_table != NULL' failed
  gtk.main()
/usr/bin/runewin:255: Warning: g_hash_table_lookup: assertion `hash_table != NULL' failed
  gtk.main()
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
/usr/bin/runewin:255: Warning: g_hash_table_find: assertion `hash_table != NULL' failed
  gtk.main()
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
python: /build/buildd/nspluginwrapper-1.2.2/src/npw-rpc.c:1225: do_recv_NPObject: Assertion `npobj != ((void *)0)' failed.
Aborted
alateriel@alateriel-A770M-A:~$ *** NSPlugin Viewer  *** ERROR: NPN_GetProperty() wait for reply: Connection reset by peer
*** NSPlugin Viewer  ***  WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue:  assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  ***  WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue:  assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  ***  WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue:  assertion failed: (rpc_method_invoke_possible(g_rpc_connection))

```I installed by adding the source```
ppa:runewin-team/ppa
``` and running the command ```
sudo apt-get install runewin
``` through terminal.  Is there anything I can do to solve the problem?

---

### Post by kamicc on 2011-08-27
Today got these:
```


java.lang.NullPointerException
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:649)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
java.lang.RuntimeException: Failed to handle message: width 1279 height 571 for instance 1
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:660)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
Caused by: java.lang.NullPointerException
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:649)
	... 2 more
sun.awt.image.ImageFormatException: Unsupported color conversion request
	at sun.awt.image.JPEGImageDecoder.readImage(Native Method)
	at sun.awt.image.JPEGImageDecoder.produceImage(JPEGImageDecoder.java:136)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:264)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:189)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:153)


```


```

	at java.util.zip.ZipFile.open(Native Method)
	at java.util.zip.ZipFile.<init>(ZipFile.java:131)
	at java.util.jar.JarFile.<init>(JarFile.java:150)
	at java.util.jar.JarFile.<init>(JarFile.java:101)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJar(JarSigner.java:287)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJars(JarSigner.java:247)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.verifyJars(JNLPClassLoader.java:903)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:389)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
java.util.zip.ZipException: error in opening zip file
	at java.util.zip.ZipFile.open(Native Method)
	at java.util.zip.ZipFile.<init>(ZipFile.java:131)
	at java.util.jar.JarFile.<init>(JarFile.java:150)
	at java.util.jar.JarFile.<init>(JarFile.java:101)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJar(JarSigner.java:287)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJars(JarSigner.java:247)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.verifyJars(JNLPClassLoader.java:903)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:389)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:604)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:395)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:395)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
java.lang.NullPointerException
	at net.sourceforge.jnlp.NetxPanel.runLoader(NetxPanel.java:99)
	at sun.applet.AppletPanel.run(AppletPanel.java:380)
	at java.lang.Thread.run(Thread.java:636)
java.lang.NullPointerException
	at sun.applet.AppletPanel.run(AppletPanel.java:430)
	at java.lang.Thread.run(Thread.java:636)
java.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
java.lang.RuntimeException: Failed to handle message: handle 102793040 for instance 1
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:660)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
Caused by: java.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	... 2 more
java.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
java.lang.RuntimeException: Failed to handle message: handle 102794838 for instance 2
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:660)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
Caused by: java.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	... 2 more

```

also, set of time-outs and warnings about unsafe
```
** Message: console message:  @1: Unsafe JavaScript attempt to access frame with URL http://www.runescape.com/game.ws?j=1 from frame with URL http://services.runescape.com/m=advert/showbanner.ws?size=729&country=-1. Domains, protocols and ports must match.

```

buggy advert banner? :/

Ubuntu 10.04 version from PPA with
```


java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.9) (6b20-1.9.9-0ubuntu1~10.04.2)
OpenJDK Server VM (build 19.0-b09, mixed mode)

```

---

### Post by kamicc on 2011-08-28
and today got this:
```


runewin
{'menu': '1', 'set': '1', 'x': '0', 'y': '0', 'w': '800', 'h': '550', 'skin': 'windowed', 'plugins': {'playerstats': '1', 'setup': '0', 'calcs': '0', 'calcs.extra': '0', 'threadwatch': '0', 'test': '0', 'notepad': '1', 'forum': '1', 'eggtimer': '0', 'gewatch': '0'}, 'notepad': {'data': ''}, 'irc': {'nick': 'unknown', 'ident': 'unknown', 'realname': 'unknown', 'autoroom': '#linuxrs', 'password': 'unknown', 'server': 'irc.swiftirc.net', 'port': '6667', 'serverpassword': ''}}
Finding Plugins
runeinfo.calcs
runeinfo.calcs.extra
runeinfo.eggtimer
runeinfo.fastaccess
runeinfo.forums
runeinfo.gewatch
runeinfo.irc
runeinfo.irc.test
runeinfo.notepad
runeinfo.playerstats
runeinfo.test
--- Done Finding Plugins
Starting
Using windowed
Done Setting up RS Window
Starting notepad
Starting playerstats
Done Setting up Plugins
** (runewin:31361): DEBUG: NP_Initialize
** (runewin:31361): DEBUG: NP_Initialize succeeded
** (runewin:31361): DEBUG: NP_Initialize
** (runewin:31361): DEBUG: NP_Initialize succeeded
** (runewin:31361): DEBUG: NP_Initialize
** (runewin:31361): DEBUG: NP_Initialize succeeded
** (runewin:31361): DEBUG: NP_Initialize
** (runewin:31361): DEBUG: NP_Initialize succeeded
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.9) (6b20-1.9.9-0ubuntu1~10.04.2)
OpenJDK Server VM (build 19.0-b09, mixed mode)
28-Aug-2011 22:02:13 sun.awt.X11.XToolkit processException
WARNING: Exception on Toolkit thread
java.lang.NullPointerException
	at sun.awt.X11.XEmbeddedFramePeer.getAbsoluteX(XEmbeddedFramePeer.java:265)
	at sun.awt.X11.XBaseWindow.getAbsoluteX(XBaseWindow.java:1159)
	at sun.awt.X11.XBaseWindow.toOtherWindow(XBaseWindow.java:746)
	at sun.awt.X11.XBaseWindow.toGlobal(XBaseWindow.java:784)
	at sun.awt.X11.XBaseWindow.toGlobal(XBaseWindow.java:767)
	at sun.awt.X11.XBaseWindow.toGlobal(XBaseWindow.java:758)
	at sun.awt.X11.XEmbeddedFramePeer.handleConfigureNotifyEvent(XEmbeddedFramePeer.java:136)
	at sun.awt.X11.XBaseWindow.dispatchEvent(XBaseWindow.java:1106)
	at sun.awt.X11.XBaseWindow.dispatchToWindow(XBaseWindow.java:1063)
	at sun.awt.X11.XToolkit.dispatchEvent(XToolkit.java:513)
	at sun.awt.X11.XToolkit.run(XToolkit.java:608)
	at sun.awt.X11.XToolkit.run(XToolkit.java:543)
	at java.lang.Thread.run(Thread.java:636)
sun.awt.image.ImageFormatException: Unsupported color conversion request
	at sun.awt.image.JPEGImageDecoder.readImage(Native Method)
	at sun.awt.image.JPEGImageDecoder.produceImage(JPEGImageDecoder.java:136)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:264)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:189)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:153)
Shutdown start - clean:true
*** glibc detected *** /usr/bin/python: malloc(): smallbin double linked list corrupted: 0x09550a00 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x211591]
/lib/tls/i686/cmov/libc.so.6(+0x6e710)[0x214710]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0xab)[0x21570b]
/lib/libglib-2.0.so.0(g_malloc0+0x3c)[0x93f13c]
/usr/lib/libgobject-2.0.so.0(g_closure_new_simple+0x2b)[0x30a7bb]
/usr/lib/libgobject-2.0.so.0(g_cclosure_new+0x34)[0x30ac14]
/usr/lib/libgobject-2.0.so.0(g_signal_connect_data+0x62a)[0x322c0a]
/usr/lib/libsoup-2.4.so.1(soup_socket_connect_async+0x1c7)[0x6f9f4e7]
/usr/lib/libsoup-2.4.so.1(soup_connection_connect_async+0x172)[0x6f813a2]
/usr/lib/libsoup-2.4.so.1(+0x34ff1)[0x6f9bff1]
/usr/lib/libsoup-2.4.so.1(+0x35138)[0x6f9c138]
/lib/libglib-2.0.so.0(+0x39661)[0x934661]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0x9365e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0x93a2d8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x187)[0x93a817]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0x10003c9]
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so(+0x15c6a8)[0xe2c6a8]
/usr/bin/python(PyEval_EvalFrameEx+0x479c)[0x80e0f9c]
/usr/bin/python(PyEval_EvalCodeEx+0x857)[0x80e2807]
/usr/bin/python(PyEval_EvalCode+0x57)[0x80e2907]
/usr/bin/python(PyRun_FileExFlags+0x12d)[0x81005ad]
/usr/bin/python(PyRun_SimpleFileExFlags+0xc2)[0x8100812]
/usr/bin/python(Py_Main+0xadc)[0x805de5c]
/usr/bin/python(main+0x1b)[0x805d03b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x1bcbd6]
/usr/bin/python[0x805cf81]
======= Memory map: ========
00110000-00134000 r-xp 00000000 08:05 16650      /lib/tls/i686/cmov/libm-2.11.1.so
00134000-00135000 r--p 00023000 08:05 16650      /lib/tls/i686/cmov/libm-2.11.1.so
00135000-00136000 rw-p 00024000 08:05 16650      /lib/tls/i686/cmov/libm-2.11.1.so
00136000-0014f000 r-xp 00000000 08:05 326185     /usr/local/lib/libatk-1.0.so.0.2511.1
0014f000-00150000 r--p 00019000 08:05 326185     /usr/local/lib/libatk-1.0.so.0.2511.1
00150000-00151000 rw-p 0001a000 08:05 326185     /usr/local/lib/libatk-1.0.so.0.2511.1
00151000-0015b000 r-xp 00000000 08:05 326043     /usr/local/lib/libpangocairo-1.0.so.0.2400.2
0015b000-0015c000 r--p 00009000 08:05 326043     /usr/local/lib/libpangocairo-1.0.so.0.2400.2
0015c000-0015d000 rw-p 0000a000 08:05 326043     /usr/local/lib/libpangocairo-1.0.so.0.2400.2
0015e000-001a2000 r-xp 00000000 08:05 16973      /lib/i686/cmov/libssl.so.0.9.8
001a2000-001a3000 r--p 00044000 08:05 16973      /lib/i686/cmov/libssl.so.0.9.8
001a3000-001a6000 rw-p 00045000 08:05 16973      /lib/i686/cmov/libssl.so.0.9.8
001a6000-002f9000 r-xp 00000000 08:05 15556      /lib/tls/i686/cmov/libc-2.11.1.so
002f9000-002fa000 ---p 00153000 08:05 15556      /lib/tls/i686/cmov/libc-2.11.1.so
002fa000-002fc000 r--p 00153000 08:05 15556      /lib/tls/i686/cmov/libc-2.11.1.so
002fc000-002fd000 rw-p 00155000 08:05 15556      /lib/tls/i686/cmov/libc-2.11.1.so
002fd000-00300000 rw-p 00000000 00:00 0 
00300000-0033d000 r-xp 00000000 08:05 59197      /usr/lib/libgobject-2.0.so.0.2400.1
0033d000-0033e000 r--p 0003c000 08:05 59197      /usr/lib/libgobject-2.0.so.0.2400.1
0033e000-0033f000 rw-p 0003d000 08:05 59197      /usr/lib/libgobject-2.0.so.0.2400.1
0033f000-003d2000 r-xp 00000000 08:05 53437      /usr/lib/libgdk-x11-2.0.so.0.2000.1
003d2000-003d4000 r--p 00093000 08:05 53437      /usr/lib/libgdk-x11-2.0.so.0.2000.1
003d4000-003d5000 rw-p 00095000 08:05 53437      /usr/lib/libgdk-x11-2.0.so.0.2000.1
003d5000-003fc000 r-xp 00000000 08:05 326035     /usr/local/lib/libpangoft2-1.0.so.0.2400.2
003fc000-003fd000 r--p 00026000 08:05 326035     /usr/local/lib/libpangoft2-1.0.so.0.2400.2
003fd000-003fe000 rw-p 00027000 08:05 326035     /usr/local/lib/libpangoft2-1.0.so.0.2400.2
003fe000-00416000 r-xp 00000000 08:05 53457      /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00416000-00417000 r--p 00017000 08:05 53457      /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00417000-00418000 rw-p 00018000 08:05 53457      /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00418000-00458000 r-xp 00000000 08:05 7351       /usr/local/lib/libpango-1.0.so.0.2400.2
00458000-00459000 ---p 00040000 08:05 7351       /usr/local/lib/libpango-1.0.so.0.2400.2
00459000-0045a000 r--p 00040000 08:05 7351       /usr/local/lib/libpango-1.0.so.0.2400.2
0045a000-0045b000 rw-p 00041000 08:05 7351       /usr/local/lib/libpango-1.0.so.0.2400.2
0045c000-00477000 r-xp 00000000 08:05 11164      /lib/ld-2.11.1.so
00477000-00478000 r--p 0001a000 08:05 11164      /lib/ld-2.11.1.so
00478000-00479000 rw-p 0001b000 08:05 11164      /lib/ld-2.11.1.so
00479000-00513000 r-xp 00000000 08:05 59209      /usr/lib/libgio-2.0.so.0.2400.1
00513000-00514000 ---p 0009a000 08:05 59209      /usr/lib/libgio-2.0.so.0.2400.1
00514000-00515000 r--p 0009a000 08:05 59209      /usr/lib/libgio-2.0.so.0.2400.1
00515000-00516000 rw-p 0009b000 08:05 59209      /usr/lib/libgio-2.0.so.0.2400.1
00516000-00517000 rw-p 00000000 00:00 0 
00517000-00545000 r-xp 00000000 08:05 34574      /usr/lib/libfontconfig.so.1.4.4
00545000-00546000 r--p 0002d000 08:05 34574      /usr/lib/libfontconfig.so.1.4.4
00546000-00547000 rw-p 0002e000 08:05 34574      /usr/lib/libfontconfig.so.1.4.4
00547000-00549000 r-xp 00000000 08:05 22685      /usr/lib/libXinerama.so.1.0.0
00549000-0054a000 r--p 00001000 08:05 22685      /usr/lib/libXinerama.so.1.0.0
0054a000-0054b000 rw-p 00002000 08:05 22685      /usr/lib/libXinerama.so.1.0.0
0054b000-0054d000 r-xp 00000000 08:05 44810      /usr/lib/libXcomposite.so.1.0.0
0054d000-0054e000 r--p 00001000 08:05 44810      /usr/lib/libXcomposite.so.1.0.0
0054e000-0054f000 rw-p 00002000 08:05 44810      /usr/lib/libXcomposite.so.1.0.0
00550000-0055d000 r-xp 00000000 08:05 52299      /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
0055d000-0055e000 r--p 0000c000 08:05 52299      /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
0055e000-00560000 rw-p 0000d000 08:05 52299      /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
00560000-00568000 r-xp 00000000 08:05 44111      /usr/lib/libXrender.so.1.3.0
00568000-00569000 r--p 00007000 08:05 44111      /usr/lib/libXrender.so.1.3.0
00569000-0056a000 rw-p 00008000 08:05 44111      /usr/lib/libXrender.so.1.3.0
0056a000-00570000 r-xp 00000000 08:05 28929      /usr/lib/libXrandr.so.2.2.0
00570000-00571000 r--p 00005000 08:05 28929      /usr/lib/libXrandr.so.2.2.0
00571000-00572000 rw-p 00006000 08:05 28929      /usr/lib/libXrandr.so.2.2.0
00572000-0057a000 r-xp 00000000 08:05 22583      /usr/lib/libXcursor.so.1.0.2
0057a000-0057b000 r--p 00007000 08:05 22583      /usr/lib/libXcursor.so.1.0.2
0057b000-0057c000 rw-p 00008000 08:05 22583      /usr/lib/libXcursor.so.1.0.2
0057c000-0057e000 r-xp 00000000 08:05 18472      /usr/lib/libXdamage.so.1.1.0
0057e000-0057f000 r--p 00001000 08:05 18472      /usr/lib/libXdamage.so.1.1.0
0057f000-00580000 rw-p 00002000 08:05 18472      /usr/lib/libXdamage.so.1.1.0
00580000-00584000 r-xp 00000000 08:05 24584      /usr/lib/libXfixes.so.3.1.0Aborted

```

:(

---

### Post by SemiJew on 2012-01-13
how do i know you wont keylog me using this? :s

---

### Post by Triggerhapp on 2012-01-13
So according to the three different bugs reported above, it looks like OpenJDK once again fails to work for runewin...

Also. If you're afraid of keyloggers, read the source code, it's in python so fairly simple to deal with.

---

### Post by SemiJew on 2012-01-13
I cant code for ****, lol. I use Linux b/c its the best OS there is atm (windows is trash, as is mac OSX) and imo stuff made by the community is usually better than stuff made by corporations. If a couple people could just reply to me saying they've used it etc. for an extended period of time (1 month+) and had no problems with their accounts being hacked etc. then that would be great.

Thanks, and if this isn't intended to keylog then great work! :)

---

### Post by SemiJew on 2012-01-13
can anyone vouch for this software? i really want it to be genuine :(

---

### Post by doorknob60 on 2012-01-14
> **SemiJew said:**
> can anyone vouch for this software? i really want it to be genuine :(

I've used it some and never had anything suspicious happen. I've had some look at the source code and there's nothing malicious at all, certainly a trustworthy program, and there's no reason I've seen not to trust Triggerhapp either :)

---

### Post by SemiJew on 2012-01-14
> **doorknob60 said:**
> I've used it some and never had anything suspicious happen. I've had some look at the source code and there's nothing malicious at all, certainly a trustworthy program, and there's no reason I've seen not to trust Triggerhapp either :)
ok thanks man, will definitely download this then!

---

### Post by Triggerhapp on 2012-01-14
It's not been updated in forever, since I've started playing again I really should update it...

Stat lookup probably doesnt work anymore, but everything else should be in order

---

### Post by SemiJew on 2012-01-20
im a complete linux noob, how do i install this?

---

### Post by SemiJew on 2012-01-21
> **SemiJew said:**
> im a complete linux noob, how do i install this?
^

---

### Post by Triggerhapp on 2012-01-23
> **SemiJew said:**
> im a complete linux noob, how do i install this?

[https://launchpad.net/~runewin-team/+archive/ppa](https://launchpad.net/~runewin-team/+archive/ppa)

Add the PPA to your system and then add install "runewin" package from your package manager.

---

### Post by SemiJew on 2012-01-28
> **Triggerhapp said:**
> [https://launchpad.net/~runewin-team/+archive/ppa](https://launchpad.net/~runewin-team/+archive/ppa)

Add the PPA to your system and then add install "runewin" package from your package manager.
I can't find anything with the word "package" on my system :(
also which PPA should i download, there are 5 i think - im running linux 11.10

---

### Post by Triggerhapp on 2012-01-28
On the very first post in this thread (on the first line too!) is a quick install script for ubuntu, courtesy of mang0 from irc. i've checked it through and it works fine.

download and run that, it should sort it out for you

---

### Post by SemiJew on 2012-01-28
> **Triggerhapp said:**
> On the very first post in this thread (on the first line too!) is a quick install script for ubuntu, courtesy of mang0 from irc. i've checked it through and it works fine.

download and run that, it should sort it out for you
sorry, im an idiot >.<

---

### Post by Triggerhapp on 2012-01-29
> **SemiJew said:**
> sorry, im an idiot >.<

Not at all, its a fairly new addition, it just helps to have it all in one place is all

---

### Post by meathdeath on 2012-06-17
Just how secure is this though? Im a paranoid freak when it comes to clients that come from anywhere but Jagex themselves.

---

### Post by Triggerhapp on 2012-06-20
Define secure, if you install plugins from an external source that you dont know, they could be malicious, but that requires root/sudo privs to do so. The program itself uses webkit to connect direct to runescape front page and if you choose to allow it then it will also connect to IRC. Other plugins will typically do as they say, if installed alongside or from my own PPA. Anyone who doesnt trust me is welcome to view the sourcecode and confirm for themselves.

I've put my name to quite a lot of other code that's opensource, so I have no reason to sulley it over a game I barely play these days :P

---

