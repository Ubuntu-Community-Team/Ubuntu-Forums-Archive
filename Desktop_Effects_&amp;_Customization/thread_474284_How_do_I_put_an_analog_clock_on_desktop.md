---
title: "How do I put an analog clock on desktop?"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by dude1234 on 2007-06-14
I saw a ubuntu picture with a rather classic looking analog clock on the desktop.

Can anyone tell me how to do this? Many thanks.

---

### Post by borris.morris on 2007-06-14
You would probably need XGL or the like to do this. It would most likely be a clock screen saver running as a background. You're going to need a fairly decent card to do this.

---

### Post by Nythain on 2007-06-14
gDesklets and Superkaramba both have clocks (well i THINK gDesklets does, i havent used it so im not 100% sure, but im about 95% sure)

gDesklets for gnome, Superkaramba for KDE

---

### Post by andrewsomething on 2007-06-14
gDesklets has an analog clock, using it right now. You can get gDesklets right from the Add/Remove Programs menu. Very easy to use... 

-Andrew

---

### Post by andrewsomething on 2007-06-14
Ha! I never would have realized the the wrong album cover is on that if Amarock hadn't popped up right when I took the screen shot...

-Andrew

---

### Post by dude1234 on 2007-06-16
Guys, this appears to be a regular thing with Ubuntu. I had a look at installing the gDesklets program with the GUI, but it wasn't there. So I used the terminal "sudo apt-get gDesklets" and that didn't work either. So I used an internet search and found the gDesklets website. Then I found the download for the clockxxx.tar.gz file. Downloaded that to my HDD. Then I found some notes where it says that typically software can be installed from the source files, so I followed the process like so:- 
sudo aptitude update (that worked)
sudo aptitude install build essential (that worked)
tar xzvf clockxxx.tar.gz (that worked)
cd clockxxxx (that worked)
./configure (that worked)
make (no file specified cannot find file - stop.........????!!!)

Where do I go from here guys?

---

### Post by andrewsomething on 2007-06-17
Strange, gDesklets is under Accessories in Add/Remove for me. Did you try searching for it in Synaptic?

I'm not sure if you can make the clock work without the rest of the gDesklets program. The [_gDesklets_](http://www.gdesklets.org/) website has the program for download, and that should include the clock as well as some other desklets. [_Here_](http://www.gdesklets.org/files/gDesklets-0.35.4.tar.bz2) is a direct link to the program.

---

### Post by happy-and-lost on 2007-06-17
xclock if you're feeling old school

---

### Post by digital_exhaust on 2007-06-17
It's in the Synaptic Package Manager.

At least that's where I found it...

---

### Post by steveneddy on 2007-06-17
Cairo clock - in the repos

The box goes away when starting Beryl or Compiz

```
sudo apt-get install cairo-clock
```

This is my current desktop.

---

### Post by steveneddy on 2007-06-17
@ andrewsomething - dude, you're gonna make me have to change my avatar now.

---

### Post by ChopperX on 2007-06-17
Well i downloaded gDesklets and extracted it to my home folder. Whats next?

---

### Post by steveneddy on 2007-06-17
gdesklets is in the repositories

```
sudo apt-get install gdesklets
```

---

### Post by ChopperX on 2007-06-17
wheres the repositories so i can extract it there?

---

### Post by Sweet Mercury on 2007-06-17
> **ChopperX said:**
> oki did that so how to i make one work?

If you installed from the repositories (the easiest way), then the shell is under **Applications-->Accessories-->gDesklets**.

The shell has to be running for the Desklets to be running as well. To have GNOME start it automatically, go to **System-->Preferences-->Sessions** Click **New**. In the *Name* Field, type a name for the startup command (I called it GDesklets), in the *Command* Field, type "gdesklets" (all lower case).

The analog clocks are in the **Time/analog** folder. Pick one you like!

---

### Post by steveneddy on 2007-06-17
> **ChopperX said:**
> wheres the repositories so i can extract it there?

OK dude, let me explain a little.

Open a terminal and type or copy this there:

```
sudo apt-get install gdesklets
```

then hit Enter.

That's it. 

Applications --> Accessories --> Terminal

And Synaptic is a GUI way of installing programs. It is at:

System --> Administration --> Synaptic Package Manager

If you click in the big window where the programs are, start typing for the name of the programs you are looking for, and it will search for you. Right click the application you want to install and then, on the top toolbar you will see a check mark with Apply. Click apply and it will install. 

The programs that are already installed have the box already filled in.

Hope this helps.

---

### Post by steveneddy on 2007-06-17
Look [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apt.2C_Software_and_Package_Basics")

and here.

I assume you are using [Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

Please read this material because it will help you understand how to install and uninstall programs. Try to get programs and application from Synaptic or do the apt-get method.

---

### Post by raul_ on 2007-06-17
it's case sensitive...it's not gDesklets, but gdesklets

---

### Post by dude1234 on 2007-06-25
Problem solved for me when "raul" noted that it's gdesklets NOT gDesklets.

I still have no idea why it didn't show up in my repository. But it installed when I used

sudo apt-get install gdesklets

---

