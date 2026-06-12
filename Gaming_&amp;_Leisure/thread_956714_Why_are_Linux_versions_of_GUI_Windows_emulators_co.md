---
title: "Why are Linux versions of GUI Windows emulators command-line only?"
date: 2008-10-23
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-10-23
What the title says, why do developers or the people who port Windows emulators (which all come with a GUI) make the Linux version command-line only? who's going to use an emulator using the command line with all the options emulators have and most people like to tweak (like myself)? it's beyond me really, with all the potential that Linux has...I mean, can't anybody make a Qt or GTK GUI for an emulator (developed by the same person/people that make the emulator of course)? is it so hard? so hard that's harder than to make it for Windows? and why is it that most of them (if they are not on the repos) tend to distribute the source only? on Windows they distribute an .exe or something and I know that compiling must be done for Windows too but they do it no problem but not for Linux?

Oh yeah and why people who actually make native Linux emulators do the same thing? I really want to know if making GUIs for Linux is much harder than it is for Windows otherwise I don't understand.

How hard can it be to compile an .rpm or .deb file? I mean, you don't even need to make both thanks to Alien.

-----------------------------------------------------------------------------

That was kind of like a rant but now I was wondering something else, is Mame for Linux (xmame or whatever other variation) still being developed? because all I see is version 1.06 or so but official mame is like at 1.26 or so, Also, is there a better frontend for it than kxmame? why hasn't anybody else developed frontends? all of them seem to be extremely outdated (kxmame's latest version is from 2005!). If I was a developer I would try to make all these things if not to satisfy just myself since I would love to give to the community but I can't develop anything for jack soo...

---

### Post by DoktorSeven on 2008-10-23
Because the standard way of doing things in Linux is to have commandline versions to allow people to write custom frontends.  Same way with many other apps (most GUI CD burning software just call a commandline CD burning program [wodim]).  And there are GUI emulators as well (Gens, for example).

The old xmame is no longer developed; its successor is SDLmame ([http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)).  kxmame has a CVS version compatible with it, plus there are several other frontends ([GMAMEUI](http://gmameui.sourceforge.net/) for one).

---

### Post by FranMichaels on 2008-10-23
Got to agree with DoktorSeven. It's a better separation of concerns. Make a great emulator. Make a front-end, someone makes a better one, it's easy to swap. Same holds true if someone makes a better emulator. 

But whatever, as long as an emulator handles commandline parameters, I won't complain.

---

### Post by Abras on 2008-10-23
I agree, from a design perspective it's better to keep the GUI and the meat of the program separated. But such a set up isn't particularly user-friendly. At least, many Windows users just aren't used to that. For many, the GUI *is* the program, which makes sense since that's what pops up when they click on an icon, and that's what they've been lead to believe. Programs aren't so much chunks of code to them as they are windows that do something useful, which to me is a perfectly acceptable way to look at the matter.

To the question at hand, I can't think of a solid reason why Linux emulators *have* to be command line only. Maybe an emu developer (like Tux0r) coud shed a little more light on the situation. Although personally, I don't mind it too much since there are plenty of GUIs for just about every worthwhile emulator that runs on Linux.

---

### Post by Moonfrost on 2008-10-23
> **Abras said:**
> I agree, from a design perspective it's better to keep the GUI and the meat of the program separated. But such a set up isn't particularly user-friendly. At least, many Windows users just aren't used to that. For many, the GUI *is* the program, which makes sense since that's what pops up when they click on an icon, and that's what they've been lead to believe. Programs aren't so much chunks of code to them as they are windows that do something useful, which to me is a perfectly acceptable way to look at the matter.

To the question at hand, I can't think of a solid reason why Linux emulators *have* to be command line only. Maybe an emu developer (like Tux0r) coud shed a little more light on the situation. Although personally, I don't mind it too much since there are plenty of GUIs for just about every worthwhile emulator that runs on Linux.

Yeah I understand, although I DO know what the hell programs are made of, it's just that it makes it unnecessarily difficult to uhh..."handle"...I know everything of how programs/applications are really made of and that the GUI is a frontend but usually...umm..."embedded" into the program itself, or at least the GUI calls for the original or "backend program"...but there aren't frontends for every good emulator on Linux.

For example, mednafen which is a pretty good multi-system emulator doesn't have any up-to-date frontends as we speak (and IF you find one for Linux you have to compile it) and the one that appears floating somewhere sometimes doesn't let you use all the options of the actual command-line emulator, and there are other good emulators that never had frontends or those frontends are either not good or outdated...

It's like the emulation community stopped paying attention to Linux some time ago even though is probably an even more capable OS for this kind of thing than Windows or even Mac OSX is.

---

### Post by Abras on 2008-10-24
Wait, what about [mednafenfe]("http://sourceforge.net/project/showfiles.php?group_id=229596&package_id=278189&release_id=605130")? It's not the greatest frontend in the world but it does the job, and it's in the repos. I'm not sure if it's still actively maintained, but I do remember the Ubuntu Gamers Arena was going to host a site for it a few months ago although that ultimately fell through.

---

### Post by GerbilSoft on 2008-10-24
One of the things I've noticed about most frontends is that they usually have very poor integration with the emulator. For instance, you usually can't change any settings while the game is running.

The Linux version of Gens (and my fork, Gens/GS) has a built-in GTK+ GUI. In the future, I may add an option to turn off the GUI to allow a fullscreen frontend to be used, such as MythGame, but the built-in GUI will always be available.

---

### Post by Moonfrost on 2008-10-24
> **GerbilSoft said:**
> One of the things I've noticed about most frontends is that they usually have very poor integration with the emulator. For instance, you usually can't change any settings while the game is running.

The Linux version of Gens (and my fork, Gens/GS) has a built-in GTK+ GUI. In the future, I may add an option to turn off the GUI to allow a fullscreen frontend to be used, such as MythGame, but the built-in GUI will always be available.

Never tried Gens because I have a Modded Xbox with a Genesis emulator (it's called Neogenesis, It's supposed to be a port from a "famous" Windows genesis emulator but I don't know which one since I've never been very interested in Genesis emulation, although I have every game ever made) and it's even more advanced than any emulator on any OS...then again, most emulators for Xbox are except for the Amiga emulator and the MSX/MSX2 emulators.

---

### Post by malleus74 on 2008-10-24
I have the same issues. I especially like MAME32's basic layout. There's no real **up-to-date **versions of this in Linux, that I've found.

Someone's already thought of what I'd like to see as a fix, using MythGame with game emulators altogether: 
[http://www.gossamer-threads.com/lists/mythtv/users/354724](http://www.gossamer-threads.com/lists/mythtv/users/354724)

I just think the MythGame setup, from my limited knowledge of it, seems a little dumbed down for what I'd ultimately want. If I have uncountable games, etc, I'd like to see screenshots and a little background info.

EDIT: I forgot to mention I also like the idea of the rom directories being kept together in MythGame. Right now I have half a dozen different directories to try and keep up with.

---

### Post by DoktorSeven on 2008-10-24
> **malleus74 said:**
> I have the same issues. I especially like MAME32's basic layout. There's no real **up-to-date **versions of this in Linux, that I've found.



sdlmame + kxmame CVS or GMAMEUI is very close to MAME32's basic look and feel, and sdlmame keeps up with MAME's versions.

---

### Post by Moonfrost on 2008-10-24
> **malleus74 said:**
> I have the same issues. I especially like MAME32's basic layout. There's no real **up-to-date **versions of this in Linux, that I've found.

Someone's already thought of what I'd like to see as a fix, using MythGame with game emulators altogether: 
[http://www.gossamer-threads.com/lists/mythtv/users/354724](http://www.gossamer-threads.com/lists/mythtv/users/354724)

I just think the MythGame setup, from my limited knowledge of it, seems a little dumbed down for what I'd ultimately want. If I have uncountable games, etc, I'd like to see screenshots and a little background info.

EDIT: I forgot to mention I also like the idea of the rom directories being kept together in MythGame. Right now I have half a dozen different directories to try and keep up with.

Yeah that was great, I also used to use MAME32 FX which had a few extra features. The good thing about MAME32 (now called MAMEUI 32 if I"m not mistaken) was that it had "all" the options of the command-line version, all the specific graphical options. For what I've tried though the latest Kxmame and GMAMEUI  are great, they have like all the options of those too which is awesome, since Linux seems an even better platform for Mame.

---

### Post by malleus74 on 2008-10-24
I've looked at gmameui and it doesn't look like it's being supported anymore. It really did look like the best, though. I'll take another look. I really don't care for the front ends I've tried so far... Wah!Cade and 

My thought, though was for a basically universal front end... a lot of the front ends are pretty badly done or don't exist.

The link in my last post is a beginning, I think. If developers could have a starting point and then modify to their specs, or even better, some kind of plugin setup... where it's possible.

---

### Post by malleus74 on 2008-10-27
Here's the brainstorm that I just posted with this idea.

[http://brainstorm.ubuntu.com/idea/14906/](http://brainstorm.ubuntu.com/idea/14906/)

---

### Post by DoktorSeven on 2008-10-27
> **malleus74 said:**
> I've looked at gmameui and it doesn't look like it's being supported anymore. It really did look like the best, though. 
[Last version was released 4 October 2008](http://gmameui.sourceforge.net/).  I didn't see anything about it not being supported anymore, and even if it wasn't, it'd still work (it's not like it's MAME itself, it's just a frontend!).  Or did you confuse it with the obsolete GXMAME, which really isn't supported?

---

### Post by malleus74 on 2008-10-28
I was wrong on the gmameui project. I'm happy to admit I was wrong on that, because I'll be happy to install it once I get to my laptop tonight! 

The overall point though still remains. Setting up an emulator in Windows is *easy* compared to doing the same in linux-based systems. Each emulator installs where it wants to, and customizing the settings isn't always easy. It's probably going to take me longer to get the directories and settings right for the various emulators than it took me to set up Ubuntu in the first place.

Each emulator has a separate front-end, some half-way decent, and quite a few that make you want to go back to the command line. 

I used mame for quite a while before I went to mame32/mame32ui. If you start getting quite a few games, or even most, it's not really practical **not** to have a front end.

I am not anywhere proficient at linux/Ubuntu, and getting all this set up is pretty intimidating to me. I can't imagine someone totally new to Ubuntu even thinking about setting it all up.

---

