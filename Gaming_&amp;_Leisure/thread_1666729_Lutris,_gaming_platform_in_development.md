---
title: "Lutris, gaming platform in development"
date: 2011-01-14
forum: Gaming &amp; Leisure
---

### Post by Ovocean on 2011-01-14
Lutris is a gaming platform planning to support as many games as possible for GNU/Linux. It takes care of installing and running the games by setting up the best environment in order to provide the most enjoyable gaming experience.
Unlike existing similar projects (PlayOnLinux, DJL), Lutris aims to support games from every operating system and console as long as there's is a way to make them run properly on Linux.
Lutris also aims to provide social tools such as inviting friends to join an online game, user ratings...

The project is at a very early stage of development, currently it's nothing much more than an emulators manager with bugs. :)
Contributions are very much welcome, there is a lot of things to do! Eg: Ideas, bug reports, coding, webdesign...

The code for the main application is in python/gtk. The website uses the Django framework (python). The games' installation scripts will be in Yaml (if I'm not mistaken), a "human-readable data serialization format".

_[Lutris.net]("http://www.lutris.net")_ | [Launchpad page]("https://launchpad.net/lutris") | _[Wiki]("http://www.lutris.net/wiki/index.php/")_ | IRC: #lutris on irc.freenode.net (if nobody greets you on the chat, it means we're all AFK and you should come back later)

[An old presentation]("http://ubuntuforums.org/showthread.php?t=1413437") by the main developer

---

### Post by R33D3M33R on 2011-01-14
> **Ovocean said:**
> 
The project is at a very early stage of development. Contributions are very much welcome, there is a lot of things to do ! Eg: Ideas, bug reports, coding, webdesign...

If you will use Launchpad for translations, I can help with translating to my language.

---

### Post by Ovocean on 2011-01-14
I'm pretty sure Launchpad will be used for translation too. We are already using all other LP tools.

I think that the underlying code structure needed for translation isn't ready yet but get in touch with Strycore, he knows the truth. 

Btw, English natives would be welcome too, we currently can't ensure a perfectly correct English. :smile:

---

### Post by strycore on 2011-01-18
Great topic :P

I wanted to answer to gotbletu on youtube ([http://www.youtube.com/watch?v=aT_lKjMMx3Q](http://www.youtube.com/watch?v=aT_lKjMMx3Q)) but youtube has stupid restrictions. Here is the full comment : 

> 
thanks for this nice review :)
Let me clarify some things about Lutris that would help understanding where the project is heading at.
The platform will come when I get more stuff done on the website. It will allow installing games from lutris.net, sharing game installers, having a friends list and other stuff similar to Steam.
Right now, there isn't much done besides the installer. It's possible to try installing games from the web but it's quite experimental, you can still try it by running "lutris lutris:quake" from the command line (this will download and install quake, but some users have reported this doesn't work for them.)

Another thing that needs clarification in my opinion is the options mechanism. There are 3 levels of configuration: system, runner and game. When you set something up in the global preferences this will affect every single game you run with lutris. When setting up runner options you can change the settings for every game that runs with that specific runner, you can also override the system options that you have previously set up in Global preferences. Finally, when configuring a game you can override again every option set up in global and runner preferences.

Getting the game covers : yes it's broken, I used Google Image for fetching the covers and google changed some stuff on their site so it doesn't work anymore. It will be fixed in a future release.

The Install Game functionnality will go under a lot of changes, it will show a list of games with available installer on Lutris.net and it will still be possible to manually launch a setup script (such as Setup.exe for wine or setup.sh for linux).

Your point about importing a thousand roms is very valid. I have plans to make use of known game databases like TOSEC in the future, like gelide or other emulator frontends.

To everyone reading this comment: the project needs testers and contributors. I would like to find someone with Django skills to help me on the website and if you know some Python (and optionnaly PyGTK), you can have a look at the GUI's source code and submit patches.
If you are not a developer, that's fine too. You can report bugs and feature wishes on [https://launchpad.net/lutris](https://launchpad.net/lutris) or hang out on the #lutris channel on the Freenode IRC servers.


---

### Post by strycore on 2011-01-18
double posting

---

### Post by Chame_Wizard on 2011-01-18
I hope Lutris is better than PlayonLinux.:guitar:

---

### Post by strycore on 2011-01-19
> **Chame_Wizard said:**
> I hope Lutris is better than PlayonLinux.:guitar:

Not yet, not yet, but I hope it will be, and soon :)

---

### Post by Ovocean on 2011-01-23
> **Chame_Wizard said:**
> I hope Lutris is better than PlayonLinux.:guitar:Can you specify what things you don't like with PoL ? Or what things you miss ?

---

### Post by doorknob60 on 2011-01-23
Yeah I found out about this from Gotbletu, looks cool, but it doesn't work on Arch, it has some dependenies that aren't on Arch (I think they're Ubuntu specific dependencies). I'll try it again as soon as it works in Arch :)

---

### Post by Hur Dur on 2011-01-23
Yeah, too bad it doesn't work on Arch. :| I'm considering making another partition with Debian just to use this and djl.

A suggestion: Add IRC to the program. See: [djl](http://en.djl-linux.org/sites/default/files/images/captures_fr/imgs/djl_irc.png).

---

