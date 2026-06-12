---
title: "Open R own console in Ubuntu"
date: 2010-04-09
forum: Education &amp; Science
---

### Post by windlove on 2010-04-09
Is there a way to open R own console in Ubuntu, rather to launch it from Terminal ?? 

Thanks

---

### Post by JoshStrobl on 2010-04-09
Something slick I like doing is CTRL + ALT + F1 to open up a full screen terminal. CTRL + ATL + F2 opens up a secondary fullscreen terminal meanwhile CTRL + ALT + F7 closes the terminal, but keeps the processes within the terminal running.

---

### Post by agm. on 2010-04-10
I've been using the package **[JGR]("http://jgr.markushelbig.org/JGR_on_Linux.html")**.  It's based off of java.  


Also, I've tried to get **[rKward]("http://sourceforge.net/apps/mediawiki/rkward/index.php?title=Main_Page") **to work, but under gnome I've been having significant problems getting it to do what I need.  

[URL="http://sourceforge.net/apps/mediawiki/rkward/index.php?title=Main_Page"]
[/URL]

---

### Post by hzambran_cl on 2010-04-10
If you are looking for a GUI, you can look at:

[R GUI Projects]("http://www.sciviews.org/_rgui/")

---

### Post by gunksta on 2010-04-11
> **windlove said:**
> Is there a way to open R own console in Ubuntu, rather to launch it from Terminal ?? 

Thanks

Is it possible to start an R session without opening a terminal and then entering "R" at the command line? -- YES.

Is it possible to start an R session without running gnome-terminal/konsole -- Not directly.

Now, let me throw some details. Both of these answers assume you are using good old fashioned R. Of course, you can always install Rkward (a very nice tool) or several other GUI front-ends to R. One of the earlier posts has a link that should be useful. Another good option is to use Emacs or Vim to interface with R. But, these are all diversions from your initial question.

The rest of this answer assumes you are on Gnome (Ubuntu). If you are using Kubuntu or some other variant of Ubuntu, let me know and I'll try to adapt the directions. Go to System -> Main Menu and create a new launcher. For an example of what you need to create, look at the one found under "Debian". Look under Debian, Applications, Science, Data Analysis. There is a launcher there called GNU R. This is what you need to make (sorry, you can't cut and paste it -- yes, this sucks ). But, this shows you exactly how you need to make your launcher work. Once you have created this new launcher (Science would be a good place to put it), you should be able to push a button and launch an R session.

Conversely, you could make it start R with the default (ugly, but functional) Tk interface. Change the starting program to:

/usr/bin/R --gui="Tk"

And when you launch your new launcher, it will open with a "nice" Tk interface. Unfortunately, to the best of my knowledge, you will still need to open the terminal to get the Tk interface. If you can find a loop-hole to this, I'd love to know about it. 

If you poke around the system, there may be a better icon in there somewhere.

Unfortunately, I'm not sure any of this is a good idea. The "Tk" interface has a small problem. if you exit with q(), everything works as expected. If you close the window with the close button on the window, it closes the only open interface to R, but the actual R session continues to persist. The only way to stop R in this scenario is a "kill R" or "pkill R". Not exactly user friendly.

And, both the gui and non-gui version of R will (by defrault) set the working directory to ~. If you plan on doing more than one project with R, it's nice to have more than one easily accessible working directory. I find it easier to browse to the correct folder and start R from there, since will will auto load any saved data from your last session (if you asked it to). This is, for example, the default behavior or ESS (Emacs) and the Vim interface to R.

see:

?setwd
?getwd

for more information on R's working directories.

For the record - I do wish R had a nicer front-end for new users on Linux. Something similar to the Mac front-end would be really nice.

---

### Post by earlycj5 on 2010-04-12
> **agm. said:**
> 
Also, I've tried to get **[rKward]("http://sourceforge.net/apps/mediawiki/rkward/index.php?title=Main_Page") **to work, but under gnome I've been having significant problems getting it to do what I need.  

[URL="http://sourceforge.net/apps/mediawiki/rkward/index.php?title=Main_Page"]
[/URL]

You shouldn't.  I'm using it right now, yes, this instant, with Gnome, also used it extensively with OpenBox.

As usual, I agree with gunksta.  I wish that Linux has a nicer R front-end like Mac.  Personally I can't stand the Windows interface.  I do like RKward though for its tight integration with help searches, etc.

---

### Post by agm. on 2010-04-13
> **earlycj5 said:**
> You shouldn't.  I'm using it right now, yes, this instant, with Gnome, also used it extensively with OpenBox.
.

Well, after that, I decided to go ahead and try and fix my problems.  Searching around I found this **[thread]("http://ubuntuforums.org/showthread.php?t=894434")** that helped solve part of my problem.

It got the thing going, but then I decided to install from source and it is a much better install.  I'd recommend that people install it from source than install from repositories (I installed from repositories first).  They have good instructions on the rKward homepage and this was my first install from source and things weren't too bad.

This seems much better than JGR.

---

