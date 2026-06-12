---
title: "Beryl: White screen of death!!!"
date: 2007-01-20
forum: Desktop Environments
---

### Post by BioGene on 2007-01-20
Hey,

Ok so I installed Beryl with the newest nVidia drivers and everything was working fine. I coudl open up both nVidia settings and beryl manager, but when I go to terminal and run the command "beryl" I see the splashy screen that says Beryl version 0.9.5 and then after that everything goes white. 

When I try to switch between the apps I can see them switch but I only see a white screen and I can not do anything at all. I can just see like black frames of screen when switching bt nothing more. other than its as if somehow my screen goes pure white, including bars at top and bottom. I do not knwo what is happening! Worst part is that I can not take a picture of my terminal if it has any errors cause I can not see it!

SO how can I fix this, please help me out, thanks!

---

### Post by alireza_a on 2007-02-03
I have the exact same problem. any reply is appreciated.

---

### Post by igknighted on 2007-02-03
try holding either ctrl, alt, or shift (I cant remember which at the moment) and scrolling the mouse wheel.  Beryl has a setting to do this which is adjusted via the mouse wheel and one of those keys by default, so it might just be that.

---

### Post by slimdog360 on 2007-02-03
> **BioGene said:**
> ...I see the splashy screen that says Beryl version 0.9.5...

Wow, where do I get that version. Mine only says ver 0.2

---

### Post by obstriegel on 2007-02-24
Hi,

The problem is in xgl. If you do a 

```
sudo apt-get install xserver-xgl=7.0.0.git.20060725-0ubuntu2
```

you get the older version and can use beryl.


Regards,
obstriegel

---

### Post by satchelpig on 2007-02-24
> 
Code:

sudo apt-get install xserver-xgl=7.0.0.git.20060725-0ubuntu2

you get the older version and can use beryl.

that didn't work for me,

---

### Post by obstriegel on 2007-02-24
You can also downgrade beryl, described in [this]("http://ubuntuforums.org/showthread.php?t=362381") thread .

> Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0


---

### Post by satchelpig on 2007-02-24
OK . . . that removes the updated version . . . how do you get the prior version?

---

### Post by obstriegel on 2007-02-25
I found the solutions and summed it up in a wiki:

[infoconnect-wiki]("http://217.20.127.208/infowiki/doku.php?id=en_us:computer:software:linux:beryl:whitecubebug")
There is a tutorial on how to downgrade beryl to the correct version.

Regards,
obstriegel

---

### Post by Patrick-Ruff on 2007-02-25
yeah all you have to do is install a version that was released 2 days ago. 

good luck

---

### Post by PriceChild on 2007-02-25
Please start beryl with "beryl --use-copy" or chose the appropriate item on the beryl-manager menus. If you can't load beryl-manager without it whitescreening then use "beryl-manager --no-force-window-manager"

---

### Post by zarathustra on 2007-02-25
> **PriceChild said:**
> Please start beryl with "beryl --use-copy" or chose the appropriate item on the beryl-manager menus. If you can't load beryl-manager without it whitescreening then use "beryl-manager --no-force-window-manager"

Thanks, this worked for me. I was having similar problems as the original poster, and I'm on Ati's drivers with XGL. I haven't had to downgrade anything for it to work.

---

### Post by dm@n on 2007-02-25
> **zarathustra said:**
> Thanks, this worked for me. I was having similar problems as the original poster, and I'm on Ati's drivers with XGL. I haven't had to downgrade anything for it to work.

Is'nt that very slow?

The white screen of death appeared for me with the latest ubuntu svn repo.. few days back. Dont know how to fix this but a way around this is to start beryl with

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
then start the decorator you want
aquamarine &
heliodor &
emerald & (wich I use)

This seems to be working for me anyways

---

### Post by Gatecrasherc6 on 2007-02-25
> **obstriegel said:**
> Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

So far this has been a life saver for me I didn't want to try *use copy* or *force window* since there's too many posts claiming it has a hit on performance.  So going from  Version 0.1.9999.2 (newest release) to 0.1.99.2 did it for me.

---

### Post by zarathustra on 2007-02-25
> **dm@n said:**
> Is'nt that very slow?

The white screen of death appeared for me with the latest ubuntu svn repo.. few days back. Dont know how to fix this but a way around this is to start beryl with

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
then start the decorator you want
aquamarine &
heliodor &
emerald & (wich I use)

This seems to be working for me anyways

At first I didn't notice the speed difference but it has been crippingly slow so I've reverted back to Metacity.

---

### Post by MikB on 2007-02-28
A useless comment from me...

I've just reverted to logging in with a Gnome session until a Beryl update is released.

Being a total noob, the last few updates that have caused me problems with beryl have led me to reinstall edgy from the live cd and start from scratch. But this time I have my settings just the way I want them.

My finger hovered over the button when I selected the updates this time lol....doh!

---

### Post by vtron on 2007-02-28
Not sure if this will work for everyone, but it worked for me.  I had the same dreaded white screen of death and the following solved it:

Use ctrl+alt+f1 to open a virtual terminal

Backup then edit your .beryl-managerrc file

```
cp ~/.beryl-managerrc ~/.beryl-managerrc.backup
vim ~/.beryl-managerrc
```

Make the beryl-settings section look like this:

```
[beryl-settings]
render_path=2
cow_mode=0
rendering_mode=0
platform=0
binding=0
```

Some of these settings may not work for you, but playing with some of the settings will probably fix the white screen problem.

---

### Post by obstriegel on 2007-03-01
setting the renderpath to "2" is the same as "beryl --use-copy" I think. And it slows down the things I guess.

Regards,
obstriegel

---

