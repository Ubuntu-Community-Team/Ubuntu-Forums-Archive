---
title: "I cannot get scrollbars in xterm"
date: 2013-04-19
forum: Desktop Environments
---

### Post by PeterTaps on 2013-04-19
Folks,

I am running Ubuntu 12.04 with OpenBox.

According to the link [http://beforewisdom.com/blog/tech/xterm-with-a-scrollbar/](http://beforewisdom.com/blog/tech/xterm-with-a-scrollbar/), I have added the following lines to my .Xresource followed by "xrdb -merge .Xresource."

> [COLOR=#373737][FONT=Consolas]! Set up scrollbars - get them, get them on the right side, and be[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]! able to scroll them with the right,left, or middle mouse button[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]xterm*ScrollBar: on[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]*XTerm*scrollBar: true[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]xterm*rightScrollBar: true[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]xterm*multiScroll: on[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]xterm*jumpScroll: on[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas] [/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]xterm*scrollbar.Translations: #override \n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :StartScroll(Continous) MoveThumb() NotifyThumb()\n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :MoveThumb() NotifyThumb() \n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :StartScroll(Continous) MoveThumb() NotifyThumb()\n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :MoveThumb() NotifyThumb() \n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :StartScroll(Continous) MoveThumb() NotifyThumb()\n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :MoveThumb() NotifyThumb() \n\[/FONT][/COLOR]
[COLOR=#373737][FONT=Consolas]  :NotifyScroll(Proportional) EndScroll()


However, when I spawn a new terminal window, I still do not see any scrollbars.

I am wondering if there is something that I missed.

Thank you in advance for your help.

Regards,
Peter[/FONT][/COLOR]

---

