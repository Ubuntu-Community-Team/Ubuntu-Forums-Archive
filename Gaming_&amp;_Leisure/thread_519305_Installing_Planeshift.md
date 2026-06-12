---
title: "Installing Planeshift"
date: 2007-08-06
forum: Gaming &amp; Leisure
---

### Post by amyfan on 2007-08-06
i have been trying to install planeshift i have read all the forums on it but none help i do not get anything when i try to install it this is what i have downloaded /home/------/Desktop/PlaneShift_CBV0.3.019-x86.bin i can not find a way to install it or mount it as a iso image any help would be greatful thanksi have even read the online site where i got the game at the website but cant find anything to install it

---

### Post by Cappy on 2007-08-06
```

cd ~/Desktop
sudo su

```
```

./PlaneShift_CBV0.3.019-x86.bin

```
take out "sudo su" if you don't want to install it as root.

---

### Post by amyfan on 2007-08-07
ok now can u lay it out in dummie terms on how to fix the card glitch where its showing blured words and no pics i would set a pic but i uninstalled it got tired of messing with it

---

### Post by cogadh on 2007-08-07
What video card do you have? Do you have the acellerated driver for you video card installed?

---

### Post by polski_orzel on 2007-08-13
Hey guys, I'm brand new to linux, and PlaneShift is going to be the first program I install that isn't in Add/Remove or Synaptic.

Anyhoo, I've been reading a lot about this stuff, but it's not really working.

I'm running Ubuntu 7.0.4 Feisty Fawn.

I downloaded the Planeshift...bin to my desktop, and I thought the name was too long to write in terminal, so I renamed it to just straight out 'PlaneShift.bin".

I get this error when I do what Cappy said:
[[IMG]http://img453.imageshack.us/img453/8821/screenshotox8.th.png[/IMG]](http://img453.imageshack.us/my.php?image=screenshotox8.png)

I think what the problem might be, that I download the x64 when I'm pretty sure Ubuntu 7.0.4 FF is x86. [It's probably the other way around, lol]

I'm gonna download the other version, since I don't mind, and it might actually solve the problem. But I do await a reply.


Also, how can I install it so it goes into a folder in my desktop called "My Games"?

---

### Post by Cappy on 2007-08-13
The best thing to it use (TAB). 
From a terminal if you did Desk(TAB)Plane(TAB) it would autocomplete to Desktop/PlaneShift_CBV0.3.019-x86.bin - the autocomplete is definitely a necessity imo.

As for installing to a folder on your desktop .. which I'm not sure why you would ever possibly want to do that, it would be far better to install it in your home folder and that is only if you have a separate partion for /home. Just leave off the "sudo su" and when you install change the directory to /home/yourusername/Desktop/newfolderyouhavemade

To see what architecture your computer is type
```
arch
```
If it is something other than x86_64 then you have a 32-bit OS. If it says "x86_64" you have a 64-bit OS.

Type ```
file ~/Desktop/PlaneShift.bin
```
and it will tell you if it is 32-bit or 64-bit.

a 32-bit OS cannot run a 64-bit program but a 64-bit OS can run a 32-bit program.

If everything checks out you may only need to
```

cd ~/Desktop
chmod +x PlaneShift.bin
./PlaneShift.bin

```

---

### Post by dmacdonald111 on 2007-08-13
> **polski_orzel said:**
> Hey guys, I'm brand new to linux, and PlaneShift is going to be the first program I install that isn't in Add/Remove or Synaptic.

Anyhoo, I've been reading a lot about this stuff, but it's not really working.

I'm running Ubuntu 7.0.4 Feisty Fawn.

I downloaded the Planeshift...bin to my desktop, and I thought the name was too long to write in terminal, so I renamed it to just straight out 'PlaneShift.bin".

I get this error when I do what Cappy said:
[[IMG]http://img453.imageshack.us/img453/8821/screenshotox8.th.png[/IMG]](http://img453.imageshack.us/my.php?image=screenshotox8.png)

I think what the problem might be, that I download the x64 when I'm pretty sure Ubuntu 7.0.4 FF is x86. [It's probably the other way around, lol]

I'm gonna download the other version, since I don't mind, and it might actually solve the problem. But I do await a reply.


Also, how can I install it so it goes into a folder in my desktop called "My Games"?

A filename can be as long as you want it in linux and include as many periods (  . ) as you want. It&#347; down to how the file is set up on linux to what you are able to do with it. Did you follow the instructions fully? Try Cappy&#347; recommendations, but if you get any problems, pm me and I&#314;l try and help you through the installation - I have planeshift here myself and have installed it before so hopefully may be able to help ;)

---

### Post by polski_orzel on 2007-08-13
Hey Cappy, yeh, it turns out I was half right. I'm running a 32-bit and the program is 64 bit.

Is there a way I can upgrade Ubuntu to 64 bit? Is it worth it?

---

### Post by cogadh on 2007-08-13
You can't use the 64 bit operating system unless you have a 64 bit processor in your computer.

EDIT - Sorry, I should have finished that thought with: Do you have a 64-bit processor?

---

### Post by polski_orzel on 2007-08-13
Hmmm not sure

Anyhoo, I got it to install, thanks a lot :D

Is there a place I can find a list of the more common/important Terminal Commands? And what they do?

Like, I always see $ sudo /sudo su and I have no idea what it does :S

---

### Post by Cappy on 2007-08-13
Here you go:
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
(just kidding - don't read this)

I would take a look at
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
It's a good beginner reference that includes examples =)

The only difference from that guide is that Ubuntu does not have "su", instead it is "sudo su". "sudo commandhere" runs one command or program as the root user (can do anything). "sudo su" logs you in as the root user for that terminal (and you get a # promp instead of a $ prompt".

Also, there is a pdf of a lot of the basic commands here:
[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

A more complicated reference would be here:
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
which shows you commands to do more complex tasks.

---

### Post by cogadh on 2007-08-13
If you don't know if you have a 64 bit processor, then you probably don't.

"sudo" is an abbreviation for "**S**uper **U**ser **DO** this". Essentially it is a command argument that gives the command you are actually running temporary administrator access.
 As for a list of terminal commands, I usually use this page:
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

EDIT - Damn Cappy, you type fast!

---

### Post by polski_orzel on 2007-08-13
Thanks a lot guys. Here is my LAAAST question about PlaneShift.

When I play it, all my text is blurred. I updated all my Drivers the other day, and some of the other games I have run prefectly. Any Tips?

---

### Post by Cappy on 2007-08-13
They have forums:
[http://hydlaa.com/smf/index.php?topic=28441.0](http://hydlaa.com/smf/index.php?topic=28441.0)

```

Solution: Font multitexturing has been broken, try the following:
Open up the file Planeshift3D/data/config/r3dopengl.cfg in a text editor, and find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

```

Also turn off beryl/compiz (the cube/pretty window effects) when you run the game.

If you aren't sure where r3dopengl.cfg is you can
```

sudo updatedb
locate r3dopengl.cfg

```
and it should give you a path right to that file.

---

### Post by polski_orzel on 2007-08-14
Sorry for being so naive, but I really am new to Linux. I have installed all my most recent ATI Drivers, however the game is REALLY sluggish. Any ideas?

Edit- I fixed it myself.

---

### Post by dmacdonald111 on 2007-08-14
Congrats on getting it fixed! I liked this game before. Must get into playing it again... lol

---

### Post by Freakshowpb on 2008-11-16
ok I got this installed but after i log in at the bottom it says connecting to server and than it crashes 

also the updater wont boot up

---

### Post by boo2060 on 2009-07-13
I still have the same problem as *Freakshowpb*, running myself 7.10.
Anyone have an idea?

---

