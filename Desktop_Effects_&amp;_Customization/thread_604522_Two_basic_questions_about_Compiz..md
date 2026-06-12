---
title: "Two basic questions about Compiz."
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Roasted on 2007-11-06
I've been tinkering around with Compiz and I've learned a lot. However, there's two things I can't seem to nail down, and I know I'm just overlooking something stupid.

For one - when I minimize/maximize things, I wanted them to wobble like the genie effect. I found magic lamp and all that, I even used a tutorial, I don't know I have to be screwing something up. Maybe hearing it from somebody else will help me out.

Second - I'd like to change the image inside of the cube. When I spin the cube, it's so nice to see a 63 Corvette doing a wheelie in the background, but inside the cube watching some cartoonish gears spin just doesn't seem to fit the particular background good. How can I change it?

---

### Post by Forlong on 2007-11-06
> **Roasted said:**
> For one - when I minimize/maximize things, I wanted them to wobble like the genie effect. I found magic lamp and all that, I even used a tutorial, I don't know I have to be screwing something up. Maybe hearing it from somebody else will help me out.
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Reasonable window effects"
> **Roasted said:**
> Second - I'd like to change the image inside of the cube. When I spin the cube, it's so nice to see a 63 Corvette doing a wheelie in the background, but inside the cube watching some cartoonish gears spin just doesn't seem to fit the particular background good. How can I change it?
You can't... the gears are more of a proof of concept.
But there's actually something like this in development (called Photo wheel).

---

### Post by Roasted on 2007-11-06
I did follow that guide. It changes nothing whatsoever. Do I have to specify which windows it applies to in the windows match? Because right now all I see is "magic lamp 50"

But that changed nothing. I don't have the magic lamp effect. :(

---

### Post by Forlong on 2007-11-06
Did you really set it like this:

---

### Post by Roasted on 2007-11-06
K, that fixed it.

New issue. I have a background set for the cube, so when I spin the cube I'll see a picture. However, it mysteriously disappeared, yet it still appears to be active. What in the world?

Secondly, I want to take a screenshot of this in progress. However, control+tab is what I use to spin the cube. When I'm holding down control in order to keep the cube stationary and I hit the print screen button, it does nothing. So I noticed there's a screenshot option in the customization features, yet it doesn't seem to work. Whatever keys I type in, like control 1, it just goes to say "none". Why?

---

### Post by Happy_Man on 2007-11-06
Use the GNOME screenshot utility (Applications --> Accessories --> Take Screenshot) and set it to delay five seconds, then spin the cube. It'll take the screenshot like that (I think).

---

### Post by dpar on 2007-11-06
> **Happy_Man said:**
> Use the GNOME screenshot utility (Applications --> Accessories --> Take Screenshot) and set it to delay five seconds, then spin the cube. It'll take the screenshot like that (I think).


Yup, it will. I tried it.:)

---

### Post by Forlong on 2007-11-06
Or use Gimp's *File &#8594; Acquire &#8594; Screenshot* function (that's what I always do)

---

### Post by Roasted on 2007-11-07
Suddenly my background picture on the cube disappeared.

I made no changes and for the life of me I can't get it back. :(

---

### Post by Forlong on 2007-11-07
If it's the same picture as before, make sure the respective Image Loading plugin is enabled (Png, JPEG, Svg)

---

### Post by Roasted on 2007-11-07
It is loaded. I'm not sure where in the world it went! What else can I look for?

---

### Post by Roasted on 2007-11-09
Still lost on this... If I simply want a background picture, that's all I have to set, right? Do I have to set a skydome image too? I forget if I did last time when it was working... But in any event, neither scenario works.

---

### Post by Rinzwind on 2007-11-09
> **Forlong said:**
> 
You can't... the gears are more of a proof of concept.
But there's actually something like this in development (called Photo wheel).

You can have a fishtank with "3D Atlantis"

---

### Post by Forlong on 2007-11-09
> **Roasted said:**
> Still lost on this... If I simply want a background picture, that's all I have to set, right? Do I have to set a skydome image too?
I thought you *were* talking about the skydome. What do you mean by you don't have a background picture - is it a solid color or transparent?

If the latter is the case, make sure **Opacity When Not Rotating** is set to 100% in *ccsm &#8594; Desktop Cube &#8594; Transparent Cube*

---

