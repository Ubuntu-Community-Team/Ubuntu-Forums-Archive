---
title: "Openarena"
date: 2008-05-23
forum: Gaming &amp; Leisure
---

### Post by sweetmoves on 2008-05-23
Hi,

I just installed Openarena and it was a success. But when I start it the screen just goes blank. I can hear sound though. Nothing else happens. I did Ctrl + Alt + Backspace and came back to the login screen. What is the problem? 
I tried to turn off desktop effects to none in Gnome but it was the same. I thought I would start openarena from the console but I have about 1/2 sec to look at the output before the screen goes blank :) How do I start it so I can view the output?

---

### Post by MrWES on 2008-05-23
Same problem here; both with open arean and ET. glxgears work fine, but when I run the games all I get is a black screen with sound....shrug.

---

### Post by sweetmoves on 2008-05-23
When I do Ctrl + Alt + F1 and write openarena in the console I can see some results but I can't scroll to the top, how do I do that? The last error line reads: Sys_Error:GLimp_Init() - could not load OpenGL subsystem. 

Help anyone? Thanks [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by disturbedite on 2008-05-23
seems the problem is with opengl.  do you have any problems with other opengl apps or games?

---

### Post by sweetmoves on 2008-05-23
No, I've never had any problems with any application whatsoever. I installed 8.04 on a clean system when it came out the end of this April. Never had any problems with graphics either. I have a Nvidia card GF6600 or something I think it's called.

---

### Post by Irritant on 2008-05-23
You appear to not have some dependencies, likely a driver issue.

---

### Post by sweetmoves on 2008-05-24
OK, how do I go about solving this problem? I'd really like to try Openarena out. I'd appreciate any help at all.

---

### Post by natirips on 2008-05-24
> **sweetmoves said:**
> When I do Ctrl + Alt + F1 and write openarena in the console I can see some results but I can't scroll to the top, how do I do that? The last error line reads: Sys_Error:GLimp_Init() - could not load OpenGL subsystem. 

Help anyone? Thanks [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

When you do Ctrl+Alf+F1 you get a unix-like console (it's all text, no graphics). If you want to view the output start it from an emulated/virtual console (it's functionality is almost the same). Press Alt+F2 (to start a program) and type "gnome-terminal" (if you're using Gnome) (without the quotes), or "konsole" (if you're using KDE) (also without the quotes). Now you can scroll up.

Edit: Ctrl+Alt+F1..F6 are text-based consoles, they don't have graphics, and thus they can't start OpenGL. Only Crtl+Alt+F7 can.

And also, this is "LINUXNOTES" file from my open arena directory (I downloaded it from [http://openarena.ws/files.html](http://openarena.ws/files.html) (OpenArena v0.7.6 ZIP archive, TuxFamily)):> If it doesn't start up at all, you may need libopenal installed.



If It still doesn't start up at all, you may need libvorbis installed. 



If it STILL doesn't start up at all, you may not have hardware OpenGL accelleration. *This is absolutely required*.  Install appropriate video drivers for your video hardware.  You can still attempt to play the game in software mode by adding +r_allowSoftwareGL 1, but that's stupid and for 1fps-loving insane peoples. Don't try this at all.

I just unzipped and double-clicked the "openarena.x86_64" binary (you might want to use "openarena.i386" binary if you have a 32-bit processor) and the game run.

---

### Post by disturbedite on 2008-05-24
@ natirips
why would you download the zipped version when it is in the repo?

---

### Post by natirips on 2008-05-24
> **disturbedite said:**
> @ natirips
why would you download the zipped version when it is in the repo?

For cross-platform multiplayer compatibility. Repos rarely have the latest versions.

---

### Post by disturbedite on 2008-05-25
> **natirips said:**
> For cross-platform multiplayer compatibility. Repos rarely have the latest versions.
it does in this case...

---

### Post by natirips on 2008-05-25
> **disturbedite said:**
> it does in this case...

I downloaded 0.7.6 in zip recently (from [http://openarena.ws/](http://openarena.ws/) ), but I see 0.7.0 (openarena) and 0.7.1 (openarena-data) in Synaptic (weird - different versions?? (no hard feelings:))).

---

### Post by sweetmoves on 2008-05-25
Thanks for answer natirips

> When you do Ctrl+Alf+F1 you get a unix-like console
I did that because otherwise I don't have chance to see what the output is, before the game starts and the screen goes blank. Is there a command I can use like:

vivaldi@vivaldi:~$ openarena -*nogui*

or something?

About the Linuxnotes you refer to...it seems to run OK, the problem is that I don't see anything. Should I still unzip and doubleclick openarena.i386? (In my case the file is called openarena_0.7.0-2_i386.deb, located at /var/cache/apt/archives) I don't have any file called openarena.i386.

---

### Post by natirips on 2008-05-25
> **sweetmoves said:**
> Thanks for answer natirips


I did that because otherwise I don't have chance to see what the output is, before the game starts and the screen goes blank. Is there a command I can use like:

vivaldi@vivaldi:~$ openarena -*nogui*

or something?

About the Linuxnotes you refer to...it seems to run OK, the problem is that I don't see anything. Should I still unzip and doubleclick openarena.i386? (In my case the file is called openarena_0.7.0-2_i386.deb, located at /var/cache/apt/archives) I don't have any file called openarena.i386.
If you installed from the repositories (either via Add/Remove programs, Synaptic, Adept, apt-get or anything else) your binary (executable) is probably /usr/lib/games/openarena/openarena.bin , but you can run it from the menu (under Games).
The zip I was/am talking about is the one downloaded from [http://openarena.ws/](http://openarena.ws/) . It's an universal downoad for 64-bit Linux, 32-bit Linux and Windows. If chose for this option all you have to do is download it ( [http://download.tuxfamily.org/openarena/rel/076/oa076.zip](http://download.tuxfamily.org/openarena/rel/076/oa076.zip) ), unzip it, and double-click the binary.

Concerning Ctrl+Alt+F1, as I said, it's easier and better to use the console in a window (Programs -> Accessories? -> Terminal). With it you can scroll the text (using your mouse scroll).

---

### Post by sweetmoves on 2008-05-25
> The zip I was/am talking about is the one downloaded from [http://openarena.ws/](http://openarena.ws/) 
OK, now I understand. I'll try downloadin from there. Thanks, appreciate it.

---

### Post by disturbedite on 2008-05-26
> **natirips said:**
> I downloaded 0.7.6 in zip recently (from [http://openarena.ws/](http://openarena.ws/) ), but I see 0.7.0 (openarena) and 0.7.1 (openarena-data) in Synaptic (weird - different versions?? (no hard feelings:))).
perhaps we only have 0.7.6 in intrepid...

---

### Post by natirips on 2008-05-26
> **disturbedite said:**
> perhaps we only have 0.7.6 in intrepid...
I know it's offtopic, but ain't the stable version of intrepid ibex supposed to be out about 4-5 months in future from now? Is there any bigger difference from hardy heron (except the repos)?

---

### Post by disturbedite on 2008-05-27
not much difference yet.  but i'm on kubuntu-kde4.  kde 4.1 has hit the repo today.  i can't wait to try it.

---

### Post by ephemerat on 2008-09-30
Just experienced a similar problem to the OP and thought I'd share my fix...

Again, OpenArena installed okay and all looked good to go, but on boot of the application I was confronted with a blank screen apart from what appeared to be faintly garbled and unreadable menu items. Sound seemed to be working okay. Restarted X to bring my desktop back up. Tried the other solutions in this thread but none worked. 

My graphics card is an NVIDIA Geforce 6200 and has no problems with other OpenGL games. Which gave me an idea: Started the application with the '-opengl' argument and all came up fine so I created a launcher with the following command:

```
/usr/games/openarena --quiet -opengl
```

This completely fixed the issue for me and the game is playing extremely well.

Hope this is of help to other Ubuntu users out there. :popcorn:

---

### Post by natirips on 2008-10-01
> **sweetmoves said:**
> When I do Ctrl + Alt + F1 and write openarena in the console I can see some results but I can't scroll to the top, how do I do that? The last error line reads: Sys_Error:GLimp_Init() - could not load OpenGL subsystem. 

Help anyone? Thanks [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

I know it's a bit late, but in CTRL+ALT+F1-6 (ttys 1-6) you can press SHIFT+PageUp or SHIFT+PageDown for obvious effect. I just figured it out recently.

---

