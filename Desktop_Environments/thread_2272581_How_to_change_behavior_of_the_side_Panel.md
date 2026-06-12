---
title: "How to change behavior of the side Panel?"
date: 2015-04-07
forum: Desktop Environments
---

### Post by Potato_Rainbow on 2015-04-07
Hi.. I'm using Ubuntu 14.0.1 and I just bought a wacom tablet (which works perfectly)..

My only problem is that the side panel would not pop out only if I put my cursor to the side of the screen (i have to kinda put more pressure on the side or move top to bottom)..
       Sadly I am not able to do that with the Wacom pen..

**What I actually want:**My side panel to pop out when I put my cursor on the side of the screen..

[SIZE=1](hopefully you guys get the Idea :) )[/SIZE]

---

### Post by Frogs Hair on 2015-04-07
Have you turned up the reveal sensitivity under appearance>behavior?

---

### Post by Potato_Rainbow on 2015-04-08
Yes, but didn't help :(

---

### Post by deadflowr on 2015-04-08
I don't know what tweaks can be done with the wacom settings, but...
You should be able to do a little bit more nuanced tweaking to the edge sensitivity with the ccsm tool.(compizconfig-settings-manager)
--Fair warning, of course, not to go mucking about too much with this tool.

But if you install ccsm go to the unity plugin and open it.
Then go to Launchers sub tab section.
In here you should see setting to adjust the for things like Launcher edge responsiveness, rate of decay, reveal pressure.
See if adjusting those helps.


Note: these changes should be instantaneous.
When done only click on the Back button and then Close to exit the program.DO NOT muck about with other settings unless you feel you can afford to do so.
And do not, I repeat, do not uncheck anything unless you want to either have a busted desktop or you know what you are doing.

---

### Post by grahammechanical on 2015-04-08
> **What I actually want:**My side panel to pop out when I put my cursor on the side of the screen..

That is exactly how my Launcher behaves. System Settings>Appearance>Behaviour>Reveal Location. Either Left Side or Top Left Corner. Do you not have these options?

Regards

---

### Post by mc4man on 2015-04-09
The ccsm settings may be more effective than System Settings regarding reveal pressure. The default is a value of 20, absolute lowest allowed  value is 1. 
(could be it won't react well to pen at any setting but I'd try 1 which is virtually no pressure..

If wanting to set that directly then it's not an available gsetting but you can write it. - 
```
dconf write /org/compiz/profiles/unity/plugins/unityshell/reveal-pressure 1
```

---

