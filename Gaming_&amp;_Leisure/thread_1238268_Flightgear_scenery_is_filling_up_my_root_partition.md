---
title: "Flightgear scenery is filling up my root partition"
date: 2009-08-12
forum: Gaming &amp; Leisure
---

### Post by Sealbhach on 2009-08-12
OK, simple enough problem I think, I want to store the Scenery files in my /home folder somewhere so that I can download as much as I want.

I tried creating a symbolic link, but that didn't appear to work. Is there a config file somewhere that will allow me to specify the path to the scenery files?

Also is there a gui add-on that will allow me to select the aircraft without having to do so on the command line?

One other thing, that annoys me in Flightgear, why doesn't it just list the available airports, rather than listing them all even though I don't have the scenery and objects  for them?

.

---

### Post by Perfect Storm on 2009-08-12
Try see if it have a local directory in your home directory eg. ~/.flightgear

or install flightgear locally instead.

---

### Post by Sealbhach on 2009-08-12
> **Artificial Intelligence said:**
> Try see if it have a local directory in your home directory eg. ~/.flightgear

or install flightgear locally instead.

Thanks. I checked, it doesn't have a ~./flightgear folder. I'm not sure how I would install it locally, I just installed it from Add/Remove. If there's no answers here I'll try on the Flightgear forums, I'm sure this must have come up before.

.

---

### Post by Perfect Storm on 2009-08-13
Found this; [http://www.flightgear.org/Docs/getstart/getstartch2.html#x6-100002](http://www.flightgear.org/Docs/getstart/getstartch2.html#x6-100002)

> 2.1.2 FG_SCENERY

If you would prefer to keep your downloaded scenery separate from the core installation, you can do so by setting your FG_SCENERY environmental variable. 

This is where FlightGear looks for Scenery files. It consists of a list of directories that will be searched in order. The directories are separated by &#8220;:&#8221; on Unix and &#8220;;&#8221; on Windows. 

For example, a FG_SCENERY environmental variable set to 

/home/joebloggs/WorldScenery:/usr/local/share/Flightgear/data/Scenery 

searches for Scenery in /home/joebloggs/WorldScenery first, followed by /usr/local/share/Flightgear/data/Scenery.

---

### Post by Sealbhach on 2009-08-13
Thanks buddy, that's the answer alright.

I did a bit of reading and found out that to make the enviromental variable permanent I needed to add this line to ~/.bashrc

```
export FG_SCENERY=/home/username/Path/to/Scenery:/usr/share/games/FlightGear/Scenery
```

This will only work if I launch the game from the terminal, if I launch it from the Gnome menu I wind up in the middle of the sea.

One other thing, the scenery I download comes in a folder called "Scenery" and contains three folders - Objects, Terrain, Airports.

In version 1.9.1 of Flightgear, the Airports folder is not stored in Scenery, so I needed to add the Airports into /usr/share/games/Flightgear in the usual way. They're not very bulky compared to the Terrain files.

Thanks again for your help.:)

.

---

### Post by Perfect Storm on 2009-08-14
Have you tried;

```
sh -c "export FG_SCENERY=/home/username/Path/to/Scenery:/usr/share/games/FlightGear/Scenery && ./<flightgear binary>"
```

as a launcher.

---

### Post by Sealbhach on 2009-08-14
> **Artificial Intelligence said:**
> Have you tried;

```
sh -c "export FG_SCENERY=/home/username/Path/to/Scenery:/usr/share/games/FlightGear/Scenery && ./<flightgear binary>"
```as a launcher.

Well, if I want to fly something other than a Cessna I have to use the command line anyway, so I may as well get used to it.

.

---

### Post by Perfect Storm on 2009-08-14
> **Sealbhach said:**
> Well, if I want to fly something other than a Cessna I have to use the command line anyway, so I may as well get used to it.

.

Maybe you should build a script up. A script which allow you to choose which airplane to use and bound the script to a launcher.

Eg.

Choose Airplane:
1. airplane 1
2. airplane 2
3. airplane 3
etc.

---

### Post by Sealbhach on 2009-08-14
> **Artificial Intelligence said:**
> Maybe you should build a script up. A script which allow you to choose which airplane to use and bound the script to a launcher.

OK, that's a good idea, I might have a crack at that, it means I have to learn a bit about bash scripting so it might take me a bit of time.:P

.

---

