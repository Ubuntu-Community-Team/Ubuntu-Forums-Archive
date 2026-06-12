---
title: "Half life 2 with wine and nvidia?"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by pay on 2007-03-26
I used to run half life 2 with wine awhile ago (0.9.20) with an ati radeon x800. I got some corrupted visuals like purple crates and things like that when I ran it with directX 9. Directx 7 worked flawlessly but it wasn't as pretty. My question are; 
Is this a problem with the ati drivers?
Do nvidia cards experience the same problems?
Is this a problem with wine itself?
Does Cedega have this problem?
Thanks.

---

### Post by frodon on 2007-03-26
Don't forget to try wine, for some reasons i don't really understand i have far more better results using wine than cedega running counter strike source (same graphic engine) and i just dumped cedega now because wine works better.

Are you using steam to start the game ?

---

### Post by xopher on 2007-03-26
For me, wine worked a lot better than Cedega. I was amazed how much better when I first tried it :)

No graphical glitches for me with wine (0.9.31), when I saw checkered boxes instead of textures, crashes etc, with cedega a while back..

---

### Post by zasf on 2007-03-26
> **pay said:**
> Is this a problem with the ati drivers?

I have a ATI X700 and play with cs under linux regularly, it works even better than windows.

---

### Post by pay on 2007-03-27
> **frodon said:**
> Don't forget to try wine, for some reasons i don't really understand i have far more better results using wine than cedega running counter strike source (same graphic engine) and i just dumped cedega now because wine works better.

Are you using steam to start the game ?Is it possible to start the game without steam?

I think that I will try it through wine again and then I might be able to dump Windows. Thanks for all your help.

---

### Post by frodon on 2007-03-27
I think that now steam is mandatory unfortunatly, for wine you will find all the instructions here :
[http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528)

BTW, i asked you if you use steam because steam allows you to pass some extra options to launch the game like the "-gl" option which make the game use opengl rendering and often solve the kind of problems you're issuing.

---

### Post by pay on 2007-03-27
> **frodon said:**
> I think that now steam is mandatory unfortunatly, for wine you will find all the instructions here :
[http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528)

BTW, i asked you if you use steam because steam allows you to pass some extra options to launch the game like the "-gl" option which make the game use opengl rendering and often solve the kind of problems you're issuing.I didn't know that Half Life 2 used openGL (did you mean wine steam.exe -gl?). I'll have to try it tomorrow. Thanks for your help.

---

### Post by frodon on 2007-03-27
> **pay said:**
> I didn't know that Half Life 2 used openGL (did you mean wine steam.exe -gl?). I'll have to try it tomorrow. Thanks for your help.It don't by default but you can force it to use opengl, it's possible with CS:source so it should be as well with HL2 which use the same graphic engine.
About the -gl option i mean to add it within the steam interface, this screenshot will tell you more :
[http://ubuntuforums.org/attachment.php?attachmentid=22955&d=1168763517](http://ubuntuforums.org/attachment.php?attachmentid=22955&d=1168763517)

---

### Post by pay on 2007-03-27
If you are using openGL, then why would you need to specify directX level 8 as per your screenshot?

---

### Post by frodon on 2007-03-27
Good question but my knowledge don't allow me to answer, i just don't know, i guess the directx level is to specify the level of effects that will be available.

---

### Post by Brynster on 2007-03-28
if you use the -pg flag to force opengl mode you can set directx emulation to any of dx7, 8,9 by using the command dxlevel 70, 80, 90 resepectivily

---

### Post by pay on 2007-03-28
> **Brynster said:**
> if you use the -pg flag to force opengl mode you can set directx emulation to any of dx7, 8,9 by using the command dxlevel 70, 80, 90 resepectivilySo are you saying the game thinks it is using directX when it is really using openGL?:confused:

---

### Post by Brynster on 2007-03-29
basically. 

Its uses directx to map everything out and draw the polygons for the game, but then passes the info to openGL to render the image when the -gl flag is used. (not -pg as my typo implied)

SO its kinda using a combo of both. Or at least thats what i think is happening still a little new to this myself

---

### Post by Breepee on 2007-03-29
> **Brynster said:**
> basically. 

Its uses directx to map everything out and draw the polygons for the game, but then passes the info to openGL to render the image when the -gl flag is used. (not -pg as my typo implied)

SO its kinda using a combo of both. Or at least thats what i think is happening still a little new to this myself

So, where do I set the dxlevel? Ingame with the tilde or also in de commandline along with -gl?

---

### Post by frodon on 2007-03-29
Yes along with -gl option, "-dxlevel 80" for directx 8.0 "-dxlevel 90" for directx 9.0 and so on.

---

### Post by zuzuzzzip on 2007-08-02
even with -dxlevel 90 and -gl, I get crappy lighting and textures...

I use
-console -novid -gl -dxlevel 90 -width 1280 -height 1024 -heapsize 1024000

I get a good picture when it says it's loading, wants it's loaded it gets ugly (pixel shader turned off)
see screenshot.

hmm ok, it works now but laggy when enabling pixelshader! great graphics now...
see 2nd screenshot

(posting it anyway if ppl could get some help out of this :))

---

