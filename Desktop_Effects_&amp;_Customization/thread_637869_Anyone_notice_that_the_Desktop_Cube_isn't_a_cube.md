---
title: "Anyone notice that the Desktop Cube isn't a cube?"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by Aikon- on 2007-12-11
Has anyone noticed that Compiz's "Desktop Cube" (an associated "Rotate Cube") plugins don't actually produce a *cube*? They don't even produce a statically-shaped object!

Here's what I mean: In the following two pictures, you are seeing a view of my cube from the top down (i.e. that's the cube cap you see). So each of the edges of the rectangle that you see is actually the **top edge** of one of the sides of the cube (where each side of has a resolution equal to your display resolution).

Running on this logic, each of the edges should be the same length, but they clearly are not. It looks like Compiz is resizing the "cube" to fit into a box that is some % of your display resolution, based on your zoom level.

Furthermore, this shape isn't even static; if you rotate the cube 90 degrees (as shown in the second picture), the object has completely changed dimensions! And correspondingly, the image on the cube cap was stretched to fit the new dimensions (hence why the picture looks different).

Does anyone else think it would be useful to at least have the option to have the cube be a "cube" (really a rectangular prism, since the height of the cube will always be different) and to have it be a statically-shaped object as you spin it around? This gets annoying when you're looking at faces of the cube on an angle, because if gives you a false perspective :(

Anyway, just my thoughts.. let me know what you guys think.

-Aikon

---

### Post by chips24 on 2007-12-11
try using beryl instead

---

### Post by zeller on 2007-12-11
Soooo...what exactly are you saying? The Cube isn't a "cube?"

Fine by me. It looks like a "cube" on my screen. I didn't measure it.

---

### Post by chips24 on 2007-12-11
:lolflag:

---

### Post by chips24 on 2007-12-11
i used to live in st. catharines

---

### Post by Aikon- on 2007-12-11
> **chips24 said:**
> try using beryl instead

..Why? Beryl is deprecated and is being merged back into Compiz-Fusion. I have no desire to go backwards to get functionality I want.

[QUOTE=zeller]Soooo...what exactly are you saying? The Cube isn't a "cube?"

Fine by me. It looks like a "cube" on my screen. I didn't measure it.[/QUOTE]

If you look at the pictures I attached I think you'll get a better idea of what I mean. This is probably much more pronounced on wide-screen monitors. Its not the fact that the height is different from the width of each side (this just makes sense), but the fact that the 3D model is changed as you rotate the cube.

The edges of the box don't even stay parallel, giving you a false perspective and making some things seem farther away than the "are", and other things closer.

But it doesn't bother, OK; that answers my question even if I think you missed what I was trying to say.

-Aikon

---

### Post by chips24 on 2007-12-11
well... atleast somthing older is more secure, beryl isnt that old

---

### Post by Krydahl on 2007-12-11
A cube is never really going to be practical, because monitors aren't square. I don't see why it shouldn't be a consistent cuboid however, except that then if you rotate it to look at a cap from above it wouldn't fit on your screen - that would have to be square.

---

### Post by chips24 on 2007-12-11
i yhink i know what youre talking about, does the screen "flickre"?

---

### Post by chips24 on 2007-12-11
try to change how many workspaces you have

---

### Post by Aikon- on 2007-12-11
> **Krydahl said:**
> A cube is never really going to be practical, because monitors aren't square. I don't see why it shouldn't be a consistent cuboid however, except that then if you rotate it to look at a cap from above it wouldn't fit on your screen - that would have to be square.

Good, you **do** understand me :P  Yes, if you were looking at it from the top it would have to be square, so you would have excess space on the sides.

Shouldn't be too difficult? You could have a simple switch that the user could turn on or off to make it whichever way they like.

And yes, a true cube is impractical because monitors aren't square; its the consistent cuboid (as you call it) that I'm after.

---

### Post by Aikon- on 2007-12-11
> **chips24 said:**
> i yhink i know what youre talking about, does the screen "flickre"?

> **chips23 said:**
> try to change how many workspaces you have

No, its not "flickering"... I'm not sure you understand what I'm talking about =/

---

### Post by Krydahl on 2007-12-11
If I rotate mine in its usual orientation it seems pretty consistent. It's only when I rotate it while looking at the caps I notice the shifting. I'm afraid this isn't something I can get worked up about - and I've certainly no idea how to change it.

Maybe you could ask on the compiz forums?

---

### Post by zeller on 2007-12-11
> **Aikon- said:**
> And yes, a true cube is impractical because monitors aren't square; its the consistent cuboid (as you call it) that I'm after.

What's the matter with not having the excess on the sides of a widescreen monitor (which I have)? It just changes the perspective when you tilt it forward or backward to fill the screen...but the desktop natively fills the screen, doesn't it? If you're using widescreen and want a "cube" you're going to be losing desktop real estate.

Maybe the next version will have a toggle for purists. :)

---

### Post by Aikon- on 2007-12-11
@ Zeller:

Its not just when you tilt it forward and back; its side-to-side as well. And I'm not talking about changing the width of each face to match the height... as I've said, each face will be a rectangle equal in resolution to your display, so you're not losing any real-estate at all.

This only comes into effect when you zoom out; the proportions of the box that Compiz draws change as the cube moves around.

---

### Post by Tristam Green on 2007-12-11
I see this effect as well.  I just solved it by having a solid color cubecap in lieu of a background.

It seems that compiz is attempting to balance between "true cube" and the desktop's resolution.

It draws the sides of the cube (as seen from above) based on the Y-component of the desktop's resolution...unless I'm mistaken.

It then interprets the front-side of the cube and draws based on that.

Doesn't seem like it would be a nightmare to base the lengths of the sides of the cube off the X-component of the active desktop's resolution instead, but I'm no programmer :)

---

### Post by zeller on 2007-12-11
I'll have to check it out later because I don't have my box with me right now. I hope it doesn't put you off from using it.

---

### Post by Aikon- on 2007-12-11
Nope, not at all.. just wondering what people's thoughts on it were. After exams are done I'll probably see about putting it in... if it really is as small a change as I think, shouldn't be hard to add the option.

---

### Post by sloggerkhan on 2007-12-11
Most people's desktops aren't square, though.....
I think I'd be okay with a squashed cube, maybe.

Generally speaking, I think the distortion does give a better view of the desktop, however, once I remember being really annoyed that my cube cap kept deforming.

---

### Post by Biggus on 2007-12-11
> **Aikon- said:**
> Nope, not at all.. just wondering what people's thoughts on it were.

I didn't actually think that you were being serious.

It's not generally something which I, speaking as someone who was simply overjoyed to get it up and running in the first place, had even noticed.

(I'm too busy messing around with that cool fire effect)

---

### Post by HeavyAl on 2007-12-11
> **Aikon- said:**
> This is probably much more pronounced on wide-screen monitors. 
-Aikon

Yeah, it looks a bit like that on my Inspiron 1720 (widescreen). It doesn't really bother me though as it's usefulness lies in the fact that it positions the applications on different sides of the 'cube' regardless of how non-cube-like it actually is.

I would imagine that cf just doesn't take into account the screen ratio when rendering the cube. Probably could be fixed fairly easily but it's not a deal breaker imo.

---

### Post by Eddie Wilson on 2007-12-11
Well I don't have a widescreen and I have never noticed any problems. I will look to be sure but mine doesn't look like yours.
Eddie

---

### Post by jlotempio on 2007-12-11
I think the point of what compiz is trying to do is keep the proportions the same all the way around, in effect trying to keep the cube static.  Otherwise, you will have different resolutions on the cube cap every other rotation.  I see what you are saying about the distortion, but doesn't it only take effect if you are looking at the top (or bottom) of the cube.

I guess what I am missing is, what is the point of rotating while looking at the top of the cube anyways?  If you rotate while looking only at the sides of the cube, it is not much of an issue.  Compiz is pretty legit in my opinion and this is definitely not something that I have ever noticed before.  Not something I have lost any sleep over...

---

### Post by chips24 on 2007-12-11
> **Krydahl said:**
> A cube is never really going to be practical, because monitors aren't square. I don't see why it shouldn't be a consistent cuboid however, except that then if you rotate it to look at a cap from above it wouldn't fit on your screen - that would have to be square.

well if it works its fine, youre going to have to give me better screenshots

---

### Post by BLTicklemonster on 2007-12-12
Looks like a cube in exaggerated perspective to me.

---

### Post by Tweenk on 2007-12-12
This is 100% by design and not an error. I suspect that the rendering of a cube (and I mean a cube - that is, all sides are equal in length) is transformed to stretch it to screen coordinates. I think this makes for a more efficient implementation, though I have no experience in 3D math, so I'm not sure.  Anyway, who looks on their cube cap that often?

---

### Post by Aikon- on 2007-12-12
> **Tweenk said:**
> This is 100% by design and not an error. I suspect that the rendering of a cube (and I mean a cube - that is, all sides are equal in length) is transformed to stretch it to screen coordinates. I think this makes for a more efficient implementation, though I have no experience in 3D math, so I'm not sure.  Anyway, who looks on their cube cap that often?

I don't, but you can see the effects even when you're just rotating it horizontally. I used the cube-cap pictures because they help make it a bit clearer to explain.

---

### Post by Brando569 on 2007-12-12
my cube never worked for me, it was always a square (2d). i tried increasing the number of desktops in both kde and compiz and that didnt fix it, so i just gave up since i never use multiple desktops anyway

---

### Post by chips24 on 2007-12-15
> **Tweenk said:**
> This is 100% by design and not an error. I suspect that the rendering of a cube (and I mean a cube - that is, all sides are equal in length) is transformed to stretch it to screen coordinates. I think this makes for a more efficient implementation, though I have no experience in 3D math, so I'm not sure.  Anyway, who looks on their cube cap that often?


i do lol, maby its a Canadian thing!!!, i love to stare at my caps!(sarcasm)

---

### Post by BLTicklemonster on 2007-12-15
lmao "Desktop Cubal Entity" maybe?

---

### Post by tad1073 on 2007-12-15
> Originaly Posted by tad1073:
I can't get beryl to work on my computer, Emerald either. The one that came with 7.04 I got to work once, but I do have wobble windows.

[s]finaly got beryl working, just need to learn how to configure it.

Everything is running smoothly now. Got beryl configured to my likes. Just need to learn the filling systm and where to put everything.

---

### Post by DiscGo on 2008-01-29
I have compiz installed and running. When I try and switch desktops, I only have 2 choices instead of 4. So instead of having a cube I have what is more like a piece of paper that I can check both sides of. I have tried changing my number of desktops from 2 to 4 and I still get only two choices.

[IMG]http://i51.photobucket.com/albums/f375/DiscGolfDiver/Website/Screenshot.png[/IMG]

I have read I don't need Beryl, but I really want the 4 sided cube. What do I do?

---

### Post by overdrank on 2008-01-29
> **DiscGo said:**
> I have compiz installed and running. When I try and switch desktops, I only have 2 choices instead of 4. So instead of having a cube I have what is more like a piece of paper that I can check both sides of. I have tried changing my number of desktops from 2 to 4 and I still get only two choices.

[IMG]http://i51.photobucket.com/albums/f375/DiscGolfDiver/Website/Screenshot.png[/IMG]

I have read I don't need Beryl, but I really want the 4 sided cube. What do I do?

Hi and welcome, you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

### Post by DiscGo on 2008-01-29
Thanks for the quick reply. 

I have installed the latest version of compiz already and I see the "desktop cube" and "rotate cube" are selected but I still can not see a full 4 desktop cube.

[IMG]http://i51.photobucket.com/albums/f375/DiscGolfDiver/Website/Screenshot-1.png[/IMG]

---

### Post by Aikon- on 2008-01-29
Okay, first, that's not a screenshot of "Compiz", its a screenshot of the "CompizConfig Settings Manager". Try to be clear about what you're saying.

In the settings manager, click on "General Options" (at the top), then go to the "Desktop Size" tab. The first slider is called "Horizontal Virtual Size". Slide that to the right until you get the number you want (for a cube, 4.. for a pentagon, 5, etc).

---

### Post by DiscGo on 2008-01-29
Aikon-

That worked great! Thanks. 


Sorry about my bad terminology. I am still getting used to Ubuntu and it's terms.

---

### Post by Aikon- on 2008-01-29
> **tad1073 said:**
> Everything is running smoothly now. Got beryl configured to my likes. Just need to learn the filling systm and where to put everything.

No problem =) Its a learn-as-you-go type of thing ;)

Glad I could help,

-Aikon

---

