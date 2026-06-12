---
title: "SlashEm configuration?"
date: 2006-03-14
forum: Gaming &amp; Leisure
---

### Post by DirtDawg on 2006-03-14
So I decided to try Slashem after about 6 billion games of Nethack. I installed both GTK and x11 styles (not really understanding what these were) but I can't seem to find a way to set any permanent options. With Nethack, I could alter the "/etc/nethackrc.console" file. I've managed to find an "/etc/slashemrc.x11" file, but altering these options doesn't seem to have any effect. Setting options at the start of each game is horrendously annoying.
My preferred setup would be console play (the x11 windows seem nice, but I can't see the, er, graphics very well on the default tan background when color is on) with preset options like num_pad movement and auto gold pickup turned on at startup. I've looked elsewhere on the Net, but no luck. Any suggestions? 
:mrgreen:  Thank you. :mrgreen:

---

### Post by DirtDawg on 2006-03-14
*BUMP!*
This question's a little arcane, so I may bump once more.

---

### Post by DirtDawg on 2006-03-14
*BUMP*
Last one I promise. I may have to either deal with setting options or not play at all :(  A fate worse than picking up a cockitrace corpse with your bare hands! 
Unless someone can help...

---

### Post by DirtDawg on 2006-03-17
For the benefit of anyone else who may be wonderting about this issue, I have figured things out (and yes, I am _quite_ proud of myself, thankyouverymuch).
What goes on, or at least what I did, was enter:
SLASHEMOPTIONS="*Enter lots of options-codestuff here*"
Then type:
export SLASHEMOPTIONS
This took me some time to figure out. I'm including the file I created for this purpose. Notice it is _not_ a script. Instead the long, gnarly looking string is to copy/paste in the console after 'SLASHEMOPTIONS='. 
I set the options the way I like them, even got the menu colors working, but you may want to check out the slashem guidebook and change a few (example: my cat's named "ButtBreath" and my ghoul's named "Richard Perl").
Anyway, I hope someone out there finds this as useful as I would have.
Here's the code & happy hacking (slashing?):
```

###################
The below lines shold be copied, then pasted into the terminal like so('$' signifies prompt):
$ SLASHEMOPTIONS="Paste code in this spot"
$ export SLASHEMOPTIONS
##################

 "autodig,autopickup,color,catname:ButtBreath,dogname:Nutz,fruit:steaming turd,ghoulname:Richard Perl,horsename:spanky,lit_corridor,lootabc,number_pad:1,pickup_types:$,pushweapon,wolfname:mittens,hilite_pet,nomail,menucolors,nolegacy,toptenwin,menucolor:\" uncursed \"=yellow,menucolor:\" blessed \"=green,menucolor:\" holy \"=green,menucolor:\" cursed \"=red,menucolor:\" unholy \"=red,menucolor:\" cursed .* (being worn)\"=orange&underline"

```

---

### Post by Zyphrexi on 2007-02-21
slashem in the reps was ascii, I wonder if falcon's eye could work with nethack.

also crossfire is very good.

---

### Post by DirtDawg on 2007-02-21
> **Zyphrexi said:**
> slashem in the reps was ascii, I wonder if falcon's eye could work with nethack.

also crossfire is very good.

Even better is [Vultures eye/claw]("http://www.darkarts.co.za/projects/vultures/"). A Nethack/slash-em continuation of the now dead Falcon's eye. 

It's totally awsome.

---

### Post by Kilarin on 2008-03-06
Hello!
I'm running Ubunto 7.10 and Slashem GTK fresh from the Ubuntu repositories.
I'm trying to set the SLASHEMOPTIONS as specified in this example.  But they seem to have no affect.  I open a terminal, enter:
```
SLASHEMOPTIONS="number_pad:1"
export SLASHEMOPTIONS
```
And then run SlashEM GTK, and the number pad is not turned on.  when I check the options, number_pad=0.   
I can change the number_pad to 1 from the options menu, and that lasts for one game, but it only last for that session.  If I shut down SlashEm and restart it, number_pad is back to 0 again.

I've looked and looked for a config file for SlashEm, thinking I could just edit that, but I can't FIND one anywhere. <sigh>

Any help would be much appreciated.

---

### Post by DirtDawg on 2008-03-07
I installed the GTK version of slashem after reading your post. I also had problems with the number pad but, interestingly, turning off my num lock actually allowed me use it for directions. I don't get it, but maybe it will work for you.

If it doesn't, you might want to try making a configuration file, which I didn't know about when I originally started this thread and will hold your options between games. All you need to do is crate a file in your home directory called ".slashemrc" and write your options to it. I'm not exactly sure of the correct syntax, but number pad activation would be something like:
```
OPTIONS=number_pad:1
```
Or maybe you don't need the ":1" part. I don't know. There is what seems to be a very good guide in pdf form here: s2.enemy.org/nethack/Slash-Em-Guidebook.pdf
The guide goes over configuration. There's another example of a configuration file on this site, about three-quarters of the way down: [http://www.basicallytech.com/blog/index.php?/archives/16-SlashEM-on-Linux-configure,-install,-setup-and-play.html#slashem_config](http://www.basicallytech.com/blog/index.php?/archives/16-SlashEM-on-Linux-configure,-install,-setup-and-play.html#slashem_config)

Good luck and have fun.

---

### Post by DirtDawg on 2008-03-07
By the way, if you like a graphical interface, I would encourage you to check out [Vulture's Claw]("http://www.darkarts.co.za/project/vultures"). There's a great guide to easy installation [here]("http://www.ubuntugeek.com/how-to-install-vultures-isometric-graphics-in-ubuntu.html").

---

### Post by Kilarin on 2008-03-14
> I would encourage you to check out Vulture's Claw.
Vulture's claw is REALLY cool.  But I actually prefer the "Big Tiles" 2D interface to the isomorphic view.  Isomorphic looks really nice, but it makes it a bit more difficult for me to judge which square is which.

The GTK Slashem interface is very nice.  I am just baffled as to why I can't find a configuration file.  It should BE there somewhere.

---

### Post by DirtDawg on 2008-03-14
> **Kilarin said:**
> Vulture's claw is REALLY cool.  But I actually prefer the "Big Tiles" 2D interface to the isomorphic view.  Isomorphic looks really nice, but it makes it a bit more difficult for me to judge which square is which.

The GTK Slashem interface is very nice.  I am just baffled as to why I can't find a configuration file.  It should BE there somewhere.

You need to create one! There is no configuration file until you do.

---

### Post by Kilarin on 2008-03-14
> You need to create one! There is no configuration file until you do.
Where?  Should it be in home/.gtkhack?

---

### Post by DirtDawg on 2008-03-14
> **Kilarin said:**
> Where?  Should it be in home/.gtkhack?

Right in your home folder:
```
 gedit ~/.slashemrc
```

---

### Post by Kilarin on 2008-03-19
> Right in your home folder:   gedit ~/.slashemrc
Thank you, I'm  a moron.  You specified that several posts ago and somehow I missed it.

BUT, I have created a file named  $(HOME)/.slashemrc

I populated it with:
```
#configuration file for SLASH'EM
OPTIONS=!autopickup
OPTIONS=name:Giklen,catname:Tiger,dogname:Woof,horsename:Doosy
OPTIONS=color,hilite_pet,lit_corridor
OPTIONS=!help,!news,!mail,silent,time
OPTIONS=showexp,showscore,showdmg,showweight,invweight
```
But when I run slashem GTK it doesn't seem to pick it up, no changes in any of the options. :(

---

### Post by Keerghan on 2008-06-28
:~$ slashem
use my $(HOME)/.slashemrc

:~$ slashem-sdl 
no...

---

### Post by Keerghan on 2008-06-29
"For the benefit of anyone else who may be wonderting about this issue, I have figured things out (and yes, I am quite proud of myself, thankyouverymuch)."

Slashem-sdl file is...
$(HOME)/.slashemrc-sdl

:)

---

### Post by audunmb on 2009-02-23
I think you should be using /.slashemrc-gtk for the gtk-version. Don't know the difference between the -sdl-file and -gtk-file, but it seems like the default is -gtk

---

