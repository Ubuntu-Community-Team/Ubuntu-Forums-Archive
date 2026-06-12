---
title: "Close button placement at top right corner problem"
date: 2008-06-28
forum: Desktop Environments
---

### Post by Ag Engineer on 2008-06-28
I need to be able to move the mouse to the far top-right corner of the screen and click to close the window.  Currently I have to backtrack a couple pixels down and to the left in order to actually click on the close button.

Also for some reason, when I go to the very top of the screen, the mouse cursor changes to the cursor for resizing a window even though it isn't possible since the window is maximized.  This makes no sense, and I want it to stop doing that, because sometimes I like to move my cursor to the very top of the screen and double click to resize the window.  Currently I have to yet again backtrack a couple pixels.

Can somebody please tell me how to fix these very annoying usability issues?  I'm using Ubuntu 8.04 and I have looked through what seems like every possible option.

I found with Emerald that I can move the close button to the top right corner to fix the first one, but that doesn't fix the second one.
That is also a poor workaround, because some of the themes look terrible with the close button up that high.

Proper behavior should be that when the window is maximized, clicking the mouse button in the corner should close the window even if the mouse cursor isn't explicitly over the close button.

---

### Post by puthut on 2009-03-07
Would you follow the article from 
[http://www.howtogeek.com/howto/ubuntu/put-closemaximizeminimize-buttons-on-the-left-in-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/put-closemaximizeminimize-buttons-on-the-left-in-ubuntu/")

Perhaps its can solve your problem.

---

### Post by -AB- on 2010-07-24
I have the same problem, after some time of waiting I upgraded to 10.04 and now I can't close my windows properly.

I put the Close button to the top right. But as the threadstarter said, the behavior has changed - clicking in the screen corner won't close the window any more. To be able to "unmaximize" a window by double clicking the window bar, you have to move the mouse 4px down, otherwise the double click will not do anything.

I use the clearlooks theme. Is this a theme-related issue, so, can this by fixed by using a different/fixed theme? Can this be solved in some other way?

Unfortunately there is no "downgrade"-button, so I'm (more or less) stuck now with this version....

//edit:
Just tried all pre-installed themes - the "New Wave" theme fixes the "Close" issue. The "unmaximize" problem still exists, but is less critical for me... Well function beats form, still I'd like to use the clearlooks theme again.

---

### Post by vek on 2010-07-28
I would like to know how to fix this also - I run without a panel on the top of the screen, and it was super useful to be able to just move the mouse to the top right and let the screen corner catch it, then click.

Its a well known principle of Human Interface Design that the corners of the screen (and the edges) are much, much easier to click on, so it surprises me a lot that the interface would be getting worse instead of better in this regard.  

For example, on ms-windows, even on themes that have the close button quite far to the right, they still allow you to click on the top right anyway - because the ui designers know this principle.

If someone knows what controls this, I Could take a look at the code or something.  I'm guessing metacity, theme controlled though, which means the designers of this current theme were just not aware of this basic principle of interface design.  [http://en.wikipedia.org/wiki/Fitts%27s_law](http://en.wikipedia.org/wiki/Fitts%27s_law)

Note:  This problem exists **also** for people who use the close button on the left hand side of the screen - its not about what side of the screen the buttons are on, but about how you can't click on them without being very precise.

Edit:  Found KIND of a workaround:

[http://gnome-look.org/content/show.php?content=103732](http://gnome-look.org/content/show.php?content=103732) - there's a DEB on there that seems to work (the PPA does not).  It lets you add a window title and the close / maximize / minimize buttons to a gnome panel (which you create and put at the top of your screen).  It also allows you to hide the original ones on maximized windows.

This is actually the best of both worlds, since it means I can put the title of the window to the right, then put the usual clock / application launcher / etc to the left, and so on (and eventually the unified menus, I'm guessing).  And yes, the close button is clickable right to the very edge of the screen and the window title (which is another panel applet) is double clickable.

It takes some getting used to, and is questionable on dual monitors.  But it might be worth a try for you:
[http://i29.tinypic.com/25p7frd.png](http://i29.tinypic.com/25p7frd.png)

---

### Post by dashesy on 2010-10-29
I hated Google when they started forcing the LHS amazing bar, without an easy option to change it the way I like. I also hate Windows 7 over-shiny taskbar, and that I cannot do anything about it.
If MAC is selling good it does not mean everyone should copy their look, if I want MAC I buy one.
I love Ubuntu and hope it does not happen here again!

No matter how developers think an idea is great, people hate them and it drives them away instead of them "get used to it"

---

### Post by OliverN on 2010-11-07
> **vek said:**
> [http://gnome-look.org/content/show.php?content=103732](http://gnome-look.org/content/show.php?content=103732) - there's a DEB on there that seems to work (the PPA does not).  It lets you add a window title and the close / maximize / minimize buttons to a gnome panel (which you create and put at the top of your screen).  It also allows you to hide the original ones on maximized windows.

That's very interesting, and certainly worth a try. One problem I can see with this is that it forces a top panel on the user, which I personally dislike.

I thought of setting a keyboard shortcut to close the window in focus when moving to the top right and clicking mouse button 1. This would work better for people who dislike the top panel, but it has another problem: It always closes the focused window, and not necessarily the window you clicked (it'll close an unmaximized focused window in the foreground before closing an unfocused maximized window in the background).

If anyone thinks of other workarounds, pretty please post them.

Also, I'm thinking maybe you could have a script that would grab the window title of a clicked window (which would automatically be the one you were trying to close) and then input that in a command to close it..? The script should run when moving the cursor to the top right and clicking mouse button 1. The last part is easily done through compiz, so does anyone know how the script should look or if it's possible at all? The only problem I see with this is accidentally clicking the top right.

---

