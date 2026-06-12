---
title: "Better GUI for R"
date: 2008-03-14
forum: Education &amp; Science
---

### Post by homeriq5 on 2008-03-14
I tried using Rcmdr as a GUI for R and was a little disappointed, along with a few of the other GUIs that are available (hard to save plots, not really integrated into Ubuntu, weirdness when trying to run pasted code).  However, I stumbled upon a new package called RKWard which turned out to work pretty well and had a lot of extra features to boot.  I recommend that you linux R users give it a try!  

website:  [http://rkward.sourceforge.net/](http://rkward.sourceforge.net/)

---

### Post by earlycj5 on 2008-03-15
Yeah, I've recommended it here quite a bit in the past myself.

---

### Post by euler_fan on 2008-03-15
The other one you'll see lots of people around here supporting is JGR.

I'm more of a terminal+gedit guy personally.

---

### Post by earlycj5 on 2008-03-16
Every time I see people comment about being more of a "terminal" type person when RKward is brought up I have to wonder if they've used Rkward.  I'm sure it has built in "point and click type functions" but I've never used them.  I use it for syntax highlighting, the ability to run, edit, save script files directly from the editor, run one line, run highlighed, text completion make it worth it for me.

Now I'm not saying everyone has to use it, or you shouldn't use the terminal, but usually comments indicated to me that people haven't used it and just think it's a point and click affair.  It's much more powerful than that.

---

### Post by gunksta on 2008-03-17
I like JGR simply because it's available on every platform that R is available on. Thus, if I put my time in to learning a tool, it is the same no matter what platform I have to use. At work, I wind up using Windows a lot, so I appreciate not having to learn a new tool.

JGR doesn't provide as many tools as rkward, but it's close. Although Kate, Gedit, etc. can provide you with the syntax highlighting, I wind up working with many variables and after a while, it gets hard to remember what I need to call upon.

JGR lets me visually keep my data.frames organized, provides syntax highlighting, built-in R console, and draggable code capabilities.

And, if you run gnome you don't have to install the KDE-libs for a single application.

But, you do have to install the Java SDK, so the space saved is probably minimal. The directions on the website for installing onto Ubuntu worked well for me.
[URL="http://rosuda.org/JGR/linux.shtml"]
http://rosuda.org/JGR/linux.shtml[/URL]

---

### Post by spamalot on 2008-12-02
hi, this seems to be an old post, but nevermind. i'm getting sick of relying on editors that crash every now and then, so the simpler the better. 

How do you use gedit with R?

---

### Post by gunksta on 2008-12-02
install the gedit-plugins package

THEN start gedit. Edit the preferences to activate the embedded terminal.

Start R in the embedded terminal.

It is now "integrated".

I finally gave up on JGR, it's too much effort. I just learned how to run emacs. Now, the world is a happier place. the ESS mode on emacs is terrific.

---

### Post by spamalot on 2008-12-03
I guess I was getting impatient in fixing Rkward which in my case turned out to be simple:

[http://ubuntuforums.org/showthread.php?t=1000411](http://ubuntuforums.org/showthread.php?t=1000411)

But I'll probably need to try to embed the terminal into gedit at a later time, so thank!

---

### Post by krcabrer on 2009-05-25
Hi

I want to know if you can select some lines in gedit
and then send them to the embedded terminal with
R running.

Thank you for your help.


> **gunksta said:**
> install the gedit-plugins package

THEN start gedit. Edit the preferences to activate the embedded terminal.

Start R in the embedded terminal.

It is now "integrated".

I finally gave up on JGR, it's too much effort. I just learned how to run emacs. Now, the world is a happier place. the ESS mode on emacs is terrific.

---

### Post by samden on 2009-05-25
No, you can't. Which makes gedit fairly useless for R.

You can however do this with Kate, the KDE text editor (you can run it in gnome no worries).

Just install Kate, activate the embedded terminal, and look through the preferences - there are key commands to sent text to the terminal and you can edit them to whatever you want.

Or try Rkward if you want a full GUI.

I use Kate with R now, I used to use Rkward. Both work very well. 

And it saves me learning Emacs or Vim :)

---

### Post by danded on 2009-09-08
Hi,
as I said in this thread ([http://ubuntuforums.org/showthread.php?t=668688](http://ubuntuforums.org/showthread.php?t=668688)), I have made a simple plug-in for gedit and R here: [http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)
Hope it'll be useful for some (be warned: it's not a full GUI but just a wrapper for the R console!)

---

### Post by samden on 2009-09-09
Looks good! Testing it at the moment. 

Currently I'm using Gedit for LaTeX and Kate for R, it would be excellent if I could switch to the one editor for both. Good on you!

---

### Post by samden on 2009-09-09
Yes, that's just what I needed. Well done!

I particularly like the feature to define and run source code blocks, I can see that being really useful.

One question - is there any way to assign a shortcut key to "Run selection through R"? That is the feature I use most frequently.

To be more flexible than that, you might like to add a preferences option to change all shortcut keys and assign shortcuts to any command. Apart from that I can't see anything else the plugin really needs.

---

### Post by danded on 2009-09-12
> **samden said:**
> Yes, that's just what I needed. Well done!

I particularly like the feature to define and run source code blocks, I can see that being really useful.

Thanks!

> **samden said:**
> One question - is there any way to assign a shortcut key to "Run selection through R"? That is the feature I use most frequently.

To be more flexible than that, you might like to add a preferences option to change all shortcut keys and assign shortcuts to any command. Apart from that I can't see anything else the plugin really needs.

This is a very good suggestion: I just uploaded a new version (v0.3) which allows custom shortcuts (R->Configure R Interface->Edit keyboard shortcuts). There are two caveats, however:
1. gedit (actually, the plug-in) must be restarted for the new shortcuts to work (I'm pretty sure there is a better way to do it but my GTK knowledge is pretty limited :D) and
2. you cannot override shortcuts used by gedit (so, you have to accommodate "free" ones)

Hope this helps...

---

### Post by purgatori on 2009-09-12
While Rkward seems like a great program, I am not too fond of installing anything that pulls in half of KDE with it. That's some bloat I don't need.

---

### Post by samden on 2009-09-13
> I just uploaded a new version (v0.3) which allows custom shortcuts
That is absolutely ideal. Well done. I can finally ditch those KDE libraries I've been using to run R for the last year (with RKward, then Kate).

And thanks heaps for the very quick response to my suggestion. Finally there's an R editor I can recommend for Gnome with no caveats.

---

### Post by sputnik on 2009-09-13
I use ESS (Emacs Speaks statistics) an Emacs mode for R and S... but then I quite like Emacs.

I will have a go with some of these other recommendations, however

---

### Post by gunksta on 2009-09-13
I have used ESS for quite some time now. Over-all, I really like it, but I have had problems with larger data-sets jamming the system. I especially noticed this happening when I imported large SPSS data sets using the foreign package. (I define jammed as being a period of time adequate for me to get a soda out of the company fridge and back to my seat without anything happening, but when I do it in R directly, it takes only a few seconds to complete.) It should not take several orders of magnitude longer for it to run in EMACS.

Lately I have been using the new R and screen plugins for vim. When I use this combo, I have not experienced any hang-ups. The only "problem" I have is that for some reason when I go open a screen session from within vim, my color scheme gets all funky. When I start in screen, and then open a vim session, everything looks fine. I suspect this may be a bug in Konsole and not the vim-plugin though.

The biggest bummer with both EMACS and VIM is the learning curve. I don't like recommending it to someone who must simultaneously learn R and Vim/EMACS. R is a funny programming language until you get your head wrapped around it (then it is beautiful). Vim/EMACS are the same way. Trying to force a colleague at work to do both at the same time nearly ended her experimentation with R. Oops.

On the other hand, if you are already comfortable with these editors, these are absolutely lovely additions to your arsenal. I love 'em to pieces.

---

### Post by samden on 2009-09-13
> The biggest bummer with both EMACS and VIM is the learning curve.
Hence why I'm very happy to be able to stick with gedit. I tried vim for a while and decided it just wasn't worth the effort learning, since I'm only using R and not doing programming or anything else complicated.

---

### Post by earlycj5 on 2009-09-14
> **purgatori said:**
> While Rkward seems like a great program, I am not too fond of installing anything that pulls in half of KDE with it. That's some bloat I don't need.

Bloat?  Really?  I have ~5gb on my netbook for / and I still have ~1.5gb free with RKward installed (and everything else that I use frequently).  To each his own.  For me Thomas keeps improving it even though I use e17 and OpenBox for my WMs the tight integration with R is enough for me.

HD space is cheap these days, even on a 16gb SSD netbook.  JMO.

Having said that rgedit is looking good these days...

---

### Post by purgatori on 2009-09-14
> **earlycj5 said:**
> Bloat?  Really?  I have ~5gb on my netbook for / and I still have ~1.5gb free with RKward installed (and everything else that I use frequently).  To each his own.  For me Thomas keeps improving it even though I use e17 and OpenBox for my WMs the tight integration with R is enough for me.

HD space is cheap these days, even on a 16gb SSD netbook.  JMO.

Having said that rgedit is looking good these days...

I try not to have anything installed on my system that I don't use -- and I don't use KDE.

---

### Post by earlycj5 on 2009-09-14
> **purgatori said:**
> I try not to have anything installed on my system that I don't use -- and I don't use KDE.

I don't use KDE either but I do use RKward. I guess I'm using that stuff since RKward needs it.  :)

---

### Post by Ctulhu on 2009-09-14
Ok, I may be somewhat thick here but I don't get Rgedit to work (using Ubuntu 9.04 32 bit and R 2.9.2). I

- installed the gedit-plugins via Synaptic;
- downloaded Rgedit 0.3 from <http://sourceforge.net/projects/rgedit/files/Rgedit0.3.tar.bz2/download> and unzipped that, which results in a folder <Rgedit0.3>;

Then, I tried and

- once put the folder into /gnome2/gedit/
- another time put the contents of the folder into /gnome2/gedit/

Then, I started gedit and activated the embedded terminal, in which I start R (as mentioned in a previous post here). But I don't get a Rgedit plugin in Preferences>Plugins, I don't get the R menu as in the screenshot, nothing. Maybe a total dumb question but any idea what I am doing wrong?

C.

---

### Post by danded on 2009-09-14
> **samden said:**
> That is absolutely ideal. Well done. I can finally ditch those KDE libraries I've been using to run R for the last year (with RKward, then Kate).

And thanks heaps for the very quick response to my suggestion. Finally there's an R editor I can recommend for Gnome with no caveats.

Glad you find it ok. On the other hand, again, it's quite different in concept from rkward in the sense that this is just an editor for R with minimal stuff added while rkward is great if you want to inspect your variables from the IDE, have a menu-driven interface, etc.

Personally, I needed a light-weight GTK alternative to rkward (which I used for quite a while) because of two things: 
1) KDE4 is not stable/polished enough for me (personal taste) and rkward 0.5 has some issues, while KDE3 + rkward 0.4 which were ok are now basically dead, and 
2) rkward was painfully slow sometimes when processing large datasets (compared to R itself) and it would also sometimes crash, bringing down R with it as well.

Now, rgedit has not been tested sufficiently long to rule out crashes but it seems stable so far and given that it does not interface in any way with the R engine except through the command line, it does not slow R down either.

---

### Post by danded on 2009-09-14
> **Ctulhu said:**
> Ok, I may be somewhat thick here but I don't get Rgedit to work (using Ubuntu 9.04 32 bit and R 2.9.2). I

- installed the gedit-plugins via Synaptic;
- downloaded Rgedit 0.3 from <http://sourceforge.net/projects/rgedit/files/Rgedit0.3.tar.bz2/download> and unzipped that, which results in a folder <Rgedit0.3>;

Then, I tried and

- once put the folder into /gnome2/gedit/
- another time put the contents of the folder into /gnome2/gedit/

Then, I started gedit and activated the embedded terminal, in which I start R (as mentioned in a previous post here). But I don't get a Rgedit plugin in Preferences>Plugins, I don't get the R menu as in the screenshot, nothing. Maybe a total dumb question but any idea what I am doing wrong?

C.
Hi [Ctulhu]("http://ubuntuforums.org/member.php?u=434351"),

I think it's a spelling error in your path: it should be ./gnome2/gedit/plugins and you should put the contents of the <Rgedit0.3> folder in there. Now, your ./gnome2/gedit/plugins folder should contain something like: 
RCtrl.gedit-plugin 
RCtrl.py 
RCtrl.preferences
RCtrl.gedit-plugin
RCtrl   <- this is a folder

I'll make the readme clearer, my fault, sorry :) Hope this helps you getting it to work...

---

### Post by samden on 2009-09-14
Ctulhi:
I think danded made a spelling error too! It should be:
```
~/.gnome2/gedit/plugins
```
.gnome2 is a hidden folder. To see it in Nautilus you will need to go to the View menu and select "Show Hidden Files".

Danded:
Sure it doesn't have the features of rkward. But I've never used those features anyway. I started using R with the native Mac OS X interface, purely using code, and it has frustrated me that every other tool seems to have all these menus full of stuff I never use. :) Which is why I had already switched from Rkward to the Kate text editor (from which you can start R in a terminal in the bottom pane and pipe commands to it, similar to what you've done with Rgedit). The main frustrating thing was that I was using gedit for LaTeX and had to have two different text editors open at once often, which seemed pointless.

Rgedit really is exactly what I need, and I am sure there are many others like me out there.

---

### Post by Ctulhu on 2009-09-14
danded, samden,

great, now that I put it in plugins, it's just fine, thx so much!

C.

---

### Post by samden on 2009-09-14
Danded:
While working with Rgedit I realise it would be really handy to have a key command to change focus between the document and the R console. I am not sure how easy that would be to implement, but it would speed things up.

---

### Post by danded on 2009-09-15
> **samden said:**
> Danded:
While working with Rgedit I realise it would be really handy to have a key command to change focus between the document and the R console. I am not sure how easy that would be to implement, but it would speed things up.

As it happens, it looks like gedit already uses Ctrl+Tab to give the focus to the bottom pane, so I added the other direction: pressing Ctrl+Tab inside an active R console sends the focus to the active (visible) document in gedit. So, if you have an R console visible in the bottom pane, Ctrl+Tab ensures the whole cycle of focus between the current document and the current R console. Unfortunately, I don't know how to change the assignment of Ctrl+Tab in gedit, so we'll have to stick with it (but for me Ctrl+Tab comes quite natural).

I've uploaded v0.4 on sourceforge...

---

### Post by samden on 2009-09-15
Awesome danded, if there's a prize for the fastest developer in the world I think you should probably get it! 

Ctrl+Tab is fine. I've switched my commonly used other commands to single-button ones where possible (F4 for "run selection" for example), because I'm lazy and can't be bothered pressing 3 keys at once if I can help it. I love being able to customise the software I use.

Keep up the great work! :)

---

### Post by samden on 2009-09-15
Just noticed that Sourceforge still just has v0.3...

---

### Post by danded on 2009-09-16
> **samden said:**
> Just noticed that Sourceforge still just has v0.3...

Yeah, it took them a while to update :) Now 0.4 is finally up...

---

### Post by scizmeli on 2011-04-23
[http://rstudio.org/](http://rstudio.org/)
[http://www.walware.de/goto/statet](http://www.walware.de/goto/statet) (using R from within Eclipse)

---

### Post by Campitor on 2011-04-29
I vote for rstudio.org it is the best IDE I've used.  A lot better than any GUI.  It's a shame its not in the repositories.

---

### Post by samden on 2011-05-01
RStudio is excellent, thanks for the link scizmeli. I'd generally stick to a plain text editor + console, but the key addition RStudio makes to this for me is the ability to scroll back through the different graphs you have made, which saves a lot of time for me. It's designed for one screen though and I use dual monitors, but it will get there, still early days.

And it's cross-platform (Lin, Mac, Win) so I can have the same user interface at work and home.

---

### Post by gunksta on 2011-05-02
There are times when ESS drives me bonkers and I just want to use something simple. This is usually because I'm hanging R up with something stupid and in the process locking up both R and EMACS. User errors are the best.

I agree with Samden that I prefer to keep my code in a separate window. My normal workflow is simple. I have the .R file open in EMACS on my 21"  external monitor and I runn ESS as an inferior mode in a separate frame  on the laptop's built in screen. Both are maximized.

I can replicate my EMACS style workflow with geany and RStudio by placing geany on my external monitor and RStudio on the laptop monitor. I minimize RStudio's text editor. I like this because I can take advantage of RStudio's other nice features like the ability to easily review all of the data frames in the current environment AND I am able to take full advantage of using two screens, which RStudio can't do alone.

The real trick is to make sure Ubuntu includes this in Natty+1 (Onieric, I think). Users who use the Ubuntu Software Center should be directed to install / use RStudio. Those of us who are perfectly happy without it can still install via the command-line without it if we prefer. To me, RStudio seems to be the perfect default GUI for R. It takes up so little room that if someone prefers to use something else, their installation is hardly becoming "bloated" and new users will find R is much easier to use.

---

