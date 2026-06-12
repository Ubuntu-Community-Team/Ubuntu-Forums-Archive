---
title: "[SOLVED] Fluxbox /apps not working"
date: 2008-02-10
forum: Desktop Environments
---

### Post by The Avatar of Time on 2008-02-10
Hello I am trying to configure ~/.fluxbox/apps as such:

[startup] (firefox)
[Dimensions] {857 1021}
[Position] {513 0}
[Shaded] {yes}
[end]

[startup] (thunderbird)
[Dimensions] {857 559}
[Position] {513 18}
[Shaded] {yes}
[end]

however this does absolutely nothing. I have checked in the ~/.fluxbox/init and it lists ~/.fluxbox/apps as the app directory. It might be worth mentioning that the apps file was completely empty before I added those things. 

I have tried right-clicking on the windows and using 'remember' but it does not do anything. I have also tried [app] (firefox) instead of [startup] (firefox) and then put a 'firefox &' in the startup file. That starts it up just fine but not with the position dimension or shading that I want. 

I had the same problem with Eterm but I got around that by using Eterm -g blahblah, which works just fine. -g doesn't seem to work on firefox or thunderbird though. Does anyone have any ideas as to why it is not accessing the /apps file? Or a nice workaround instead?

---

### Post by kerry_s on 2008-02-10
you need to do it outside the gui. it won't work while it's running. you can logout and use the failsafe terminal or ctrl+alt+f1->6 and kill the gui, then change the file. do you have mc, it makes it easy with mcedit, if not you can use nano or what ever your prefered terminal editor is.

---

### Post by cknight on 2008-02-10
try this instead of "firefox"
```
(name=gecko) (class=Firefox-bin)
```

---

### Post by The Avatar of Time on 2008-02-10
Thank you for the replies. Before I forget I should mention I am using fluxbox version 1.0.0 from the repositories (ubuntu, obviously). I tried both of your suggestions. Still nothing. 

Though I was curious, since I have already written in /apps should I delete it all and retype it once I leave the gui? I didn't I simply typed a letter and deleted it so that I could save the file again.  Is there something I must do to make fluxbox look in the apps file? It is listed in the ~/.fluxbox/init. 

However the apps file does not seem to do anything. Clicking remember on the windows should write to /apps right? The remeber does not right to the apps, and only works until I exit fluxbox. I generally use ctrl-alt-backspace but I have also tried the 'exit' in the fluxbox menu. I do not have a login manager would that matter? I am thinking of getting fluxbox source and compiling to see if that will help, but I would really rather not have too.

---

### Post by kerry_s on 2008-02-10
you might have somehow corrupted it, try deleting it, log out and back in so it can make a new 1. then try the right click save settings thing on the window.

---

### Post by The Avatar of Time on 2008-02-10
Well that worked like a charm. Looks like everything is good now. Thanks for the help, I don't know how much they are paying you but you deserve a raise :) By the way, how do the 'thanks' work?

---

### Post by kerry_s on 2008-02-10
lol, glad that worked.
you look like you need more, so here's 1 from me to you. :)

---

### Post by The Avatar of Time on 2008-02-11
Hmm, looks like I figured it out. Thanks for the thanks and whatnot.

---

