---
title: "Installing flash4linux"
date: 2005-11-17
forum: Desktop Environments
---

### Post by beercz on 2005-11-17
Hi Guys

Has anyone successfully installed flash4linux (using the downloaded package f4l_0.2-1_i386.deb) in breezy?

When I attempt this (sudo dpkg -i f4l_0.2-1_i386.deb) I get dependency errors:

libqt3c102-mt (>=3:3.3.4) and libxrender1 (>=1:0.9.0-2).  I'm struggling to find and install these dependencies.

Can anyone point me in the right direction?

Thanks in advance.

Ian

---

### Post by bin on 2005-11-17
Hi 

You may have a problem here as the libqt3c102-mt has been replaced in 5.10 - been down the same path with a different app that I'd alien'd from a SUSE rpm. There are some threads in the forum.

So, if you can find an rpm of the app, apt-get install alien, then alien -d blah.rpm you may get a working flash4linux

in light

bin

---

### Post by beercz on 2005-11-21
Thanks bin

I'll give it a go

Ian

---

### Post by tomwell on 2005-11-29
Hey guys, I have managed to install f4l but there is no launcher and i am trying to launch the darn program... lol

Any help greatly appreciated!!!!

Peace 

Tom

---

### Post by JKoder on 2005-12-01
[QUOTE=beercz]Hi Guys

Has anyone successfully installed flash4linux (using the downloaded package f4l_0.2-1_i386.deb) in breezy?

When I attempt this (sudo dpkg -i f4l_0.2-1_i386.deb) I get dependency errors:

libqt3c102-mt (>=3:3.3.4) and libxrender1 (>=1:0.9.0-2).  I'm struggling to find and install these dependencies.

Can anyone point me in the right direction?

Thanks in advance.

Ian[/QUOTE]
Hello
Try to find those packagesat [www.debain.org](www.debain.org)
There is quite a good place for missing packages in Ubuntu
Give it a try ;)

---

### Post by akiro.yamamoto on 2005-12-01
Hey tomwell:
If you want an icon....?
Right click on the gnome desktop and choose create launcher, fill in the info, command, choose an icon and done :smile:
For Command you can check where the program was installed and check there for the initiation script of bin file that will run the program.
If it was not installed in your PATH that is....
You can check that by :
[ALT]+[F2] this is the run dialog....
and type in the program.... if it runs...well then it's in your PATH and you can specify it as typed at the run command in the command field for your desktop launcher....

---

### Post by rejser on 2005-12-01
If you downloat the .ta.gz file from f4l homepage, you can run it out of the folder, the install cares for the libqt3c102-mt, but the program don't.
Not a good solution, but it will run

---

### Post by tomwell on 2005-12-01
[QUOTE=akiro.yamamoto]
[ALT]+[F2] this is the run dialog....
and type in the program.... [/QUOTE]

Akiro,

Thanks for the Alt F2 thing that is going to be a great help in the future...
I have figure what i did wrong and it had nothing to do with me not finding the launcher... it was the wrong file... I used version 02.2 when i used version 02.1 of Flash 4 linux it suddenly worked....

so if F4l 02.2 doesnt work maybe try 02.1...

Peace

Tom

---

### Post by filipenetto on 2005-12-06
[QUOTE=tomwell]Hey guys, I have managed to install f4l but there is no launcher and i am trying to launch the darn program... lol

Any help greatly appreciated!!!!

Peace 

Tom[/QUOTE]

Hi guys .... I'm having a seemed problem of tomwell. I've instaled the f4l, an it's working well (by the 'f4l' command). But, his not create any launcher, and I wan't to create a launcher with the icon, but I can't find the folder to point the icon.

Somebody know were is that folder ?

Tks ... :p

---

### Post by tomwell on 2005-12-06
[QUOTE=filipenetto]
Somebody know were is that folder ?[/QUOTE]

Ok you need to go into applications>system tools> applications menu editor,

Then you create a new menu in programing since that is where i want my launcher to be...and click on new menu...

Ps: now that you have installed the program can you read this thread and contribute... its another one regarding f4l...

Thanks man!!!

[http://www.ubuntuforums.org/showthread.php?t=99738](http://www.ubuntuforums.org/showthread.php?t=99738)

Peace

Tom

---

### Post by filipenetto on 2005-12-06
[QUOTE=tomwell]Ok you need to go into applications>system tools> applications menu editor,

Then you create a new menu in programing since that is where i want my launcher to be...and click on new menu...

Ps: now that you have installed the program can you read this thread and contribute... its another one regarding f4l...

Thanks man!!!

[http://www.ubuntuforums.org/showthread.php?t=99738](http://www.ubuntuforums.org/showthread.php?t=99738)

Peace

Tom[/QUOTE]

Hi Tom, 

Right, I create a launcher for him, but, I don't know were is the icon for that ... do you know were is ???

Thanks ! ;)

---

### Post by tomwell on 2005-12-07
Ok if you have created the launcher and it works fine.... you will now need to create an icon for f4l... i for instance have created in gimp a flash "looking" icon.... lmao hope no one thinks am cheating copyrights thingys... lmao

see my screenshot....

Good luck ...

(what you could do to make a icon like this would be to use a picture of something you find on the internet... and cut out the outline by selecting choose by colour... then invert it so you only get the "f"... and also perhaps you could paste it on to a transaprent background...??? Imagination is a great tool!!!)

Peace

Tom

---

### Post by filipenetto on 2005-12-07
Hi Tom, 

Well, but I think that the F4l include a flash icon on your instalation, or it would have include, like many other applications, right ? :(

---

### Post by tomwell on 2005-12-08
Not sure... I dont think so because it doesnt automaticly create an entry in your menu or a launcher... and including a flash icon would infringe copyright laws but anyhow its dead easy to make one at home... lol 

Peace

Tom

---

### Post by filipenetto on 2005-12-11
Ok Tom, so, I will create the icon. Thank you very much.

Bye ... :)

---

