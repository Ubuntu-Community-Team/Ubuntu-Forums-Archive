---
title: "desktop effects!"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by RyviusRan on 2008-03-13
just wondering when I watched some videos of ubuntu most users were shown with no panel at the bottom of the screen. Instead they only had a row of program icons which when they run the mouse over them they become bold. 

Anyone know how to create this effect and does it only owrk with certain versions of ubuntu.

also I saw some other add-ons like some had it when they close any window it would look like it was being burnt like a piece of paper from the bottom up.

and someone else had it so he was able to bump his mouse against desktop icons so they would be pushed away. One more had it so it was having a cool snowing effect on his desktop.

I have looked in advanced desktop effect settings but found nothing like those. I also use compiz and ubuntu fiesty 7.10.

---

### Post by Therion on 2008-03-13
Here's an explanation of the [animations](http://wiki.opencompositing.org/Plugins/Animation) you saw being used.  You just need to configure them. 

[This blog thing](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) will get you started with configuring Compiz.

---

### Post by Cerny on 2008-03-13
A lot of these effects are under compiz fusion. It is effect programs that allows you to custmize your desktop quite nicely. I have mine a cube and the windows burn up into greenish smoke and when minimized they turn into light. 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=%28compiz%29%7C%28fusion%29](https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=%28compiz%29%7C%28fusion%29)

---

### Post by PeterJS on 2008-03-13
The bottom bar of icons was probably a dock there are a couple floating around:

Kiba:
[http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)
AWN
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
Cairo Dock:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by RyviusRan on 2008-03-13
i tried install kiba-dock but it seems not to work I followed all the steps and have the files created but it doesn't seem to know "make install" as a command.

---

### Post by RyviusRan on 2008-03-13
whenever i try to access the configure.ac it says access denied.....what does that mean?

how do i fix that i need to run it so i can make kiba work

---

### Post by RyviusRan on 2008-03-13
anyone know?

---

### Post by PeterJS on 2008-03-13
Try one of the other docks instead, I did a poor job of reading the kiba guide before posting it and didn't realize that it was being built from source, which as you're learning is a real pain in the backside.

As for the access deneied error, what are the permissions on configure.ac? you probably don't have permission to access the file.

---

### Post by RyviusRan on 2008-03-13
I am trying to install the AWN dock but I ran into a problem

i use this site as reference to how to install it
[http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource)


I am ok until I get to the part where it says Compile awn and associated libraries/helper programs:

then gives the code "make"

my terminal says it doesn't recognize the command

---

### Post by CJ56 on 2008-03-13
Don't know if this will help, but the best tutorial I know for AWN is this - 

[devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html]("devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html")

As for general Compiz effects, have you tried 

[forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") ?

They've both been pretty helpful to me... ;)

---

### Post by RyviusRan on 2008-03-13
now the program shows up in the system/preferences, but when I go to click on it nothing happens

---

### Post by RyviusRan on 2008-03-13
nevermind got it to work had to go into applications instead

---

### Post by RyviusRan on 2008-03-13
now that i got that working i still have one more question.

I know in advanced desktop effect settings you can add effects

but even though i have them all checked none of them seem to be workings under the animations part. for example the burn animation.

---

### Post by RyviusRan on 2008-03-13
bump....

---

### Post by PeterJS on 2008-03-13
The check boxes just control what effects are in the pool to be used as random effects. The actual rules that associate effect to use on what kind of window are in the list box at the top of the tab. Select one of the rules, and then edit which effect it uses.

---

