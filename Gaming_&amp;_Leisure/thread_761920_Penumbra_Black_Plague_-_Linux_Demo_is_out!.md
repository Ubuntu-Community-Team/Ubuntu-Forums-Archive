---
title: "Penumbra Black Plague - Linux Demo is out!"
date: 2008-04-21
forum: Gaming &amp; Leisure
---

### Post by dudeofthedead on 2008-04-21
Get it [here](http://www.penumbrablackplague.com/site/demo.php) while it's still hot.  More info can be found at this [address](http://www.linuxgames.com/archives/10250).  Now, if you'll excuse me, I'm going to play me hands numb.

---

### Post by aidanr on 2008-04-21
Awesome!

---

### Post by Dark Aspect on 2008-04-21
> **dudeofthedead said:**
> Get it [here](http://www.penumbrablackplague.com/site/demo.php) while it's still hot.  More info can be found at this [address](http://www.linuxgames.com/archives/10250).  Now, if you'll excuse me, I'm going to play me hands numb.

What is this? Episode 2 of penumbra Overture or a completely new game?

Either way those screen shots looked great,I must play.

---

### Post by Wobedraggled on 2008-04-21
Grabbing it now

---

### Post by curvedinfinity on 2008-04-21
Looks great!

---

### Post by Wobedraggled on 2008-04-21
Grrrr, Demo is just segfaulting on the installer.

---

### Post by happyhamster on 2008-04-21
It's segfaulting on Hardy Heron too here. It's  in the last part of startupinstaller.sh:

```

`pwd`/$FRBIN

```

When I comment that line, I get:

Error: Couldn't find any suitable frontend for your system. 

So perhaps something didn't configure right or it's expecting different package versions, etc.

---

### Post by aidanr on 2008-04-21
[quote=penumbra forums]Oh, and for what it's worth, the Linux demo *installer* crashes after it extracts the files and attempts to run the installation gui. Run "unset DISPLAY" to use the character-based installer and it works fine.

Kubuntu 7.10, i386,

-edfardos[/quote] .

---

### Post by noerrorsfound on 2008-04-21
Thanks for the thread. I've been waiting for this.:)

---

### Post by meborc on 2008-04-22
just played it on my hardy... it gave me the creeps... in the morning :) 

i don't know if i am able to play it like they recommend: lights off, contrast up, brightness down

for all of you having problems running the installer, this is what i did step-by-step:

1. download the installer from given link... i used the torrent site
2. save it to /home/YOURUSERNAME
3. ctrl+alt+F2 to get to the console
4. **sudo /etc/init.d/gdm stop** to stop x
5. **sh ./PenumbraBlackPlagueDemo-2567.sh** answer all the questions moving around with tab and hitting enter where needed... be sure to choose /home/YOURUSERNAME as the default installation location
6. after this all is done **sudo /etc/init.d/gdm start**
7. you will find the game demo under the games menu in gnome

---

### Post by dudeofthedead on 2008-04-22
> **Dark Aspect said:**
> What is this? Episode 2 of penumbra Overture or a completely new game?

Either way those screen shots looked great,I must play.

It is the second and last installment in the Penumbra series.  It was originally thought of as a trilogy but developers said they would rather not extend the story for the sake of it.  I can understand that.

Those Greys sure are interesting, even though I doubt they are an alien species. :)  Has anyone else noticed that formless, tube-like phallus between their crotch?  Odd.

By the way, is it possible to take screenshots while in-game?  I tried every possible key but it's not working.

---

### Post by dudeofthedead on 2008-04-22
It's definitely possible!  Just hit F8 for a quick screenshot (BMP).

Now about sharing some of our findings?  Here's [one](http://www.sendspace.com/file/bqf4rm).  Cool stuff huh? :)

---

### Post by meborc on 2008-04-22
> **dudeofthedead said:**
> ...
Now about sharing some of our findings?  Here's [one](http://www.sendspace.com/file/bqf4rm).  Cool stuff huh? :)

what? where?

---

### Post by dudeofthedead on 2008-04-22
I'll give you 'one' clue. :lolflag:

---

### Post by meborc on 2008-04-22
> **dudeofthedead said:**
> I'll give you 'one' clue. :lolflag:

damn, this new format of the forums makes spotting the links really bad... :(

---

### Post by Dark Aspect on 2008-04-22
> **dudeofthedead said:**
> It is the second and last installment in the Penumbra series.  It was originally thought of as a trilogy but developers said they would rather not extend the story for the sake of it.  I can understand that.

Awesome,Penumbra Overture was an awesome Linux game.Hopefully Black Plague will be equally as cool.

---

### Post by Sockerdrickan on 2008-04-23
yay :D

---

### Post by Everybody Loves Hypnotoad on 2009-07-19
Graphical installer PenumbraBlackPlagueDemo-2567.sh works in gnome-terminal on 9.04 by doing

cd whatever-directory-you-have-the-demo-in
chmod 700 PenumbraBlackPlagueDemo-2567.sh
./PenumbraBlackPlagueDemo-2567.sh

At the end of the installation it seems to stop without finishing, I just hit enter in the main windows log and then it went on to say install completed.

This weekend you can get the Penumbra collection with the three games Penumbra: Overture, Penumbra: Black Plague and Penumbra: Requiem for only USD 5 from [http://frictionalgames.com/site/](http://frictionalgames.com/site/) be sure to select the linux version when buying.

---

