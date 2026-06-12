---
title: "Help with Compiz Fusion/Advanced Desktop Effects"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by ftmscott on 2008-04-06
I've tried numerous times to install Compiz Fusion, unfortunately not once have i been able to get it working. I've used guides down to the T but had no so such luck.

I have relised that for what ever reason the CCSM will not load, and when i go into System  > Preference > Appearance and try to turn extra effects on all my borders disappear and i am unable to select 'Preference' under the Custom option.

I'm running Ubuntu 7.10 Gutsy, Has anyone had similar problems or know of a solution to get round this so i can use CompizFusion, any more information can be provided upon request.

Thanks in advance.

---

### Post by sdennie on 2008-04-06
It sounds like your video card driver isn't being loaded correctly.  You may want to try using envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) if you are using an nvidia or ati card.

---

### Post by ftmscott on 2008-04-06
I tried this and it seemed to do something, i reinstalled CompizFusion but still having problems.

When i try to run the Compiz Config settings manager it still doesn't load, but when i load the Compiz Settings Manager which wasnt there previously it says Compiz isn't running. When i try to enable custom or extra visual settings it says "Desktop Effects could not be enabled".

Any ideas?

---

### Post by sdennie on 2008-04-06
What is the output when you try to run "compiz --replace" from a terminal (Note: After you try that, I would recommend doing an Alt-F2 and running "metacity --replace".  Bad things can happen if you completely kill the window manager).

---

### Post by ftmscott on 2008-04-06
I get this

> compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'video'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'scale'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'switcher'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'regex'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fade'


I've just noticed i've got Catalyst Control in my menus,unfortunantley it doesnt work it says ive got problems with my drivers but Envy seemd to work.

---

### Post by geezerone on 2008-04-06
I have stumbled across Compiz and installed from Applications > Add Remove  and searched for compiz.

How do you go about applying the effects (cube rotation for example)? I have tried Restricted Nvidia gfx driver (envy and synaptic) to no avail but presume this is why it doesn't work.

---

### Post by sdennie on 2008-04-06
I've never used an ATI card so, I'm not sure that I can be of more help.  Did you install any extra packages/code to try to get compiz working?  Also, if it's simply a matter of not having window borders, you should make sure that you have the decorations plugin enabled in ccsm.

---

### Post by geezerone on 2008-04-06
I use a 6600 nvidia card but the restricted driver (or Envy) doesn't work :(

I will need to get the advanced gfx driver working first somehow I suppose.

---

### Post by george21f on 2008-04-06
y didnt anybody answer the guy who asked about the cube effect thing, also i wanted to ask, which compiz can run the cube thing , normal compiz or compiz-fusio? Thanks

---

### Post by ftmscott on 2008-04-07
> **vor said:**
> I've never used an ATI card so, I'm not sure that I can be of more help.  Did you install any extra packages/code to try to get compiz working?  Also, if it's simply a matter of not having window borders, **you should make sure that you have the decorations plugin enabled in ccsm.**
As i mentioned in a previous post the CCSM wont load, nothing happens when i try to run it. It must be a video card driver issue due to ATi Catalyst Control not working, it mentions a aticonfig but i cant find it the package manager?

---

