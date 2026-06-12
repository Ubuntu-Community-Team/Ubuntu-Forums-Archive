---
title: "Unity, is it possible to..."
date: 2011-11-27
forum: Desktop Environments
---

### Post by ECPCLINUX on 2011-11-27
Hi, I was wondering if there is a way to have the Unity Launcher on the left show (Show/Hide) below the back and forward arrows on Firefox?  It can sometimes becomes very distracting.  Currently, I'm trying to remember to use the mouse back and forward buttons. However, after years of being trained like a monkey :( it does not feel natural nor are the buttons on my mouse easy for me to reach with my thumb. I'm trying to avoid to make the Unity Launcher permanent, I tried it and did not like it.  Any help would be appreciated.

---

### Post by kurt18947 on 2011-11-27
I'm not sure how it would work for you but I moved the Firefox forward/back arrows to the right of the address bar.  It took a little while to adapt but now I prefer arrows to the right even though I seldom use Unity, preferring Gnome 3 shell.  I sometimes use the mouse to speed scrolling which is on the right as well.  To move the arrows you just click View -> Toolbars -> Customize and drag.
[ATTACH]208067[/ATTACH]

---

### Post by TDK24 on 2011-11-27
To help make the Unity launcer easier to work with i first placed it across the bottom of the screen and then i configured the time out for 2 or 3 seconds. By doing this the unity launcer does not appear unless i mouse over the bottom of my screen for 2 or 3 seconds. You can configure both of these settings and more in the compiz config manager --> unity plugin. 
 
hope that helps

---

### Post by Copper Bezel on 2011-11-27
I usually suggest changing the Launcher Reveal Behavior from "Left" to "Upper Left," also in the Unity plugin in CompizConfig. Moving the cursor to the upper left corner of the screen then reveals the launcher, but hitting the left side of the screen doesn't. It really comes down to which of the possible configurations works best for you, of course. = )

---

### Post by lovinglinux on 2011-11-27
You could also use [FireGestures](https://addons.mozilla.org/en-US/firefox/addon/firegestures/) to make your browsing experience better and avoid using the forward/backward buttons.

---

### Post by mc4man on 2011-11-27
If still an issue - 
In 11.10 setting the edge reveal to top left only no longer works as before - it requires a bit of a special cursor move.

Move cursor to top left corner coming into it from slightly to the right or below the actual corner.
Then pulling the cursor down into the launcher area along left edge will reveal. Works ok once you get the hang of it.

A better solution, as somewhat mentioned, to inadvertent launcher reveal is to either set edge reveal to bottom left corner only or just leave on the default of left edge reveal & raise the delay
The default delay is 150 ms, I think you'll find that 500 - 600 ms is more than enough &  actually is quite a long time in terms of using your cursor near the left edge.

If you have compizconfig-settings-manager installed then you can go directly to the unity settings by Alt+F2, then using this command
```
about:config
```

Or just set directly  thru gconf - Ex 500 ms
```
gconftool -s -t integer /apps/compiz-1/plugins/unityshell/screen0/options/launcher_reveal_edge_timeout 500
```

(I just leave it on the left edge reveal & use a 500 ms delay

---

### Post by ECPCLINUX on 2011-11-27
Wow, everyone thank you so much. The response from the community has been great. I've pretty much tried all the suggestion.  Changing the launcher to top left (Thanks Copper Bezel) seemed like it did not work till I read mc4man's post. To date so far I've delayed the launcher as suggested by TDK24, to 250 and move the Launcher to top left. I have the pointer gesture nailed down.  That seems to work well so far.  I downloaded FireGeststures as recommended by lovinglinux but have not tried to configure it yet. However, because of lovinglinux suggestion I right click on the screen by mistake and realized that there is a "back" on the drop down menu.  So I will use those things in combination and see how it goes for me.  

While messing with Unity and researching I came across this:

[http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher](http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher)

I was thinking that might also be a solution if I'm not totally happy or just feeling Frisky and want to mess with it.  If all else fails I will add the back/forward buttons on Firefox to the right as suggested by kurt18947.

Once more thank you all for your help. I believe this issue is solved :) However, more great ideas are always welcome.

---

### Post by MG&amp;TL on 2011-11-27
Incidentally, you can get a similiar gesture interface for chromium (any lubuntu users!), it's under spanner menu, extension, get more extension, search for gestures, first hit.

---

### Post by ECPCLINUX on 2011-11-28
Thank you MG&TL for the tip.  Specially since I use Chromium as my secondary browser it's good to know.  Things are working well so far with what I've mentioned earlier.  I'm going to close this thread as solved.;)

---

