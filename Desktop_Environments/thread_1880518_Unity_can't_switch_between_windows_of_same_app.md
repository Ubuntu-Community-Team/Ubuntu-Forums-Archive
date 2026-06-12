---
title: "Unity: can't switch between windows of same app"
date: 2011-11-13
forum: Desktop Environments
---

### Post by parsim on 2011-11-13
I swear, I have searched.

Since upgrading to 11.10, I can't easily keyboard-navigate between windows of the same application (e.g. multiple OpenOffice windows). The only way is to:
[LIST=1]
[*]Alt-TAB to open application switcher
[*]Alt-left to focus on current application
[*]Alt-down to expand application into multiple windows
[*]Alt-left + alt-right as necessary to navigate to correct window
[/LIST]

(Step #4 is incredibly error-prone, incidentally, since the windows are tiled vertically, but I have to use left and right to navigate between them.)

This is astonishingly slow when all I want to do is rapidly flick back and forth between two windows. There must be SOME method, but I have searched and dug through compiz-settings and I cannot find it.

While searching for an answer, I have seen people recommend using Alt+`, but this does nothing.

---

### Post by typhoon_tip on 2011-11-13
There are two easy ways:

- Bring on the ALT+TAB task switcher, and stay on the program that has two windows for a while, it will show you automatically the options on the switcher, you can use up down to select (slow way)

- Use the launcher: if you click once on the program with multiple windows that is minimized, it will open the last one that was open. If you click one more time, it will show on screen all windows with the scale plugin of compiz (enabled by default), you can then select the window in two clicks (very fast way)

Hope it helps.

---

### Post by parsim on 2011-11-13
Thanks for the reply!
> **typhoon_tip said:**
> - Bring on the ALT+TAB task switcher, and stay on the program that has two windows for a while, it will show you automatically the options on the switcher, you can use up down to select (slow way)
I think this is the way I described (except that "up down" actually closes and opens display of the app's individual windows--I need "left right" to navigate between them).

> - Use the launcher: if you click once on the program with multiple windows that is minimized, it will open the last one that was open. If you click one more time, it will show on screen all windows with the scale plugin of compiz (enabled by default), you can then select the window in two clicks (very fast way)

Right, but that isn't very fast: I need to take a hand off the keyboard, seize the mouse, and click two things. I switch back and forth between two or three documents in OpenOffice Writer very frequently, often checking things mid-sentence, and having to switch to the mouse every time I do that is really slow.

I don't believe Unity would have removed this ability; I just need to find where it's gone!

---

### Post by typhoon_tip on 2011-11-13
> **parsim said:**
> Right, but that isn't very fast: I need to take a hand off the keyboard, seize the mouse, and click two things. I switch back and forth between two or three documents in OpenOffice Writer very frequently, often checking things mid-sentence, and having to switch to the mouse every time I do that is really slow.

I don't believe Unity would have removed this ability; I just need to find where it's gone!

Actually alt+tab rapidly without even bringing on the task switcher on screen works for me with multiple windows, the same way it did before.

---

### Post by parsim on 2011-11-13
That's definitely not the case here. Alt-TAB skips over any windows belonging to the same application, unless I specifically drill down into them via the method described in my first post.

---

### Post by parsim on 2011-11-13
Aha! Apparently this behavior is caused by having "Bias alt-tab sorting to prefer windows on the current viewport" checked in CompizConfig Settings Manager -> Switcher. If I disable that, Alt-TAB no longer ignores windows belonging to the same app.

But that causes Alt-TAB to whisk me away to other workspaces, which I dislike, so I have disabled the switcher and enabled "Static Application Switcher" in CCSM, which makes Alt-TAB act like it used to.

---

### Post by typhoon_tip on 2011-11-13
Oh yes ! As I remember, it was possible to enable back the "almost" default switcher in compiz. Tried that but still prefer to stick to the new one, maybe helpful to report some bug to the community after all.

---

### Post by markbl on 2011-11-13
Both unity and gnome-shell work the same as Mac OS (and probably Windows for all I know?). I.e. Alt-tab to switch between applications and then alt-<key above tab> to switch between windows of the same application.

---

### Post by parsim on 2011-11-13
> **markbl said:**
> Alt-tab to switch between applications and then alt-<key above tab> to switch between windows of the same application.

I've seen this advice before, but alt-<key above tab> does not do anything on my machine, and I can't figure out where the option might be to enable it.

---

### Post by mc4man on 2011-11-13
I can get to 'step 4' a bit quicker it seems but the whole left, right arrow deal is terrible. Either arrow key should be 'circular'

It does seem to work that way if I keep opening that window group, usually on the 3rd try or so. Before that hitting the L or R arrow one time to many exits the window picker.

(there has to be a bug there just on the inconsistency

---

### Post by jlindbergh on 2011-11-15
> **parsim said:**
> I've seen this advice before, but alt-<key above tab> does not do anything on my machine, and I can't figure out where the option might be to enable it.

I found your thread being annoyed by this very same behaviour... 
On my 11.10 machine, Alt-§ works as markbl suggests, but I can't find that shortcut assigned anywhere!
I looked in CCSM->Ubuntu Unity Plugin and in System Settings->Keyboard->Shortcuts->Navigation.
In CCSM the option doesn't even exist, and under Keyboard shortcuts I can see that "Switch applications" is set to Alt+Tab, but the row below that - ie "Switch windows of an application" - is set to "Disabled".

---

### Post by manzdagratiano on 2011-11-15
Whoa whoa whoa! I hurriedly cruised through the posts - but maybe I can elaborate on markbl's advice?

The ALT + <key above TAB> by itself does nothing at all. Now, press ALT + TAB, and you will see all the different applications cycle through when pressing TAB repeatedly... now suppose one of them is Firefox, for which you have two windows open, while still holding the ALT key, now press the key above TAB, and you will be able to cycle between these two windows while repeatedly pressing that key - the ALT key has to be held all the while, for both TAB and while switching to the key above TAB.

I believe this is the  default behavior - I did not make any changes in ccsm to enable this, but it seems like the switch to gnome3 has brought this welcome change along, just as in gnome-shell.

---

### Post by mc4man on 2011-11-15
> **manzdagratiano said:**
> Whoa whoa whoa! I hurriedly cruised through the posts - but maybe I can elaborate on markbl's advice?

The ALT + <key above TAB> by itself does nothing at all. Now, press ALT + TAB, and you will see all the different applications cycle through when pressing TAB repeatedly... now suppose one of them is Firefox, for which you have two windows open, while still holding the ALT key, now press the key above TAB, and you will be able to cycle between these two windows while repeatedly pressing that key - the ALT key has to be held all the while, for both TAB and while switching to the key above TAB.

I believe this is the  default behavior - I did not make any changes in ccsm to enable this, but it seems like the switch to gnome3 has brought this welcome change along, just as in gnome-shell.

That's certainly better than using the arrow key(s) to navigate between windows of the same window group.

At least here Alt+[COLOR="Red"]`[/COLOR] (<key above TAB>) does directly open the switcher on current window group with focus

---

### Post by parsim on 2011-11-15
> **manzdagratiano said:**
> Whoa whoa whoa! I hurriedly cruised through the posts - but maybe I can elaborate on markbl's advice?

The ALT + <key above TAB> by itself does nothing at all. Now, press ALT + TAB, and you will see all the different applications cycle through when pressing TAB repeatedly... now suppose one of them is Firefox, for which you have two windows open, while still holding the ALT key, now press the key above TAB, and you will be able to cycle between these two windows while repeatedly pressing that key - the ALT key has to be held all the while, for both TAB and while switching to the key above TAB.

Thanks -- I did not realize that.

However, it still doesn't do anything. I'm doing this:
[list=1][*]Open two windows in Firefox
[*]Hold down ALT
[*]Tap TAB. The switcher appears. Focus is highlighting the most recently used other application, which right now happens to be OpenOffice. The Firefox icon is just to the left of this, with two arrows indicating it has two windows.
[*]Tap ` (the key above TAB). Nothing happens. I am still holding down ALT from Step #2.
[*]Tap TAB until the switcher's focus reaches Firefox, then quickly tap `. Nothing happens.
[*]Wait a few seconds. The switcher automatically expands Firefox into two windows.
[*]Tap `. Nothing happens. I am still holding down ALT from Step #2. I can navigate only with the arrow keys.[/list]

---

### Post by parsim on 2011-11-15
> **jlindbergh said:**
> I found your thread being annoyed by this very same behaviour... 
On my 11.10 machine, Alt-§ works as markbl suggests, but I can't find that shortcut assigned anywhere!
I looked in CCSM->Ubuntu Unity Plugin and in System Settings->Keyboard->Shortcuts->Navigation.
In CCSM the option doesn't even exist, and under Keyboard shortcuts I can see that "Switch applications" is set to Alt+Tab, but the row below that - ie "Switch windows of an application" - is set to "Disabled".

Hmm, so it's out there somewhere!! I wonder where.

I tried setting a keyboard shortcut for that "Switch windows of an application" line in "Keyboard" -> Navigation, just in case, but it had no effect.

---

### Post by parsim on 2011-11-15
Actually, from my research, it seems that Alt+"key above TAB" ***is*** supposed to do something by itself.

But everyone just says it works, they don't say where the option is to enable it. :(

---

### Post by manzdagratiano on 2011-11-15
Yeah now that I am back in Ubuntu, I see that ALT + <key above TAB> opens up the cycler for windows of the current application by itself. I did not however have to do anything to enable this.

When I first saw gnome-shell, I thought I had to use the arrow keys or the mouse to switch between windows of the same app and I thought "dang! This is torture!", and then I read the gnome tips page and realized this was good - works pretty well so far in gnome-shell and Unity and I don't miss gnome2 at all!

My Keyboard -> Navigation has "Switch windows of an application" set to disabled, so I am surprised myself! It is not in gnome-tweak-tool either, since that requires gnome-shell to be installed, which I don't have on Ubuntu.

---

### Post by nosmokenofire on 2011-11-18
I used to find it useful in the launcher to be able to click on an app icon with multiple windows open to be able to get a spread of all the windows. For some reason this no longer works. Neither does super+d to get back to the desktop, something else I used to find handy.

I'm using Ubuntu 11.10

Many thanks for any help

---

### Post by stinkeye on 2011-11-18
> I used to find it useful in the launcher to be able to click on an app icon with multiple windows open to be able to get a spread of all the windows.
Check the scale plugin is enabled.


> Neither does super+d to get back to the desktop, something else I used to find handy.
Set the shortcut key in 
ccsm generel > general options > keybindings

---

### Post by nosmokenofire on 2011-11-23
Thank you,

this sorted it out.

---

### Post by parsim on 2012-05-02
I upgraded to 12.04, hoping this problem would be fixed, but no.

But I have found something odd about my keyboard layout. It looks like this:

[IMG]http://i.imgur.com/ls6dm.png[/IMG]

Notice: no tilde key!

Now, this key does exist, sitting right above Tab, and it works when I press it. See: `~`~`~`~```~~~

But ALT+` does nothing.

Could this be related? Do other people with US layout keyboards have a tilde key showing in Keyboard Layout -> Preview?

My keyboard is a Microsoft Natural Ergonomic Keyboard 4000.

---

### Post by rafe101 on 2012-07-04
The scale plugin is enabled (I even enabled the extra scale plugin), but I still can't get to a second window from the launcher.

---

### Post by kansasnoob on 2012-07-04
I get this type of effect a lot with Firefox. Sometimes if I download something and rather than closing Downloads I just click on the maximized Firefox window I can't for the life of me get "downlaods" to come up again until I close Firefox and restart it.

Same way with the forum "manage attachments" app. If I'm not careful it ends up playing hide-n-seek requiring that I restart X :(

---

### Post by kansasnoob on 2012-07-04
Oh, forgot to add, this only seems to happen if I'm working with a maximized app :)

---

### Post by funicorn on 2012-07-21
I think the best way to switch among windows of the same app is to take advantage of the mouse wheel. The way to do this is mouse hovering on the app icon in the unity panel, and scrolling the mouse wheel would either switch between windows or trigger the switching widget.

---

### Post by harun3d on 2012-09-14
There are two sort of people in this thread:
1. people who think that the problem is "not being able to switch between windows of same app"
           =>there is a solution for this. don't worry. 
                               a. alt tab +wait  
                               b. alt tab + down key
                               c. alt tab + ` key
             That is not the problem. the problem is that it takes to much actions to do that.

2. people who think that the problem is "being able to switch between windows of same app BUT NOT IN AN USER       FRIENDLY WAY" (with less actions as possible) (this is hard to understand for people from first category;doing one   thing in one step or ten steps has no difference between each other for them)

The second one is the discussion here however the title gives wrong idea because you cannot tell everything in the title.
=>no solution untill sept 2012 ubuntu 12

---

### Post by parsim on 2012-09-18
> **harun3d said:**
> There are two sort of people in this thread:
1. people who think that the problem is "not being able to switch between windows of same app"
           =>there is a solution for this. don't worry. 
                               a. alt tab +wait  
                               b. alt tab + down key
                               c. alt tab + ` key
             That is not the problem. the problem is that it takes to much actions to do that.

2. people who think that the problem is "being able to switch between windows of same app BUT NOT IN AN USER       FRIENDLY WAY" (with less actions as possible) (this is hard to understand for people from first category;doing one   thing in one step or ten steps has no difference between each other for them)

The second one is the discussion here however the title gives wrong idea because you cannot tell everything in the title.
=>no solution untill sept 2012 ubuntu 12

Yes, I wish I could edit the title now. When I started the thread, I didn't know about Alt+`, which is supposed to be the command for quickly switching between windows of the same app.

If I could edit the title, I would make it: **Alt+` does nothing**.

This is still a problem on 12.04 and it is the single most infuriating thing about Unbutu for me. It's an absolute productivity killer.

---

### Post by parsim on 2012-09-18
AHHHH fixed!!

I got Alt+` to work by following [the instructions on this page](http://askubuntu.com/questions/175696/why-isnt-the-alt-shortcut-working-on-my-international-keyboard).

Quick answer: run 'ccsm', open the "Unity Plugin", open the "Switcher" tab, click the button next to "Key to flip through windows in the switcher" that is probably labeled "Disabled", click "Enable", click "Grab key combination", hit Alt+`.

---

