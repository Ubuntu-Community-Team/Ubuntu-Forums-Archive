---
title: "[Unity] -- Dodge focus windows and launcher transparency not working..."
date: 2011-05-01
forum: Desktop Environments
---

### Post by Entyrion on 2011-05-01
I've recently upgraded to 11.04 and I've been tinkering with Unity and CCSM to try to get back all the cool old eye candy I used to have back in 10.10. Unfortunately I'm stuck on two separate problems: 

1. The Compiz dodge effect when changing focus between windows only works occasionally, but not every time. Most of the time when I click between overlapping windows, there is no effect at all :( (Note that I HAVE been successful in enabling other Compiz settings like cube desktop and window open/close animations.)

2. When I tweak the launcher transparency or launcher icon size options in the Unity Plugin section of CCSM, there is no effect, even when I relog.

Screenshots of my current settings for both issues are attached.

Thanks to anyone who can offer some help for one or both of these issues!

---

### Post by Entyrion on 2011-05-01
As a follow up to my original post, I was able to find a solution to the panel transparency issue (problem #2 above).

I found an old forum thread from back in 2008 at [http://ubuntuforums.org/showthread.php?t=708744](http://ubuntuforums.org/showthread.php?t=708744) with a similar question to my own. There, they discuss a feature that allows you to use the "Opacity, Brightness, and Saturation" menu in CCSM to selectively modify the opacity of UI elements. 

At [http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching) I found specific instructions to use the terminal to identify the specific "title=" values for the components of the Unity UI.

Combining the info from these two places, I was able to keep the top panel at 100% opaque and set the launcher/side panel at an independent opacity value of my choice.

I hope this helps someone who might have a similar question in the future, I certainly learned something after all my work and I'm glad I was able to figure out a solution!

In regards to the first problem I mentioned about the focus window dodge feature, I'm still having a bit of trouble so I'd appreciate any help. I'm not sure if I'm just misunderstanding what the dodge feature is supposed to do or what... when one window overlaps another, when click from one to another the dodge effect kicks in about 1/2 the time. Am I just misunderstanding the definition of "shifting focus" between windows or what?

/noob

Thanks again for any help!

---

### Post by Krytarik on 2011-05-02
You understand correctly, the "Focus Animation" feature *should* indeed apply an effect on the window upon becoming the focus, no matter how. I know it because it works sometimes this way, but sometimes not, exactly like you are experiencing it, and I'm running Lucid 10.04. So, it seems those feature is just running not that stable.

Greetings.

---

### Post by iliketurtles2000 on 2011-06-29
I have the same problem with the launcher transparency/opacity...

I have searched for answers for hours now and yours was the best so far... but I still haven't gotten it working.

Check out my screenshot... I have the value substantially lowered and I feel like I have the correct item specified  (ie launcher dock). But, the launcher is still dark as ever!

Does the CCSM opacity setting just not work? Is there a workaround?

Help, please!

---

