---
title: "desktop launchers for applications that run in terminal behave oddly in 15.10"
date: 2016-01-26
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2016-01-26
I made .desktop files for some applications that run in the terminal and pin them to the unity launcher bar for convenience (set "Terminal = true" in .desktop files) In Ubuntu 15.04 they behave just like other desktop launchers when clicked (see first screen shot), but in 15.10, when clicked, a new icon of the terminal appears in the unity bar and the original launcher becomes inactive (second screenshot)

The desktop files are exactly the same, I just copied the ones in 15.04 over to 15.10. e.g the one for polymake (the application showed in the screenshot)
```

[Desktop Entry]
Version=1.0
Name=Polymake
Comment=run polymake in a terminal
Type=Application
Exec=polymake
Terminal=true
Categories=Math;Science;Education;
Icon=/home/monkeybrain/share/icons/polymake.png
Encoding=UTF-8

```

How can I make these launchers to behave like they do in 15.04? Thanks

---

### Post by mc4man on 2016-01-26
I'm likely seeing this wrongly but it seems 15.10 is more correct.

The 'job' of the launcher is to open a terminal & run a command in it. That's what 15.10 seems to be doing.
What would be the use case of the launcher remaining active for something that only exists/runs in the terminal?
(- vs launching an app in a terminal that exists/runs outside the terminal in it's own window.

---

### Post by monkeybrain20122 on 2016-01-26
I prefer the behaviour of 15.04 when I have several programs like this opened, it is a lot easier to keep track through the different launcher icons (just as you would with multiple non terminal apps) than having multiple instances of the terminal in the launcher bar (which terminal is what??)

---

### Post by mc4man on 2016-01-26
> **monkeybrain20122 said:**
> t is a lot easier to keep track through the different launcher icons (just as you would with multiple non terminal apps) than having multiple instances of the terminal in the launcher bar (which terminal is what??)

That's what I would never see, here all instances of a terminal use just one launcher terminal icon. 
In screen 1 (15.04) does that polymake icon control the terminal polymake is running in?
( and if so,  do you have a gnome-terminal icon pinned to the 15.04 launcher?

---

### Post by monkeybrain20122 on 2016-01-26
Seems to have something to do with StartupWMClass [here]("http://askubuntu.com/questions/396448/google-chrome-opens-in-a-new-window-in-a-new-launcher-icon") If I add StartupWMClass=gnome-terminal-server or StartupWMClass=Gnome-terminal to polymake's .desktop file then its desktop launcher remains active the terminal's launcher does not appear in Unity's bar (so far so good) but then polymake's .desktop file will be associated with every instance of the terminal regardless whether I am using polymake or not.

---

### Post by monkeybrain20122 on 2016-01-26
> **mc4man said:**
> That's what I would never see, here all instances of a terminal use just one launcher terminal icon. 
In screen 1 (15.04) does that polymake icon control the terminal polymake is running in?
( and if so,  do you have a gnome-terminal icon pinned to the 15.04 launcher?

Yes in 15.04 the polymake icon controls the terminal polymake runs in and only that one terminal (**Edited**: and the terminal icon doesn't appear separately) That is exactly what I want. I have several programs like polymake. I want each's icon to control the terminal that particular application runs in rather than having the terminal icon controlling all.

---

### Post by monkeybrain20122 on 2016-01-27
Digging around a bit, apparently something changed in the behaviour of the gnome-terminal going from 3.14 in Vivid to 3.16 in Wily. I think it has something to do with messing around with the --disable-factory mode somehow though I am not sure how it works except that it is related to exactly the behaviour I want in this thread. See [here]("https://penguindroppings.wordpress.com/2011/04/08/unity-and-me/")

> 

[LIST]
[*]***Update (2011/04/10):*** Custom launchers for  terminal applications can also be used, which can be very useful for  applications such as irssi and mutt. **The thing to remember is that  you&#8217;ll want to specify a different window manager class for the  terminal, otherwise after you start your application via the Launcher,  it will show up with all your other terminals and you can&#8217;t use a  superkey keyboard shortcut with it.** For example, to create a launcher to  login to another server, you can use something like the following for a  .desktop file (see above for how to get this into the Launcher): 
[*][Desktop Entry]
Version=1.0
Name=My Server
Comment=Login to my server
Exec=gnome-terminal --sm-client-disable --disable-factory --class=MyServer -x ssh -t myserver.example.com
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=utilities-terminal
StartupNotify=true
StartupWMClass=MyServer 
[*]***Update (2015/04/27):*** gnome-terminal removed &#8216;&#8211;disable-factory&#8217; ([https://bugzilla.gnome.org/show_bug.cgi?id=707899](https://bugzilla.gnome.org/show_bug.cgi?id=707899))  so if you were relying on it to separate different window manager  classes, this will no longer work. &#8216;mate-terminal&#8217; seems to be a  suitable replacement 
[/LIST]
 

in vivid I never had to apply the --disable-factory mumbo jumbo, everything just works,--the terminal is patched apparently by Canonical's dev. Ubuntu's changelog for the gnome-terminal [here]("https://launchpad.net/ubuntu/+source/gnome-terminal/+changelog").There have been several updates between vivid and wily involving the --disable-factory feature, though I don't quite understand it and am not sure whether the current behaviour is a bug or expected.

In  the meantime downgrading to gnome-terminal 3.14.2 restores this terminal per icon behaviour (the scrollbar area is a little ugly since the overlay scrollbar is removed in wily and 3.14.2 has not be patched, but it works 100% functionally) Since downgrading is not a perfect solution (and probably won't work in 16.04) so I will leave the thread open.

Edited: Also took the chance to test out your editdeb script. Instead of pinning the downgraded version I pumped up its version number so that it won't get upgraded. Worked like a charm, just had to change the output directory. Thanks!

---

### Post by monkeybrain20122 on 2016-01-29
Probably a better solution instead of downgrading would be to use the Mate-terminal and use the --disable-factory and --class options as the link suggested above. But gnome has removed the gsettings (same as dconf) option to set default terminal. It just says that it is deprecated and default terminal is handled now by GIO ??? I have wasted an hour googling it and still have no idea what GIO is except that gnome has now hard coded the terminal in some system library and the user simply has no option to change it %$$#@#???!!! (What's wrong with Gnome?? It has become a major pain to use because of its incessant removal of features and options. I really hope Unity 8 matures so I don't have to deal with gnome anymore)

So instead of wasting more of my time figuring out GIO I just removed gnome-terminal, installed the Mate-terminal and made a symlink from /usr/bin/mate-terminal to /usr/bin/gnome-terminal and change my .desktop file to

```
[Desktop Entry]
Version=1.0
Name=Polymake
Comment=run polymake in a terminal
Type=Application
Exec=gnome-terminal --disable-factory --class=polymake -x polymake
Terminal=false
Categories=Math;Science;Education;
Icon=/home/monkeybrain/share/icons/polymake.png
Encoding=UTF-8
StartupWMClass=polymake



```

Logged out and logged in and it works! Removing gnome-terminal apparently doesn't have any bad effect so far but probably need more testings to be sure. Tested on Fedora 23 (of course not on my working Ubuntu system :)) which has gnome-shell 3.18 and mate-terminal 1.12.1 so this is likely going to work in Ubuntu 16.04 as well.

---

