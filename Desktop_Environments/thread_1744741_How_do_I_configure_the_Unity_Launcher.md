---
title: "How do I configure the Unity Launcher"
date: 2011-04-30
forum: Desktop Environments
---

### Post by rtobyr on 2011-04-30
I've already Googled this without success.

I'm not going to join the throngs of people who are complaining about Unity. The thing is this: Everyone hates change. Sometimes change is good, and sometimes change is bad. In the long run, it leads to better things as people learn from both success and mistakes.

The thing is though, I can't figure out how to configure the launcher. I'd like to resize it, move it to different edges of the screen, and if possible make it behave a bit more like Mac's Dock. I will say that IMO, there is one important feature that's missing from the launcher: Right-clickitty goodness for setting properties & adding/removing stuff.

To get back on my soap box, I don't think that folks ought to be posting stuff like: "I just installed 11.04 ten minutes ago, and Unity sucks!" You just said that you've only had a few minutes of experience with it. Don't jump to conclusions.

---

### Post by sikander3786 on 2011-04-30
Hope this would help you.

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

Also, take a look here.

[http://ubuntu4beginners.blogspot.com/search/label/Unity](http://ubuntu4beginners.blogspot.com/search/label/Unity)

---

### Post by otherethe on 2011-04-30
> **rtobyr said:**
> I've already Googled this without success.

I'm not going to join the throngs of people who are complaining about Unity. The thing is this: Everyone hates change. Sometimes change is good, and sometimes change is bad. In the long run, it leads to better things as people learn from both success and mistakes.

The thing is though, I can't figure out how to configure the launcher. I'd like to resize it, move it to different edges of the screen, and if possible make it behave a bit more like Mac's Dock. I will say that IMO, there is one important feature that's missing from the launcher: Right-clickitty goodness for setting properties & adding/removing stuff.

To get back on my soap box, I don't think that folks ought to be posting stuff like: "I just installed 11.04 ten minutes ago, and Unity sucks!" You just said that you've only had a few minutes of experience with it. Don't jump to conclusions.

You have to do it from the ever other app tho has very tiny cant hardly see scroll bars and the arrow buttons only show up once you mouse over it then it'll if you dont have it installed yall need to, only thing you can really do how ever is resize the icons

---

### Post by Rubi1200 on 2011-04-30
Here is another guide for Unity:
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by Wiebelhaus on 2011-04-30
If some people think that Unity sucks , they obviously haven't tried gnome shell lol anyway , thanks for the links! Cheers.

---

### Post by rtobyr on 2011-04-30
Thank you all for the guides & tutorials. Still, I haven't been able to figure out how to move the launcher. I prefer ANY edge instead of left. Right would be best, but any other edge will be better than left. My eyes naturally drift to the left while I'm working, and it's distracting. If it could be on the right, then it would be less annoying. Help?

---

### Post by Krytarik on 2011-04-30
> **rtobyr said:**
> Thank you all for the guides & tutorials. Still, I haven't been able to figure out how to move the launcher. I prefer ANY edge instead of left. Right would be best, but any other edge will be better than left. My eyes naturally drift to the left while I'm working, and it's distracting. If it could be on the right, then it would be less annoying. Help?
Currently, there is apparently no way to move the launcher at all. But speaking out of my own recent experience with AWN, it's really the most ergonomic to have the launcher/dock at the left edge, at least if you are right-handed. Try it for a while, I, too, thought at first I would like it more to have it at the right edge, but that didn't turn out to be the best place. One major reason is that if you set launcher/dock to autohide, and then move your mouse pointer over to the scrollbar of a maximized window, which are there, too, you will very often unintentionally unhide the launcher/dock, and *that* becomes really annoying after a few times. So, again, just try it for a while.

That is just my personal experience, I don't need to convince someone here, imo it's ergonomically and practically the best place for that. And I do believe that Canonical and the Gnome team (Gnome Shell) did think about that thoroughly, and came to the same conclusion. Although it would of course be better if one could move it to whereever one wants, and the lack of that feature imo doesn't make really sense, technically.

Greetings.

---

### Post by sikander3786 on 2011-04-30
And might be, the overlay scrollbars have do something with that missing feature i.e, change location of the Launcher. It would be annoying as mentioned by **Krytarik** above.

---

### Post by mc4man on 2011-04-30
> **sikander3786 said:**
> And might be, the overlay scrollbars have do something with that missing feature i.e, change location of the Launcher.
You can't change to launcher location because it wasn't part of the design for natty

It may become an option in the o release, it may not. I'd expect 11.10 to be superior in many ways, unless there are hardware concerns I'd consider natty to be a throwaway release, at least as far as the unity shell

---

### Post by hreichgott on 2011-04-30
I'd really like to be able to move the launcher buttons. Or just get them to hide themselves unless I ask for them to pop out. (If I go to System Settings -> Launcher and Menus, it looks like I can set an option for the buttons to become visible when the mouse "pushes" the left side of the screen, or when the user clicks on the top left corner of the screen. Either would be very useful... except the buttons never become INvisible, so what is the point of providing options for what action makes them visible?)

The reason, for me, is not just dislike of change. To work efficiently on writing projects, I need to be able to look at two word processor windows, or sometimes a word processor and a pdf viewer, side by side at the same time. 1366x768 resolution was an important factor in shopping for computers. Now after an upgrade, I discover that a bunch of my precious screen width is now gone and I cannot get it back.

I feel the same way about workspaces btw. Possibly useful feature, but not if it cuts into left-right screen availability.

---

### Post by hreichgott on 2011-04-30
Well, I found out how to hide the launcher, at least.
Goes to show you can't always find stuff by googling... sometimes the official help pages are better /:)

Here are some instructions on howto configure the Unity launcher
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

I used the gconf solution:
run gconf-editor, navigate to apps -> compiz-1 -> plugins -> unityshell -> screen0 -> options
change launcher_hide_mode to 1

There is an option called launcher_reveal_edge that looks like you should be able to use it to control whether the launcher is on the left or right or what. Unfortunately, options other than Left seem to stop the launcher from appearing altogether.

---

### Post by petteriIII on 2011-05-01
By the way, it operates. But it operates little differently you think; the launcher appears allways on the same place. Normally it appears also when mousepointer goes near left ege - but when you set the value to be Right it does not. Not a good solution, but helps anyway.

---

