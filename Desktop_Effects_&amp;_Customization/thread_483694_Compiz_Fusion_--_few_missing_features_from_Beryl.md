---
title: "Compiz Fusion -- few missing features from Beryl"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by hyperair on 2007-06-25
Hi. I recently installed Compiz and the Compiz Fusion plugins. It runs perfectly on my computer, except that it seems to have a few missing features (or I haven't found them)

[LIST]
[*]Blur Windows doesn't work
[*]There's no option to allow the mousewheel to work at screen edges.
[*]I can't bind Ctrl+Alt+Button4  and Button5 to switch viewports in the Rotate Cube section (they show up as though assigned, but when I try to turn the desktop using the hotkeys, they don't work, and when I restart the CompizConfig Settings Manager it goes back to disabled)
[/LIST]

Is there any way to have these back in Compiz Fusion? Perhaps some hidden setting that I had failed to see, or some workaround?

---

### Post by kpolice on 2007-06-25
1)Blur works, I don't use any of the fusion settings managers so you probably will have to search. First enable the blur plugin, then enable alpha blur and finally set the alpha blur match to "any" (without the quotes).

2) I have no idea what do you mean :P

---

### Post by hyperair on 2007-06-25
For blur windows, I tried that. What did you use to configure it? CompizConfig Settings Manager? Gconf-editor?

The second one, I was referring to Beryl's Rotate Cube plugin setting "Rotate with mouse wheel near edges" It's gone from Compiz Fusion.

---

### Post by Yes_It's_Me on 2007-06-25
I really need the zoom plugin from beryl! the one that comes with compiz fusion is crap (no offense to the developer at all, it's just it's quite impractical). the beryl one allows you to  pan the screen while zommed and allows you to use your computer mouse and keyboard as usual, the compiz one can do neither. I use it so much as my eyes are bad :)

Oh and the 3d windows, where they lift off the cube, that was awesome, they need to merge that too.

But i'm not complaining, it hasn't had a solid release yet and it seems quite stable for me already. and expo....oh man....it's like sex....soooo purdy :)

---

### Post by crimesaucer on 2007-06-25
@ hyperair- Do you still have Beryl in the your menu?

After I first installed Compiz Fusion and ran it with:

```
compiz --replace
```

I had some plug-in problems and some binding/button problems...like cube caps, reflection, and scale... 

Then I opened up my Beryl Settings Manager and it still was using Beryl as the Window Manager even after running the command "compiz --replace"...so I selected my xubuntu default Window Manager "xfwm" and it of course went back to the xfce regular desktop with no Emerald...

Then I ran compiz --replace again, and also emerald --replace to get Emerald back, and then all of the plug-ins worked perfectly....even better then Beryl (except wobbly windows).

I don't know if this will help you or not...but after seeing what Compiz Fusion is like when it is working perfectly, I just removed Beryl and the Beryl Settings Manager...made xfwm my default window manager and just run the two command at start up...I had them on my Start Up Apps...but I decided to play it safe for a few upgrades.

---

### Post by hyperair on 2007-06-25
Actually, I'm pretty sure that Beryl isn't running, because the cubecaps for Compiz are completely different from the Beryl ones. Compiz's cubecaps have the Ubuntu logo, whereas Beryl's have the Beryl logo.

Also, Beryl isn't running. I can be sure of that ("pidof beryl" yields no results). I still have Beryl Manager running though. Beryl's blur works, but Compiz Fusion's blur doesn't. T_T

---

### Post by RAH66 on 2007-06-25
> **Yes_It's_Me said:**
> I really need the zoom plugin from beryl! the one that comes with compiz fusion is crap (no offense to the developer at all, it's just it's quite impractical). the beryl one allows you to  pan the screen while zommed and allows you to use your computer mouse and keyboard as usual, the compiz one can do neither. I use it so much as my eyes are bad :)

Oh and the 3d windows, where they lift off the cube, that was awesome, they need to merge that too.

But i'm not complaining, it hasn't had a solid release yet and it seems quite stable for me already. and expo....oh man....it's like sex....soooo purdy :)

yeah the 3d windows I miss allot isn't there a way to get it from beryl yourself?

But anyway I'm shure they will include it in a later or final release coz it's one of the sexiest features of beryl...

---

### Post by pt123 on 2007-06-25
> **hyperair said:**
> Hi. I recently installed Compiz and the Compiz Fusion plugins. It runs perfectly on my computer, except that it seems to have a few missing features (or I haven't found them)

[LIST]
[*]There's no option to allow the mousewheel to work at screen edges.
[/LIST]


So can rotate the cube to the next surface?

For me it didn't come by default.

Go to "Enable Viewport Mouse Swith"

Enable that. 

In actions it should have  button 4 , & button 5.

---

### Post by crimesaucer on 2007-06-25
> **hyperair said:**
> Actually, I'm pretty sure that Beryl isn't running, because the cubecaps for Compiz are completely different from the Beryl ones. Compiz's cubecaps have the Ubuntu logo, whereas Beryl's have the Beryl logo.

Also, Beryl isn't running. I can be sure of that ("pidof beryl" yields no results). I still have Beryl Manager running though. Beryl's blur works, but Compiz Fusion's blur doesn't. T_T



I wasn't saying that it was Beryl running that was giving you problems (I might not have described it too good in my other post), I was trying to say that it was the Beryl Settings Manager that might be causing the problem.


I believe if you have the Beryl Settings Manager running, that it conflicts with Compiz's ccsm manager. I could be wrong, but that was what messed with my first few minutes on Compiz Fusion.


I had no cube caps (just a plain color) and only a few of the plug-ins working properly...but after making sure to turn off my Beryl Settings Manager, everything worked perfectly...so I just removed Beryl, and the Beryl Settings Manager...kept Emerald and everything is perfect.


I also removed my Beryl start up shell script and my /usr/share/xsessions/Beryl.desktop file and also removed Beryl from my start up apps.



Just to be sure you understand me...I had Compiz Fusion running with a working cube, and all of the old Beryl plug-ins that were the exact same as the Compiz Fusion plug-ins, like: the wobbly windows and scale, resize, rotate cube... they were all working, some were acting strange...


But the main thing is that the binding keys weren't working for any of them, and neither were any of the new Compiz Fusion plug-ins that aren't in Beryl, like the reflection...


...so I checked to see if I had still had the Beryl Settings Manager running, since the Beryl Settings Manager loads it's self automatically on my system, and it was still running as "Beryl" ( even after using the "compiz --replace" command). So after shutting the Beryl manager off and removing it, everything works perfectly.


You might as well remove Beryl, and the Beryl Settings Manager, and all of your start up scripts, just don't remove your configuration folders so all of your old settings will still be the same if you need to re-install Beryl again...it takes like 2 minutes. Then you can see if there was a conflict
.

I believe if you have the Beryl Manager still running, that it might conflicts with Compiz's "ccsm" manager.



EDIT: I just tried my zoom plug-in and it doesn't work either...so maybe there is something wrong...but anyway, most everything else works....and what doesn't work now will be fixed soon since they do a good job on their beta and SVN projects...

---

### Post by kpolice on 2007-06-25
> **hyperair said:**
> For blur windows, I tried that. What did you use to configure it? CompizConfig Settings Manager? Gconf-editor?

The second one, I was referring to Beryl's Rotate Cube plugin setting "Rotate with mouse wheel near edges" It's gone from Compiz Fusion.

I am using gconf-editor.

---

### Post by hyperair on 2007-06-25
Well I tried it using gconf-editor and it still doesn't work. 

@crimesaucer: my beryl-manager and beryl-settings-manager are both not running, yet I have trouble.

@pt123: I was referring to something that'll allow me to change viewports using the mousewheel, regardless of whether the mousewheel focus is on the desktop or not. It seems that the plugin you were talking about handles only input on the desktop. Anyway, my Ctrl+Alt+Mousewheel still refuses to get binded.

---

### Post by kpolice on 2007-06-25
gconf-editor will only work if you choose it as your backend.

---

### Post by Depressed Man on 2007-06-25
> **Yes_It's_Me said:**
> I really need the zoom plugin from beryl! the one that comes with compiz fusion is crap (no offense to the developer at all, it's just it's quite impractical). the beryl one allows you to  pan the screen while zommed and allows you to use your computer mouse and keyboard as usual, the compiz one can do neither. I use it so much as my eyes are bad :)

Oh and the 3d windows, where they lift off the cube, that was awesome, they need to merge that too.

But i'm not complaining, it hasn't had a solid release yet and it seems quite stable for me already. and expo....oh man....it's like sex....soooo purdy :)

I believe I read on the Compiz Fusion forums that one of the developers (or someone with a red name.. Kristian or something similar) was going work on that for Google&#347; Summer of Code. So no fear, the zoom will be improved shortly. 

As for 3D windows I don´t know about that. Just that there&#347; a few threads about it on there. So it might be worth checking it out.

I happy with it..though I have noticied one annoyance.. my ´ key doesn´t work that well. Not sure why..maybe it&#347; just an issue with something I did. I have to press and wait for it to show up before I start typing again otherwise words like don´t turn into dont. I think it has something to do with compiz fusion though because when I strike the ´ key at my normal typing pace the window shakes a little.

---

### Post by hyperair on 2007-06-25
@kpolice: I do use it as my backend. What is the type of blur you use? Bilinear? Gaussian? Mipmap? Anyway when I use Beryl, it does output in the command line something about no framebuffer_object and no fragment_program so only simple blur is available. Is there a chance that this blur plugin does not support the so-called "simple blur" and hence will not work on my graphic card?

---

### Post by sekazi on 2007-08-02
I noticed some other features from beryl which I found quite useful. The one which if the mouse is close to the edge would allow the scroll wheel rotate the cube and the one which allowed you to rotate the cube from the desktop. I wish these were part of Compiz. Another feature which I miss is the ability to use the mouse button 1 and 2 to bring up the cube instead of ctrl and alt plus mouse button 1. It seems auto rotating the top and bottom cube image while moving  is missing also. I have a widescreen so it makes them look weird. Maybe they could fix that issue with widescreens instead and make the top of the cube 1280x1280 instead of 1280x800.

---

### Post by hyperair on 2007-08-02
Ok I'm not really sure about the widescreen issue, but for the other issues, there are fixes already.

Firstly, for the viewport switching on the desktop using just the mouse wheel, activate the plugin called "Viewport Mouse Switch" or something of that sort in CompizConfig Settings Manager. You'll get the middle button cube activation on the keyboard and all.

Secondly, for the edge scroll-switching, go to the Rotate Cube plugin, and for the Rotate Left and Rotate right or something like that (Those that are bound with Ctrl+Alt+Left  and Control+Alt+Right):
1. Rotate Left: Check all the screen edges, and for the screen edge button, use Mouse4.
2. Rotate Right: Check all the screen edges, and for the screen edge button, use Mouse5.

Also, for my Blur issue, it's because my graphic card doesn't support fragment_program or more widely known as Pixel Shaders.

---

### Post by sekazi on 2007-08-02
I did what you said about the screen edge for the mouse wheel to rotate and it does not work for me. After I set it, it will not work and when I exit and go back into the CompizConfig the settings are changed back to nothing.

The first one to rotate on the desktop and to use the middle mouse button to bring up the cube worked but the second part only works on the desktop.

Heres a image of the widescreen issue I was talking about and on it I have the configuration I used for the edge rotation.
[URL="http://img463.imageshack.us/img463/6168/screenshotrh3.jpg"]
[IMG]http://img463.imageshack.us/img463/6168/screenshotrh3.th.jpg[/IMG][/URL]

The image does not auto rotate like it does on beryl because I guess there is not a setting to do it. Now if I goto that desktop and start there it will rotate after I have went and left the desktop.

---

### Post by hyperair on 2007-08-02
Try deleting your .compizconfig folder and configuring from scratch again. That removes the bug where the settings won't stick. Also use the flat file backend, not the gconf backend. It's more stable. And turn on the Inotify plugin, as well as DBus.

---

### Post by sekazi on 2007-08-02
Thanks that worked.

---

