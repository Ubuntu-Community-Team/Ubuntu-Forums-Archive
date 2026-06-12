---
title: "gnome-screensaver and cycling through a random list of screensavers?"
date: 2009-04-11
forum: Desktop Environments
---

### Post by cfogelberg on 2009-04-11
Hi everyone,

One of the things I really miss in gnome-screensaver from xscreensaver is the ability to use a subset of screensavers that I like (and not have to watch the ones which are rubbish:)

I was flipping through gconf-editor recently, and I came across /apps/gnome-screensaver/cycle_screensaver (documentation: [http://www.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html]("http://www.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html")). I don't know what this does or how to configure it, but it seems to smell something like that feature of xscreensaver.

If anyone knows how to make gnome-screensaver cycle through a subset of the whole bunch of other screensavers I'd love to know how!

Thanks,
Christo

---

### Post by Niniel on 2009-05-07
I'd love to find out too.
In XFCE 4.6 it's as easy as checking (off) the savers you (don't) like. 
I suppose I could uninstall unwanted screensavers... but how?

Update: Looks like excluding individual screensavers from the random list cannot be done through the GUI due to decisions of the Gnome developers (kind of stupid, but oh well). Deleting individual screensavers/moving them away may the the only option. Supposedly, they are located in /usr/lib/xscreensaver.

---

### Post by cfogelberg on 2009-05-07
Sorry, I solved this a while back and I should have posted the solution here. It's a bit hacky but it works well. Here are the snippets from my changelog:

```
20090411 - Downloaded xfx screensaver settings (http://xfx.net/utilities/sss/index.htm). Tried to use the deb package but it was compiled for i386. 
20090411 - sudo apt-get install mono-mcs mono-gmcs (7mb; made decisions based on this webpage: http://www.builderau.com.au/program/dotnet/soa/Gallery-Installing-and-using-mono-on-Ubuntu/0,339028399,339279567,00.htm)
20090411 - Unzipped src tar.gz file; ./configure, make, sudo make install --- had to edit ./configure to specify $GMCS=gmcs2, makefile to change references to gmcs to say gmcs2
20090411 - This installed it to /usr/local/bin, /usr/local/lib, /usr/local/share/applications instead.
20090411 - gnome-screensaver was crashing because xfx screensaver app had written /apps/gnome-screensaver/cycle-delay to be a float, not an int
```

As you can see the solution is basically to download this app, hack the files up a bit to work with Jaunty, then manually edit the Gnome settings with gconf-editor because (I think) screensaver-xfx put a float in when it should be an int.

Best,
Christo

---

### Post by convert_mrta on 2010-06-28
I installed the .deb package which I downloaded from [http://xfx.net/utilities/sss/index.htm](http://xfx.net/utilities/sss/index.htm).

But I cannot find it in any of my menues.  I've tried invoking from Run Application with both Screensaver-settings and screensaver-settings.  Both "not found" and its' not in my list of known applications.

I also installed the .deb package a second time.  Got a message that the application is already installed - reinstall?   I clicked the affirmative.  

Still no luck 

Any ideas how to run it?

---

### Post by cfogelberg on 2010-06-29
Hi convert_mrta,

Unfortunately I've since installed 10.04 over the top of the install that had xfx on, so I don't have a running installation to hand that I can use to help you with.

Anyway, it sounds like it is installed. The question is where. Ideas and questions that might help... [LIST]
[*]Is it in /usr/local/bin? 
[*]What happens at terminal when you type screensaver (or whatever its name started with) and then hit tab a few times?
[*]Are there any useful log messages from when you installed it?
[*]What happens when you run "which screensaver-settings"
[*]What happens when you run "sudo find / -name screensaver-settings -print"
[/LIST]

---

### Post by convert_mrta on 2010-07-02
# s it in /usr/local/bin?

No

# What happens at terminal when you type screensaver (or whatever its name started with) and then hit tab a few times?

Nothing, no command is populated in the window
# Are there any useful log messages from when you installed it?

Also screensaver-settings at command prompt results in "command not found"

no log that I can see.

# What happens when you run "which screensaver-settings"

nothing, just goes back to command prompt

# What happens when you run "sudo find / -name screensaver-settings -print"

Finds 

/screensaver-settings-0.1/screensaver-settings
/usr/share/doc/screensaver-settings

the first contains what appears to be source code,
The second contains a changelog.Debian file

No executables

---

### Post by SoFl W on 2010-07-02
Removed by author

---

### Post by cfogelberg on 2010-07-03
> **convert_mrta said:**
> No executables

Hmmm, looking through the deb now you're right. Here is my changelog from when I installed it:

```
20090411 - Downloaded xfx screensaver settings (http://xfx.net/utilities/sss/index.htm). Tried to use the deb package but it was compiled for i386. 
20090411 - sudo apt-get install mono-mcs mono-gmcs (7mb; made decisions based on this webpage: http://www.builderau.com.au/program/dotnet/soa/Gallery-Installing-and-using-mono-on-Ubuntu/0,339028399,339279567,00.htm)
20090411 - Unzipped src tar.gz file; ./configure, make, sudo make install --- had to edit ./configure to specify $GMCS=gmcs2, makefile to change references to gmcs to say gmcs2
20090411 - This installed it to /usr/local/bin, /usr/local/lib, /usr/local/share/applications instead.
20090411 - gnome-screensaver was crashing because xfx screensaver app had written /apps/gnome-screensaver/cycle-delay to be a float, not an int

```

I don't remember whether it tried to make and install just from running the deb file or whether I installed it, saw it was source only and tried to make it myself but as you can see that did not work straight out of the box. Still, it only needed pretty minor modifications to get it working and something similar might work for you. Also you might have to edit some of the gnome settings manually after using the app (last of the changelog lines above).

Anyway, HTH :)
Christo

---

