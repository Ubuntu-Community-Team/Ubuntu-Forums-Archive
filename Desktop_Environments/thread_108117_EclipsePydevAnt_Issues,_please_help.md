---
title: "Eclipse/Pydev/Ant Issues, please help"
date: 2005-12-25
forum: Desktop Environments
---

### Post by viscount on 2005-12-25
I would really like to start doing as much development as I can
with the most powerful tools I can get my hands on, in this case
it would be a professional grade IDE and likewise for a build system.

I've chosen Eclipse and Ant. 

Now, as it just so happens I found a great [tutorial]("http://www-128.ibm.com/developerworks/opensource/library/os-ecant/")
on the IBM developerworks site that describes how to install the Pydev plugin for 
Eclipse and goes through making a sample Python and then building it with Ant using
the PyAntTasks.py plugin for Ant.

I'm having a few problems following the article. So if there are any developers out 
there who wouldnt mind spending a few minutes and perhaps helping me out with this
 I would be eternally greatful.

I have managed to install the Pydev plugin by following the article, however the article
 lists it as Pydev 0.4.1 but the version that gets installed by following the steps is 
0.99.5 which is the most recent according the the Pydev website.


**Figure 4** seems that something has changed with Pydev because I dont see 
any options for "Comment" or "Uncomment" and I've checked with the Pydev 
website and that is listed as a features for 0.98.5

**Figure 5** another change in Pydev, there is no "Pythong -> Run" instead right 
clicking shows an option to "Run As -> Python Run" however when I select that it 
seems nothing happens, perhaps Im just not sure what to expect and dont see it.

**Figure 6** another change, cant find the debug option

**Figure 7** worked perfectly which was pretty cool :D 

**Figure 8** is a big problem. When I click "Add Jar" it just says "no entrys available".
Ok, so I try to do "Add External Jar" and point it to the location of PyAntTasks.py
and it seems to import the jar, but when I go on with the exercise and try to build
the program it fails saying that it can not find the PyAntTasks.py module.

I've tried adding the .jar while running Eclipse as a regular user, and also while
running Eclipse in sudo mode, both have the same result.

Rather disapointing. Im really hoping that some kindly developers will help me
to get back on track so that I can start to contribute.

Eclipse+Pydev+Ant would be such a powerful toolset if only I could figure out
how to get them all to work in harmony.

thanks muchly
Alex

---

### Post by viscount on 2005-12-25
Well.. 

I have to say those Gnome folks are mighty cool people!

"nsh" from #gnome-love helped me out, we got the pyAntTasks.jar working.

So now I am a happy camper, Thanks nsh :) you the man!


To get pyAntTasks.jar to work, just copy here
/usr/lib/eclipse/plugins/org.apache.ant_1.6.5/lib/pyAntTasks.jar

We also chmod 755, but im not sure if thats nessisary.

Then in eclipse you go to 'window->preferences->ant->runtime' then select "Ant 
Home Entrys (default)" from the list, then click "Add Jars" or if that doesnt work you 
can do "Add External Jars" and browse for pyAntTasks.jar.

---

### Post by viscount on 2005-12-25
Further comments about that dW IBM article.

I've now got everything to work, and I gotta say its pretty nice.

Comment and Uncomment figure 4 has been moved to the main window menu
under "Source"

Also the Pydev plugin does not automatically find your python location
but it will seem as though it does so if you're having trouble with it
make sure to set "Window->Preferences->Pydev->Interpreter Python->Python Interpreters" 
click new, then browse to /usr/bin/python to set it

If you have any trouble with [ant finding the correct version of java]("http://www.ubuntuforums.org/showthread.php?p=602913") just take a look at that link, it can be a bit of a bugaboo
to get that to work properly.

cheers!

---

