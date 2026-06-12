---
title: "PlayOnLinux and dosbox?"
date: 2010-12-23
forum: Gaming &amp; Leisure
---

### Post by Bromden on 2010-12-23
[OLD TOPIC]
I wanted to try the dosbox integration for PlayOnLinux but i can't realize how it works...i have enabled the plugin but i don't know what to do next.
I've tried to install the game (Doom II in this case) but there are no dosbox options O_o
[OLD TOPIC]

**[SKULLTAG GUIDE]**

Skulltag will let you play all those games that make use of .wad files like, Doom and Heretic series, and will offer you a good way to play them Online too.
For more info click **[HERE]("http://www.skulltag.com/")**[U]


INSTALLATION[/U]

Open
"Applications --> Ubuntu Software Center --> Edit --> Software Sources --> Other Software --> Add..."

Ok now paste this line "*deb [http://skulltag.net/download/files/release/deb](http://skulltag.net/download/files/release/deb) stable multiverse"* and click on "Add source"

Wait a bit of seconds to let the Software Center getting updated. It  will give some error, but it's not a problem. Close the Software Center,  open the terminal and write this:

"sudo aptitude install **skulltag"**

I prefer to use "aptitude", but obviously it's possible use "apt-get" too.
You'll have to answer "yes" and not only "y" to let the installation start.

Ok now just install doomseeker-skulltag using the following command: 

"sudo aptitude install **doomseeker-skulltag**"


It puts also a launcher in the "Applications" menù.

To play doom, just put the .wad file in:

"user folder"/.skulltag

(remember that to show these folders it's necessary press "ctrl-h")

---

### Post by Hur Dur on 2010-12-23
DOSBox runs natively on Linux. No need for PlayOnLinux.

Short DOSBox tutorial for installing Doom 2:

mount c /path/to/doom2
c:
setup

Enjoy.

---

### Post by mastablasta on 2010-12-24
also for DOSBox GUI see here: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
 
or you can use zDoom or maybe even jDoom (add openGL effects and 3D models to Doom).

---

### Post by ronnielsen1 on 2010-12-24
Is Doom 2 a dos game? I know versions of doom were but I don't think Doom 2 was

---

### Post by Bromden on 2010-12-26
> **Hur Dur said:**
> DOSBox runs natively on Linux. No need for PlayOnLinux.

Short DOSBox tutorial for installing Doom 2:

mount c /path/to/doom2
c:
setup

Enjoy.
Yeah it works perfectly but i wanted to try PlayOnLinux to have all games on a single GUI. Thank you anyway ;)

> **mastablasta said:**
> also for DOSBox GUI see here: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
 
or you can use zDoom or maybe even jDoom (add openGL effects and 3D models to Doom).
zDoom on linux?! Wow, i'm gonna compile it!

> **ronnielsen1 said:**
> Is Doom 2 a dos game? I know versions of doom were but I don't think Doom 2 was
Yes Doom 2 was also a dos game. All the games for win 95 usually have also a dos alternative.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


OK I've abandoned the idea to use PlayOnLinux because i've found that skulltag runs perfectly also on Ubuntu Maverick 10.10.
You just have to follow this passages:

Open
"Applications --> Ubuntu Software Center --> Edit --> Software Sources --> Other Software --> Add..."

Ok now paste this line "*deb [http://skulltag.net/download/files/release/deb](http://skulltag.net/download/files/release/deb) stable multiverse"* and click on "Add source"

Wait a bit of seconds to let the Software Center getting updated. It will give some error, but it's not a problem. Close the Software Center, open the terminal and write this:

"sudo aptitude install **skulltag"**

I prefer to use "aptitude", but obviously it's possible use "apt-get" too.
You'll have to answer "yes" and not only "y" to let the installation start.

Ok now just install doomseeker-skulltag using the following command: 

"sudo aptitude install **doomseeker-skulltag**"


It puts also a launcher in the "Applications" menù.

To play doom, just put the .wad file in:

"user folder"/.skulltag

(remember that to show these folders it's necessary press "ctrl-h")


[B]Awesome!


[/B]------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by ronnielsen1 on 2010-12-27
Never heard of skulltag. Thanks

---

