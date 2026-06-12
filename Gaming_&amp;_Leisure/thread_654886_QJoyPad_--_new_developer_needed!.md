---
title: "QJoyPad -- new developer needed!"
date: 2007-12-31
forum: Gaming &amp; Leisure
---

### Post by ethana2 on 2007-12-31
Before I go on to the subject of this post, here is an excerpt from a conversation I had with Nathan Gaylinn, the creator of QJoyPad.

(He had just helped me get it working and explained its development status to me, via email)

me to Nathan Gaylinn:
Thank you for the work you've done on this project, and the support you've given me.  I think that QJoyPad has a lot more potential than some people realize, and I think I will try to find someone with the time and will to take the torch, as well as perhaps rolling some up-to-date packages for you myself.
		
Nathan Gaylinn to me:
I'd love to see that  :)  I wrote QJoyPad because there was a niche that needed to be filled, and I'm very proud of what I've done. I've also grown and become a much better programmer, so in some ways I'm almost embarrassed by it; it certainly could be a much better program, from many perspectives. Unfortunately, I'm just not the person to make those improvements anymore.

That said, I would be very grateful if you could help the project, and I'd be glad to share all I know about the program and all I learned about the technology involved in the process of making it. Please let me know if you find someone!  ;)

----this is a call for developers----
I'm bringing this request to the Ubuntu community because I believe that you here recognize the potential of the Linux operating system for purposes some others write it off for.  They said it wasn't suitable for the desktop.  You /made/ it suitable for the desktop.  Many people say it's not suitable for gaming, and every day, you get closer to changing that.  By making it the best desktop operating system in existence, you are bringing it to the attention of game developers everywhere, even if it only means that a windows game is written with OpenGL instead of DirectX.

As many of you are aware, there is a project called QJoyPad, [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/) , which is meant to allow Linux gamers to use their gamepads, joysticks, and other controllers with, of course, games on Linux.  Today we have a problem: QJoyPad doesn't support SDL, and Nathan does not have the resources to continue development, and hasn't for some time.  As more games use SDL every day, this problem slowly relegates QJoyPad to worthlessness.  To be blunt, QJoyPad, while somewhat functional, is dead.  I submit to you that it is very important that we resurrect it immediately, get it up to spec with a new developer, and get it into Ubuntu repositories.

Nathan Gaylinn needs a replacement, and every Linux gamer with a controller needs someone to step up to that position.  If you have the skill needed for the job, and you have time on your hands that you wouldn't mind spending helping the community out, I, Nathan, and many others here would be very grateful if you'd take on the challenge.  If you're interested, please email me: [email]ethana2@gmail.com[/email]

---

### Post by csi_ on 2008-01-02
I found a version of qjoypad, compiled for gutsy, which (only) corrects CPU usage:

[INDENT][http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100](http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100)[/INDENT]

cheers

---

### Post by ethana2 on 2008-01-02
Thanks for the reply, but that french guy didn't really do much; he altered the sleep timer for a loop that shouldn't exist...
I passed a Todo list to Nathan that he could post on the qjoypad page if he chooses to, but I'll post it here as well:

-Replace check for input/sleep loop with native X input event handler.
-Add support for SDL apps that don't take advantage of non-standard input devices.
-Update GUI to the latest QT/KDE
-Roll some updated packages.
-get updated code into distribution repositories-- especially psubuntu, wiili, and Free360, where non-mouse/keyboard devices are owned by every user.

---

### Post by Praadur on 2008-01-02
I completely agree with the first poster...

I admit, I had trouble compiling this one (on an amd64 sytem), I had to edit the sources myself to cure the CPU issues, and the GUI doesn't work so I have to create and edit the lyt files it needs by hand, which means keeping a keycode list handy.

But I swear by this program, though that might sound nuts, considering.

It's primarily because there's nothing else out there like it, and it serves multiple uses.  For example, even though I can't use the GUI to set key-to-controller-function bindings, I can use it to *test* joypads.  When I buy a new joypad, I always test it first in qjoypad to make sure it's working fully.  After that, I keep it around for games and emulators that don't have proper joypad support (there are more of these out there than one might think, Gens -- which I'm just using as an example -- tends to completely freak out when trying to configure joypads, at least on an amd64 system).  By setting gamepad functions to keys, I can allow those to work, but I can even allow things that were never meant to have pad support running too.  Such as using a wireless pad as a KPlayer remote, or playing flash games on a pad, et cetera.

If someone did take up the task of developing it, then the first order of business really would be fixing whichever bug in the GUI doesn't permit key-grabbing (in some cases, not all) or saving a finalised setup to a lyt file.  Those are the only two things that really keep it from perfection as far as a stable end-user application is concerned, the memory issue has already been cured, after all.

After that, it might be nice to see some new features...

i.) It would be wonderful to have support for linking lyt configurations to focused windows.  For example, if I have KPlayer focused it could automatically switch to the KPlayer.lyt configuration, and if I were to run game X or Y, then by the name of the window/process, it could switch to the lyt set for that.

ii.) 'Macro support'.  By that, I mean being able to have strings of keys entered when a button is pressed.  The user would hit a 'record' button and then enter in a string of keys, following that they'd press stop or somesuch to save it.  This would be useful for all manner of things in different games which could use a level of automation.

With those two features, qjoypad could easily become just as powerful as any driver-configurator that one might see packaged with joypads for windows.  This really could be the 'killer app' for Linux gamepad and joystick users.

Just my thoughts on the matter, anyway!

---

### Post by ethana2 on 2008-01-02
per-window layout support
macros

Good ideas.  I'll be sure those get on the list.  Thanks.

---

### Post by ethana2 on 2008-01-02
Also, note that while Ubuntu's goal is to basically be the best desktop OS, it should also be the best game console OS, 'cause that's where it's being put.

This consists of:
-The nouveau driver's gallium OGL implementation
-Solid QJoyPad and fully integrated
-Shuffling the DE off to swap when running SDL/OGL apps.

People are abandoning the PC for game consoles because of Windows.  Let them run /to/ us for their gaming by being solidly established where they're going.
Microsoft won't have seen it coming.
Anyway, that's part of the vision, and this is the first step.

Anyone?  Anyone?

---

### Post by ethana2 on 2008-01-02
"More than anything else, I think it was installing Vista that made me hate PC gaming. The constant, system-level interruptions, the impaired compatibility, and most of all the savage kick to my framerate's exposed groin made me wonder what precisely in the ********  **** I was doing screwing around with this onyx monolith. I knew I was just going to have to upgrade eventually (no), and I wanted to see if there was anything to this DirectX 10 thing (no), and I wanted to see what the Windows version of Live was like (a warcrime) so I bit the bullet. I shouldn't have. It was a bullet! That should have been my first clue. "

--that's what I'm talking about.  A good gaming OS needs a game /mode/.
We have the flexibility to do that.

---

### Post by Vadi on 2008-01-02
Unfortunately I'm not up to the coding task, or have any controllers. But this sounds like a very useful project; I'll keep it in mind and mention it whenever possible :)

---

### Post by ethana2 on 2008-01-03
Yeah, thanks.

I can't code either as of yet...
You know, it just dawned on me how valuable that passing idea is: a gaming mode:  Where all applications are suspended to swap but one and its runtime dependencies...  An OS that does that would be excellent for gaming, on a pc, on a console, or really wherever you stick it.

I think we can honestly make Ubuntu the best gaming OS on the planet if we do this right.  The games will follow.

Step one is QJoyPad, but a game mode can be developed simultaneously.  Once we get a developer for this, I guess I'll see if someone wants to take on that project.

---

### Post by acoustibop on 2008-01-03
There's a couple of threads already floating around here on gaming versions of Ubuntu, ethana2 - one is  [Gubuntu the gaming distro]("http://ubuntuforums.org/showthread.php?t=267336&highlight=gubuntu").

BTW, love the description of the 'Onyx Monolith!'  Is it yours, because I propose stealing it?

---

### Post by ethana2 on 2008-01-03
There's no need to make a special distro.
Just two apps that need to be brought up to spec.  Let me give your brain something to render for you:

You install a package from repos called gaming-mode.  It's a container, like WINE, but much different.  When you pass a program to this application, it puts it in a special state, where it's the only program running.  So you go through your menus and edit them so that all your FPS games use it, to see what happens.

Upon executing this program, a window pops up, because it is the first time you've run it.  It asks you for settings regarding more than one app being able to run at a time, and other container settings.  You tell it, this time anyway, that you just want to run tremulous and its runtime dependencies, with the exception of your adding qjoypad.
You click 'ok', the window closes.  After a second, you're screen goes black and a small shiny looking splash appears in the center of your screen with a picture of the tremulous .svg icon and a red progress bar labeled 'entering game mode'.  The bar rapidly progresses from the left, and as it does, text appears under it describing what it's doing:
suspending unwanted processes; preparing to unload suspended processes to swap; unloading RAM; executing tremulous.
When it's done, there are few things in your RAM.  You have the kernel, your graphics driver, a few modules of your X server perhaps, QJoyPad, and Tremulous.  Very handy of course, as you're actually running it on a modded xbox...  with the xbox controller...  and we all know how consoles skimp on memory.  You go online, play a round on transit and get owned by a bunch of lucifer cannon toting jettards... then you exit the application, and the gaming-mode program automatically loads your DE, webkit konqueror, and pidgin back into RAM, and you realize how grateful you are to those awesome folks over at the nouveau project with their new gallium rendering :)

---

### Post by ethana2 on 2008-01-03
This would also be awesome on the PS3, but I don't know if they've regained access to it's GPU (the RSX) yet.  I suppose it may not matter, as they're actually going to try to get 3d rendering up on the SPEs with gallium..

I wish them good success.

---

### Post by abelthorne on 2008-12-07
Any news about someone developing a new version of QJoyPad ? I can't compile the current version (3.4.1) on Intrepid, nor find a usable DEB.

---

### Post by ethana2 on 2008-12-07
None yet :(

---

### Post by cx23 on 2009-03-04
> **abelthorne said:**
> Any news about someone developing a new version of QJoyPad ? I can't compile the current version (3.4.1) on Intrepid, nor find a usable DEB.

[http://ubuntuforums.org/showpost.php?p=6839066&postcount=2](http://ubuntuforums.org/showpost.php?p=6839066&postcount=2)

works like a charm

---

