---
title: "Dungeon Master Tools for Linux"
date: 2005-12-09
forum: Gaming &amp; Leisure
---

### Post by Grue on 2005-12-09
I just started DM'ing (for the first time) a tabletop D&D game and I thought to my self 'I can't be the only roleplaying geek using linux'. So I was wondering, what kind of FLOSS you use to keep track of it all when you're DM'ing :).

Right now I'm using Kate for the storyline, Inkscape to do various graphical things and my notepad...

What I'm looking for is an easier way to make maps and keep track of all the stats.

---

### Post by nrwilk on 2005-12-09
I'm interested in this too.  Hopefully there's some nifty tabletop-RPG utilities out there for linux.

---

### Post by fellwind on 2005-12-13
PCGen, the best character creation utility out there, runs on both Windows and Linux.  It has GM Utilities included in it, combat tracking and the like.

[http://pcgen.sourceforge.net/02_overview.php](http://pcgen.sourceforge.net/02_overview.php)  if you want to read about the features.

---

### Post by Grue on 2005-12-14
Thank you very much. It sounds like it's exactly what I'll need. It's pretty weird that it hasn't come up in any of my searches... It seems to be a pretty old (in a good way), but popular tool.

---

### Post by nrwilk on 2005-12-17
[QUOTE=fellwind]PCGen, the best character creation utility out there, runs on both Windows and Linux.  It has GM Utilities included in it, combat tracking and the like.

[http://pcgen.sourceforge.net/02_overview.php](http://pcgen.sourceforge.net/02_overview.php)  if you want to read about the features.[/QUOTE]

Nice.

---

### Post by sfabel on 2005-12-19
Hi,

this happens when I try to run it:

```

stephan@gemini:~/pcgen580$ ./pcgen.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at pcgen.util.Logging.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at pcgen.core.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./pcgen.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...5 more

```

Anybody any idea?

Cheers,
Stephan

---

### Post by xvolks on 2005-12-19
Hi,

It seems you are trying to launch a java program, you should try with sun's JRE.
You can get it at [http://java.sun.com](http://java.sun.com)
unpack it with : sh jreXXXX.bin
update-alternatives --config java

and retry.

--Xvolks

---

### Post by spaceghoti on 2006-05-17
Anyone know what's up with the datasets for PCGen?  Older versions used to come with rules for D&D 3.0 (including Epic campaigns), but 5.10 doesn't even have that.

---

### Post by asimon on 2006-05-17
[QUOTE=spaceghoti]Anyone know what's up with the datasets for PCGen?  Older versions used to come with rules for D&D 3.0 (including Epic campaigns), but 5.10 doesn't even have that.[/QUOTE]
A lot of stuff in the D&D books is non-free content and they have no license to include and distribute it. They can only include OGL licensed (for example the SRD) or otherwise freely distributable stuff. So most stuff from the D&D splash and world books is missing, as is some stuff from the D&D core books.

AFAIK Code Monkey Publishing sells some non-OGL data files for PCGen.

Otherwise for plans, campaign ideas, stories, and my DM notes I use good old vim. And I keep them under version control via bzr, which is convenient because they are usually of a very dynamic nature.

I was never satisfied with any DM tool or character generator. Either they were full of bugs (I mean rule 'bugs'), lacking easy extensibility, or their usability was just too awful.

---

### Post by leech on 2006-05-17
Check out openrpg.  [http://ubuntuforums.org/showthread.php?t=114823&highlight=openrpg](http://ubuntuforums.org/showthread.php?t=114823&highlight=openrpg)

Leech

---

### Post by KingBahamut on 2006-05-18
[http://gxconf.sourceforge.net/ddgen/index.php?page=1](http://gxconf.sourceforge.net/ddgen/index.php?page=1) 

[http://dnd3rd.sourceforge.net/](http://dnd3rd.sourceforge.net/) - Netbased

[http://www.turnwatcher.com/](http://www.turnwatcher.com/) - This one is a jewel, couldnt live without something like this.

---

### Post by James_Nostack on 2006-05-28
come to think of it -- a lot of the stuff in D&D 3.5 is heavily dependent on look-up tables: randomly generated treasure, traps, even dungeons themselves.  Considering that D&D is (IMO) absurdly high-prep, anything that cuts down on that overhead is a good thing.

This appears to be a pretty decent treasure generator based on Java: [Dungeons & Dragons treasure generator](http://www.cs.queensu.ca/home/dalamb/java/treasure/)

And I'm a big fan of [The Hypertext d20 SRD](http://www.d20srd.org/), which includes an Encounter Calculator, and filters for monsters ("Hey, I wonder what they could fight that lives in a temperate desert?") or spells ("Gee, what's a good 3rd level  Necromancy spell that doesn't require a 'somatic component'?")

What I have NOT found yet is a random trap generator, or a random generator for the various rooms & incidental features of the dungeon.  Has anyone seen anything like that?

---

### Post by leech on 2006-05-29
Just personal opinion, but D20 sucks.  It's the one thing that I wish Neverwinter Nights would change.  If there were an engine similar to Neverwinter Nights, but with Gurps or another universal role-playing system in it, I would be a happy camper.  

Leech

---

### Post by James_Nostack on 2006-05-30
"Just personal opinion, but D20 sucks."

I don't disagree, but saying so is probably asking for trouble!  Still, I wanna point to an excellent fantasy RPG using a Creative Commons License: [The Shadow of Yesterday](http://www.anvilwerks.com/?The-Shadow-of-Yesterday).  It's available for purchase, but it's also a free download--[Rule Book](http://zork.net/~nick/loyhargil/tsoy2/book1--rulebook.html) and [Setting Material](http://zork.net/~nick/loyhargil/tsoy/book2--world_of_near.html).  I've played it several times, and it's a lot of fun--worth checking out if you like fantasy games but not the whole D&D thing.

---

### Post by solstice on 2006-06-04
not sure if anyone is interested, but here is a tool I have worked on. It isn't quite finished yet, but pretty neat anyway.

it is geared toward players to keep track of inventory and money for Dungeons and Dragons v3.5. I haven't shared it w/ anyone yet so be nice :P
[http://dnd.solsticeonline.net](http://dnd.solsticeonline.net)

---

### Post by zodwallop on 2006-06-06
Looks pretty cool from the screenshots!

---

### Post by sharperguy on 2006-06-06
Someone in a D&D article I read was usinga graphics program with the map loaded on his laptop, he then suspended and projector from the roof and used a mask on the map to cover the unexlpored area and erased it as the game progressed.

---

### Post by ticopelp on 2007-05-07
Just a public service announcement that pcgen and Beryl do not play well together. I could not get it to run at all under Java 6 JRE, and couldn't get it running under JRE 5 either, until I turned Beryl off. Then it started working pretty much perfectly.

Just in case someone ends up with the same problem later on. :)

---

### Post by Perfect Storm on 2007-05-07
Generally java based applications plays very poorly with beryl (both games and software in generally).

---

### Post by dooglio on 2007-07-30
> **KingBahamut said:**
> 
[http://www.turnwatcher.com/](http://www.turnwatcher.com/) - This one is a jewel, couldnt live without something like this.

Thanks for the kudos!  I'm glad you enjoy the application!

I'd just like to let you know that we've released an update for Turn Watcher (version 1.2) which adds support for spell and ability effects tracking. Enjoy!

---

### Post by tijmz on 2010-01-05
Does anyone know of some good mapmaking tools, both for plotting dungeons and landmasses?

---

