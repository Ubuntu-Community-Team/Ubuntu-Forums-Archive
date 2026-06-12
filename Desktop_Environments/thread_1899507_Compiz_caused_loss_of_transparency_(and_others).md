---
title: "Compiz caused loss of transparency (and others)"
date: 2011-12-23
forum: Desktop Environments
---

### Post by k1ngman on 2011-12-23
Hello everyone.

I have just bought a new machine and installed Ubuntu 11.04 on it. (don't like Unity and the rest of the "novelties" from 11.10). Thing is, right at the end, after I installed and configured all the necessary software, on the last two clicks in Compiz, everything started to go wrong. Basically what happed was that every dock and screenlet I had on my desktop, lost it's transparency and on top of that all the windows lost their borders and cannot be moved and/or resized.
All this started after I clicked to enable "Rotate Cube" and "Desktop Cube". By doing that it automatically deselected "Expo", "Viewpoint Switcher" and "Wall". I'm more that sure that it deactivated something else but those where the check boxes that I saw being unchecked.
Meanwhile I enabled "Windows decoration", previously disabled and got back the windows borders, but that was all, so now I'm stuck with the loss of transparency and the dead windows.
So, definitely this being a Compiz problem, can someone give the an idea what was the cause if this all?
Oh, and btw, I uninstalled  and reinstalled Compiz and ATI driver but nothing.

So, thanks in advance for all the help you guys can give me.

B.

---

### Post by wildmanne39 on 2011-12-24
Hi click on the second link in my signature and there is a guide for setting up the cube and effects go to the section you need and there is a link for resetting unity and compiz.
Thanks

---

### Post by k1ngman on 2011-12-24
Thank you for your recommendations but unfortunately it didn't worked. I tried to reset the compiz settings but no luck. One more thing that I forgot to mention is that I'm using Ubuntu Classic and not Unity. Tried to switch to login with Unity out of curiosity but there I can't even see the mouse cursor and the upper menu panel. (L.E. - I see that this is a pretty common problem)

---

### Post by azkraja on 2011-12-24
My suggestion is to install "MyUnity" instead of CCSM, as it is making trouble off and on with unity. you can customize unity now, follow below link for information and installation of "MyUnity". I recomond you to uninstall CCSM first and use unity. 
[http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/)

---

### Post by BC59 on 2011-12-24
I don't think the problem is CCSM. Compiz as a program is unstable.

---

### Post by k1ngman on 2011-12-24
Well... never mind now, I lost it and reinstalled the whole thing again :)
Thanks anyway you guys for all the suggestions, appreciate it.

Regards, B.

---

### Post by wildmanne39 on 2011-12-24
Hi, I did not now you were using classic, in the guide I sent you too under the 11.04 section it tells you what you need to do to fix that problem there are two plugins that get unchecked when you change settings in compiz in classic mode they are resize and move windows for future reference you just recheck them and you should be good.

@BC59 > Compiz as a program is unstablethere are issues with compiz mainly due to so many different computer configurations but I have used it safely for about five years in every ubuntu version including unity,the second link in my signature makes his problem easy to fix. 
Thanks

---

### Post by k1ngman on 2011-12-24
@wildmanne39 I noticed that what you gave me was for Unity, and starting from there I adapted it for classic and fixed the moving and resizing issues, but I was still stuck with the transparency issue which in the end was a deal breaker for that install.  Anyways, one again, thank you for the help and I hope all this will perhaps help others dealing with this issues in the future.

---

### Post by BC59 on 2011-12-24
> **wildmanne39 said:**
> @BC59 there are issues with compiz mainly due to so many different computer configurations but I have used it safely for about five years in every ubuntu version including unity,the second link in my signature makes his problem easy to fix. 
Thanks

We could start a poll to see the opinion of the users....

---

### Post by wildmanne39 on 2011-12-24
Hi, did you change the settings in compiz for transparency? I believe there are still two different transparencies in ubuntu one in compiz and one for panels and launchers but I have never looked for the other setting I just use the one in compiz. I am glad you have it back to the way it was in unity it is a little tricky changing settings in compiz but it has gotten easier with 11.10.
Enjoy

---

### Post by k1ngman on 2011-12-24
@wildmanne39  No, didn't even touched the transparency plug-in. All I did was to check the "Rotate cube" box witch in turn auto checked the "Desktop cube" box and unchecked a whole set of other boxes and lead to this.

---

### Post by wildmanne39 on 2011-12-24
Okay, thank you for letting me know.

---

### Post by BC59 on 2011-12-24
What about a Compiz reset?

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

### Post by k1ngman on 2011-12-24
@BC59 Tried that too, didn't worked.

---

### Post by BC59 on 2011-12-24
I would reinstall the Graphic drivers, through Synaptic.

---

### Post by k1ngman on 2011-12-24
Done that too. Both synaptic and downloaded from ATI website. All in all, it was a compiz problem, got nothing to do with the drivers or anything else.

---

