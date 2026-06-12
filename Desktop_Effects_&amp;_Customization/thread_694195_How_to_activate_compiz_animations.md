---
title: "How to activate compiz animations"
date: 2008-02-11
forum: Desktop Effects &amp; Customization
---

### Post by bharkins on 2008-02-11
I have the Animations checked, but I don't see the usual Action tab to get them to work. How to make them do their stuff?

---

### Post by johnn1949 on 2008-02-11
Did you install xgl
______________________________
10 - Install XGL
- Open a terminal: Applications > Accessories > Terminal and run the following:

sudo apt-get install xserver-xgl


- When complete, close the terminal and reboot
______________________________
This got everthing working for me.

---

### Post by johnn1949 on 2008-02-12
Try going to animations where you checked the box.  double click the word aninations.  select effects settings.  At the top right check the box for random effects.

If things start happenning its all installed.  I still haven't figured out all the settings,  but that lets me show off a little it.

---

### Post by bharkins on 2008-02-12
> **johnn1949 said:**
> Did you install xgl
______________________________
10 - Install XGL
- Open a terminal: Applications > Accessories > Terminal and run the following:

sudo apt-get install xserver-xgl


- When complete, close the terminal and reboot
______________________________
This got everthing working for me.

Just tried it through Synaptic and received an error message about not being able to get to the Ubuntu repository for xserver-xgl. I'll try that later. Using your command, I get an error, :Invalid operation xserver-xgl' .

---

### Post by johnn1949 on 2008-02-13
Make sure you have enabled all the Ubuntu software repositories. Main ,universe,restricted, and multiverse

and these  2 in the third party softwar

[http://archive.canonical.com/ubuntu/ubuntu](http://archive.canonical.com/ubuntu/ubuntu) gutsy partner
[http://archive.canonical.com/ubuntu/ubuntu](http://archive.canonical.com/ubuntu/ubuntu) gutsy partner (source code)

They should all be there with the installed system.

reload in synaptic before trying to install

Hope that helps

---

### Post by bharkins on 2008-02-13
> **johnn1949 said:**
> Make sure you have enabled all the Ubuntu software repositories. Main ,universe,restricted, and multiverse

and these  2 in the third party softwar

[http://archive.canonical.com/ubuntu/ubuntu](http://archive.canonical.com/ubuntu/ubuntu) gutsy partner
[http://archive.canonical.com/ubuntu/ubuntu](http://archive.canonical.com/ubuntu/ubuntu) gutsy partner (source code)

They should all be there with the installed system.

reload in synaptic before trying to install

Hope that helps

I have all the repos and installed xserver-xgl OK. I still don't understand how to get any animation action. There are 20 animations and all are checked by default and 6 tabs related to animations. Now how do I initiate an action for something animated? Anything will do to prove it works.

---

### Post by johnn1949 on 2008-02-13
I'm not sure how far your are getting compiz running.  Do you have the cube and are able to rotate it.  If you do you should be able to annimations---effects settings --->check random box.  And things should happen randomly.  

If you don't have the 3d cube try General-->desktop size  and the settins should be 4-1-1 from top to bottom.

Like I said I haven't been able to figure out individual settings yet but the random is interesting.

May be you can find some thing here: [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

I'm surprised no one else has answered,  keep trying and googling and reading forums.

John

---

### Post by bharkins on 2008-02-13
> **johnn1949 said:**
> I'm not sure how far your are getting compiz running.  Do you have the cube and are able to rotate it.  If you do you should be able to annimations---effects settings --->check random box.  And things should happen randomly.  

If you don't have the 3d cube try General-->desktop size  and the settins should be 4-1-1 from top to bottom.

Like I said I haven't been able to figure out individual settings yet but the random is interesting.

May be you can find some thing here: [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

I'm surprised no one else has answered,  keep trying and googling and reading forums.

John

I have the cube, 3D cube and quite a few of the other features, such as Snow. However, there are still a series of features that I can't run from the Compiz window such as Freewins, Stars, Anaglyph, as well as some of the Animation features. Are they independent of each other or are some not available based on specific other features? What I would like to see is the developers produce a guide or a MAN for Compiz.

---

### Post by johnn1949 on 2008-02-13
Here's some sites.  I just googled them.

[http://members.cox.net/mushroomlake/Compiz.html](http://members.cox.net/mushroomlake/Compiz.html)

[http://arstechnica.com/journals/linux.ars/2008/01/30/experimental-compiz-plugin-allows-window-tilting-rotation](http://arstechnica.com/journals/linux.ars/2008/01/30/experimental-compiz-plugin-allows-window-tilting-rotation)

---

