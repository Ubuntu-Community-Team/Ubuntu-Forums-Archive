---
title: "Is is possible to disable window shading in Desktop effects?"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by maluze on 2007-04-24
I upgraded to Fiesty two days ago, and enabled the desktop effects. Everything is fine, except out of nowhere, if a window is left alone for (*gasp*) 2 seconds, the window gets shaded...and this is where my computer acts reeeaaaaaaaaaaaaallly slow, and I have even had to shut down and restart my computer 3 times today becuase it became so unresponsive. Its a shame, becuase otherwise i really like Compiz, and the workspace and window effects perform admirably, given my hardware specs:

emachines T2742; Intel Celeron 2.7Ghz, 256 MB memory, and integrated Intel extreme graphics 3d video card..

Is there a way that i can disable just window shading and keep the desktop effects? :confused:

---

### Post by OmniCloud on 2007-04-25
Don't know man...I'm fairly new and still playing around with the new Ubuntu myself...There isn't anything in preferences though?

---

### Post by eentonig on 2007-04-25
With the default desktop effects, I don't know.

But you could install beryl and beryl-manager. Then you can tune those (and a lot more) effects to suit your machine.

---

### Post by maluze on 2007-04-25
there is no such option to turn window shading off, only to turn the 3d workspace and wobbly windows off/on; it would make sense to include one for window shading as well =/

Well, i will take a stab at Beryl, see how everything works out, but if anyone knows a way to disable it, it be greatly appreciated :)

---

### Post by kyle_fransham on 2007-04-25
There's lots of settings for compiz in gconf-editor.  Type "gconf-editor" into a terminal, and you'll get a window that controls a whole bunch of programs and system processes.  

Navigate to apps -> compiz -> general -> allscreens -> options and you'll see a list of active plugins at the top.  Here you can select which plugins you want compiz to use.  

If you navigate to apps -> compiz -> plugins you can see what all of these plugins do.

The only one I could find that has anything to do with shading is the minimize plugin, so perhaps you want to try disabling that one???  (just double click on the list of plugins and you'll get a chooser where you can delete it)

I looked through all of the other ones, and couldn't find anything about shading in them, but maybe it's buried in there somewhere.  I tried deselecting the minimize plugin, and found that the animation was gone when I minimized windows, but minimizing still worked.  

Let me know how it goes!

---

### Post by aktiondan on 2007-04-25
I spent about an hour playing around with gconf-editor and there is so much you can configure it's crazy.  I didn't mess with too many options, since so far everything is working great, but you can change the spring constant and friction of the wobbly effect, so that it wobbles forever and is super slow.  Or you can make it wobble super quick.  You can change how fast it fades into menus, change the opacity of moving windows, so when you drag them around you can see through them, and do a whole bunch of other things.  I didn't find anything specific to your problem, but I'd click around all the plugin options and look for opacity-related configurations to tweak.  Some of the descriptions aren't very obvious what function they perform though.

---

### Post by maluze on 2007-04-26
thanks for the tips...I went to gconf-editor, and went to minimizing and cahnged shading  resistance from 75 to 100, but apparently that didnt work. So I tried to change other configurations, and now when I maximize a window, I can't click on the top menu bar buttons for minimizing or close the program..but the buttons will work if the window is not maximized (and sometimes when it is)...I dont know how to change it back :(

so now i have two problems instead of one...lol. theres so much to configure, and many dont have appriopriate descriptions, that i really dont know...maybe if there is some guide saying what all (and i mean ALL) the options in compiz do...

---

