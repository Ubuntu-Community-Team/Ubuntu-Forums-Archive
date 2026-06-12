---
title: "install WINE screensaver in gnome-screensaver, possible?"
date: 2010-05-19
forum: Desktop Environments
---

### Post by mattkerle on 2010-05-19
ok, this is a curveball question I know...

There's an OSS screensaver on windows that I love called PixelCity (links:[blog post]("http://www.shamusyoung.com/twentysidedtale/?p=3220"), [github]("http://github.com/skeeto/pixelcity")). it's pretty cool. and it runs fine on my Ubuntu (Karmic 9.10) with wine.

Is there a way I can tell the gnome-screensaver about it so I can use it as one of my screensavers? I'm still fairly new to Gnome and the whole "screensavers as themes" thing is still confusing me...

I've found my themesdir and tried to create a .desktop file for it, but obviously I've gotten something wrong as it just doesn't show when I open the screensaver prefs dialog, no error, no message, it's just not there.

here's my pixelcity.desktop file:
```

[Desktop Entry]
Encoding=UTF-8
Name=PixelCity
Comment=A 3D animation of a City at night, completely generated procedurally
TryExec=wine /home/myuser/etc/pixelcity/pixelcity.scr /S
Exec=wine /home/myuser/etc/pixelcity/pixelcity.scr /S
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

I've had a look on the [Gnome admin guide]("http://library.gnome.org/admin/system-admin-guide/stable/screensavers-0.html.en") and the [desktop guide]("http://library.gnome.org/users/user-guide/2.29/prefs-screensaver.html.en"), neither of which are very helpful in terms of explaining the .desktop syntax.

It's quite likely that this can't be done, by the fact that I can run pixelcity as a fullscreen app with wine makes me think there's a possibility...

I've tried swapping to Xscreensaver, but that kills my lock-screen functionality, which is a deal breaker. I miss <super>+L too much.

Installing the xscreensaver packages added the extra screensavers I was missing, and I'm a pixelcity away from perfection...

Of course the perfect solution would be if someone ported the screensaver natively to linux, which shouldn't be too hard as the source is open, it already runs on openGL and tries to confine most windows stuff to a single file. But I don't know C++ or 3D code or win/linux internals so I wouldn't know where to start... :)

cheers!

---

### Post by emilywind on 2010-05-19
It seems okay. Just put it in /usr/share/applications/screensavers If it does not work after doing that, let me know.

---

### Post by mattkerle on 2010-05-20
> **emilywind said:**
> It seems okay. Just put it in /usr/share/applications/screensavers If it does not work after doing that, let me know.

so the .desktop file I have above is in the /usr/share/applications/screensavers directory as pixelcity.desktop, but still doesn't show up in the gnome-screensaver list... :-(

will gnome-screensaver be happy with a command such as "wine pixelcity /S" instead of the usual "scrnsvr -root"? At the moment the issue is trying to get it to be recognised as a screensaver by gnome, maybe there's somewhere else I need to config stuff?

---

### Post by Bob63 on 2010-05-21
> **mattkerle said:**
> so the .desktop file I have above is in the /usr/share/applications/screensavers directory as pixelcity.desktop, but still doesn't show up in the gnome-screensaver list... :-(

will gnome-screensaver be happy with a command such as "wine pixelcity /S" instead of the usual "scrnsvr -root"? At the moment the issue is trying to get it to be recognised as a screensaver by gnome, maybe there's somewhere else I need to config stuff?

Although I don't use the gnome-screensaver, I can tell you about xscreensaver which may help you. With xscreensaver installed, in your home directory is a hidden file **.xscreensaver**. This file holds user preferences and the command lines that xscreensaver uses to run the individual "hacks", or screensavers. The lines for a particular hack would read:
```
  GL:                 glplanet -root                    \n\
```This tells the xscreensaver app that it is OpenGL, the name of the hack, run it on a root window (something required by xscreensaver), and a \n\ end-of-line for the cli. Perhaps creating a similar line for pixelcity would work. You might have to drop the *wine* portion because I don't know if the xscreensaver cli would understand that. Also remember to put the -root after the screensaver options. With Really Slick Screensavers installed, the line(s) in the .xscreensaver file look like this:
```
GL:  "Really Slick Euphoria (bad math)"                      \
                  rs-euphoria -wisps 2 -background 2          \
                  -density 20 -visibility 35 -speed 30          \
                  -feedback 40 -feedbacksize 5 -root           \n\
```These screensavers add extra info to the line. The quoted section provides the hack name as it will appear in the screensaver list. This particular hack is called rs-euphoria, which is followed by space-separated options needed to make this configuration (bad math) work. Again, each option line is terminated by a backslash (\) for editor wrapping, and the option list ends with  -root and \n\.

Oh, and xscreensaver does allow screen-locking - it's on the bottom of the first configuration gui screen.

_***CAUTION!***_
I have ***not tried*** integrating an .exe-type screensaver, so I might be way wrong. Hope this helps.

---

### Post by emilywind on 2010-05-21
I tried getting to work and also ran into the same issue of it not showing up. I shall play around with it a bit more later. Cheers.

---

### Post by mattkerle on 2010-05-23
@Bob, thanks for the post. When I tried swapping to xscreensaver previously I followed [this howto]("http://ubuntuforums.org/showthread.php?t=195557"),(yes I probably shouldn't have followed a nearly 4yo howto!), and I could only lock the screen by adding a launcher to the panel and linking that to "xscreensaver -lock", which from a usability perspective gave me the willies. 

I'm too tied to <super> + L, I tried playing with the keyboard shortcuts applet but it didn't seem to respect the bindings. 

If it's possible to tie <super> + L (the windows key in a parallel universe...) to lock screen in xscreensaver I'd gladly swap!! gnome-screensaver does pretty much suck, why it disables screensaver configuring I have no idea, and it makes it so painful to add new screensavers.

Also, Pixelcity is a .scr file...

@emilywind, thanks, let me know if you figure anything out.

thinking maybe I should hit up the xscreensaver community and see if anyone would like to port it over... if it got rolled into one of the packages that would be ideal...

---

### Post by Bob63 on 2010-05-24
> **mattkerle said:**
> @Bob, thanks for the post. When I tried swapping to xscreensaver previously I followed [this howto]("http://ubuntuforums.org/showthread.php?t=195557"),(yes I probably shouldn't have followed a nearly 4yo howto!), and I could only lock the screen by adding a launcher to the panel and linking that to "xscreensaver -lock", which from a usability perspective gave me the willies. 

I'm too tied to <super> + L, I tried playing with the keyboard shortcuts applet but it didn't seem to respect the bindings. 

If it's possible to tie <super> + L (the windows key in a parallel universe...) to lock screen in xscreensaver I'd gladly swap!! gnome-screensaver does pretty much suck, why it disables screensaver configuring I have no idea, and it makes it so painful to add new screensavers.

Also, Pixelcity is a .scr file...

@emilywind, thanks, let me know if you figure anything out.

thinking maybe I should hit up the xscreensaver community and see if anyone would like to port it over... if it got rolled into one of the packages that would be ideal...

@mattkerle,
Out of curiosity, what version of xscreensaver have you tried? xscreensaver v5.10 is available in the lucid repos. Alternatively, it is possible to compile from source. (I'm not much of a programmer, but there are some tools available that can help with pulling in dependencies). Right now I am running LinuxMint 9 [Isadora] - Main. This is based on Ubuntu Lucid, so nearly all the apps and dependencies are from the lucid repos.

I am running xscreensaver v5.10 currently, but before I upgraded to Mint 9 I had compiled xscreensaver 5.11 from source and added the Really Slick Screensavers which I also compiled from source. Yes, it took several tries and some tweaking - mostly because I didn't understand the configuration options to use during compiling.

If you are not familiar with Really Slick Screensavers they are some OpenGL Windows screensavers that were ported to Linux after the author open-sourced his code and can be integrated with xscreensaver. It might be worth our while to contact one of the people who ported the Really Slick Screensaver package and see if they are interested in porting the PixelCity code (There are two different people who did that, so there are two very similar versions of the RSS that can run under the Linux/xscreensaver setup). I'm pretty sure I don't have the necessary skills to do this myself.

I used the same guide you did, BTW, to setup xscreensavers. It is starting to need updating, but generally works well enough that I can get the rest on my own.

Here's how to make the lock screen function work with xscreensaver from the keyboard:
1. System > Preferences > Keyboard Shortcuts
2. Click on the "Add" button
3a. Give the name you want displayed in the listing of shortcuts in the top Name text box
3b. in the bottom Command text box, type ***xscreensaver-command -lock***
4. Click "Apply" button
The new shortcut should appear at the bottom of the list under "Custom Shortcuts"
Next assign the key combination you want to use The text to the right of the shortcut name should read "New Shortcut..." Press the key combination you want to use. You may need to de-select the new shortcut and re-select it to make the "New Shortcut..." text appear. You will not get a text box to enter a key combo, the new key combo is applied immediately. I believe that the reason you need to create a custom shortcut for this is that the existing lock screen which appears in the keyboard shortcut list is mapped to the original gnome-screensaver's screen lock function. Since to make xscreensaver work it is necessary to disable the gnome-screensaver, the keymaps that  it uses are also disabled. This is how my keyboard shortcut looks after building a new lock screen shortcut and assigning it to use the "Windows" key+L (see thumbnail #2):

If you need more help let me know...:-\"

ps: I looked at PixelCity and the video and it looks pretty cool. Maybe I'll add that to my Windows screensaver collection, even though I don't use it (Windows) much. I also downloaded the source code from the person who is trying to port it to Linux. The original source code is all c++,; the fellow porting the code added a diff file which makes adjustments to the various source files for the Linux environment. I have not tried compiling it yet.

---

