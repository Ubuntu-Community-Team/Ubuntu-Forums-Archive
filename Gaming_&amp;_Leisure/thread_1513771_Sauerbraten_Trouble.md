---
title: "Sauerbraten Trouble"
date: 2010-06-20
forum: Gaming &amp; Leisure
---

### Post by Joseph Schwenker on 2010-06-20
I use Sauerbraten a lot, especially in co-op multiplayer editing, and I keep building a really nice puzzle that I want people to try.  However, I keep having a problem with the text input.  I press t to type, then I can't type anything.  I can move the move, but I can't press escape or any keys to exit the chat field.  Since Sauerbraten's developers are too lazy to integrate it well with Gnome, I can't alt tab out of it.  The only solution is to do a ctrl alt F1 and kill the game, and lose my puzzle again and again.  I replace the batteries on my keyboard with other ones, I unplug and plug in the wireless plug, but nothing allows me to type.  I'm sick of this!  Who has a way that I can alt tab out of Sauerbraten if I need to, and who can give me a way to exit the text field if needs must.

---

### Post by HoKaze on 2010-06-20
Testing it right now ESC works fine for me when in chat (t) or command (/) modes and I can resume playing at any time. It's possible that your config or install is messed up, so I advise reinstalling or looking through your settings.
Also, to make sure I understand you, you can type stuff fine after pressing T to talk but ESC doesn't escape? How about just deleting all the text you've written with backspace until only the > remains and pressing enter? Or just typing whatever it was you wanted to say then press enter? Again, this works fine with me, either sending the message or if blank returning me to the game.
I've also done a very quick, brief search for you and can't find anyone else with this bug, so...if it persists you might want to file a bug report with the developers. 

If you want to be able to switch out and do other stuff without closing Sauerbraten then I simply switch desktop/workspace (should be set to ctrl-alt-right). In most managers and settings I've used if you have bound moving workspaces to a key combination, most games usually pick up on this.
If you really need to do something on your first workspace then move your mouse to where the game window won't be then switch back to the first workspace. As soon as the mouse goes over the game window it'll be sucked back in and let you play, but if you move around it to minimise you can then do other stuff.

As for complaining about the developers "being lazy" that's more than a bit unfair. Firstly, very few FPS games I've played on Linux or Windows have good alt-tab support and secondly Gnome is just 1 of countless window managers and desktop environments. To only add support for Gnome but ignore everything else when the game is supposed to be used across multiple platforms would be the true foolishness.

---

### Post by Joseph Schwenker on 2010-06-20
I am not able to press any keys while the chat field is jammed.  I cannot type any messages, nor press enter, nor press escape.  I have to force quit the game.  I'll try reinstalling.  I do not mean for the developers to ignore other desktop environments, though they could make different packages for each different desktop environment, as the lack of being able to adjust volume or alt tab will really annoy new Linux users coming from Windows or Mac.

---

### Post by HoKaze on 2010-06-20
Completely jammed? Odd to say the least. Do any other programs or games result in similar issues?
You may have to completely remove then install rather than simply choose re-install if troubles persist. Also, you can't adjust volume? o.O Is this in full screen or window mode, because I've always been able to adjust volume using my volume keys in windowed mode.
Also, developers rarely make packages or when they do, it's usually very limited. Normally it falls on the distro or individuals to make packages seeing as the develops tend to be more focused on their actual software than supporting every distro + every architecture + every different modern version of each distro + tweaks to have said software work in different environments seamlessly.  As you can imagine, this would result in a lot of packages.

Again, after searching you're the only person I've found experiencing these issues so I'm quite bewildered. And I don't know about your last statement. I came from a long history of using windows and I've never been put off...then again, unlike you Sauerbraten has always ran fine for me despite my terrible graphics card.

---

### Post by Joseph Schwenker on 2010-06-20
I'm not using the windowed mode, I'm using the fullscreen mode.  I can't switch using ctrl alt right.

---

### Post by HoKaze on 2010-06-20
Yeah, I just checked and in full screen mode it does ignore keyboard shortcuts for volume and changing desktops/workspaces. I normally don't run full screen, so sorry about that. I don't know what else to tell you really.

---

### Post by Joseph Schwenker on 2010-06-21
I just completely removed Sauerbraten and cleared out everything in ~/.sauerbraten.  I am still having the problem.  I was the master of a co-op editing server, and I pressed t to type, then some major lag came in as someone made a large change, then I couldn't exit the type input.  I couldn't do anything, the map restarted and people were griefing, I was being called a bad master, but I simply couldn't do ANYTHING.  I couldn't type or anything.  I could move, that was, until I was shot down.  I was the master of the server, so force quitting meant loosing master.  Not force quitting meant having no power against griefers.  I pressed ctrl alt F1, then ctrl alt F7, but I didn't regain control of the field.  I ended up force quitting.  THIS NEEDS TO BE SOLVED.  I'm SICK of having to close my game out, and not being able to use ANY of my keys because the developers were too damn lazy to integrate their application with the desktop environment.  What's a new user supposed to do?  They don't know about ctrl alt F1, and can't do ANYTHING.  They have to manually restart.  NO APPLICATION SHOULD BE ALLOWED TO DENY THE USER ACCESS TO THE WINDOW MANAGER.  The window manager should be on top of all other windows, so that nothing can override it.  I'm absolutely disgusted at these developers.  This is just one more thing for people to use to make fun of Linux.  It has games, but you can't switch out of them.  I can't even ADJUST THE VOLUME while playing.

---

### Post by HoKaze on 2010-06-21
> **Joseph Schwenker said:**
> THIS NEEDS TO BE SOLVED.  I'm SICK of having to close my game out, and not being able to use ANY of my keys because the developers were too damn lazy to integrate their application with the desktop environment.  What's a new user supposed to do?  They don't know about ctrl alt F1, and can't do ANYTHING.  They have to manually restart.  NO APPLICATION SHOULD BE ALLOWED TO DENY THE USER ACCESS TO THE WINDOW MANAGER.  The window manager should be on top of all other windows, so that nothing can override it.  I'm absolutely disgusted at these developers.  This is just one more thing for people to use to make fun of Linux.  It has games, but you can't switch out of them.  I can't even ADJUST THE VOLUME while playing.
So, instead of going to file a bug report or finding out why only you are having this problem out of the countless players of Sauerbraten who have never experienced this before, you're going to whine about it and flame the developers for their hard work? Real mature. Yeah, you've got a problem and it's frustrating but going out and screaming to the world how disgusted you are at the developers isn't going to do anything and just makes you seem like an ungrateful guy who's favourite toy just got broken, which isn't helpful if you want anyone to actually help you.

Pretty much all full-screen applications have similar levels of "denying user access to the window manager" to use your words. Run windowed. Is it really that big a deal to have your gaming resolution knocked down to the next highest? As for your main problem involving your keys, have you contacted the developers instead of moaning about how incompetent they are? Have you actually filed a bug report? Have you tried searching for an answer yourself? 
If absolutely nobody else has ever suffered this problem except for you and you've reset the game to the default settings, then you can't blame the developers because 1 out of (at least) several hundred thousand combinations of hardware and software doesn't work. Nobody else has been able to replicate this bug. It affects only you, which means that the problem may not even be with Sauerbraten itself but could be with one of the libraries the game depends on or it could be almost anything else causing it.

It's a game you're having issues with here, not some massive world-serving business software. One game out of many. Nobody likes it when people rage out at them because of computer issues but why so serious? You're making it out as if this is some massive disaster that has cost you everything. Nobody is gonna help you with an attitude like that, so relax a second, contact the developers (and/or pretty much anyone more knowledge about this than me), see if anyone else has experienced issues, see if other people can replicate the bug, try upgrading some libraries if they're outdated, fiddle with settings and if all else fails: it's just one game, find something else to entertain yourself with.

(I apologise if this was out of line but seriously...o.O)

---

### Post by Joseph Schwenker on 2010-06-21
You say it's just one game, but it's one of the, what, seven free games for Linux?  I can't find some other game to entertain myself with.  Blood Frontier closed down (it was my favorite game ever), and the fork to Red Eclipse is taking a while.  Yes, I was a bit too serious, though this is as serious as an application crashing for me.  The coop edit mode is a level editor, and if it crashes, I lose all of my work.  The fact that I can't simply alt tab out of it IS a problem.  I believe that is SDL that provides that API for taking input, but the developers are the ones who used it.  It is a real problem for people coming to Linux, as they'll be the ones whining about how "in Windows this wouldn't happen".  To me, it is a flaw that needs to be fixed.  I do not know how to report bugs.  Maybe it's just my keyboard.  I've been having quite a lot of problems with it.  Then again, probably not, as I am able to type after press ctrl alt F1.  I think it is a problem with something losing focus.  When I press t, I am able to press ctrl alt space to summon ibus, so it seems like the keyboard input has some special type of focus.  You should realize how annoying this is, and you shouldn't make saints out of the developers.  They make bad decisions sometimes, and using SDL was a bad decision.  Just like the movement to Pulseaudio, the lack of people supporting it (Wine's stubborn developers), or the Pidgin team being all stubborn about video chat.  If you're going to flame or criticize me for criticizing developers any more, then I suggest you leave.  If you would care to help me in reporting the bug, then please do so.  Developers shouldn't take shortcuts in porting things.  They need to make them work as well as the next system.

---

### Post by HoKaze on 2010-06-21
I apologise for my earlier behaviour. I was out of line and I have my reasons by none of them are valid excuses. Let's work together on this:
Looking around the only place I've found so far where you can submit bug reports is here: [http://cubeengine.com/forum.php4?action=display_thread&thread_id=1890](http://cubeengine.com/forum.php4?action=display_thread&thread_id=1890)
Thankfully you don't need to register and I think some of the posts as well as the guidelines at the top should help you with setting things out. However, as they say, the problem needs to be reproduced by others in order for them to stand much chance of finding the solution or cause. I'd mention the losing focus thing to them, it seems odd.

Have you tried running in windowed mode? Are you able to alt-tab and adjust volume there? Additionally, when in windowed mode do you see the focus changing on the window title (e.g. it fades as if you clicked off the window)? If you're able to bring up ibus with a keyboard shortcut, can you try binding a terminal to a key combination? That way at least you can kill the program without having to login on tty1 and save some time. Also, if it is a focus issue, and you can bring up a terminal, you may be able to alt-tab into Sauerbraten even if you can't alt-tab out. This may have an effect.
I'm just guessing with all these above but it can't hurt to try them, right? In any case they give you more data for your bug report.

There are some good lists out there for Linux games and I daresay that when it comes to FPS games we're a bit saturated compared to other genres. Try searching "top linux games" or "top 42 linux games". There are a lot of repeats and some in these sorts of lists won't be free but most will. There aren't any I know of that have the great map editing as Cube 2: Sauerbraten or Blood Frontier/Red Eclipse but I'd imagine that the original Cube, outdated as it may be shouldn't be too far away from Cube 2 and with the Quake style gameplay Sauerbraten has there are plenty of similar games out there.
(Also, um, Sauerbraten was never ported to Linux. It was made for Linux since day 1 as far as I can tell, what with it being based on the original Cube and all. Just saying...)

---

### Post by Joseph Schwenker on 2010-06-21
I'll try running in windowed mode soon.

---

### Post by Joseph Schwenker on 2010-06-28
I'm having the problem again... in windowed mode.

---

### Post by Joseph Schwenker on 2010-07-04
I'm having the problem... again.  It's in windowed mode, and for some reason, the text field froze.  After a while, it disappeared, and I could move.  Not sure why.  Is there a timer for the text field, and after a certain time, it disappears?  Either way, when I pressed t again, the text field was frozen.

---

### Post by Joseph Schwenker on 2010-07-04
Hmm.  Well, when the chat field froze, minimize the application, switching to another, or anything else did nothing.  Eventually, I found that if I hit super space to open Gnome Do, then typed in "chrome", then hit enter, that when Chrome opened, the chat field disappeared.  However, when I pressed t to explain what had just happened, the field froze again.  Opening Chrome from Gnome Do seems to free me from the field, but does not allow me to continue typing. I have to restart Sauerbraten for that.

---

### Post by Joseph Schwenker on 2010-07-04
It seems to happen after a lag spike, and always happens in edit mode.  It happens in both windowed and fullscreen.  Opening any application through Gnome Do exits the chat field.  After the chat field freezes, you will never be able to type in it without it freezing until you restart the game.

---

### Post by Joseph Schwenker on 2010-07-04
Now it's happening every time I play the game on the map I made in coop edit mode.  EVERY SINGLE TIME.  I'M SICK OF THIS.  THIS NEEDS TO BE SOLVED.  How can I report this bug?

---

### Post by Joseph Schwenker on 2010-07-04
Hmm... it may be associated with my input method in Ibus.  I use the Esperanto X-Method, but just enabled Anthy for Japanese.  I had the problem even before I enabled Anthy, so it may be the fault of Esperanto X-method.  I could reproduce the problem by:

Opening Sauerbraten
Pressing T
Pressing enter
Repeating pressing t and enter until enter does not exit the chat field.

Now, quit Ibus, which will disable the x-method input.

Open Sauerbraten
Press t
Press enter
Repeat pressing t and enter, and notice how the chat field does not freeze

It seems that Sauerbraten it not integrating well with Ibus's x-method Esperanto input.

---

### Post by Joseph Schwenker on 2010-07-11
A lot of applications have problems with Ibus, and specifically, the Esperanto x method input.  That particular input method is underdeveloped.  Either way, if I quit Ibus, I no longer have the problem in Sauerbraten.  Source Engine games have more responsive input, too.  I love Ibus, but it's not good for games.  We should report this to Ibus, and, if necessary, Sauerbraten.

---

