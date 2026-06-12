---
title: "How does the screensaver dims the screen before it would start?"
date: 2010-03-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ddiddo on 2010-03-28
I am using Ubuntu 9.10 and the "Blank Screen" screen saver. Before the screen saver starts it gradually dims the screen and it does it very well, much better compared to the gksu dimming. I like this capability and I want to take advantage of it. May anybody give me a hint at how this is done? A tool (programme) that may set the dimming level would be really helpful or just a hint at what I should look for in the Internet.

---

### Post by ddiddo on 2010-03-28
What I have found:
Most likely it is a result of the XF86VidModeSetGammaRamp function call. xcalib looks like a tool that can be used to alter gamma ramps but it behaves really strange - brightness cannot be decreased at all and the contrast cannot be increased if once decreased. For example:

Every time you execute:

[COLOR=Blue]xcalib -contrast 90 -alter[/COLOR]

the contrast will decrease and cannot be increased back unless [COLOR=Blue]xcalib -c -alter[/COLOR] is executed to clear the changes.

Similar with:

[COLOR=Blue]xcalib -brightness 10 -alter

[/COLOR][COLOR=Black]It always increases the brightness and the only way to return it to normal is to clear all changes.

Does anybody know a way to just decrease the brightness? I am not in the mood to dig in the code of xcalib.
[/COLOR]

---

