---
title: "A new user with a backlog of issues"
date: 2009-03-13
forum: General Help
---

### Post by larrel on 2009-03-13
Greetings to you all ubuntu forum dwellers,

I am more-or-less a new ubuntu user, and ummm, the only part of ubuntu i have been experiencing so far, is "troubleshooting" .. from day one.:(

After ~15 linux installations in the timespan of < 1 month, i decided to settle with a stable ubuntu 8.10 installation.

Despite spending hours on googling, i still got a backlog of cases needed to be solved, and i am really hoping for some help here [-o<
Here they come:

[COLOR="Blue"]1)Screen tearing:[/COLOR] [COLOR="Red"]*FIXED*[/COLOR]
[http://tinypic.com/view.php?pic=1zwda21&s=5](http://tinypic.com/view.php?pic=1zwda21&s=5) <-with metacity
[http://tinypic.com/view.php?pic=zvrip1&s=5](http://tinypic.com/view.php?pic=zvrip1&s=5) <-with compiz
Works flawlessly on kubuntu/kde, vista, win7, without setting any vsync or whatsoever

[COLOR="Blue"]2)Partial audio[/COLOR] [COLOR="Red"]*FIXED*[/COLOR]
This problem somewhat changed, when i installed ubuntu, it used PulseAudio instead of my CK804 device - alsamixer would only show PulseAudio, i had no sound in Skype or in a Screenlet's radio applet.
Tried stuff like : asoundconf set-default-card CK804; sudo alsa reload;
..but to no avail.. following this guide ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) didn't help either.
Only removing pulseaudio packages did the trick, skype's working, alsamixer shows correctly .. but the radio applet still doesn't work, and sound from java applet's dissapeared as well.

[COLOR="Blue"]3)Can't force compiz as the default window manager[/COLOR]
This is somewhat weird. If i uninstall fusion-icon, compiz is used by default .. but i need the icon to switch between metacity/compiz easily.
When ubuntu boots up, "select window manager->" in fusion-icon shows that compiz is already selected.. i just have to click "Reload window manager" every time. I tried adding "compiz --replace" to startup programs in "Sessions", but that didn't change anything

[COLOR="Blue"]4)Cairo-dock vanishes:[/COLOR] [COLOR="Red"]*FIXED*[/COLOR]
Cairo-dock, which i like a lot (more than Avant or default panel atleast), keeps dissapearing when i click any of its launchers. Pressing the "show/hide dock"  shortcut key reveals it. I believe it worked fine on a previous ubuntu installation

[COLOR="Blue"]5)Webcam isn't working.. should it ?[/COLOR]
Heard ubuntu has issues with webcams, so i am not even sure if its possible to solve, but oh well:
my MSI Starcam Genie...simply doesn't work. In fact, skype crashes when i do the webcam video test ( it didn't crash before.. just gave messed up video or pure green background )

Phew, if anyone got this far, i'll thank them for reading so much atleast =)

ps: wasn't sure where to post, since i had a lot of different types of problems, i'd go with the "general" area

---

### Post by fabounet on 2009-03-13
for Cairo-Dock, if you read the tootip of the shortcut option in the config panel, you will see that this is a feature and not a bug ;-)
Remove the shortcut if you don't want it

---

### Post by larrel on 2009-03-13
".... .The rest of the time it stays invisible. ..."

Gosh, i gotta start reading those tooltips :D

Thanks, you've relieved some of my pain ;)

---

### Post by larrel on 2009-03-13
*bump*

guess the third one isn't that important, can always use alt+f2: compiz/metacity --replace if needed;

It's the screen tearing issue that is a real pain >.<

---

### Post by antitroll on 2009-03-13
For the compiz tearing, try the following:

ccsm | General Options | Display Settings | Sync To VBlank - ticked

nvidia-settings | OpenGL Settings | Sync to VBlank - ticked (also "Allow Flipping" is ticked)

Disable detect refresh rate in compiz and set it to 60

[http://www.nvnews.net/vbulletin/showthread.php?t=129744](http://www.nvnews.net/vbulletin/showthread.php?t=129744)

The refresh rate problem is a bug in compiz where 59.99hz gets rounded down to 50hz.

---

### Post by richard.gizinia on 2009-03-13
Kia Ora 
  I'm definitely a new user of Ubuntu and after many years of working construction find myself completely lost in forums and technology. 
 Decided to start with Linux, but am plagued with issues as I see, so are others.
 If I could get my desktop to look like it is not bending around corners and use the entire monitor I might feel a little bit more encouraged.
 Since you have dealt with some of these issues maby you can help or point me in the right direction.

 Cheers

---

### Post by larrel on 2009-03-13
> **antitroll said:**
> For the compiz tearing, try the following:

ccsm | General Options | Display Settings | Sync To VBlank - ticked

nvidia-settings | OpenGL Settings | Sync to VBlank - ticked (also "Allow Flipping" is ticked)

Disable detect refresh rate in compiz and set it to 60

[http://www.nvnews.net/vbulletin/showthread.php?t=129744](http://www.nvnews.net/vbulletin/showthread.php?t=129744)

The refresh rate problem is a bug in compiz where 59.99hz gets rounded down to 50hz.

Thanks, just "Sync to VBlank" in CCSM did the trick , i've left my refresh rate at 75, happy with the way it works now :P
The only thing thats bothering me regarding refresh rates, is that "Screen resolution" window shows 50hz and 50hz only, where as everywhere else its set to 75

Was struggling with the sound issue, reinstalling java had no effect ofc, still no sound in java aps, in the radio desklet as well;
I am also starting to wonder if getting rid of pulseaudio was a good idea. Mplayer, for example, before starting a video displays an error "AO [pulse] Failed to connec to a server. Connection refused."
Even skype that started working, gives some errors:
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)


@richard.gizinia : "not bending around corners and use the entire monitor", not sure what you mean by that ... default panels?

---

### Post by DigiTan on 2009-03-13
Nobody move!!  This is a hijacking!  I said NOBODY MOVE!!!

I have a question for anyone who wants to be a hero.  If I installed Compiz just like larrel did.  I also want to Compiz the primary window manager.  How do I do it?  So far my configurations have no effect.  I'm new to Linux in general, so my question might have an obvious answer.

I mean...GET DOWN ON THE GROUND!!

---

### Post by DigiTan on 2009-03-23
Nevermind, I found my answer and my plane to Mexico.  You just have to go to the "Appearances" control panel and enable "advanced desktop effects."  Compiz worked after that.

---

