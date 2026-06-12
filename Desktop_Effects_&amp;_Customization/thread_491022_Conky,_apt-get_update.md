---
title: "Conky, apt-get update"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by Tavorisch on 2007-07-03
Okay after Conky totally screwing up beryl, i am back up and running again with beryl and an odd semi working version of conky... So I am able to get conky to work.. I couldn't find the conky config file for the life of me.... I pretty much have no clue what I am doing. so i went through reinstalling conky but now I think my sources.list is screwed.. apt-get update doesn't seem to work right..... Anyway I know this is a dumb place to post hey wtf should my sources.list look like.. but the main thing I'm wondering is where is the config file to change conky position and certain display?.. reason being.. running conky in user a window pops up that i can move, and it matches my backround color but it stil is a movable window.. when I run conky from root it works as long as I have the console open, which I imagine is how it works.. but it imediatley permanently places itself in the lower left hand corner and i can only see like .25 of the top of conky. is it just as simple as find that config file and change a position? anyway any help much appreciated I will post the sources.list problem elsewhere unless it can be answered here! thanks much.. I am running an ATI radeon 9600 mobile. 128mb.

---

### Post by crimesaucer on 2007-07-03
Your position, and style that Conky is drawn from, is called the:

.conkyrc

and it should be in your home folder.

Read these links: 

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)


...also ask someone here for help, or to see different .conkyrc files and how they look: [http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky)

---

### Post by notwen on 2007-07-03
Depending on whether you've created your own custom .conkyrc you may or may not find one.  If you've only used ```
sudo apt-get install conky
``` then you're using conky's default config file, which is coded into conky.  Simply create your .conkyrc in your /home folder and make your very own conky.  An easy way to do so is simply copy and paste info from the "Post your .conkyrc" thread Crimesaucer linked to above.  As far as it interfering w/ Beryl/Compiz, you'll need to let Beryl/Compiz finish loading before launching conky, I believe that it is mentioned in the How-To conky posts here in the forums and possibly even in the "Post your .conkyrc" thread.  Good luck and scream if you run into any issues.  =]

---

### Post by Tavorisch on 2007-07-03
hey thanks guys.. I'm sure I'll figure it out eventually from the sourceforge links and i definitely  will scream =)! take it easy.

---

