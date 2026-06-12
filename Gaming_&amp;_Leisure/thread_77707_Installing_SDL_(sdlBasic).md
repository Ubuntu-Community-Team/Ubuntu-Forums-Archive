---
title: "Installing SDL (sdlBasic)"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by nitrofurano on 2005-10-17
Hi!
i'm trying to use sdlBasic on Ubuntu, and i can't do it (on Linux, i only could run sdlBasic ([http://sdlbasic.sf.net](http://sdlbasic.sf.net)) from the Slax distribution)
it seems to need to install SDL libraries over the installed Ubuntu - how can i install SDL libraries being offline?  which installers are and where can i found and install them? (specially from the Ubuntu repositories)
thanks!

ps: btw, is Ubuntu planned to come with a working SDL?

---

### Post by Biased turkey on 2005-10-17
[QUOTE=nitrofurano]Hi!
i'm trying to use sdlBasic on Ubuntu, and i can't do it (on Linux, i only could run sdlBasic ([http://sdlbasic.sf.net](http://sdlbasic.sf.net)) from the Slax distribution)
it seems to need to install SDL libraries over the installed Ubuntu - how can i install SDL libraries being offline?  which installers are and where can i found and install them? (specially from the Ubuntu repositories)
thanks!

ps: btw, is Ubuntu planned to come with a working SDL?[/QUOTE]

Ubuntu by default installs the runtime SDL libraries, just check that fact using Synaptic. The runtime SDL sound library sdl-mixer is installed too.
What you need to install ,if you want to compile programs sources using SDL ,is   the SDL development libraries like libsdl1.2-dev

---

### Post by nitrofurano on 2005-11-07
> Ubuntu by default installs the runtime SDL libraries, just check that fact using Synaptic. 

Synaptic is that online update from Ubuntu, isn't it? the problem is i'm not connected online with Ubuntu, as well i'm completelly not interested to do constantly online updates every time i reinstall Ubuntu (for me online updates are the same as nothing) - so what i really need are the installing packages, like the .deb ones...



> The runtime SDL sound library sdl-mixer is installed too.
What you need to install ,if you want to compile programs sources using SDL ,is the SDL development libraries like libsdl1.2-dev
where from can i get (urls) the package or installer (assuming are .deb files?)


What i really want to invite everyone here is to try to install sdlBasic into a freshly installed offline Ubuntu, and report here, sdlBasic official forum, or anywhere, each step is needed to get sdlBasic completelly installed and working! :-)

---

### Post by slimb on 2005-11-07
by default, if you're installing ubuntu from the CD (offline) - SDL is indeed installed already.

synaptic is not online only.  it'll check your cds first if you're sources.list is setup to do so.  and again SDL is installed automatically - open up synaptic and do a search for SDL.

what is it that you're trying to accomplish?  you have sdl already so i'm not sure what you're trying to do by installing it again?  perhaps further info would allow us to help you better or possibly answer your questions in a better manner.

---

### Post by Biased turkey on 2005-11-07
[QUOTE=slimb]

what is it that you're trying to accomplish?  you have sdl already so i'm not sure what you're trying to do by installing it again?  perhaps further info would allow us to help you better or possibly answer your questions in a better manner.[/QUOTE]

I think the original poster want to compile a program that uses SDL so he needs the SDL development libraries. Those libraries include for example the headers files.
If the user just want to run applications that requires SDL (  like UT ), he just needs the runtime libraries that are ( as you mentions ) installed by default.

---

### Post by slimb on 2005-11-07
[QUOTE=Biased turkey]I think the original poster want to compile a program that uses SDL so he needs the SDL development libraries..[/QUOTE]

I believe this may be correct, but until he specifies we can't be sure :) 

--
if indeed you do need the development stuff - you'll need libsdl-devel i believe is how its called and again it's in synaptic and can be pulled off the CD w/o needing internet access.

---

