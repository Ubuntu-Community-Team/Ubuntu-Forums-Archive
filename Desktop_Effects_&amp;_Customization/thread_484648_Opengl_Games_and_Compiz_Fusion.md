---
title: "Opengl Games and Compiz Fusion"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by cwood06 on 2007-06-26
My problem is really not that bad just an annoyance. I want to play WoW it works and everything is great is just that i can run it full screen.

Im running aiglx/Compiz-Fusion, when its up and running my opengl app just gets stuck behind the top bar. Im not sure if there is a way to fix this. I know the redirect thing didnt work for me from the compiz manager. So if anyone knows any hacks or workarounds id appreciate it! :-)

---

### Post by cwood06 on 2007-06-26
-BumP-

Still havent figured it out yet... been trying to figure out how to use the gnome fullscreen toggle

---

### Post by cwood06 on 2007-06-26
i tryed to make a script that would replace metacity then launch WoW then reload compiz. Does anyone know a better way just to pause compiz then launch the game then start compiz again?

Or if there is a way to make it so I can make the game fullscreen w/o doing a script would be great too.

---

### Post by steveneddy on 2007-06-26
Why don't you make a launcher that sits in the upper tool bar with the command

```
metacity --replace
```

I have launchers that start compiz-fission AND metacity. 

Metacity starts up by default and if I want the eye candy, I push the button. Easy.

---

### Post by cwood06 on 2007-06-26
I sopose that could work I also see on the compiz-fusion forum that there are window rules but im not sure how to work on them ill try waht you said and make launchers for em

---

### Post by steveneddy on 2007-06-26
It just makes it easier, and it oly takes about four seconds per launcher.

And I fell like you have more control if you can turn it on or off with a push of a button.

One for compiz-fission, one for metacity.

I also made one for emerald because sometimes it doesn't want to launch when I launch fission.

---

### Post by cwood06 on 2007-06-27
Well iv been trying to set it up for the Window Rules im On the compiz-fusion site right now and got a topic on there but so far i havnt got much further, I could set it up for that way i just want ti to work w/o going that way is all.

---

### Post by karlhm76 on 2007-06-29
I have a similar problem, my problem is that my openGL apps go fullscreen, and they don't get "caught" behind the top bar, but they are transparent so you can see the desktop and the top bar through them. Fullscreen videos are fine, but my screensaver is also transparent.

I've tried removing the opacity setting in the options, but it just puts it back. Also, if I try and add an opacity setting for specific apps, the new string turns into a funny square with 0, 1, 0, 1 in it, and so does the original line. No changes are applied whatsoever.

Anyone have any solutions for this?

---

### Post by cwood06 on 2007-06-29
check the compiz-fusion forum. Iv seen posts like yours on thier

---

### Post by dexter on 2007-06-30
> **karlhm76 said:**
> I have a similar problem, my problem is that my openGL apps go fullscreen, and they don't get "caught" behind the top bar, but they are transparent so you can see the desktop and the top bar through them. Fullscreen videos are fine, but my screensaver is also transparent.

I've tried removing the opacity setting in the options, but it just puts it back. Also, if I try and add an opacity setting for specific apps, the new string turns into a funny square with 0, 1, 0, 1 in it, and so does the original line. No changes are applied whatsoever.

Anyone have any solutions for this?

Had the same problem, go to System, Preferences, CompizConfig Settings Manager. Go to general options, tab Opacity Settings and remove "Unknown" from the list.

---

### Post by karlhm76 on 2007-06-30
ok, that seemed to work to fix the opacity problem. The string turned into the funny little symbol, but it applied the settings. Thanks for that. 

But then I got the problem with the visible top bar.. arrg. :(

So I removed the top bar ;)

Problem solved!

However this still doesn't explain why it decides to do that most annoying thing.

---

