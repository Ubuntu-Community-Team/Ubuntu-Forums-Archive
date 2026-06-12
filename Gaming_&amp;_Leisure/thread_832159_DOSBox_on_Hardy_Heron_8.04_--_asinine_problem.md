---
title: "DOSBox on Hardy Heron 8.04 -- asinine problem"
date: 2008-06-17
forum: Gaming &amp; Leisure
---

### Post by gazelle974 on 2008-06-17
Hi guys, I have recently just converted to Linux, and ubuntu hardy heron is my first distribution. Everything works great, and I love it, with the exception of one problem so far. 

DOSbox 0.72 keeps returning this error when I try to run it from the shell:

ebrahim@ebrahim-desktop:~$ dosbox
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
Exit to error: Can't init SDL No available video device

I tried looking at other posts regarding this topic, but to no avail. Perhaps this problem is unique to my hardware and setup. Nevertheless, I was wondering if any of you guys can help me out with this problem. Anything is greatly appreciated, thanks in advance.

---

### Post by pytheas22 on 2008-06-17
Try turning desktop effects off (go to System>Preferences>Appearance and select the Effects tab to set them to "none") and see if it makes a difference.  My guess is that dosbox doesn't like the opengl video driver, and this will at least confirm that and tell us where to look for a solution.  Please report back after desktop effects are turned off.

---

### Post by gazelle974 on 2008-06-17
Hi pytheas, thank you for your response and FYI:
     I am running compiz fusion and so by turning off effects I take it you meant running "metacity --replace", since it seems to accomplish the same thing. Nevertheless I tried both approaches separately; meaning I replaced the window manager, and I also turned off effects through the appearance dialog box as well, -- with no desirable results unfortunately. I did not try both methods concurrently. So since this venue does not corroborate your hunches, does this necessarily mean that openGL is completely out of the picture for this troubleshooting process? Regardless, what would be our next course of action?

---

### Post by pytheas22 on 2008-06-17
Alright, must not be the opengl then; I just thought it was the most obvious place to look.

I found another thread--maybe you've already seen it--that says you needs to have done this:
```

sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa libsdl-net1.2 libsdl-sound1.2
```

try that and see what happens.  In the meantime I'll take a look at my dosbox configuration and see if I can find anything that might explain your problem.

---

### Post by gazelle974 on 2008-06-17
> ebrahim@ebrahim-desktop:~$ sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa libsdl-net1.2 libsdl-sound1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian is already the newest version.
libsdl1.2debian-alsa is already the newest version.
libsdl-net1.2 is already the newest version.
libsdl-sound1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Okay, that's what I get, since I have already installed those libraries. I installed my box via "sudo apt-get install dosbox." By the way what release of Ubuntu are you running?

---

### Post by pytheas22 on 2008-06-17
I'm on Hardy 64-bit with Intel video.

I looked at my dosbox.conf and didn't find any options relating to video that looked interesting.

I did read, however, about someone having this problem with dosbox version 0.7x, but in 0.6 it's fine.  So you might try installing an older version of dosbox from [http://packages.ubuntu.com/dapper/dosbox](http://packages.ubuntu.com/dapper/dosbox) (scroll to the bottom of the page and click on the appropriate link for your architecture, and after it's finished downloading a GUI will come up for installing it).  Does that make a difference for you?

Other workarounds if you're interested are to use dosemu, another DOS emulator (not as many features as dosbox, but it works alright for me) or to try running the Windows build of dosbox in wine--kind of silly to emulate an emulator, but it might work.

But for the time being, why don't you see if you can use the 0.6 version of dosbox and we'll go from there.

---

### Post by gazelle974 on 2008-06-17
Alright I'll give 0.6 a shot. I know DosBox through Wine would work, but isn't that a little inefficient?

---

### Post by gazelle974 on 2008-06-17
> ebrahim@ebrahim-desktop:~$ dosbox
Exit to error: Can't init SDL No available video device


....And that is what I got. The only difference I noticed was that the prompt was more terse.:)
This was dosbox_0.63-2.1_i386.deb

I did try getting version 0.72 for windows and using Wine to emulate it. It actually works fine. It just seems a little inefficient (Although I don't think the difference is noticeable by human perception). I guess it will keep me going for a while. I just don't understand why the algorithm comes to the conclusion that there is not an available video device. Strange, isn't it?

---

### Post by gazelle974 on 2008-06-17
By the way, how is dosemu for running old games?

---

### Post by pytheas22 on 2008-06-17
Sorry that the older build of dosbox gives you the same error.

Dosemu works fine for Commander Keen for me, but it can sometimes be a little choppy.  I prefer dosbox.

Running dosbox through wine isn't necessarily any more inefficient than running the native Linux build.  Unlike dosbox, wine isn't actually an emulator; it implements reverse-engineered Windows libraries and system calls to make it possible to run Windows software, but it doesn't emulate any hardware.  In most cases wine is just as efficient as running the same software on a real Windows system.  In a few cases (Starcraft is a notable example) wine is known to be faster because its libraries are more efficient than native Windows ones.  And in any case, if all you're doing is running circa-1990 games in dosbox, it would probably work fine even if wine were really inefficient.

That aside, I'll do some more reading and see if I can find any other ideas for solving this issue.

---

### Post by gazelle974 on 2008-06-17
Hmmmm, good point. Well I'll keep you updated regardless, let me know if anything comes to your mind. So SDL is just a protocol supporting archaic multimedia, is that the function behind these libraries? Is this synthesized problem between dosbox and sdl in anyway portentous of further problems where sdl is involved?

p.s. (commander keen is gold, I tried that one on wine and dosbox myself)

---

### Post by FranMichaels on 2008-06-17
> **gazelle974 said:**
> Hmmmm, good point. Well I'll keep you updated regardless, let me know if anything comes to your mind. So SDL is just a protocol supporting archaic multimedia, is that the function behind these libraries? Is this synthesized problem between dosbox and sdl in anyway portentous of further problems where sdl is involved?

p.s. (commander keen is gold, I tried that one on wine and dosbox myself)

"Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer. It is used by MPEG playback software, emulators, and many popular games, including the award winning Linux port of "Civilization: Call To Power."
[http://www.libsdl.org/](http://www.libsdl.org/)

In your dosbox.conf or .dosboxrc try changing
output=overlay

if that doesn't work try

output=opengl

---

### Post by gazelle974 on 2008-06-18
Strange, I don't have a dosbox.conf???
That is kind of weird. Does that have anything to do with the packaging system for the repository? Maybe I have to go directly to the dosbox website. I'll give that a try. I'll keep in touch with you; but as for now I need to get to sleep, I'll keep you updated. Thanks for all your help today though, both of you.

---

### Post by gazelle974 on 2008-06-18
Well I created a conf file, and copied in default settings from a website that makes this available. I then tried what you said with overlay and opengl, but it still doesn't work out for me. I'm starting to think that Wine might be the better option for me. Nevertheless, let me know if you guys stumble upon anything.

---

### Post by pytheas22 on 2008-06-18
How did you create the configuration file?  Because you're supposed to do it by typing CONFIG -writeconf dosbox.conf at the dosbox command prompt (I would have mentioned this before but I forgot that it was sort of complicated).  If you just copied and pasted text from a website, it might not work for your version of dosbox.  Also, dosbox.conf needs to be in the same directory as the dosbox executable, which should be /usr/bin.  If this isn't where yours is, you could try moving it there and seeing if the change mentioned by FranMichaels makes a difference.

---

### Post by FranMichaels on 2008-06-18
> **pytheas22 said:**
> How did you create the configuration file?  Because you're supposed to do it by typing CONFIG -writeconf dosbox.conf at the dosbox command prompt (I would have mentioned this before but I forgot that it was sort of complicated).  If you just copied and pasted text from a website, it might not work for your version of dosbox.  Also, dosbox.conf needs to be in the same directory as the dosbox executable, which should be /usr/bin.  If this isn't where yours is, you could try moving it there and seeing if the change mentioned by FranMichaels makes a difference.

The issue is he or she cannot launch dosbox period, to even get to the "Z" prompt. 

Also, you can rename your dosbox.conf to .dosboxrc and dosbox will see it fine. I prefer this as it seems more appropriate for a *nix app (I like my personal configs in my home folder) :)

I will create a brand new config file, and just tweak the output option. Due to forum upload requirements, I will call the file .dosboxrc.txt. Please save it to your home folder, and remove the .txt. Press ctrl + h to view hidden files (those preceded by .) in nautilus.

If the issue still arises, I would recommend going to the dosbox forums, because this sounds like one heck of a bug.

[http://vogons.zetafleet.com/viewforum.php?f=31&sid=dc013113e735724201897a80c4b18814]("http://vogons.zetafleet.com/viewforum.php?f=31&sid=dc013113e735724201897a80c4b18814")


EDIT: pytheas22, don't worry. :) I didn't really think about this either, or I would have posted a dosbox config file in my first reply to gazzelle974. It's just so odd for dosbox to not run out of the box is all. I've used it since like .58... :)

---

### Post by pytheas22 on 2008-06-18
> The issue is he or she cannot launch dosbox period, to even get to the "Z" prompt.


Sorry, my mistake.  I knew that but wasn't thinking properly, or I would have realized that it's impossible for the original poster to run the CONFIG command.

---

### Post by gazelle974 on 2008-06-18
Okay Fran, So you are saying that I just have to save your modified configuration file directly to my home folder (If I installed via apt-get dosbox), is that it? no other folder, just go straight to /home/user-name/

If so, I'm going to give it a shot right now. I'll let you know what happens, thanks for the config.

---

### Post by gazelle974 on 2008-06-18
Okay, so I renamed your output file to .dosbox.rc and copied it straight to my "/home/user-name/" directory, then I went to the gnome-terminal and proceeded as follows:

> 
ebrahim@ebrahim-desktop:~$ dosbox
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
Exit to error: Can't init SDL No available video device

ebrahim@ebrahim-desktop:~$ 


Yea, looks like nothing is helping. It looks like Windows DosBox conjoined with Wine just might have to suffice for now. Still thanks for your help; I'll be sure to check out what happens on Vogon.

---

### Post by gazelle974 on 2008-06-18
P.S. You all have some interesting websites. OS comparisons, mail servers, compilations, emulation; those are some pretty scintillating topics. Lol, my technical expertise extends to rudimentary knowledge of C, hehe. Within the scope of linux you can classify me as some sort of a dilettante. :(

But I'll keep learning, and hopefully I'll eventually accrue enough knowledge to function more independently (Although I'm sure that's not the philosophy that is preached within the Linux community, but still :)). 

Another thing: I heard of the open source Python Language, and I am also aware of the fact that some database and research software support scripting using Python as a medium. I was just wondering, can any of you convince me of a good reason to take up Python. Based off of your experiences (if you have any), how does it stand up against C. What are some hypothetical situations where it would be useful (or not)? Feel free to expound as elaborately as you deem necessary. Remember, I'm a newb :)

---

### Post by yarjar on 2008-06-18
Meh, my dosbox works fine but the sound has been choppy ever since switching to PulseAudio. What is PulseAudio even good for anyway?

---

### Post by gazelle974 on 2008-06-18
I think it's just a sound server that can accept input from more than one process, and redirect that as output to the soundcard. That's just me, but pytheas and fran seem to know more about this kind of stuff.

---

### Post by FranMichaels on 2008-06-18
> **gazelle974 said:**
> Okay, so I renamed your output file to .dosbox.rc <snip>

.dosboxrc

:) No extension.

Mmm... programming. I really keep it minimal. I use bash to automate tasks I like to do from commandline (like downloading source code off of svn or git, then building and installing it)
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)

As for python, just take a look
[http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)
See if you like the language and play around. If not, you can always still use C.
Have fun with it, there is plenty to explore and people from varying knowledge backgrounds happy to help. Or why not look at the source code from a python program that interests you?

Looking at synaptic I feel like a kid in a candy store. Want to look into music synthesis, render fractals, art, science, calculators, games, emulators, astronomy software, etc. Quite amazing. 

yarjar: I've decided to keep pulse audio off, and just use plain ALSA or OSS. So I honestly don't know. You don't have to use it if you do not want to, choice is nice :)

---

### Post by pytheas22 on 2008-06-18
I don't know much about PulseAudio but from what I do understand it's basically just a way to simplify how sound works by abstracting it away from the hardware a bit so that it's easier to accept input from multiple sources and output it properly.  But I really don't know much about these things; indeed I don't know as much about computers as you might think.  I'm a PhD student in history and plan to end up in a humanities department somewhere eventually, not anywhere near IT.  I only started using Linux because I didn't want to pay for stuff anymore.  I don't know how to program beyond really, really basic stuff, and I don't understand much about Linux beyond what I've had to deal with personally.  So the point is, don't think you have to be overly technically inclined to use Linux, especially Ubuntu.

As for Python: as I say, I'm not a programmer at all, but I did take a four-week course once about Linux/Unix where we spent a couple days on Python and had to write a few very basic programs.  Even I was able to understand it without too much difficultly, so you might want to give it a shot.

From what I understand, Python's advantages include portability (it's self-compiling, so you don't have to deal with putting out different builds for different processor architectures and operating-systems; you can port it with very, very minimal effort), simple and efficient syntax (no need to declare variables or classes, et cetera), easy to extend into GUI's, it enforces good programming techniques, code is clear (indentation is required because it's used to tell the program how to run, so the code ends up being quite readable no matter who writes it, even me) and lots of freely available modules exist so that you're not always having to start from the ground-up...for instance my teacher showed us how he wrote an entire web server in Python in less than 100 lines by taking advantage of pre-existing modules that deal with a lot of the dirty work.

Python is a really big deal in the open-source world, so you might want to give it a try.  It's not as fast as C, so you can't use it to write a kernel or other very low-level stuff, but it's faster than a lot of other languages, which is especially impressive since Python is self-compiled at runtime.  For most applications, however, Python is plenty fast.

This [thread]("http://ubuntuforums.org/showthread.php?t=271383") might be useful if you want to play with Python.

---

### Post by gazelle974 on 2008-06-19
> **FranMichaels said:**
> .dosboxrc

:) No extension.

Mmm... programming. I really keep it minimal. I use bash to automate tasks I like to do from commandline (like downloading source code off of svn or git, then building and installing it)
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)

As for python, just take a look
[http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)
See if you like the language and play around. If not, you can always still use C.
Have fun with it, there is plenty to explore and people from varying knowledge backgrounds happy to help. Or why not look at the source code from a python program that interests you?

Looking at synaptic I feel like a kid in a candy store. Want to look into music synthesis, render fractals, art, science, calculators, games, emulators, astronomy software, etc. Quite amazing. 

yarjar: I've decided to keep pulse audio off, and just use plain ALSA or OSS. So I honestly don't know. You don't have to use it if you do not want to, choice is nice :)
Ooops, I'll give it another shot then.

---

### Post by gazelle974 on 2008-06-19
Cool, sounds like a potentially expedient type of language. One that can accomplish more simple tasks quickly.

---

### Post by gazelle974 on 2008-06-19
Cool, sounds like a potentially expedient type of language. One that can accomplish more simple tasks quickly.

> From what I understand, Python's advantages include portability (it's self-compiling, so you don't have to deal with putting out different builds for different processor architectures and operating-systems; you can port it with very, very minimal effort), simple and efficient syntax (no need to declare variables or classes, et cetera), easy to extend into GUI's, it enforces good programming techniques, code is clear (indentation is required because it's used to tell the program how to run, so the code ends up being quite readable no matter who writes it, even me) and lots of freely available modules exist so that you're not always having to start from the ground-up...for instance my teacher showed us how he wrote an entire web server in Python in less than 100 lines by taking advantage of pre-existing modules that deal with a lot of the dirty work.

Python is a really big deal in the open-source world, so you might want to give it a try. It's not as fast as C, so you can't use it to write a kernel or other very low-level stuff, but it's faster than a lot of other languages, which is especially impressive since Python is self-compiled at runtime. For most applications, however, Python is plenty fast.

This thread might be useful if you want to play with Python. 

---

### Post by gazelle974 on 2008-06-19
Okay, I took out the imaginary "rc" extension, and this time I knew it worked since a backup file was instantly created upon my ordered execution of dosbox. However, after typing dosbox into the prompt I still get the same result.

---

### Post by FranMichaels on 2008-06-19
Ok last couple of ideas.

```
sudo apt-get install ia32-libs
```

If that still doesn't help, try to reinstall dosbox from synaptic.

Last, absolute last idea.

```
sudo apt-get build-dep dosbox
```
This will get what is required to build dosbox from source. Perhaps there was some missing dependency in the package, or you can try your hand at building from source.

[http://prdownloads.sourceforge.net/dosbox/dosbox-0.72.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.72.tar.gz?download)

Extract the file

In the terminal, go to the directory (dosbox-0.72)

type
```

./autogen.sh
./configure
make
sudo make install
```

Look for any pertinent error messages along the way.

Hopefully the dosbox devs can provide an answer if this still doesn't work... I don't have a 64-bit box to test on (my core duo laptop isn't a core2duo :KS)

---

### Post by gazelle974 on 2008-06-19
> ebrahim@ebrahim-desktop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs


Different package name?

---

### Post by gazelle974 on 2008-06-19
Hold on, are you sure I should do this? -- I don't have an AMD chipset.

---

### Post by FranMichaels on 2008-06-19
> **gazelle974 said:**
> Hold on, are you sure I should do this? -- I don't have an AMD chipset.

Ignore the ia32-libs thing, I got confused, thought you had 64-bit Hardy when I skimmed the first page in this thread.

As for compiling, can't hurt.

---

### Post by gazelle974 on 2008-06-22
Alright, I'll give it a shot next weekend when I have time. Thank you all for your input though.

---

### Post by wingnux on 2008-07-04
I too get choppy audio on dosbox when pulseaudio is enabled =/

---

