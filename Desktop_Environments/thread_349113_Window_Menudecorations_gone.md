---
title: "Window Menu/decorations gone"
date: 2007-01-29
forum: Desktop Environments
---

### Post by linuxpimp on 2007-01-29
Hi all

I upgraded to Edgy and now i cannot switch desktops, have no window menu (yje top border with the buttons to mimize etc. is gone).

Cannot alt tab windows.

What's missing?

Thanks

lp

---

### Post by ComplexNumber on 2007-01-29
> **linuxpimp said:**
> Hi all

I upgraded to Edgy and now i cannot switch desktops, have no window menu (yje top border with the buttons to mimize etc. is gone).

Cannot alt tab windows.

What's missing?

Thanks

lp
what happens when you try to switch desktops? 

go to the command line ad type in 'killall metacity'. that will solve it if its a glitch, but you haven't given much info to go on, so thats all i can suggest for now.

---

### Post by linuxpimp on 2007-01-30
Hi

There was not metacity process running.

Also, all the window decorations are gone, that whole top bar is gone. When looking at "them details" there is no longer a tab for "window decorations. See the screenshot. It seems that some software was un-installed, i just need to know what gives these properties to reinstall. This is the same for all themes. IN the screenshot you see how the windows have no decoration bar and cover the top panel. Nothing happens when i try change workspaces (not desktops, sorry) and right click does nothing.

What is interesting is if i open the preferences menu >> windows i get an error that their is no app associated with it.

Thanks

LP

---

### Post by linuxpimp on 2007-01-30
Problem solved. I had compiz as my window manager . Now i went ahead and installed beryl, wow amazing.

BUT i'm back to having ni top window panel...everything else works, but no panel...please assist

LP

---

### Post by nkkromhof on 2007-01-30
if by top window panel you mean the Gnome Panel, then try

"killall gnome-panel" in a terminal

If you mean you don't have each window's title bar, then right click the Beryl icon in the taskbar and check to see that Emerald is the Window Decorator, and try to reload it there.

Good luck!

---

### Post by joselin on 2007-01-30
Just type "metacity &" and this must solve your problem. Next time you restart you will have metacity running.

Regards.

---

### Post by ComplexNumber on 2007-01-30
[quote=linuxpimp]Problem solved. I had compiz as my window manager[/quote]
hmmm i'm not surprised. if you start compiz/beryl WHILST YOU HAVE SEVERAL APPLICATIONS RUNNING, those applications will be left without any window decoration because metacity has been effectively kiled. only applications started after you start compiz/beryl running will have window decs defined by compiz/beryl.

---

### Post by nkkromhof on 2007-01-30
> **ComplexNumber said:**
> hmmm i'm not surprised. if you start compiz/beryl WHILST YOU HAVE SEVERAL APPLICATIONS RUNNING, those applications will be left without any window decoration because metacity has been effectively kiled. only applications started after you start compiz/beryl running will have window decs defined by compiz/beryl.

I'm not sure I agree, but I may have misunderstood you.

---

### Post by ComplexNumber on 2007-01-30
> **nkkromhof said:**
> I'm not sure I agree, but I may have misunderstood you.
you've misunderstood, because thats what happens.

---

### Post by linuxpimp on 2007-01-30
Hi all

Thanks for taking the time to reply, here are my updates:

1) emerald is selected
2) metacity & tells me i already have a window manager running
3) Even new apps don't have the top border/panel/decoration

Thanks again

edited to add: it may be thet emerald is not loaded/running; when i open the emerald manger, i can choose/highlight themes but have no save/apply option..see screesnhot
lp

---

### Post by ComplexNumber on 2007-01-30
> **linuxpimp said:**
> Hi all

Thanks for taking the time to reply, here are my updates:

1) emerald is selected
2) metacity & tells me i already have a window manager running
3) Even new apps don't have the top border/panel/decoration

Thanks again

edited to add: it may be thet emerald is not loaded/running; when i open the emerald manger, i can choose/highlight themes but have no save/apply option..see screesnhot
lp
mine doesn't have a save button either. you're meant to double click on them to select them.

---

### Post by linuxpimp on 2007-01-30
> **ComplexNumber said:**
> mine doesn't have a save button either. you're meant to double click on them to select them.

Yup,  double click until i'm blue in the face and have a sprained forefinger, but no difference :-)

Thanks for taking the time to answer.

lp

---

### Post by ComplexNumber on 2007-01-30
> **linuxpimp said:**
> Yup,  double click until i'm blue in the face and have a sprained forefinger, but no difference :-)

Thanks for taking the time to answer.

lp
maybe its not installed. try some of the others.

---

### Post by linuxpimp on 2007-01-30
> **ComplexNumber said:**
> maybe its not installed. try some of the others.

Good advice, but BTDT, even retrieved some new ones.

lp

---

### Post by ComplexNumber on 2007-01-30
> but BTDT
whats BTDT?

---

### Post by linuxpimp on 2007-01-30
> **ComplexNumber said:**
> whats BTDT?


Sorry, Been There Done That :-)

---

### Post by ComplexNumber on 2007-01-30
just curious, but when you have beryl running, does it show the little red gemstone icon in the notification area on the panel?
also, when you right or left click on it, it brings up some options, right?

---

### Post by linuxpimp on 2007-01-30
> **ComplexNumber said:**
> just curious, but when you have beryl running, does it show the little red gemstone icon in the notification area on the panel?
also, when you right or left click on it, it brings up some options, right?

Yeah, it didn't as my notification area dissapeared during upgrade, but it;s there as you describe now.

lp

---

