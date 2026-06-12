---
title: "less known desktop"
date: 2008-03-09
forum: Desktop Environments
---

### Post by Drmgiver on 2008-03-09
Everyone knows about Gnome, KDE, and XFCE, are there any other maybe lesser known desktop environments out there?

---

### Post by mali2297 on 2008-03-09
[LXDE]("http://lxde.sourceforge.net/about.html")
[ROX]("http://roscidus.com/desktop/")
[CDE]("http://www.opengroup.org/cde/") (not free)

---

### Post by fracturedmorals on 2008-03-09
There are more.

Equinox -- [http://equinox-project.org/](http://equinox-project.org/)

Enlightenment (Technically a window manager, but they seem to bundle just enough apps to qualify) - [http://www.enlightenment.org/](http://www.enlightenment.org/)

---

### Post by Drmgiver on 2008-03-09
Is there a way to possibly put in Etoile into Ubuntu?

---

### Post by x1a4 on 2008-03-10
[AfterStep]("http://afterstep.org/") is an excellent GUI.  Check out [my AfterStep screenshots]("http://hex1a4.net/xubuntu/screenshots/?gallery=afterstep/").  

Another great GUI is [FVWM-Crystal]("http://fvwm-crystal.org/").  [My FVWM-Crystal screenshots]("http://hex1a4.net/xubuntu/screenshots/?gallery=fvwm-crystal/")

Another still is [WindowMaker]("http://www.windowmaker.info/").  [My WindowMaker screenshots]("http://hex1a4.net/xubuntu/screenshots/?gallery=window_maker/").  You can also augment AfterStep with WindowMaker components, and WindowMaker with AfterStep components. 

They are all in the repositories.

---

### Post by Drmgiver on 2008-03-10
I was a big fan of NeXT, those afterstep pics look great.  However not seeing Windowmaker in the repositories  I see windowlab, is that it?  Still looking at how to get etoile though.

Update:  I just tried using Afterstep after installing it from the repositories, the look was much better then its application in my opinion, I rely too much on a GUI, and it just wasn't applicable in that case.  I would definately recommend that one to someone that doesn't depend on GUI though.

---

### Post by x1a4 on 2008-03-10
> **Drmgiver said:**
> I was a big fan of NeXT, those afterstep pics look great.  However not seeing Windowmaker in the repositories  I see windowlab, is that it?  Still looking at how to get etoile though.

The WindowMaker package is named **wmaker**.  Other packages include: 
wmaker-data
wmaker-usersguide-ps
wmakerconf
wmakerconf-data  

WindowMaker applets begin with **wm**

---

### Post by x1a4 on 2008-03-10
> **Drmgiver said:**
> Is there a way to possibly put in Etoile into Ubuntu?

You can download Étoilé from [etoile-project.org]("http://www.etoile-project.org/") or if you have Subversion installed: ```
svn co svn://svn.gna.org/svn/etoile/tags/Etoile-0.2
```

Étoilé will not be added to the repositories because it's too early in its development.  Once the Étoilé team gets close to version 1, I'm sure it'll be added.

---

### Post by Drmgiver on 2008-03-11
Now this Windowmaker I can definately put to good use.  I did just install subversion so I could put in etoile via that command but I don't see it selectable.

---

### Post by SunnyRabbiera on 2008-03-11
the terminal! :D

or how about UDE?

---

### Post by jken146 on 2008-03-11
The terminal isn't a desktop environemnt, silly! ;)


I second ROX -- that's mainly because I remember the good old days of RISC OS on Acorn computers.  That was a nice GUI.

---

### Post by santiagoward2000 on 2008-03-11
Hi!
Not actually a DE, but there's [Ion]("http://modeemi.fi/~tuomov/ion/"). Doesn't it look awesome? :lolflag:

---

### Post by Drmgiver on 2008-03-11
Wanted to install equinox desktop environment so I could use my computer to introduce some windows people over to Linux as EDE looks alot like it. However I am a little bit lost as to how to install it. Could anyone help me out?

---

### Post by x1a4 on 2008-03-11
> **Drmgiver said:**
> Now this Windowmaker I can definately put to good use.

Yes WindowMaker is a pretty good GUI, and there are plenty of excellent GNUstep applications out there you can use in WM, though you can run any other Linux app as well, of course. 

> I did just install subversion so I could put in etoile via that command but I don't see it selectable.

That's because Subversion is a version control system for managing source code, which is what you downloaded.  You now have to compile it.  It was downloaded into the directory from which you executed **svn**.  You should move it to /usr/local/src/ and compile from there.  Look for files named README, INSTALL[ATION] and other text files which are sure to have installation instructions.  The Étoilé Web site also has [installation instructions]("http://www.etoile-project.org/etoile/mediawiki/index.php?title=Install").

Before you can compile and install, get yourself root priviledges like so: ```
sudo -s
``` and compile from the directory where the source resides by making it the working directory, ie: ```
cd /usr/local/src/etoile
```

**Remember, Étoilé is very early in its development stage and has been released for developers and testers.**

---

### Post by #Reistlehr- on 2008-03-11
> **santiagoward2000 said:**
> Hi!
Not actually a DE, but there's [Ion]("http://modeemi.fi/~tuomov/ion/"). Doesn't it look awesome? :lolflag:

Don't make fun of ion, it's an awesome wm..

---

### Post by Drmgiver on 2008-03-11
Exactly, don't make fun of Ion, when you can make fun of UDE's idea of window management and their "hex menu" :lolflag:

---

### Post by dark_phantom on 2008-03-12
> **mali2297 said:**
> [LXDE]("http://lxde.sourceforge.net/about.html")
[ROX]("http://roscidus.com/desktop/")
[CDE]("http://www.opengroup.org/cde/") (not free)

Never heard of LXDE or ROX, but ROX looks pretty ok.  Who would want to use CDE? lol

---

### Post by angry_johnnie on 2008-03-13
> **mali2297 said:**
> [LXDE]("http://lxde.sourceforge.net/about.html")
[ROX]("http://roscidus.com/desktop/")
[CDE]("http://www.opengroup.org/cde/") (not free)
You mean you actually got Rox-desktop working in Feisty?  How?  I keep getting into dependency problems.  :-(  Then I tried to install it in gutsy, but it didn't work either.

And how about amiwm?  It's the weirdest one I've found so far. :-)

---

### Post by mali2297 on 2008-03-13
> **angry_johnnie said:**
> You mean you actually got Rox-desktop working in Feisty?  How?  I keep getting into dependency problems.  :-(  Then I tried to install it in gutsy, but it didn't work either.


I haven't tried it. I just took the challenge to name a few less known desktop environments.

> **dark_phantom said:**
> Never heard of LXDE or ROX, but ROX looks pretty ok.  Who would want to use CDE? lol

I used CDE on Solaris back in the days. I remember it as a nice desktop with a professional look, not as childish as the desktops of today. I guess I'm getting old. :-|

---

### Post by dark_phantom on 2008-03-13
> **mali2297 said:**
> I haven't tried it. I just took the challenge to name a few less known desktop environments.



I used CDE on Solaris back in the days. I remember it as a nice desktop with a professional look, not as childish as the desktops of today. I guess I'm getting old. :-|

Don't get me wrong I don't hate it or anything, I still use it today at work in Solaris as well.  And only because we are not allowed to use anything else.  I just find anything else much better than CDE.

---

### Post by Drmgiver on 2008-03-20
> **angry_johnnie said:**
> 
And how about amiwm?  It's the weirdest one I've found so far. :-)

Amiwm doesn't look too much like a desktop environment at all, looks just like a (very) simple window manager.

---

### Post by cardinals_fan on 2008-03-20
They're technically window managers, but I can't believe that nobody's mentioned the *boxes!  Fluxbox and Openbox are the two that I've tried, and they're both very nice.

---

### Post by spupy on 2008-03-20
Emacs! :D


Seriously.,I use Fluxbox, but find Rox very interesting - it has some strange ideas which are not present in other DEs. Most actions in Rox use Drag'n'Drop - browsing, saving, (un)zipping, installing, deleting, renaming - almost everything is drag and drop. For example you drag a link from Firefox onto an icon to install a program! Or you drag an zipped text from firefox, drop it on the icon of the archiver program, it creates a small icon of the unzipped stuff, you drag that icon to the icon of the text editor, view the text, click save, another small window with a icon, drag that icon back to the archiver, drag the archived icon to the icon of the script that creates a new email with the file as attachment, click send. It's not a plausible scenario, but it demonstrates the wickedness of Rox. :)

---

### Post by urukrama on 2008-03-24
Have a look at this excellent list of window managers: [http://www.gilesorr.com/wm/table.html](http://www.gilesorr.com/wm/table.html)

I recommend Openbox or Pekwm. Icewm is nice too. Of the tiling window managers I like wmii.

---

