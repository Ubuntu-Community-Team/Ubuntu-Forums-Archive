---
title: "Ubuntu11, classic view + unity sidebar"
date: 2011-10-04
forum: Desktop Environments
---

### Post by duub7 on 2011-10-04
Hello,

Is it possible to use ubuntu 11 classic desktop and also add the sidebar that is in "default" ubuntu desktop? 

:)

---

### Post by kapad on 2011-10-04
You could try disabling the bottom panel and then using a dock (like docky or awn) as a side panel. 
You would definitely have to do a lot of configuration for it to be like unity.

---

### Post by Krytarik on 2011-10-04
You could run the Launcher of Unity 2D in your classic Gnome session, meaning *only* those, not the top panel. :P
Would be much easier and perhaps better fitting your taste than setting up an entirely different dock.

Therefore, just install "unity-2d" from the official repos, and follow the instructions here:

[http://www.webupd8.org/2011/01/run-unity-qt-panel-or-launcher-in.html](http://www.webupd8.org/2011/01/run-unity-qt-panel-or-launcher-in.html)

To run the Launcher automatically at login, just add "unity-2d-launcher" to your "Startup Applications".

Greetings.

---

### Post by duub7 on 2011-10-04
> **Krytarik said:**
> You could run the Launcher of Unity 2D in your classic Gnome session, meaning *only* those, not the top panel. :P
Would be much easier and perhaps better fitting your taste than setting up an entirely different dock.

Therefore, just install "unity-2d" from the official repos, and follow the instructions here:

[http://www.webupd8.org/2011/01/run-unity-qt-panel-or-launcher-in.html](http://www.webupd8.org/2011/01/run-unity-qt-panel-or-launcher-in.html)

To run the Launcher automatically at login, just add "unity-2d-launcher" to your "Startup Applications".

Greetings.

Thanks!
Ive got the sidebar and all but the only problem is it isnt hiding itself and when i put my things to full screen they are partially hidden behind the sidebar. Have any idea how to solve that? :)

---

### Post by duub7 on 2011-10-04
Ive found this and hoped that it may help me:
[http://marianochavero.wordpress.com/](http://marianochavero.wordpress.com/)

ive installed it with "ubuntu software center" but the silly thing is that i dont know how to start it, anyone have any ideas? :D

---

### Post by Krytarik on 2011-10-04
> **duub7 said:**
> Ive found this and hoped that it may help me:
[http://marianochavero.wordpress.com/](http://marianochavero.wordpress.com/)

ive installed it with "ubuntu software center" but the silly thing is that i dont know how to start it
Good, you've already found this! :D
Sorry for not mentioning it in the first place!

To run it, you should find "2D-Desktop Settings" under "System -> Preferences" in the classic Gnome menu, or by searching the Dash. Another way is to run "/usr/share/2d-desktop-settings/2dsettings.py" via the Alt+F2 dialog or from the Terminal.

---

### Post by viperdvman on 2011-10-04
I've used my Compiz settings, specifically the Unity-related ones, to make it to where my Unity Launcher autohides. I'd have to check, but I'm sure it was in Compiz. But, that's when I'm running regular Unity *(I have 2D ONLY on my netbook, but don't use it)*. I wonder if that works for your situation, using the Unity 2D launcher in GNOME 2.x?

---

### Post by Krytarik on 2011-10-04
> **viperdvman said:**
> I wonder if that works for your situation, using the Unity 2D launcher in GNOME 2.x?
Nope, CCSM's settings for - the 'real' - Unity don't affect Unity 2D at all.

---

### Post by duub7 on 2011-10-04
Ran into a new problem again.
If the settings should look something like this:
[http://www.ubuntugeek.com/wp-content/uploads/2011/04/app.png](http://www.ubuntugeek.com/wp-content/uploads/2011/04/app.png)

Then cant select 4 of the first selections, only 2 last are available. Couldnt find a similar problem in google. Any more ideas? :D

---

### Post by Krytarik on 2011-10-04
> **duub7 said:**
> Then cant select 4 of the first selections, only 2 last are available.
To enable the "hide_mode" options, you apparently need to add the respective key to GConf manually; I learned this from the very last comment on the site of those tool:

[http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/#comment-82](http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/#comment-82)

And, given that you say you can't change all the 4 first options in the tool, you might need to add the key "super_key_enable" as well; and also make sure the key "use_strut" is there, too; screenshot of all those options in "gconf-editor" here:

[http://1.bp.blogspot.com/-eHlkOJ-JYKs/ThF4leCgvRI/AAAAAAAACHg/Pl-NjW6i6fM/s1600/edit+2d+applauncher+settings.png](http://1.bp.blogspot.com/-eHlkOJ-JYKs/ThF4leCgvRI/AAAAAAAACHg/Pl-NjW6i6fM/s1600/edit+2d+applauncher+settings.png)

---

### Post by duub7 on 2011-10-05
Thank you for help. Finally got it to work but while browsing around the internet for solutions earlier i found 2 more soulutions: Docky and Avant Window Navigator. After trieing them both out i decided to stick with Avant for the moment :)

---

### Post by Krytarik on 2011-10-05
> **duub7 said:**
> After trieing them both out i decided to stick with Avant for the moment
So!? That's my choice of dock - and panel - , too. :D
In fact, I'm loving it; and I'm despising Docky. :-#

Another dock I've tried is Cairo Dock; not bad, too, but way too much effects for my taste, and therefore way too heavy on the resources, at least with the default settings. You need to shift it down a lot only to make it kinda usable ;-) , and even then it's still much heavier than AWN.

---

### Post by viperdvman on 2011-10-05
I use Avant Window Navigator as well on my Ubuntu (both desktop and netbook). It's a very pretty dock, and I like how I can customize it. However, the Zoom effect when hovering over an applet really sucks. It's barely a 25% zoom, and is nothing like the RocketDock on my Win7 or the dock on Mac OS X. That's just a minor gripe about AWN. Overall, I love it, and use it all the time.

Enjoy your dock. Docks are great :)

---

### Post by Krytarik on 2011-10-05
> **viperdvman said:**
> However, the Zoom effect when hovering over an applet really sucks. It's barely a 25% zoom, and is nothing like the RocketDock on my Win7 or the dock on Mac OS X.
Well, I'm just using the "Glow" effect there, as I'm not a fan of too much effects anyway, as mentioned in my previous post. ;-)

---

### Post by viperdvman on 2011-10-06
I too use "Glow" on my AWN for the icon effects... that and "Fade", depending on my mood. :D

---

