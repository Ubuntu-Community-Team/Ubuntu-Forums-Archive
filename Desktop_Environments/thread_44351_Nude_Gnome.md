---
title: "Nude Gnome"
date: 2005-06-25
forum: Desktop Environments
---

### Post by served on 2005-06-25
[B]How can i make ubuntu to take less memory?
I have 128 mb ram but if i use xmms and firefox together then xmms just closes.
I'd like to get some ideas how can i do it and what i should do!

I think in linux tehere should be services and stuff, Im ready to disable some helping things and sounds and some bling bling stuff, i just want better berformance!
[/B]

---

### Post by jdong on 2005-06-25
First of all, do you have any swap?

Turn off all backgrounds, switch to a plainer theme.

---

### Post by served on 2005-06-25
i guess i have swap pcs. when i installed ubuntu then i diddnt remove swap space.
whats the plainer theme? I have a solid colour background #E6E6FA

---

### Post by Xian on 2005-06-25
[QUOTE=served]i guess i have swap pcs. when i installed ubuntu then i diddnt remove swap space.[/QUOTE]
Do a quick check of how Gnome is utilizing your system memory and swap.
From the main panel:

Applications > System Tools > System Monitor

When the System Monitor opens click on the 'Resources' tab.
Look and see what it lists for 'User Memory' and 'User Swap'.

---

### Post by drummer on 2005-06-25
You could also give xfce a try for a lighter Desktop Manager... (unless you particularly want Gnome)

$  sudo apt-get install xfce4 xfce4-goodies

There are also other applets / plugins in synaptic, search for xfce4

---

### Post by served on 2005-06-26
id like to try that xfce and i downloaded file "xfce4-4.2.2-installer.bin"
Now how can i install it?

I dont get it what is wrong with my PC ](*,) !!! When xmms is running and i listen music 
then if i open somekind a program then xmms just closes it just pisses me off. Like it crasses or smthing. system monitor didnt show me none critical exept CPU is critically high. I have Amd-k6 450Mhz and its working at 450mhz all the time( i can cange speed on the motherboard manually) So is there a problem or its normal?

---

### Post by drummer on 2005-06-26
I think the .bin file should execute when double-clicked and run the graphical installer (if that's what you've downloaded) but I haven't used that method of installing xfce before. If it doesn't execute.. perhaps ' ./xfce4-4.2.2-installer.bin ' in a terminal. Xfce 4 is also in Universe (not the absolute latest, but fairly new).

As for xmms crashing, try running xmms from terminal to see if there is any useful output when it crashes. I don't use xmms and don't know much about it, but the errors might point to something else useful.

---

### Post by Xian on 2005-06-26
If you desire to try xfce that's fine but I wouldn't put it on in response to this issue as you appear to simply have a runaway program in XMMS. Opening that program from the terminal was a good idea as you might catch some error messages when it fails. You might go with using another media player until you isolate this problem. Beep media player is available in Synaptic and will perform nicely.

---

### Post by served on 2005-06-26
Looks like u were right i recived an error: 
libmikmod.so.2: cannot open shared object file: No such file or directory
( but xmms crashes later, if i surf on the internet but if i wont do none then none happens)

Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.

Xlib: unexpected async reply (sequence 0x3d91)!

Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.


So what next?

BTW: i dont have that media player in my synaptic list

---

### Post by drummer on 2005-06-26
[QUOTE=served]BTW: i dont have that media player in my synaptic list[/QUOTE]
The package name is beep-media-player and it's in the Universe repo. If you haven't enabled extra repositories: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Not sure what libmikmod.so.2 is exactly but it looks like that's the culprit. All I could suggest is reinstalling xmms or the package that libmikmod.so.2 belongs to. A google search gave me some results of similar errors with xmms and libmikmod.so.2

Beep media player is a viable alternative and I've heard that it's very similar to xmms, but built on gtk2 rather that gtk1 (as xmms is).

---

