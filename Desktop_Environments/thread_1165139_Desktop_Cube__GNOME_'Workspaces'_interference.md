---
title: "Desktop Cube / GNOME 'Workspaces' interference"
date: 2009-05-20
forum: Desktop Environments
---

### Post by MahBumble on 2009-05-20
Hi, 

I've been using Ubuntu (Jaunty, wubi) for about a week now, it has been fantastic. Was worried about problems (being a lifetime Windows user), but it has been very easy, thanks to these forums! The only issue I've stumbled on so far has been in using the multi-desktop features of compiz' desktop cube, alongside gnome's workspaces. 

I would like to use the desktop cube (and *only* the desktop cube), but for this to function I have to set there to be four workspaces in gnome. Now when click on the workspaces it seems i have four desktop cubes! 

1) Is there a way to have the four workspaces in the bottom right of gnome interface correspond to the four sides of your cube? 

Also, panel icons build up like nobody's business with a few programs running, so:

2) Is there a way to have your minimised icons on the panel correspond only to the face of the cube you're currently working on?

Thanks,
MahB

*There goes my bean-ginity*

---

### Post by balboost on 2009-05-20
hello,

your problem sounds weird. do you have a screenshot ? it would help me understand. it is like you had 4x4 desktops, right ? 

first of all, how did you install compiz ? it can come from this. secondly, have you installed the compiz-config-session-manager (cssm) ? it is very useful and it allow to configure compiz and thus the cube.

> 1) Is there a way to have the four workspaces in the bottom right of gnome interface correspond to the four sides of your cube? 

by default, you have 2 panels, one on top and one another on the bottom. on the right corner of the bottom one, do you still have the desktop switcher ? it is set to 2 workspaces by default. if you right click on the top panel for example, choose 'add to panel', then desktop switcher. it should bring you the tool you want.

> 2) Is there a way to have your minimised icons on the panel correspond only to the face of the cube you're currently working on?

yes, you can configure it with ccsm.

hope i helped ! i'm not sure of my translations (i'm french).
cheers

---

### Post by Sarai the Geek on 2009-05-20
> **balboost said:**
> 
your problem sounds weird. do you have a screenshot ? it would help me understand. it is like you had 4x4 desktops, right ? 

That's certainly what it sounds like. MahBumble, when you go to the preferences for the workplace switcher (right click on the panel applet to get a menu) it should look like this:

[IMG]http://farm3.static.flickr.com/2449/3549344594_81c829e471.jpg?v=0[/IMG]

If it doesn't, change it then try to use the desktop cube again.

---

### Post by MahBumble on 2009-05-20
Apologies, I did make it sound like I have four desktops on screen at once, what I mean to say is I have four workspace icons on the bottom right panel (my workspace switcher preferences are set exactly as you recommend Sarai). 

My issue is that I'd like the panels in the bottom right to refer to the four sides of the cube, not four workspaces each with a fresh cube. I hope I'm clear enough! Screenshots attached demonstrate my desktop cube working as it should.  

I'm worried having three other workspaces available but unused will waste RAM, perhaps I shouldn't worry!

Cheers
MahB

---

### Post by mcduck on 2009-05-20
> **MahBumble said:**
> Apologies, I did make it sound like I have four desktops on screen at once, what I mean to say is I have four workspace icons on the bottom right panel (my workspace switcher preferences are set exactly as you recommend Sarai). 

My issue is that I'd like the panels in the bottom right to refer to the four sides of the cube, not four workspaces each with a fresh cube. I hope I'm clear enough! Screenshots attached demonstrate my desktop cube working as it should.  

I'm worried having three other workspaces available but unused will waste RAM, perhaps I shouldn't worry!

Cheers
MahB

Install CompizConfig Settings Manager (if you haven't already got that). Then use that and go to General Options/Desktop Size. Set Horizontal Virtual Size to 4 (or any amount of desktops you want) and both Vertical Virtual Size and Number of Desktops to 1.

Memory use of virtual desktops is something you really don't need to worry about on any modern machine. After all, Linux & Unix systems have had virtual desktop pretty much since the first graphical desktops and if a 386 with 16MB of RAM can handle couple of virtual desktops without problems modern computers shouldn't have much problems either.. ;)

---

### Post by MahBumble on 2009-05-20
Fantastic, my problem was I had set Number of Desktops to 4, the icons in the bottom right refer to sides of the cube, and my question about minimised windows (Q2) is solved as a bonus! Thanks mcduck, now we're cooking with gas! 

...only one small detail...The workspace icon in the bottom-right (see scrnshot) seems to have room for a second 'row' of virtual desktops (or second desktop cube?), it's purely aesthetic, but annoying none-the-less. Do you have any hints how to adjust the panel icon so the four desktops fill the space?

Thanks all!
MahB

---

### Post by mcduck on 2009-05-20
> **MahBumble said:**
> Fantastic, my problem was I had set Number of Desktops to 4, the icons in the bottom right refer to sides of the cube, and my question about minimised windows (Q2) is solved as a bonus! Thanks mcduck, now we're cooking with gas! 

...only one small detail...The workspace icon in the bottom-right (see scrnshot) seems to have room for a second 'row' of virtual desktops (or second desktop cube?), it's purely aesthetic, but annoying none-the-less. Do you have any hints how to adjust the panel icon so the four desktops fill the space?

Thanks all!
MahB

Try removing the Workspace Switcher applet from your panel and adding it back again. I've seen couple of people having the same problem and if I remember right that should help.

---

### Post by MahBumble on 2009-05-20
Perfect fix! Call me OCD, but only now can I get some work done. 

Thanks
MahB

---

### Post by ckonestroh on 2009-05-20
Hmmm...  I just push control + alt + down arrow it show all the desktops in a plane mode and what is on each desktop....


later


Confusing post.... !@#$#$%%^&^!

---

### Post by Sarai the Geek on 2009-05-21
> **MahBumble said:**
> Fantastic, my problem was I had set Number of Desktops to 4, the icons in the bottom right refer to sides of the cube, and my question about minimised windows (Q2) is solved as a bonus! Thanks mcduck, now we're cooking with gas! 

...only one small detail...The workspace icon in the bottom-right (see scrnshot) seems to have room for a second 'row' of virtual desktops (or second desktop cube?), it's purely aesthetic, but annoying none-the-less. Do you have any hints how to adjust the panel icon so the four desktops fill the space?

Thanks all!
MahB

Wow, that is some wallpaper! I don't think I'd be able to focus on work with all that going on in the background! :popcorn:

---

