---
title: "XDVDShrink"
date: 2006-01-07
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-01-07
I converted via alien, installed it....and I can bring it up...but for some reason when I start the process a pop up window comes up and it goes away....like it tries to start something but obviously errors out.  Since I am very very new to linux....I have no idea where a log file would be that might point me in the right direction...

Can anyone help.....I thought I would try this app since I cant get DVD Decrypter to work or Dvd Shrink.....

I am about to give up........all I want is a linux app that can make backups of my DVDs.....

I could do this in Windoze easily enough.....

Sorry I am just getting frustrated.....going on week 3 trying to get this to work....

---

### Post by Aphorism on 2006-01-07
It works quite flawlessly.  Further, because it is all open source, it runs like mad on my dual core x2 amd processor.

You *will* need to install three other packages that it uses, as it is only a 'glue' script that binds together other tools.

[http://ubuntuforums.org/showthread.php?t=92198&highlight=xdvdshrink](http://ubuntuforums.org/showthread.php?t=92198&highlight=xdvdshrink)

The above link has the method to install xdvdshrink.  From there, run it, and you will see the three libs you will need to also install.

You may also wish to check out k9copy once you get your hands dirty with linux...

---

### Post by PapaWiskas on 2006-01-07
[QUOTE=Aphorism]It works quite flawlessly.  Further, because it is all open source, it runs like mad on my dual core x2 amd processor.

You *will* need to install three other packages that it uses, as it is only a 'glue' script that binds together other tools.

[http://ubuntuforums.org/showthread.php?t=92198&highlight=xdvdshrink](http://ubuntuforums.org/showthread.php?t=92198&highlight=xdvdshrink)

The above link has the method to install xdvdshrink.  From there, run it, and you will see the three libs you will need to also install.

You may also wish to check out k9copy once you get your hands dirty with linux...[/QUOTE]

I did the install as it said.....I had found that link and that is how I got it installed.
But something is not right.  I am guessing it has something to do with my devices....
dev/dvd

I know for that other program that windows uses for Ubuntu you had to change it to cdrom or something....

I am still lost on this....

---

### Post by Aphorism on 2006-01-13
What is the exact error?  Can you lend some more information?


Thanks...

---

### Post by PapaWiskas on 2006-01-14
Well now it is working....I am not exactly sure what I did to get it working.  I kept messing with my settings and my dvd burner settings and eventually whatever the heck I did it now works flawlessly like you said it would.

So I am happy....

---

### Post by Aphorism on 2006-01-14
Apparently K9Copy has released a new version too.  It will require compiling, but it preserves menus and such.

PS:  A friend noticed a known error with xdvdshrink -- you can fix it, but just be aware of it.  If you try to do subtitles, it will NOT copy them.  You need to patch it.

---

### Post by handy on 2006-01-14
[QUOTE=PapaWiskas]
Can anyone help.....I thought I would try this app since I cant get DVD Decrypter to work or Dvd Shrink.....
[/QUOTE]

If your on 32bit Breezy, I highly recommend installing Wine using Automatix,

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

& then use WineTools

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

to configure Wine. (Don't install internet explorer, especially it you are going to install DVDshrink) then download & install DVDshrink,

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

which is so simple to use & incredibly reliable. As you allready know!  :D 

For easy burns, as fast as your media allows (max speed of your burner permitting) & Multi-Session :KS   Download NeroLINUX trial.  It works for a couple of weeks or more.

[http://www.nero.com/us/NeroLINUX.html](http://www.nero.com/us/NeroLINUX.html)

If you like it $20- US.

Works perfectly for me...

---

### Post by Aphorism on 2006-01-14
Thanks for the tip.  I like software that comes with sourcecode though.  

Further still, I like open source operating systems.  I refuse to support Apple or Microsoft, and finding workarounds doesn't help the cause.


Thanks for the tip, just trying to avoid Winblows.

PS:  There is no use in running Nero -- burning is built into every open source operating system out there.

---

### Post by PapaWiskas on 2006-01-14
[QUOTE=Aphorism]Thanks for the tip.  I like software that comes with sourcecode though.  

Further still, I like open source operating systems.  I refuse to support Apple or Microsoft, and finding workarounds doesn't help the cause.


Thanks for the tip, just trying to avoid Winblows.

PS:  There is no use in running Nero -- burning is built into every open source operating system out there.[/QUOTE]


Agreed......I really appreciate the help....

---

### Post by Aphorism on 2006-01-16
Ok Papas, I figured I would point you at these tools thus far that I have found for native linux:

Of the first batch, we have the DVD9 to DVD5 format shrinkers.  The following crunch the file down to a format that a standard DVD player will read (assuming it can read recordable 4.7 gig discs):

xdvdshrink:  
[INDENT]Pros:  Rips main title only, and as a result, will increase the overall quality by freeing up the extra space for important image information.  Command line and graphical interfaces.  Quick.  Can do multi-title television compilations as well, but not with original menus.  Uses transcode under the hood.  Basically a 'wrapper' that glues together various rip command line tools, and therefore runs without too many problems.

Cons:  No menus, etc.  Not a full redo of the original disk, only main title.  Submenu bug that needs addressing.[/INDENT]

The following make the effort with menus:

lxdvdrip:
[INDENT]This one looks quite promising.  I am going to give it a try shortly.[/INDENT]

k9copy:
[INDENT]Pros:  Rips full menus and extras.
Cons:  KDE based, which means it brings with it the need for kde-core libs and such.  Buggy as hell on amd64 last time I tried.  Might try a new compile.[/INDENT]


The following rip a DVD to a wrapper of various forms.  Will not play on a standard DVD player, but will help you if you simply want to rip the movie for archival purposes to your hard disk:

dvd::rip:
[INDENT]DVD ripping package.  Default kind of drove me nuts because I couldn't easily specify that I wanted the title into a single file, etc.  Didn't tinker with it too much.[/INDENT]

thoggen:
[INDENT]LOVE this one.  It is simple and rips to Theora and Ogg for sound!  Great little app.  Unfortunately requires you to run it as superuser (sudo thoggen) or it bombs out.  That said, quite a nice app.  Seems to be on the slower side (2 hours to encode at quality '30' on my dual core x2 amd64 chip -- but the fact that it defaults to Theora and Ogg are HUGE upsides in my mind.)  Uses gstreamer for encoding to the Theora / Ogg end of things.[/INDENT]

acidrip:
[INDENT]Same sort of idea, but more aimed towards supporting avi/divx out of the box.  Not a fan of divx/xvid with avi wrappers here though.  Also, it uses mplayer and mencoder to do the encoding.[/INDENT]

---

### Post by handy on 2006-01-16
Yep, I appreciate your point of view, I'm not THAT far away from it myself...

All I can add on DVDshrink's behalf is that it is & always has been freeware.

NeroLINUX, & DVDshrink are both so easy to use for a Ubuntu (linux) noob like me! :KS

---

### Post by PapaWiskas on 2006-01-16
Thanks Aphorism,

I have been going down the same paths you mentioned.....minus the lxdvdrip....didnt know about that one.

K9 kinda gave me fits, and I do not like KDE all that much.  To much clutter....

I have been using xdvdshrink but ran into some problems on a disk, not sure what the errors meant and I am currently trying to figure out if there is a forum that deals just with that particular app.  I am not sure how much questioning we can do on apps that rip dvds as I dont want to offend anyone.  But I do like xdvdshrink alot, I could care less about menus.....:p 

I will be trying out the others that you mentioned though.  I am getting more comfortable in Linux...

Thanks for all your help...if you run into anything else, let me know.

---

