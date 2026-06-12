---
title: "i need help with skydome and panels(screenshot included)"
date: 2009-01-02
forum: General Help
---

### Post by chriskin on 2009-01-02
i have two problems with my cube
1)when moving the cube, there are some white lines or dots at the end of the panels, as seen in the image below
2)there is a straight line in the middle of the skydome


fixing the second one is not really needed, the first one though is a little too irritating for the eye after some time, can you please help me?



the white lines are not very clear in the screenshot , but some times they are many more

---

### Post by Intrepid Ibex on 2009-01-02
This isn't a bug.

Your graphics card isn't good enough to show those lines as sharp as they 'should'.

---

### Post by chriskin on 2009-01-02
it is an nvidia 8600 (512mb), i thought it would be good enough :O
are you sure that this is the problem?

---

### Post by Intrepid Ibex on 2009-01-02
You won't even notice these dots, once you get used to this.

I thought that you wouldn't have that good graphics card, so now that I checked my compiz also, it shows the same-like dots that you have on your picture.

Because I have worse  graphics card ( yet x) ), I believe that you kinda have the max sharpness in your compiz (as well as I do) ...

Well, even compiz fusion isn't coded THAT well, but it doesn't matter _once you get used on it_.


**OBS.** my current graphics card is Nvidia Geforce 7400

**OBS2.** I guess that coding Compiz Fusion to that detailed must be pretty tough, as the compiz development is pretty hi-quality (fast, moreover).

---

### Post by chriskin on 2009-01-02
well if noone finds a solution i will probably have to just get used to it :S

thanks anyway :)

---

### Post by 5BallJuggler on 2009-01-02
The white lines or dots, I don't think you'll be able to do anything about, but the line through the middle you can, I assume you want some thing like the attached image?

If you go to CCSM in terminal, and then look for "Desktop Cube", then click on the appearance tab, then click on Skydome at the bottom.
You'll notice two colour bars.

the top one should be set to #000000 opacity 255
the bottom one should be set #7A2222 opacity 204

or something like that

---

### Post by Intrepid Ibex on 2009-01-02
> **5BallJuggler said:**
> ......
|an attached picture with different bg images on different sides of the cube|
I never understood, how you get different background images on different sides of the cube.

Could you give me a link or tell yourself? :)

---

### Post by ellalan on 2009-01-02
> **Intrepid Ibex said:**
> I never understood, how you get different background images on different sides of the cube.

Could you give me a link or tell yourself? :)
You need to have wallpaper plugin and need to untick show desktop in nautilus preferences.HTH.

---

### Post by Intrepid Ibex on 2009-01-02
> **ellalan said:**
> You need to have wallpaper plugin and need to untick show desktop in nautilus preferences.HTH.
I have Kubuntu and Dolphin, but I have no idea, where to find 'Kconfigeditor'.

It's not on synaptic, or Menu (even when searched)

---

### Post by 5BallJuggler on 2009-01-02
> **Intrepid Ibex said:**
> I never understood, how you get different background images on different sides of the cube.

Could you give me a link or tell yourself? :)

If you go into CCSM, towards the bottom there is a section called Utility.
If you go to the Wallpaper option you can add them there, just select one new image for each of the workspaces, then enable the wallpaper.

you may also need to edit gconf, 
press Alt + F2, type gconf-editor (this maybe "kconf-editor" in Kubuntu)
select the apps file on the left then scroll down to nautilus
select preferences
on the right panel find show desktop, uncheck it, then exit gconf-editor by closing the window.

hope this helps

---

### Post by Intrepid Ibex on 2009-01-02
There is no kconf-editor either

---

### Post by 5BallJuggler on 2009-01-02
then you need to ask someone with kubuntu experience, sorry

---

### Post by ellalan on 2009-01-02
Right click the ubuntu(kubuntu) logo and select Edit Menus then you can tick Configuration Editor under system tools (I hope).

---

### Post by Intrepid Ibex on 2009-01-02
already tried but it isn't there.

and with kubuntu the path is: Menu Editor -> System

---

