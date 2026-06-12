---
title: "What is your favorite Genesis/MegaDrive emulator for Linux?"
date: 2005-09-30
forum: Gaming &amp; Leisure
---

### Post by blueturtl on 2005-09-30
I've tried the following:

GENS RC3 - buggy and in a general state of not-working properly
Generator/GTK - works nice, but does not go fullscreen

What emulator would you recommend? Added points go if the emulator is also capable of 32X and SegaCD emulation...

---

### Post by KingBahamut on 2005-09-30
Dgen and M1 are the only two Ive played around with. But I wasnt a fan of Sega Genesis, so that explains alot.

---

### Post by iAlta on 2005-10-01
[QUOTE=KingBahamut]Dgen and M1 are the only two Ive played around with. But I wasnt a fan of Sega Genesis, so that explains alot.[/QUOTE]

I have downloaded M1 and modeler, how do I run them.

And how do I use binerys?

ps. are there SNES emulators for Linux?

pps. Where do I get the games?

---

### Post by mcduck on 2005-10-01
[QUOTE=iAlta]
ps. are there SNES emulators for Linux?
[/QUOTE]
Try snes9x, and if you want a GUI get also snes9express. You can find them with synaptic.

---

### Post by iAlta on 2005-10-01
I have snes9x for Windows, I can try to run it on Ubuntu. It wont hurt.

---

### Post by iAlta on 2005-10-01
I have downloaded snes9xpress. But I dont know what to do nxt. in the INSTALL file, it says '...by typing "./configure" while in the snes9express source directory.' but what the hell is the snes9express source directory?

---

### Post by BoyOfDestiny on 2005-10-01
[QUOTE=iAlta]I have downloaded M1 and modeler, how do I run them.
And how do I use binerys?
ps. are there SNES emulators for Linux?
pps. Where do I get the games?[/QUOTE]
ZSNES! It is my favorite snes emulator. Don't flame me snes9x folks, I used to use it too (even before it was 9x remember snes96 and snes97?)
Zsnes is fast and has top notch compatibility. It has a built in gui (which is optional... it takes command line options too)
Sadly, Ubuntu has version 1.36... which is over 2 years old... and cannot run star ocean or use .jma... 
You can either build from source, or I'll post a .deb of a cvs build...

[www.zsnes.com](www.zsnes.com)

EDIT: I noticed you asked for games... well... 

[http://www.pdroms.de/](http://www.pdroms.de/)

These are all legal, either freeware or public domain...

To get commercial games, you either need to dump the rom from your cartridge... or... well use your brain. :)

---

### Post by iAlta on 2005-10-02
I have downloaded zsnes, but Star Ocean is one of my favorite games.
But I stil dont know how to install a program.

---

### Post by BoyOfDestiny on 2005-10-02
[QUOTE=iAlta]I have downloaded zsnes, but Star Ocean is one of my favorite games.
But I stil dont know how to install a program.[/QUOTE]
No promises... but I'll try and post the deb (and source since it's gpl) on my page tonight. It's a cvs build about 1 week old... has been running pretty well.

EDIT: [http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb](http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb)

This was compiled in breezy... may work with hoary...

---

### Post by iAlta on 2005-10-03
[QUOTE=BoyOfDestiny]No promises... but I'll try and post the deb (and source since it's gpl) on my page tonight. It's a cvs build about 1 week old... has been running pretty well.

EDIT: [http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb](http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb)

This was compiled in breezy... may work with hoary...[/QUOTE]

Thanks
I hanen't tried it yet. I will come back when I have.

I don't konw what a DEB-file is. I wil try if I con use it on "hoary"(or what ever I have)

---

### Post by iAlta on 2005-10-03
hmmm... I assume the usr/local/bin/zsnes shall be in usr/locl/bin. But when I move zsnes to bin it says something like(it's on danish): you are not allowed to wrigth on this folder.
the same happens when I move man1 to man.

---

### Post by Crazy Man on 2005-10-03
Apart from dgen (which is a complete bunch of unconfigurable crap), are there any other emulators available (in apt). If so, how do I get them (just for reference I use Fusion/Kega on my Windows desktop)?

---

### Post by iAlta on 2005-10-03
if u have windows. rom-worldcom

---

### Post by kerm on 2005-10-03
I couldn't find any other genesis/megadrive emulators in apt either besides 'dgen'. 

I used to love 'GENS' when I was running Windows. According to the first poster, the Linux version stinks though.

So far, 'dgen' hasn't been too bad to me but I wouldn't mind trying something a bit more current.  So to answer the original question, I'd have to go with 'dgen' for right now.

---

### Post by BoyOfDestiny on 2005-10-03
[QUOTE=iAlta]Thanks
I hanen't tried it yet. I will come back when I have.
I don't konw what a DEB-file is. I wil try if I con use it on "hoary"(or what ever I have)[/QUOTE]
Ah... no problem. Basically think of it as an installer for Debian and Ubuntu. It will show up in synaptic... and can always be removed cleanly (unlike when you do a make install...).
So basically open up a terminal, and type sudo dpkg -i nameofthedeb.deb
If this is too tricky (I haven't tried this way), right click on the .deb and choose open with, then custom command, and try "gksudo dpkg -i"

---

### Post by iAlta on 2005-10-03
I think I know how to use it. open with Add/Remove Programs, but I have to enter a password, but I dont remember it. Can I get, change or remove the password, or must I reinstall Ubuntu? And if i have to reinstall it can I do so and keep all my data?

---

### Post by iAlta on 2005-10-03
[QUOTE=BoyOfDestiny]
So basically open up a terminal, and type sudo dpkg -i nameofthedeb.deb
If this is too tricky (I haven't tried this way), right click on the .deb and choose open with, then custom command, and try "gksudo dpkg -i"[/QUOTE]
ahh... great!
didnt see this til now, 2 pages. I will try that tomorrow, I just turnd off the PC, gone to bed.

oftopic: its my bday today Im 16 I can drive 30km/h on a scooter and if we stil lived in Denmark, buy akcohol!!

---

### Post by iAlta on 2005-10-04
[QUOTE=iAlta]ahh... great!
didnt see this til now, 2 pages. I will try that tomorrow, I just turnd off the PC, gone to bed.
oftopic: its my bday today Im 16 I can drive 30km/h on a scooter and if we stil lived in Denmark, buy akcohol!![/QUOTE]
 the custom comand worked, but.
I have enter the password.

---

### Post by BoyOfDestiny on 2005-10-04
[QUOTE=iAlta]the custom comand worked, but.
I have enter the password.[/QUOTE]

Well, if you boot in recovery mode, you'd have root access, and you can change your password from there. I'm not exactly sure since I haven't tried to recover a password, you should ask the question in another part of the forum, see if someone can give you the step by step.

---

### Post by iAlta on 2005-10-10
[QUOTE=BoyOfDestiny]Ah... no problem. Basically think of it as an installer for Debian and Ubuntu. It will show up in synaptic... and can always be removed cleanly (unlike when you do a make install...).
So basically open up a terminal, and type sudo dpkg -i nameofthedeb.deb
If this is too tricky (I haven't tried this way), right click on the .deb and choose open with, then custom command, and try "gksudo dpkg -i"[/QUOTE]
OK I know my password now, but when I wright the custom command and my password, geuss what happens,... nothing!
I'll try opening a terminal, but how do i do that??

---

### Post by Zotova on 2005-10-10
[QUOTE=blueturtl]I've tried the following:

GENS RC3 - buggy and in a general state of not-working properly
Generator/GTK - works nice, but does not go fullscreen

What emulator would you recommend? Added points go if the emulator is also capable of 32X and SegaCD emulation...[/QUOTE]

Try [this page](http://www.ghostwhitecrab.com/generator/) - it states it has fullscreen support. You say generator works nice and this is based on generator so it should be an all-round win.

I haven't tested it myself, just compiling it now so I'll report back later to say if it works.

---

### Post by BoyOfDestiny on 2005-10-10
[QUOTE=iAlta]OK I know my password now, but when I wright the custom command and my password, geuss what happens,... nothing!
I'll try opening a terminal, but how do i do that??[/QUOTE]

Actually that sounds about right. To open a terminal it should be under Applications -> Acessories. If it installed, type the word zsnes, if it works you should see zsnes. 

There used to be a menu entry for "run" but it was removed for some reason. So just make a launcher or add an applet to the gnome panel. Basically type zsnes in one of these and you are golden.

---

### Post by Zotova on 2005-10-10
I've now installed the version of generator in the link and can confirm you can run the games full screen.

[Screenshot here](http://shanghai.me.uk/fireimage/images/36102998.png)

The game I was testing didn't show in the screenshot for some reason but basically the window which is black is where the game runs, you can resize and make full screen and the other window is for configuring how the game plays. I needed to tweak a few sound settings for the games to run correctly.

Works a heck of a lot better than dgen and is thankfully resizable.

---

### Post by iAlta on 2005-10-10
[QUOTE=BoyOfDestiny]To open a terminal it should be under Applications -> Acessories. If it installed, type the word zsnes, if it works you should see zsnes. 

There used to be a menu entry for "run" but it was removed for some reason. So just make a launcher or add an applet to the gnome panel. Basically type zsnes in one of these and you are golden.[/QUOTE]
Under Acceories are: Archive Maneger, Calculator, Charater Map, Dictionery and Text Editor. Under Application is a Run Application... (if that helps)

---

### Post by iAlta on 2005-10-10
I found "Terminal"! It's under System Tools.
But stil some problems. This time I have a pic(well... not this time, I have a pic I just don't know how to add it here.)

---

### Post by sabitha on 2005-10-10
i dont know what's wrong with this ubuntu hoary 5.04. but now i can see all my network computer in network place . Place->network server
from the the first i install ubuntu i can all my network but now all gone
all of computer on my network use ubuntu (11 comp) and 1 win XP
anybody can help me .... :???:

---

### Post by sabitha on 2005-10-10
[QUOTE=sabitha]i dont know what's wrong with this ubuntu hoary 5.04. but now i can't see all my network computer in network place . Place->network server
from the the first i install ubuntu i can see all my network but now all gone
all of computer on my network use ubuntu (11 comp) and 1 win XP
anybody can help me .... :???:
because this for internet cafe
sorry about my english ...

---

### Post by iAlta on 2005-10-10
Hah, now I know!!! You send me a e-mail to magnusvalle[at]hotmail.com, and I'll send you a e-mail with the pic attachd. If that's OK with you.

---

### Post by iAlta on 2005-10-10
OR I made this e-mail address. the address is [email]dlkkfs@hotmail.com[/email] teh password is 654321. just login and read the mail from [deleted by user], this way everybody can look at the pic, and it woun't limit my help source(or whatever)

---

### Post by seethru on 2005-10-10
you've misspelled desktop :)

edit: oh, and incase you ever need to post a screenshot again, try [http://www.imageshack.us](http://www.imageshack.us) for posting images :)

---

### Post by blueturtl on 2005-10-10
> Try this page - it states it has fullscreen support. You say generator works nice and this is based on generator so it should be an all-round win.

I've now installed the version of generator in the link and can confirm you can run the games full screen. Works a heck of a lot better than dgen and is thankfully resizable.

Thank you so much!

Exactly what I've been looking for. I'll give it a try sometime in the near future. :o

---

### Post by iAlta on 2005-10-10
[QUOTE=seethru]you've misspelled desktop :)

edit: oh, and incase you ever need to post a screenshot again, try [http://www.imageshack.us](http://www.imageshack.us) for posting images :)[/QUOTE]
 Ohh... thanks. and zsnes(xsens).

:???: but I din't know what to open it with?? It just never works for me....:(

---

### Post by blueturtl on 2006-01-26
I tested the improved Generator and there seems to be a problem:

The program runs very jerkily and there are graphics errors. I looked at the install instructions and it clearly states I should have compiled it using GCC 2.95 or something newer than 4.x because GCC 3.x will not correctly compile. Hoary ofcourse by default uses GCC 3.xx.

My question is if I do manage to install another version of the GCC, how do I tell the make utility which compiler to use?

---

