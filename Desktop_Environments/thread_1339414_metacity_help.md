---
title: "metacity help"
date: 2009-11-27
forum: Desktop Environments
---

### Post by phillychease on 2009-11-27
i cant find metacity so i can turn off the stupid wires when i minimize a window.

---

### Post by yossell on 2009-11-27
Could you give a fuller description of what you're trying to do and what the problem is? I'm not sure what wires you're talking about...

if I were to guess, is it a compiz effect that you want to get rid of and replace with metacity?

If so, alt+f2 and then typing

metacity --replace

in the box should get metacity going. Alternately, try system->preference->appearance, choosing the visual effects tab and select 'none' - it should have the same effect.

---

### Post by phillychease on 2009-11-27
well you know when you minimize a window, theres an animation of an outline of the window like wires. 
i read somewhere u can use metacity to get rid of it but i cant find it. 
unless you have a easier solution to get rid of the animation! :)

---

### Post by yossell on 2009-11-27
Ah!
I think it's in the configuration editor. Call it up, choose the metacity folder and check on 'reduced_resources' and the animation should go.

---

### Post by phillychease on 2009-11-27
wheres the configuration editor?
sorry imma noob. just installed ubuntu 3 days ago. :)

---

### Post by yossell on 2009-11-27
It could be at Applications>System Tools>Configuration Editor.

But if this isn't in your menu list, enter

gconf-editor

in a terminal should bring it up. Choose the folder called apps, and scroll down to the folder called metacity and choose the folder called general. Some options and tick boxes should appear, find the one called reduced_resources and tick it. 

The description says that other animations and features will be disabled - hmm - I don't know what those are, so maybe this will have some other annoying affects for you. 

You might find the configuration editor worth exploring though - I keep finding options I didn't know about. 

Yossell

---

### Post by phillychease on 2009-11-27
OMG thank you! but after when you move a window other lines appear too. 
but i got rid of that!
system > preference >  assistive technologies > tick enable
yayaya!

---

