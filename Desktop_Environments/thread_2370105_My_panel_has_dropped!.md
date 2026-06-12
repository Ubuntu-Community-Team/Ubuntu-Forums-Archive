---
title: "My panel has dropped!"
date: 2017-08-30
forum: Desktop Environments
---

### Post by makem2 on 2017-08-30
I am using an XFCE desktop with the panel at the top. The panel is not locked and it is not transparent.

I was surprised to notice today that for no apparent reason, the panel has moved down from the top of the screen by about half its width.

If I move a window up to the top of the screen it goes under the panel to the top of the screen with the panel across the top of the window. I am able to 'grab' the top of the window and move it.

If I open VLC media player to full screen it also goes under the panel, but, it does not go beyond the panel. This means I cannot resize the window or close it as those controls are hidden behind the panel.

I have tried moving the panel via its preferences and it moves vertically but cannot be dragged anywhere. It is as if the panel had 'forgotten' the top extremity of the screen.

I hope the description I give provides enough to suggest how this has occurred and its cure.

EDIT: Changing the screen resolution has no effect on the panel position.

Found a web page which said the icons at each end of the panel moved inwards and revealed invisible 'handles' when 'unlock' was chosen. I never select lock so these handles have always been there but invisible! I was able to move the bar using those handles!

Why are they invisible?

---

### Post by ClickXT on 2017-08-30
Interesting indeed. Have you tried resetting the panel to default?

*pkill xfconfd; rm -rf ~/.config/xfce4/panel ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml; xfec4-panel*
^This would stop you from having to logout, and not nuke other potentially useful settings in ~/.config/xfce4

or

The directory where Xfce stores the configurations of the panel is:
*/home/user/.config/xfce4/panel/*
Just erasing it and logging out and in will restore the defaults configurations that your distro ships in.

---

### Post by #&amp;thj^% on 2017-08-30
> **makem2 said:**
> I am using an XFCE desktop with the panel at the top. The panel is not locked and it is not transparent.

I was surprised to notice today that for no apparent reason, the panel has moved down from the top of the screen by about half its width.

If I move a window up to the top of the screen it goes under the panel to the top of the screen with the panel across the top of the window. I am able to 'grab' the top of the window and move it.

If I open VLC media player to full screen it also goes under the panel, but, it does not go beyond the panel. This means I cannot resize the window or close it as those controls are hidden behind the panel.

I have tried moving the panel via its preferences and it moves vertically but cannot be dragged anywhere. It is as if the panel had 'forgotten' the top extremity of the screen.

I hope the description I give provides enough to suggest how this has occurred and its cure.

EDIT: Changing the screen resolution has no effect on the panel position.

What happens if you open the terminal and run:
```
killall xfce4-panel
```
Followed with:
```
xfce4-panel & disown
```
Also did you copy a old home diectory to this install?
Ninj'ed by ClickXT :)

---

### Post by makem2 on 2017-08-30
Sorry, I didn't see the replies before I edited the original post as follows:

[COLOR=#000000]Found a web page which said the icons at each end of the panel moved inwards and revealed invisible 'handles' when 'unlock' was chosen. I never select lock so these handles have always been there but invisible! I was able to move the bar using those handles![/COLOR]

[COLOR=#000000]Why are they invisible?

[/COLOR]I have marked the post as solved.

---

