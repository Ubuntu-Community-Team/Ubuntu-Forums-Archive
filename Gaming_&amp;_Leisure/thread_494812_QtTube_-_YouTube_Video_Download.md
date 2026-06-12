---
title: "QtTube - YouTube Video Download"
date: 2007-07-07
forum: Gaming &amp; Leisure
---

### Post by RainCT on 2007-07-07
Hey,

I've just released the first version of [QtTube](http://wiki.ubuntu.com/QtTube), a graphical application to download videos from YouTube.


[[img]http://img526.imageshack.us/img526/9079/qttubesmallio7.png[/img]](http://wiki.ubuntu.com/QtTube)


You can [download it from here](https://launchpad.net/qttube/0.x/0.1/+download/QtTube-0.1.tar.gz). To run it, just install the dependencies ([for Feisty](https://wiki.ubuntu.com/QtTube/Installation/Feisty) / [for Gutsy](https://wiki.ubuntu.com/QtTube/Installation/Gutsy)), extract it somewhere and run the executable ("qttube") by double-clicking on it and selecting "Run in a terminal". If you want to install it, follow [this instructions](https://wiki.ubuntu.com/QtTube/ManualInstall).

What do you think about it? :)


If you have any bug report or feature requests please [report them](https://launchpad.net/qttube/+filebug) on Launchpad.

*(I hope this is the right forum to post this, wasn't sure where to write it but because of "Leisure" I've chosen to do it here.)*

---

### Post by dfreer on 2007-07-07
Hmmm gonna have to check it out, screenshots look good!

---

### Post by jimminy_kriket on 2007-07-07
Nice, but why the gaming forum? :P

---

### Post by psmorgan on 2007-07-07
Gaming & **Leisure** ? ;)

---

### Post by RainCT on 2007-07-08
So, has anybody tried it?

---

### Post by MonkeyBoy on 2007-07-08
I just tried it.  Works very well but it would be handy if it turned the video files into avi or something more universal than fla.

I suppose I need to find a converting app for that.

---

### Post by RainCT on 2007-07-08
> **MonkeyBoy said:**
> I just tried it.  Works very well but it would be handy if it turned the video files into avi or something more universal than fla.

I suppose I need to find a converting app for that.

(You can convert it to ogg from command line with ffmepg2theora.)

And I'll add many conversion possibilities on QtTube 0.2 or 0.3, see [https://wiki.ubuntu.com/QtTube/Blueprints/format-conversion](https://wiki.ubuntu.com/QtTube/Blueprints/format-conversion) ;).

---

### Post by lordhebe on 2007-07-08
This is a program that downloads directly into AVI: [http://www.youtube-d.com/]("http://www.youtube-d.com/")

It's for windows, but it runs flawlessly under wine.

---

### Post by jephrandall on 2007-07-08
I'd rather support an application written natively for Linux. :p

---

### Post by RainCT on 2007-07-09
> **jephrandall said:**
> I'd rather support an application written natively for Linux. :p

:D

---

### Post by mindtrick on 2007-07-09
Nice job! A debian package would be awesome

---

### Post by RainCT on 2007-07-09
> **mindtrick said:**
> Nice job! A debian package would be awesome

Thanks :)

Yea, I'll make one once the program is a bit more complete (like version 1.0).

---

### Post by lordhebe on 2007-07-09
> **jephrandall said:**
> I'd rather support an application written natively for Linux. :p

Of course, but I'm just saying that there is a program that does it. I do think this program looks a lot easier to use though, unlike the windows one it actuall allows you to choose where to save it, and what you can call it, nice job!

---

### Post by waggygee on 2007-07-09
I tried to install qttube0.1 using the instructions at the link given, I got this response and Qttube did not run:

Traceback (most recent call last):
  File "./qttube.py", line 24, in <module>
    from PyQt4 import QtCore, QtGui
ImportError: No module named PyQt4

---

### Post by RainCT on 2007-07-09
> **waggygee said:**
> I tried to install qttube0.1 using the instructions at the link given, I got this response and Qttube did not run:

Traceback (most recent call last):
  File "./qttube.py", line 24, in <module>
    from PyQt4 import QtCore, QtGui
ImportError: No module named PyQt4

Have you also followed the "[for Feisty](https://wiki.ubuntu.com/QtTube/Installation/Feisty)" link?

You need to run this on a terminal to get the needed stuff:

```
sudo aptitude -y install python-qt4 && cd ~/Desktop && wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl && sudo mv ./youtube-dl /usr/local/bin && sudo chmod +x /usr/local/bin/youtube-dl
```

;)

---

### Post by waggygee on 2007-07-09
> **RainCT said:**
> How you also followed the "[for Feisty](https://wiki.ubuntu.com/QtTube/Installation/Feisty)" link?

You need to run this on a terminal to get the needed stuff:

```
sudo aptitude -y install python-qt4 && cd ~/Desktop && wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl && sudo mv ./youtube-dl /usr/local/bin && sudo chmod +x /usr/local/bin/youtube-dl
```

;)

Cool! It works! I knew I did something wrong! Thanks!:)

---

### Post by doomster on 2007-07-09
pretty good and flawless job:) ty :) another Linux native i wanted installed instead of using wine.

(still waiting for blizzard to release an Uber-Linux Patch for us wow gamers, to get rid of wine once and for all)

---

### Post by RainCT on 2007-07-09
Nice that you like it :D

I'm currently working on version 0.2, which probably * will feature:

 - Notification when a download finishes (if pynotify is available).
 - First file format conversion possibilities.
 - An installations script (which will also download and install youtube-dl, if needed).
 - Indicate currently downloaded / total video size.
 - Some other minor improvements.

(* This is what I think that I'll get into it, but it may some of the stuff, or it may get even more than expected.)

Any suggestion you have is welcome, just tell it either here or on [Launchpad](http://launchpad.net/qttube).

Also, some highlights that will come before 1.0 are making the application translatable, and (if I'm able to figure out a good way for that) continue aborted or failed downloads.

---

### Post by Extreme Coder on 2007-07-09
Great program RainCT! Me like a lot :)

A nice feature you could add is pausing/resuming downloads, but I don't know if that's possible..

---

### Post by era86 on 2007-07-10
This program is sexy... :)

---

### Post by Nehvrook on 2007-07-10
Worked fine for me. Good job :) I had been using an addon for firefox to download youtube video's but it wasn't as good as this.

---

### Post by RainCT on 2007-07-10
> **Extreme Coder said:**
> Great program RainCT! Me like a lot :)
> **era86 said:**
> This program is sexy... :)
> **Nehvrook said:**
> Worked fine for me. Good job :) I had been using an addon for firefox to download youtube video's but it wasn't as good as this.

Thanks. I'll speed up development of 0.2 :).


> **Extreme Coder said:**
> A nice feature you could add is pausing/resuming downloads, but I don't know if that's possible..

Okay, added it to TODO. If it's possible, it shouldn't be very difficult... Will have a look at it now ;)

---

### Post by RainCT on 2007-07-10
By the way, I've just created a mailing list for QtTube. Anyone is welcome to join it: [http://eurion.net/mailman/listinfo/qttube-dev_eurion.net](http://eurion.net/mailman/listinfo/qttube-dev_eurion.net).

---

### Post by Qwerty_ on 2007-07-10
Awesome application. Great job RainCT. :)

---

### Post by RainCT on 2007-07-19
**Current Status:**

 - Notification bubble when download finishes. [COLOR="DarkGreen"][IMPLEMENTED][/COLOR] (if *pynotify* is available).

 - Indicate currently downloaded / total video size. Edit: [COLOR="DarkGreen"][IMPLEMENTED][/COLOR]

 - Installation Script. Edit: [COLOR="PaleGreen"][MOSTLY IMPLEMENTED][/COLOR]

 - Translations. Edit: [COLOR="PaleGreen"][IN PROGRESS][/COLOR] (Brazilian Portuguese, Catalan, Galician, German, Spanish.)

 - Download Pausing. I started implementing this but didn't got it working yet. I don't think this will get into 0.2.

 - File Format Conversion. [COLOR="PaleGreen"][PLANNING][/COLOR]

 - Download URL Storage. [COLOR="DarkGreen"][IMPLEMENTED][/COLOR] (disabled by default)
   This feature, if enabled, will store the URL's from where it gets the videos you download to make re-downloading faster. It's a experimental feature and is basically only for developers (me) to make it faster to test QtTube.

 - Many other minor improvements, division of the Preferences window into tabs and new options added.

**[EDIT: The release of 0.2 will take a bit longer since I broke an arm and can't work on it until I can use it again.]**

---

### Post by cisforcojo on 2007-07-24
Good work, sir!

---

### Post by Kuoi on 2007-08-07
Thanks for this !!

---

### Post by glosman15 on 2007-08-07
Very nice, keep up the good work.

---

### Post by ashishgoel on 2007-08-17
awesome....

---

### Post by Tim T on 2007-08-19
Too bad on the arm mate, hope you recover soon!

I had a question for you though... would it be possible to add a button to play the downloaded file in VLC or some other media player after it's finished playing for even quicker gratification?

---

### Post by Polygon on 2007-08-19
hey,

you could implement the vixy code for conversions

its a website that does a darn good job at converting youtube videos, and the code is open source

[http://sourceforge.net/projects/vixynet/](http://sourceforge.net/projects/vixynet/)

although the only problem is that it doesnt seem to compile...... maybe you could work around that..?

but yeah vixy.net is the only conversion resource for me. everything else sucks and makes the sound all gross and stuff.

---

### Post by RainCT on 2007-08-25
> **Tim T said:**
> Too bad on the arm mate, hope you recover soon!


Thanks :)


> **Tim T said:**
> 
I had a question for you though... would it be possible to add a button to play the downloaded file in VLC or some other media player after it's finished playing for even quicker gratification?

I've tought on adding something like this, but I think I'll leave it for 0.3, since I want to just add some basic file format conversion to it and then finally get 0.2 out before adding more new stuff.

You could fill a Bug or Blueprint on [Launchpad](https://launchpad.net/QtTube) if you want to ensure that I don't forget about this.

---

### Post by RainCT on 2007-08-25
> **Polygon said:**
> you could implement the vixy code for conversions

Thanks, I'll have a look at this.

However, most probable is that I won't directly implement a specific way of conversion but instead allow to choose between many different external (terminal) programs to do the work, whose are predefined in an INI file that comes with the program.

I'm not sure if this is secure at all, but I don't think it's much of a problem and would be the most flexible option.

Any comments are welcome though. And it would also be nice if you can tell me what program calls you would like to see on it by default (just as you would write it on the terminal, using a placeholder as filename).

---

### Post by darkadvice on 2007-08-25
And how is this any different then just opening up your temp folder after going onto Youtube and having the video load?

---

### Post by hikaricore on 2007-08-26
> **darkadvice said:**
> And how is this any different then just opening up your temp folder after going onto Youtube and having the video load?

....

If you don't want to use it then don't use it.
Nothing wrong with having an opinion, but we don't need **trolls** here.

---

### Post by Martje_001 on 2007-08-27
Can somebody post an URL which works? Nothing works for me :(. I mean a youtube video :)

Btw: the error is:
Failed. Couldn't get the URL of this video

---

### Post by RainCT on 2007-08-27
> **Martje_001 said:**
> Can somebody post an URL which works? Nothing works for me :(. I mean a youtube video :)

Btw: the error is:
Failed. Couldn't get the URL of this video

Just a YouTube url, like *[http://youtube.com/watch?v=nPecBxM2f6c](http://youtube.com/watch?v=nPecBxM2f6c)* for example.

If you already tried this and it isn't working then the problem is that you either don't have youtube-dl installed or that you have a version of it that is too old. If you have the version from Feisty installed, uninstall it. Then run this:

```
sudo aptitude -y install python-qt4 && cd ~/Desktop && wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl && sudo mv ./youtube-dl /usr/local/bin && sudo chmod +x /usr/local/bin/youtube-dl
```

---

### Post by Martje_001 on 2007-08-27
Yeah! it's working now! However, I use Gutsy...

---

### Post by cmat on 2007-08-27
Does this thing do Google Video too?

---

### Post by RainCT on 2007-08-27
> **cmat said:**
> Does this thing do Google Video too?

No, at moment no. But it is planned that it'll support many other pages in the future.

---

### Post by cmat on 2007-08-27
> **RainCT said:**
> No, at moment no. But it is planned that it'll support many other pages in the future.

That's good to read :)

---

### Post by RainCT on 2007-09-29
Hey all,

Just wanted to say that now that I'm OK I'll probably get version 0.2 finally out soon.

---

### Post by odzk on 2007-10-02
thanks for this. will this work with other video downloading sites like you know heheheh

---

### Post by RainCT on 2007-10-14
Well, I've been working many hours today on QtTube and I decided that I will add the option to convert videos to another format after downloading, get the installation working decently and then finally release it and make a package for Ubuntu and Debian.

[img]http://img69.imageshack.us/img69/4134/qttubeconvertyz5.png[/img]

That's the option I finally choose for the format conversion. I'm implementing some sort of "plugin" system, that uses sh or bash scripts to do the conversion. You will be able to select a default [plugin](https://wiki.ubuntu.com/QtTube/Plugins) from the settings, and also switch it for a particular video with a new submenu in the "Edit" menu. The automatic plugin detection isn't working at all yet (probably because I did the first ones with sh, but my Bourne scripting isn't really good, I will try if they work better swtiching to bash), but I hope I'll get everything ready in 1-2 weeks.

**Edit:** Plugin detection is working now, thanks to the guys in #python.

---

### Post by icycool on 2007-10-22
hi,

        I tried installing Qttube on ubuntu 6.10 and got the following error when i executed ./qttube command:

Traceback (most recent call last):
  File "./qttube.py", line 372, in ?
    mainApp = Gui(sys.argv[1])
  File "./qttube.py", line 38, in __init__
    self.ui.setupUi(self)
  File "/home/ruby/Desktop/QtTube/src/ui_main.py", line 48, in setupUi
    self.progress_text.setTextInteractionFlags(QtCore.Qt.TextSelectableByMouse)
AttributeError: setTextInteractionFlags

I m new to linux ,kindly help.

thanks in advance

---

### Post by RainCT on 2007-10-22
icycool: What version of "python-qt4" do you have?

---

### Post by Conrad76877 on 2007-10-22
I too would like to support ONLY Linux software -->> :) In doing so, it will aid in software manufacturers being pushed for programming GAMES that run natively on Linux but..... if wine is used and people using Linux PURCHASE these games designed specifically for windows, the creators have NO reason to expend more energy (most importantly money) in designing games and software that natively runs in Linux. It is a VERY complicated matter! Good day all -->> Oh... it works good here too and I like ogg vorbis as it is OPEN SOURCE :) and I personally think it sounds better than mp3 compression.

Conrad

---

### Post by nalmeth on 2007-10-22
Hey, nice to see someone developing such an app for linux, hopefully the program matures nicely.

For the record, my preferred method is just having my /tmp folder open. Right after the youtube vid is cached, you can copy it directly from /tmp.

---

### Post by icycool on 2007-10-23
I have 4.0.1 version of python-qt4

---

### Post by RainCT on 2007-10-23
The problem is probable because the installed python-qt4 is too old. I try QtTube with 4.1-0ubuntu6 (Feisty) and now with 4.3-2ubuntu7 (Gutsy).

You can try opening all files in the src/ directory which name starts with "ui_" (ui_about.py, ui_main.py and ui_preferences.py) with your favourite text editor and removing all lines that contain "setTextInteractionFlags" from there, but there might still be other incompatibilities.

---

### Post by Fabiolas on 2008-06-07
> **RainCT said:**
> Have you also followed the "[for Feisty](https://wiki.ubuntu.com/QtTube/Installation/Feisty)" link?

You need to run this on a terminal to get the needed stuff:

```
sudo aptitude -y install python-qt4 && cd ~/Desktop && wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl && sudo mv ./youtube-dl /usr/local/bin && sudo chmod +x /usr/local/bin/youtube-dl
```

;)


Thank You.. I have the same problem and i fix it with your command..:guitar:

---

### Post by johnfu on 2008-06-14
HI,

I was using the 0.2 version, but when i download the file, it only 0k, not sure where have the problem!

thanks
jOHN

---

### Post by MaindotC on 2008-06-17
Has anyone heard of "Capture 'n Convert" and if so do you have a link?

---

### Post by pitingo on 2009-07-11
Hello Everybody! How to install it in jaunty? thanks!

---

### Post by RainCT on 2009-07-11
> **pitingo said:**
> Hello Everybody! How to install it in jaunty? thanks!

Download [http://edge.launchpad.net/qttube/0.x/0.2/+download/QtTube-0.2~pre1.tar.gz](http://edge.launchpad.net/qttube/0.x/0.2/+download/QtTube-0.2~pre1.tar.gz), extract it and run the included install script.

---

