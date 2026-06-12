---
title: "wallpaper changer with fade in effect"
date: 2009-01-16
forum: General Help
---

### Post by amirage on 2009-01-16
Hello all

I have been searching high and low for the above topic. Did a google search, ubuntuforum search, but neither gave satisfying results. Well, I'm looking for a wallpaper changer in ubuntu that has fade-in transitions. I know there are a number of programs out there such as wallpapoz, desktop dapper, wallpaper-tray. I have tried all these but neither really has a fade-in effect. They all cut into the next wallpaper, which is quite useless! 

Can anyone out there help me out? I'd greatly appreciate your help. I'm not into coding and most of searches ended in coding in xml. I'm trying to promote ubuntu in my office and this effect could steal the show from the existing mac users.

I would really be grateful if anyone could give me a step-by-step guide as to how this can be done. 

Lastly, I think it's high time that ubuntu adds this as default in the new distros...

Looking forward to your advices....

Amit

---

### Post by midtown on 2009-02-11
This seems to be happening out of the box in Jaunty when you change wallpapers. I am confused and fascinated!

---

### Post by hansdown on 2009-02-11
Hi amirage.

Try drapes in synaptic.

[http://ubuntuforums.org/showthread.php?t=798634](http://ubuntuforums.org/showthread.php?t=798634)

---

### Post by sgissinger on 2009-02-20
Is drapes capable of fading out wallpaper?

---

### Post by nathand28 on 2009-02-20
You could always try making an xml file with the overlay effect?
       Basically, move all the pictures you want to be the wallpapers into a folder, and make an .xml named whatever you want. Edit it so it is something like this:
```

<background>

<static>
<duration>1.0</duration>
<file>/home/USERNAME/PATH/TO/IMAGE</file>
</static>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/USERNAME/PATH/TO/IMAGE</from>
<to>/home/USERNAME/PATH/TO/IMAGE</to>
</transition>

<static>
<duration>10.0</duration>
<file>/home/USERNAME/PATH/TO/IMAGE</file>
</static>

</background>

```

In this example, each picture will stay on the screen for 10 seconds, it would be much better to set it to either 300 or 600 seconds ( 5 or 10 minutes ).
Make sure you put the time in seconds.
;)

---

### Post by sgissinger on 2009-02-22
Thanks for this nathand, but it's not very convinient for someone like me (and I guess the most part of wallpaper-tray, wallpapoz and drapes users) who want to randomly display more than 100 wallpapers contained in 1 folder... Maybe there is something to do with wp-tray sources if they are open ones, or just a config file...

---

### Post by merlin_ie on 2009-05-15
i dont know if you have found a solution to this, but i came across "gbackground"..you can set it for anytime you wish (even 10 seconds) BUT, the only drawback i find is that it doesnt remember the directory (i have it set to start on bootup and show Pictures director but i still have to enter the directory name)..i hope this SOMEWHAT helps, and if you find a solution to making it remember the directory, please post here :D

---

### Post by amirage on 2009-05-15
Hi all

Thanks for all the help. Just wanted to let everyone know that I have moved onto Jaunty from 8.10. And, it has been a wise decision to say the least. It's a very quick OS - boots quickly, runs programs even faster, uses openoffice 3.0 aaaannnnddd (drum roll) has fading effect when changing backgrounds...

I use wallpapoz as a program to change the wallpapers...

I'd really suggest everyone to shift to Jaunty...great OS...

Can't wait for 9.10 to be released...

Also, can't imagine what Ubuntu will come up with version 10.

Amit

---

