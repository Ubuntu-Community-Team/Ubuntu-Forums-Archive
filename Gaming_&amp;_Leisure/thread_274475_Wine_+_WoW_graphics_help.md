---
title: "Wine + WoW graphics help"
date: 2006-10-09
forum: Gaming &amp; Leisure
---

### Post by bline163 on 2006-10-09
Hello,
I've went through the howto for installing wine and world of warcraft and everything went fine.  The problem I'm having is when I launch "wine wow.exe -opengl" the screne is flickering like a strobe light.  I can see the main graphics and all, but at character slection I don't see my chars and when I do select enter I don't see the world I just see all my buttons etc.

So at this point I'm not sure what to try next.  I guess I would try uninstalling everything and re-doing what I already did?  Otherwise maybe someone with a little more linux / wow / ubuntu experience can help me out.  Pretty sure my graphics are ok, since I have had a Ogre3D app running before without problems.  If anyone has any ideas or can suggest something for me to try I'm would appreciate it.

Thanks!

---

### Post by bline163 on 2006-10-09
I just launched the game and click on the cenematics and when the video started there was a block rectangle in the middle to top left part of the screen.  Has anyone else had this problem?

---

### Post by bline163 on 2006-10-10
Anyone?

---

### Post by Quacker on 2006-10-12
Yup I have this same problem and I dont know how to fix it. plz help somebody

---

### Post by hikaricore on 2006-10-12
don't really have a solution to wow issues but something you might want to check first is to see if you have direct rendering enabled

```
glxinfo | grep rendering
```

should return:
**direct rendering: Yes**

if it does not you'll need to search around for how to install the correct video drivers for your graphics card.

I stopped playing wow so i won't be able to help any further with this.

---

### Post by iiiears on 2006-10-13
Font Corruption Workaround.

    1.) In the game open video options. DISABLE "UI Scale" 
    2.) Use A lower color depth. 
    3.) Change color depth any time there is font corruption.

    Of course this workaround left me with as many questions as it     answered. 
     A.)Does Font Hinting or other settings modified by sudo           dpkg-reconfigure fontconfig affect wine/cedega/crossover office.
     B.)Does the type of font used affect corruption.
     c.)Do settings in Xorg.conf affect font rendering. Frame buffer, composite, DRI,GLX modifiers.

     This for me is a minor annoyance and i am grateful for all the work done to make World of Warcraft playable. 

Many Thanks to all the developers involved, see you soon in Azeroth!
Lathrop*

---

### Post by ty13 on 2006-10-13
I have the same problem aswell, tried to fix, but to no avail

---

### Post by Redcard on 2006-10-13
My suggestion would be to get the Codeweavers Crossover Beta.  It supports WoW. 

Now I realize that would mean buying a product, but.. honestly, I had tried to get WoW running in linux for _MONTHS_ and it just was one hassle after another.  This got it going in a matter of minutes. (Well.. hours, I had to patch WoW, of course, from the CDs up to the current PL.. but it was RUNNING within minutes)

Just a thought.  It's really one of those time vs money decisions.

---

### Post by NickRich on 2006-10-13
Did you patch wine before installing?  
Running wow under wine has a well known flickering bug w/ nVidia cards.

If you didnt didnt patch before installing you will eithor need to install wine again, after patching(directions & patch links in the forums somewhere), or take the easy way out and install a prepatched wine([http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb](http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb))

Hope this helps.

---

### Post by bline163 on 2006-10-16
Sorry it's been a bit since I looked at the replies to my post.  I tried messing around with all the different settings for wine + WoW and couldn't get anything to work.  So I said what the heck 15$ isn't too spendy and purchased Cedega.  Honestly it was well worth it for how easy WoW installed.  I can't say this about other games yet since I've only been playing WoW.  I'm going to try Guild Wars soon and see if I can't get that up and running.

I'm still really new to understanding how linux works.  I don't know what Cedega did to get it working, but it must be something small since I could launch wow and actually get into the game, but I just could'nt see anything.  Maybe I'll try NickRich's idea and see if that solved my problem.  Also thanks to everyone sending in their ideas.

---

