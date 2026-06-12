---
title: "Compiz cube help"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by steviear on 2008-01-01
Hi there. I am having trouble with the cube in ubuntu gutsy. When i ctrl+alt+left click mouse to rotate cube. It rotates, but from inside the cube and i want it to zoom out how do i do this. Thanks
btw happy new year

---

### Post by Krydahl on 2008-01-01
In CCSM (Preferences -> Advanced Desktop Effects) go into the rotate cube bit and set the zoom to something - I use 0.2.

---

### Post by steviear on 2008-01-01
i just done that and nothing happens everything still the same

---

### Post by Krydahl on 2008-01-01
OK, I'm confused. Can you describe in more detail what happens? Do you get the same affect as Ctrl + Alt left arrow?

Obvious things to check:

You are moving the mouse as well as pressing Ctrl Alt left click I assume?

Have you got both the desktop cube and the rotate cube options checked?

Also check that you have viewport switcher enabled and the plugin in there set to rotate.

---

### Post by overdrank on 2008-01-01
> **steviear said:**
> Hi there. I am having trouble with the cube in ubuntu gutsy. When i ctrl+alt+left click mouse to rotate cube. It rotates, but from inside the cube and i want it to zoom out how do i do this. Thanks
btw happy new year

Hi and sounds like inside the cube. In CCSM, desktop cube then behavior tab untick inside cube. :KS

---

### Post by steviear on 2008-01-01
thanks overdrank sorted. out of all the options i changed didnt even see that one

---

### Post by Seguaro on 2008-01-01
I'm having the same problem.  The rotation looks like it's inside the cube. Zoom setting has no effect. Cube and Rotation are both set on.

Ctrl-Alt-Arrow rotates the screens in a 3D sort of way but doesn't show a cube (difficult to verbalize).  Alt-Ctrl-Mouse Drag rotates from a viewpoint inside of a cube. Not at all like any screen shots of the cube that I've seen.

I'm using Gutsy, and have an ATI Radeon X-1650 Video card (which I suspect may be the culprit).  I'm using the updated proprietary ATI driver from their website. 

I would love to get the cube working properly if I could.  I've read all the threads about the cube but nothing really describes this particular problem.

---

### Post by Krydahl on 2008-01-01
> **overdrank said:**
> Hi and sounds like inside the cube. In CCSM, desktop cube then behavior tab untick inside cube. :KS

I'd never seen that one before. Cool option, but I think I prefer the outside view.

---

### Post by Seguaro on 2008-01-01
Duh, didn't see that option. :)

Works for me now too.

Thanks

---

### Post by drumpat01 on 2008-01-13
Thank you guys for the help. I was having the same problem and now it works great!! This is so awesome!

---

### Post by mondoUNC on 2008-01-13
To get an actual 3d cube check "Cube Reflection" under settings. Its odd that they call it that but I think thats what you want.

---

### Post by Absinthe Minded on 2008-01-13
> **mondoUNC said:**
> To get an actual 3d cube check "Cube Reflection" under settings. Its odd that they call it that but I think thats what you want.[FONT="System"][COLOR="DarkOrchid"]"Cube reflection" is actually under "Effects" in CCSM (not "Settings"), thanks for that though mondo, you sorted my problem![/COLOR][/FONT]

---

### Post by Dojjah on 2008-01-13
Im having a similar problem, when i hit ctrl alt right it will switch to another desktop. But I cant figure out how to zoom out and see multiple desktops as a rotating cube. I try holding ctrl alt left click but that does nothing (i am using a laptop touch pad and left/right buttons). I have my desktop size set to 4. 

Desktop cube,rotate cube, viewport switcher, and cube reflections are all checked. What am  I doing wrong?

---

### Post by rune0077 on 2008-01-13
> **Dojjah said:**
> Im having a similar problem, when i hit ctrl alt right it will switch to another desktop. But I cant figure out how to zoom out and see multiple desktops as a rotating cube. I try holding ctrl alt left click but that does nothing (i am using a laptop touch pad and left/right buttons). I have my desktop size set to 4. 

Desktop cube,rotate cube, viewport switcher, and cube reflections are all checked. What am  I doing wrong?

You need to run CCSM, then alter the settings under Roatet Cube until you get something you like. Especially, change zoom and speed for a better view of the cube.

---

### Post by mondoUNC on 2008-01-14
> **Dojjah said:**
> Im having a similar problem, when i hit ctrl alt right it will switch to another desktop. But I cant figure out how to zoom out and see multiple desktops as a rotating cube. I try holding ctrl alt left click but that does nothing (i am using a laptop touch pad and left/right buttons). I have my desktop size set to 4. 

Desktop cube,rotate cube, viewport switcher, and cube reflections are all checked. What am  I doing wrong?

Try clicking on the actual desktop and dragging it left or right, that should get it to zoom and and actually show the whole cube. I the way the cube shortcuts are written ctrl+alt+right just flicks right real fast but click the desktop should definitely do it if all the settings are right. If you have vertical scrolling you can also scroll through the desktops when no window is active.

---

### Post by fetisha on 2008-02-24
> **steviear said:**
> Hi there. I am having trouble with the cube in ubuntu gutsy. When i ctrl+alt+left click mouse to rotate cube. It rotates, but from inside the cube and i want it to zoom out how do i do this. Thanks
btw happy new year

When I do ctrl+alt+left click nothing happens. And when I do ctrl+alt+left/right arrow key it changes my workspace, but I don't see a cube. I have both desktop cube and rotate cube installed and enabled. :(

---

### Post by overdrank on 2008-02-24
> **fetisha said:**
> When I do ctrl+alt+left click nothing happens. And when I do ctrl+alt+left/right arrow key it changes my workspace, but I don't see a cube. I have both desktop cube and rotate cube installed and enabled. :(

Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. and the rest set at 1

---

### Post by fetisha on 2008-02-24
> **overdrank said:**
> Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. and the rest set at 1

It was already set like that

---

### Post by overdrank on 2008-02-24
> **fetisha said:**
> It was already set like that

HI and under system, preference, appearance, the visual tab you have set to extra or custom.

---

### Post by fetisha on 2008-02-24
> **overdrank said:**
> HI and under system, preference, appearance, the visual tab you have set to extra or custom.

There isn't a preferences under systems. Maybe it's because we're using different versions of ubuntu? I'm using Xubuntu 7.10

---

### Post by overdrank on 2008-02-24
> **fetisha said:**
> There isn't a preferences under systems. Maybe it's because we're using different versions of ubuntu? I'm using Xubuntu 7.10

Ok that will make a difference, try using the alt,F2 keys and use the command compiz --replace
and see what happens.

---

### Post by fetisha on 2008-02-24
> **overdrank said:**
> Ok that will make a difference, try using the alt,F2 keys and use the command compiz --replace
and see what happens.

Done, but nothing happens

---

