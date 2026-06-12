---
title: "[SOLVED] How to enable windows blasting effect ?"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by sourabhsharma149 on 2008-02-26
Hello All,


I am able to  perform desktop effects on Gutsy but as far as emerald themes are concerned I am only able to change windows border ....

Please can some guide how  I can get effects like windows turns into sparklings when closed...WallPapers, login screen, the background of cubes,transparent cube etc...like shown in many Ubuntu videos in youtube ?

Thanks

---

### Post by owbizi on 2008-02-26
I don't know if it's what you want, but...

$ sudo apt-get install compizconfig-settings-manager

After, go Main Menu -> System -> Preferences -> Advanced Desktop Effects Settings.

Hope it helps!

---

### Post by Therion on 2008-02-26
This explains link [How to Set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) so you can do all that stuff.

---

### Post by sourabhsharma149 on 2008-02-29
Thnx all to reply....

I meant by this post that I have already installed compiz manager (Advanced Desktop Effects Settings) and I can do most of the effects...

But I want to change look n feel of my desktop theme ....


As of now I can only change things like border colors using emerald theme manager ......

But I want to add effects like to add gadgets, window blats into sparklings when closed...backgroung of cube while rotating....

like in this video:

[http://www.youtube.com/watch?v=44S33l-R0ms](http://www.youtube.com/watch?v=44S33l-R0ms)

or 

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)


Thanx..

---

### Post by dark_harmonics on 2008-02-29
Do the effects under the animations menu have what you want? I like to set that to apply to all events so it randomly does it. The people in those videos have them statically assigned to specific events.

---

### Post by Therion on 2008-02-29
Walking you through how to set up everything you see happening in those videos would take hours.  Basically what you want to do is use the "Burn" animation in Compiz Fusion to get the sparkling animations when windows open or close (choose the "Randomly Colored Fire" option) while the background behind the rotating cube is the Skydome plugin for Compiz.  

The gadgets can be enabled by installing [gDesklets](http://www.gdesklets.de/) or [Screenlets](http://screenlets.org/index.php/Home).  

The dock you see at the bottom is Avant Window Navigator, or [AWN](http://wiki.awn-project.org/index.php?title=Main_Page) for short.

That should get you started.

---

### Post by sourabhsharma149 on 2008-02-29
Thank you all ..Specially Therion.....For your great effort to understand my post...

Now you know what exactly I wanted....I will surely follow it...

however Therion can you please explain how to get burn enable burn (window to sparkling) from compiz manager on events of windows,poups etc on closeing ?

---

### Post by rainwalker on 2008-02-29
Go to the Animations section, under the "close animation" tab set the close animation to burn, then go to the "effect settings" tab and go to the Fire settings and check the box for "randomly colored fire"

---

### Post by Therion on 2008-02-29
> **sourabhsharma149 said:**
> ... however Therion can you please explain how to get burn enable burn (window to sparkling) from compiz manager on events of windows,poups etc on closeing ?
Sure...  I'm at work right now and behind a Windows machine, so I'm going by memory, but this should get you close:

Open the Compiz Settings Manager: System -> Advanced Desktop Effects  
Put check in the Animations plugin box to enable them.
Now open the "Animations" Plugin by double-clicking on the plugin.
Click on the "Close Effects" tab. There will be three lines at the top: Glide, Fade, and another Fade. 
Double click on the Glide entry to open the Advanced Settings. 
Now you will see a drop-down menu where you can select whatever effect you want to happen when you close a window, along with the duration and color. 
Choose the option for "Colored Fire" or "Multi-Colored Fire", something like that. 
You can also choose to have "smoke" appear or not by clicking on the box for it. 
Lastly, I increase the duration from a default setting of 300 to 500 to make the effect last a little longer.

---

### Post by sourabhsharma149 on 2008-03-01
Thank you very much Therion....

I am able to do it at last......With many new things to try...

---

