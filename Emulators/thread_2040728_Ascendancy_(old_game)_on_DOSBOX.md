---
title: "Ascendancy (old game) on DOSBOX"
date: 2012-08-11
forum: Emulators
---

### Post by aaeamdar on 2012-08-11
So I've been trying for the last few days to get [Ascendancy]("http://en.wikipedia.org/wiki/Ascendancy_%28video_game%29"), an old game that I really like, to run again on my computer. I got this game to run under [DOSBOX ]("http://www.dosbox.com/")around a year ago, but I was running Windows at the time (not 100% sure why this should make a difference but thus far it has).

I've done dozens of google searches, and tried to go through all the  step-by-step instructions but they all fail. Part of the problem at  least seems to be that almost everything I've found is from 2008 (or  earlier). I DO have the game, legally owned, bought, on CD and so on, so  that's not a problem, though a lot of these walk-throughs instruct me  to download the game from xyz website, and I wonder if these download  versions have something that my actual legit version doesn't.

Essentially, it all breaks down at this point: I know how to mount both a  CD and a non-CD drive on DOSBOX. I do that, and then I run the install  batch file (or I directly run the install.exe. Or I run the install.exe  through "dos4gw.exe" like the install.bat file does). And it spits out a  bunch of text about how the game has been installed... but nothing has  actually happened. I've tried a lot of different approaches, including  copying all the CD files to my harddrive, but thus far that's still  what's happened.

The one point of progress I've made is to make superficial changes to  the install.bat file (the one on my harddrive, not the original) to  remove extraneous text and also a couple CLS calls that were possibly  deleting some feedback. When I do that, I get:

```

Illegal command: setsound
Ascendancy has sort of been installed successfully!
Press any key to continue.
Illegal command: uvconfig
Ascendancy installation is complete! But not really.

```from this fill:

install.bat (my version):

```
@echo off 
/data/dos4gw /data/install.exe 
if errorlevel 2 goto end 
if errorlevel 1 goto 1 
setsound 
echo Ascendancy has sort of been installed successfully! 
pause 
uvconfig -gen 
goto 2 
:1 
setsound 
:2 
echo The Ascendancy installation is complete! But not really. 
:end 
 

```The sarcastic comments are part of my additions, of course.

Anyway, long story short after doing this nothing changes. If I try to  run Ascend.exe it gives me copyright information, a 2 second delay, and  exits with no error message.  I also tried getting this from an SVN  repository ([here]("http://code.google.com/p/ascendancy/wiki/WikiSVNCompilUbuntu")) but encountered errors. If anyone wants details I can provide that but this post is already super-long. 

I'm on the latest version of Ubuntu, fully updated. Further details on request.

Thanks in advance for any help.

---

### Post by cwsnyder on 2012-08-11
Have you tried running it in a FreeDOS virtual machine, instead of DOSBox?

FreeDOS is at [http://www.freedos.org](http://www.freedos.org)

---

### Post by aaeamdar on 2012-08-11
I was unable to use that program, since chapters 2 through 6 of the setup guide were missing. If you have information about how to move through that process let me know.

---

### Post by sanderj on 2012-08-12
I downloaded a certain file ascendancy.rar, and then:

```
unrar x ascendancy.rar 
cd ASCEND/
dosemu ASCEND.EXE
```

... and that worked: a screen with a game, a menu and flying things.

Does that help?

---

### Post by aaeamdar on 2012-08-12
> Does that help?

Unfortunately, not really. Where did you get your "ascendancy.rar" file? What do those commands do? How do they fix the problem? I have some basic trust that people aren't trying to screw me on these forums but I'm not going to just randomly run commands without having a clue what they're supposed to do.

---

### Post by sanderj on 2012-08-12
> **aaeamdar said:**
> Unfortunately, not really. Where did you get your "ascendancy.rar" file? 


Via a well known torrent site. 

> **aaeamdar said:**
> 
What do those commands do? 


If you have your own copy of Ascendancy in a directory, so with ASCEND.EXE in it, you can skip the first command. Then only running 'dosemu ASCEND.EXE' in that directory should be enough.


> **aaeamdar said:**
> 
How do they fix the problem? 


By using a different method: by using the tool 'dosemu'. I have no errors; it just works. YMMV.

> **aaeamdar said:**
> 
I have some basic trust that people aren't trying to screw me on these forums but I'm not going to just randomly run commands without having a clue what they're supposed to do.

To find out what a command does, you could do 'man <command>'. So:

```
man unrar
man dosemu
```

'cd' has no manual page, but if you know DOS, I guess you know 'cd'.

HTH

---

### Post by aaeamdar on 2012-08-12
Hey! It worked. I guess all I needed was where the ascendancy.rar file was (I did google ascendancy.rar but got nothing). I guess forum rules prohibit talking about specific torrent sites? Anyway I was confused by the vagueness. But thanks for your help.

---

