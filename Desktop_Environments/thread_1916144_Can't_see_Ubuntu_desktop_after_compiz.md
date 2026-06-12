---
title: "Can't see Ubuntu desktop after compiz"
date: 2012-01-27
forum: Desktop Environments
---

### Post by Lateralus138 on 2012-01-27
Hello all, I have Ubuntu 11.10 and tried using Compiz settings to use wobble, animations etc... and after I rebooted I could no longer see anything on the desktop except for the wallpaper. I tried going into recovery mode and ran the repair thing and when I logged back in everything was back to normal, but after I rebooted again I couldn't see anything again. I tried to reset the compiz settings to default and change them, but as soon as I rebooted the settings witched back and I couldn't see anything again and so I have to recover each time to be able to see the desktop. Can someone please help?

---

### Post by Lateralus138 on 2012-01-27
Ok I fixed this by completely uninstalling all of the Compiz, so now it's fine, but I would still loved to use it. Might it be a hardware driver problem?

---

### Post by rg4w on 2012-01-27
> **Lateralus138 said:**
> Might it be a hardware driver problem?
It's possible.  On my system I can do some very adventurous things with CCSM, but when connected to a projector I can't temporarily turn off Unity (as seems to be often done to turn on the Cube) without a freeze.  Without the projector even turning off Unity works well - provided of course I turn it back on before I quit CCSM.

Did you perhaps turn off the Unity plugin before rebooting?  You symptoms sound familiar to what I've experienced when I was experimenting with such things.

When that happens, I find using "unity --reset" does restore my settings to their defaults as expected, but due to what's been reported as a bug with that command sometimes under such unusual circumstances it doesn't want to finish; that is, it does all the important stuff, then gets hung up with an error about a file it can't find and stays there.  When that happens I've been able to force-quit Terminal, restart, and my system seems good beyond that (been using it for many days since my last of those kinds of experiments).

You may try "unity --reset" to see if it will restore your setup.

Please post how it works out.

---

### Post by Hreinsi on 2012-01-27
> **Lateralus138 said:**
> Hello all, I have Ubuntu 11.10 and tried using Compiz settings to use wobble, animations etc... and after I rebooted I could no longer see anything on the desktop except for the wallpaper. I tried going into recovery mode and ran the repair thing and when I logged back in everything was back to normal, but after I rebooted again I couldn't see anything again. I tried to reset the compiz settings to default and change them, but as soon as I rebooted the settings witched back and I couldn't see anything again and so I have to recover each time to be able to see the desktop. Can someone please help?

If you can do unity --reset try enable this way newer had prob

[http://www.youtube.com/watch?v=diqzqrCdMH8&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRMpV](http://www.youtube.com/watch?v=diqzqrCdMH8&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRMpV)

---

### Post by Lateralus138 on 2012-01-27
> **rg4w said:**
> 

Did you perhaps turn off the Unity plugin before rebooting?  


When that happens, I find using "unity --reset" does restore my settings to their defaults 

You may try "unity --reset" to see if it will restore your setup.

Please post how it works out.

I was searching for more help online and came upon the same suggestion of unity --reset and when I ran unity in the terminal it said that it was not detected or whatever and it told me to use the get the apt-get install and so I just did and will try re-installing Compiz and seeing if I can do anything with it... My setup was restored I think when I uninstalled Compiz.

---

### Post by Hreinsi on 2012-01-27
> **Lateralus138 said:**
> I was searching for more help online and came upon the same suggestion of unity --reset and when I ran unity in the terminal it said that it was not detected or whatever and it told me to use the get the apt-get install and so I just did and will try re-installing Compiz and seeing if I can do anything with it... My setup was restored I think when I uninstalled Compiz.

dont have solution maybe search for unity in synaptic

if you have never done unity --reset dont rush things can take long time many have done wrong trying to rush things watch this well thats not slow but can be :)

[http://www.youtube.com/watch?v=gg9C_F-0H8A&feature=context&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRM](http://www.youtube.com/watch?v=gg9C_F-0H8A&feature=context&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRM)

---

### Post by Lateralus138 on 2012-01-27
Thanx everyone for you input and suggestions... I have narrowed the problem down to wobbly windows... more specifically when I select wobbly windows it says I have to disable snapping windows; which, is the actual problem. Now I just have to figure out what's happening when I disable the snapping windows....

---

### Post by MG&amp;TL on 2012-01-27
Well...two things-uninstalling compiz would be even more terminal to your system than fiddling with the settings in CCSM. The reason for this is that Unity is a compiz plugin.

You would also do well to follow [this]("https://help.ubuntu.com/community/CompositeManager") guide if you wish to enable stuff with Unity. I can personally vouch that it works.

---

### Post by Hreinsi on 2012-01-27
> **Lateralus138 said:**
> Thanx everyone for you input and suggestions... I have narrowed the problem down to wobbly windows... more specifically when I select wobbly windows it says I have to disable snapping windows; which, is the actual problem. Now I just have to figure out what's happening when I disable the snapping windows....

[http://www.youtube.com/watch?v=diqzqrCdMH8&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRMpV](http://www.youtube.com/watch?v=diqzqrCdMH8&context=C3ccbacbADOEgsToPDskJtcKAxscdsREWBJXpcRMpV)

Did you try this

---

### Post by Hreinsi on 2012-01-27
dont enable by cliking the boxes go to preferences and pluggin list doit from there

---

### Post by Hreinsi on 2012-01-27
be carfull what pluggins you enable some dont work well together

---

### Post by Lateralus138 on 2012-01-27
> **Hreinsi said:**
> be carfull what pluggins you enable some dont work well together

I looked at the video and selected just the ones I needed I have wobbly selected and it's not working. That's the thing I am almost sure it's the wobbly plugin not working well with the snapping windows plugin because the wobble works, but when I maximize the window then I can no longer grab or move it and when I restarted the windows work, but no wobbly even though the plugin is selected.

> **MG&TL said:**
> Well...two things-uninstalling compiz would be  even more terminal to your system than fiddling with the settings in  CCSM. The reason for this is that Unity is a compiz plugin.

You would also do well to follow [this]("https://help.ubuntu.com/community/CompositeManager") guide if you wish to enable stuff with Unity. I can personally vouch that it works.

I understand what you mean and have Compiz installed. I will take a look at that guide and thank you very much.

---

### Post by Hreinsi on 2012-01-27
> **Lateralus138 said:**
> I looked at the video and selected just the ones I needed I have wobbly selected and it's not working. That's the thing I am almost sure it's the wobbly plugin not working well with the snapping windows plugin because the wobble works, but when I maximize the window then I can no longer grab or move it and when I restarted the windows work, but no wobbly even though the plugin is selected.



I understand what you mean and have Compiz installed. I will take a look at that guide and thank you very much.
 wobbly dont work with snapping i think

---

### Post by Hreinsi on 2012-01-27
This the pluginlist that i have enable and works for me wery well you could try to do unity --reset and install thi and see how it works just these diable others just enable these to begin with

core
bailer
detection
composite
opengl
imgjpeg
decor
mousepoll
gnomecompat
grid
vpswitch
compiztoolbox
text
imgpng
place
session
imgsvg
snap
resize
ring
regex
move
animation
wobbly
fade
workarounds
cube
td
rotate
unitymtgrabhandles
expo
unityshell

and disable wall

---

### Post by Hreinsi on 2012-01-27
you can see it here to

[http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d](http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d)

---

### Post by Lateralus138 on 2012-01-27
> **Hreinsi said:**
> This the pluginlist that i have enable and works for me wery well you could try to do unity --reset and install thi and see how it works just these diable others just enable these to begin with

td


  I have done everything you said and nothing else is broke, but wobbly isn't working. One thing I did notice after talking to you all and browsing the Internet elsewhere, is that I do have the "td" plugin I see here and in other screenshots and videos. Is this "td" important?

---

### Post by Hreinsi on 2012-01-27
> **Lateralus138 said:**
> I have done everything you said and nothing else is broke, but wobbly isn't working. One thing I did notice after talking to you all and browsing the Internet elsewhere, is that I do have the "td" plugin I see here and in other screenshots and videos. Is this "td" important?

it isnt its 3d windows that is from compiz plugin extra pakage

---

### Post by Hreinsi on 2012-01-27
I going to do fresh install my self some bugs after testing some stuff its  do you have seperate home partition if so i would set the system up again
maybe somthing went wrong when you unistaled compiz just saying for me with seperate home it is somtimes quiker than finding solutiton :)

---

