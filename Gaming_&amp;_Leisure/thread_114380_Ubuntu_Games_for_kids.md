---
title: "Ubuntu Games for kids"
date: 2006-01-08
forum: Gaming &amp; Leisure
---

### Post by Steve S. on 2006-01-08
Does anyone recomend good ubuntu games for kids?  This computer has a nice Radeon video card and it would be a shame to not let the kids go nuts with it some (two boys, 8 and 5).

I come from the gentoo world (well, that's the only other linux I've used) and there you can search for ebuilds/packages via the web site.  Can you do that with ubuntu?  Where can I find that?

Also, you could emerge --search (name/subject) and find stuff.  Is there a way to do that with ubuntu?  Is it apt-cache search (name/subject)?  Is that right?

Any suggestions in that area are greatly appreciated.

---

### Post by matthew on 2006-01-08
The easiest way is to use a program called Synaptic. If you are running Gnome you can find it in System->Administration->Synaptic Package Manager. Fire it up and play for a few minutes and you will get the trick.

It is likely you will need to enable the extra software repositories to get the full benefit of apt and Synaptic. To do this, follow this link: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

While you are looking, I like a program for kids called gCompris, which is a suite of educational games and is quite well done and age appropriate for your kids. I'm sure you will find more.

---

### Post by Steve S. on 2006-01-08
Excellent, Matthew, very appreciated...I'll check it out!

---

### Post by akurashy on 2006-01-08
Also, I think gcompris will do, you can get it from repository :)

---

### Post by Perfect Storm on 2006-01-08
[Childsplay]("http://childsplay.sourceforge.net/") is also in Synaptic if you enable universe.

---

### Post by Imexius on 2006-01-09
Just dont let them play potato guy *shudders* that game gave me nightmares...

---

### Post by chimera on 2006-01-09
[QUOTE=Imexius]Just dont let them play potato guy *shudders* that game gave me nightmares...[/QUOTE]

:lol:

Just give them gnometris and mahjongg. They'll never get tired of it. Well, I didn't, lol;) I think they're both preinstalled.

---

### Post by madjinx on 2006-01-09
if you dont mind commercail games, theres GIsh, Marble Gold. maybe sim city 3k, or railroad tycoon for the 8 year old.

---

### Post by leech on 2006-01-09
[QUOTE=Steve S.]Does anyone recomend good ubuntu games for kids?  This computer has a nice Radeon video card and it would be a shame to not let the kids go nuts with it some (two boys, 8 and 5).

I come from the gentoo world (well, that's the only other linux I've used) and there you can search for ebuilds/packages via the web site.  Can you do that with ubuntu?  Where can I find that?

Also, you could emerge --search (name/subject) and find stuff.  Is there a way to do that with ubuntu?  Is it apt-cache search (name/subject)?  Is that right?

Any suggestions in that area are greatly appreciated.[/QUOTE]

If I can get the project off of the ground, I am going to work on a website similar to the ebuilds site that Gentoo has.  That was one of the sites I had looked at as a model for my ideas.  Unfortunately I've been having to spend too much time looking for a job to make some money....  I need to become independently wealthy, I think :D

Leech

---

### Post by Steve S. on 2006-01-10
[QUOTE=leech]I need to become independently wealthy, I think :D

Leech[/QUOTE]

Yeah, don't we all.  Look forward to the ebuild site...

I'll check out all the games...have already added many of them via synaptic.  5 year old has already enjoyed the puzzle one on gcompris...good call.

I've enabled universal (pretty sure) and set up my Radion 800XL ok, but there are a couple of issues that I'm sure y'all could help me with, in addition to the overall game search:
1. Don't have many sounds with many things.

2. My kids liked the penguin going down the ski slope thing in gentoo (I think it is superpenguin-racer or something in ubuntu) so I put it on ubuntu.  but, I tried ti once before setting up the Radion and it was slow as crap (as you might expect, hence the reason I messed with the Radion set up).  Then, rebooted and all that and can't get the game to come on.  Then reinstalled it via Synaptic and still can't get it.  Should I try command line or something?  Any ideas?

---

### Post by %hMa@?b&lt;C on 2006-01-10
i enjoy Planet Penguin Racer
sudo apt-get install ppracer
I also like frozen bubbles
i know that  it is in the repositories
and also check the add-remove programs area and search in games.  There is plenty of good stuff

---

### Post by Steve S. on 2006-01-10
[QUOTE=jeffc313]i enjoy Planet Penguin Racer
sudo apt-get install ppracer
I also like frozen bubbles
i know that  it is in the repositories
and also check the add-remove programs area and search in games.  There is plenty of good stuff[/QUOTE]

that's exactly what I needed for the Racer.  Thanks, jeffc313.

---

### Post by matthew on 2006-01-11
[quote=Imexius]Just dont let them play potato guy *shudders* that game gave me nightmares...[/quote]That's my 2 year old's favorite!! :)

---

### Post by jobezone on 2006-01-11
My nephew likes tuxpaint, although it isn't a game per se, but he has fun with it.

---

### Post by Steve S. on 2006-01-11
Hey all,

I tried this: sudo apt-get install ppracer
and I got this: E: Couldn't find package ppracer

Anyone know what gives?

---

### Post by Perfect Storm on 2006-01-11
You properly didn't set up your sourcelist. Namely universe and/or multiverse.

---

### Post by Steve S. on 2006-01-11
I did this:
> ## Uncomment the following two lines to fetch updated software from the network
###italian mirror#####
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted

that's right, yes?

---

### Post by Steve S. on 2006-01-12
You got me thinking, Artificial Intelligence, so I updated via the gui setting in gnome and a lot of boxes got checked that weren't previously, apparently, so that should open it up.

I downloaded ppracer via the Synaptic after that and it looked like it set up great, but it won't run, said it can't find the intial screen or something to that effect.  Any ideas?

Need more info?  Tell me what to run so I can give more input.  I ran it via command line also and it kicked back the error message; running it via the gui didn't do anything at all.

---

### Post by Jave27 on 2006-01-12
If the kids are old enough and can control a mouse fairly well, go for [Pingus]("http://pingus.seul.org") (**sudo apt-get install pingus**).  My 4-year old cousin could do quite a few of the levels until the action got too fast for him.

Disclaimer:  I'm now one of the active developers of that project, so I'm biased.  :-)

---

### Post by Perfect Storm on 2006-01-12
Without any more information my guess: Did you setup your 3D card? It could be that.

---

### Post by Steve S. on 2006-01-12
[QUOTE=Jave27]If the kids are old enough and can control a mouse fairly well, go for [Pingus]("http://pingus.seul.org") (**sudo apt-get install pingus**).  My 4-year old cousin could do quite a few of the levels until the action got too fast for him.

Disclaimer:  I'm now one of the active developers of that project, so I'm biased.  :-)[/QUOTE]

I vaguely remember that one from the gentoo box.  What was that one again?  I'll put that one on there tonight.

Edit: just checked out the site.  Yep, the 8 year old likes that one...I'll put it on there.

---

### Post by Razorback on 2006-01-12
I downloaded and installed Rafkill.  It's a spinoff of an old arcade game Raptor.  My 13 year old really likes it.

---

### Post by dustyculler on 2006-01-12
> I downloaded ppracer via the Synaptic after that and it looked like it set up great, but it won't run, said it can't find the intial screen or something to that effect. Any ideas?

Have you installed the fglrx package?  That is the ATI video driver that allows you to use 3D.  You'll need to run fglrxconfig from a terminal to have it generate a new X.org config after installing that package, and unfortunately it doesn't seem to be able to autodetect your monitors, so grab the refresh rate out of your existing /etc/X11/xorg.conf before running fglrxconfig, and/or make a backup copy of that file before proceeding.

Also for younger children, Tux Paint is great.  It's a painting program with sound effects and colorful stamps.

---

### Post by Steve S. on 2006-02-02
Hey all,

And I noticed a distinct lack of sound on the games in Ubuntu.  Any idea what I missed?  Is there a configuration step that I need to take?

---

### Post by Perfect Storm on 2006-02-02
Is [1]libsdl-mixer1.2[/i] and *libopenal0* installed?

---

### Post by Steve S. on 2006-02-02
[QUOTE=Artificial Intelligence]Is [1]libsdl-mixer1.2[/i] and *libopenal0* installed?[/QUOTE]

I don't believe so...I'll check and post back.

By the way, cool desktop.

---

### Post by Steve S. on 2006-02-17
[QUOTE=dustyculler]Have you installed the fglrx package?  That is the ATI video driver that allows you to use 3D.  You'll need to run fglrxconfig from a terminal to have it generate a new X.org config after installing that package, and unfortunately it doesn't seem to be able to autodetect your monitors, so grab the refresh rate out of your existing /etc/X11/xorg.conf before running fglrxconfig, and/or make a backup copy of that file before proceeding.
[/QUOTE]

I went through the whole configuration process and think I did it right, but I still got this error message:
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)

What did I do wrong?

---

### Post by charlieg on 2006-02-17
[Professor Fizzwizzle](http://www.happypenguin.org/show?Professor%20Fizzwizzle) is an excellent game for kids.  My 5 year old loves it.  It's not free though, although you can get a good feel for the game with the demo.

---

### Post by Steve S. on 2006-02-18
[QUOTE=Steve S.]I went through the whole configuration process and think I did it right, but I still got this error message:
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)

What did I do wrong?[/QUOTE]

Can anyone help me with this one?  Is there more information that I need to provide to figure it out?

---

### Post by Steve S. on 2006-02-19
Ok: I reconfigured and got the ppracer to work...almost.

As SOOOO many others have mentioned in various ways: I've got no sound on the games.  I have sound on everything else, just not the games.  In fact, when I go to preferences-->sound-->sound effects I can select on each sound effect for each game and it sounds just fine.

When I run ppracer from terminal I get this error message:
```
%%% ppracer warning: Warning: Couldn't set 22050 Hz 16-bit audio
  Reason: No available audio device
```

I have already done this:
> Is [1]libsdl-mixer1.2[/i] and libopenal0 installed?

So I don't think that is it.

I go to preferences-->multimedia selector--> then select ALSA for both of the audio options.  The top one tests fine, but the bottom one comes back with:
```
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
```

When I check in Applications-->Sound&Video-->Volume Control it indicates that everything is turned all the way up.

Looking in the device manager, it seems I have a C-media Electronics Inc CM8738 sound card.

I am running Breezy, by the way, if that is of significance.

Anyone have any idea how to fix this?  Need any other information?

---

### Post by Steve S. on 2006-02-20
Well, either no one else is out there or I'm not giving enough information, so I'll press on! ;-)

I searched some more and found a suggestion that seemed logical, although it would seem that I had already done at least part of it.  Anyway, from terminal I entered:
```
sudo apt-get install libsdl-mixer1.2 libsdl-mixer1.2-dev
```

I don't know if that is significant or not since it said that it already had these latest versions selected.  Oh, well...EXCEPT

NOW I have sound in the games when I run them from terminal.  But, if I create an icon in the panel, using the same command that I used from terminal, there is no sound on the game. ???

From terminal, the comment it gives is:
```
open /dev/sequencer: No such file or directory
```

What does that mean?  Can I fix this so that I can run games from the gui rather than the terminal?  Anyone?

---

### Post by Steve S. on 2006-02-24
No one? Hmmmm....

Well, it seems to be a gui issue, since I can have sound from terminal and when we click directly on the game program from back in the files, rather than straight from the desktop.

Do we not have a way of fixing this?  Am I not giving enough info?  Anyone?

---

### Post by jobezone on 2006-02-25
Ok, I think I may know why is it that if you run a game from the terminal you have it with sound, but not if executed from a launcher: Do you have system sounds activated? You probably have, and so, when you click the launcher, a Bong sound is played, which makes the sound device (?) busy and unavailable for the game. The solution is to disable the system sounds, or even gnome's sound system altogether.

The 2nd part, "open /dev/sequencer: No such file or directory". It is asking for a midi device. Either your soundcard has one builtin, or it doesn't, and you can use software midi synthesis. See [https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo?highlight=%28midi%29](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo?highlight=%28midi%29)

---

### Post by Steve S. on 2006-02-26
Wow, jobezone, I'm hugely impressed.

So, I disabled system sounds, and it worked immediately.  Obviously I can't use things like xmms (any way around that?) but the terminal games sounds work right away.

I'll have to check on the other, but I knew someone out there would know.  Well done.

---

