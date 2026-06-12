---
title: "Ubuntu 14.04 LTS - Alt-tab: switch between apps (not windows)"
date: 2014-12-07
forum: Desktop Environments
---

### Post by Giango42 on 2014-12-07
Hi, I'm a new Ubuntu user. 
I was wondering if there is a way to use Alt-Tab to switch *only* between applications, not windows. I find that switching between windows, for my workflow style, is unuseful and confusing. I just want to switch between apps, and find all the window configuration of *that app* just like I left it. Like OS-X. 
I tried CompizConfig, but it won't do what I need. Is there any other way, plug-in, program, hack, etc. to make the switching shortcut behave like I wish?
Thanks in advance for any kind of help, 
and please forgive my bad english.
G.

---

### Post by mc4man on 2014-12-07
The alt-tab switcher is only for open apps that are running  in a window.
Not sure what you're looking for then..

---

### Post by grahammechanical on 2014-12-07
Pressing Alt+Tab in a workspace will reveal a panel showing icons for all applications opened in that workspace. Then if we hold Alt and tap Tab we cycle through the opened appplications.

Pressing Ctrl+Alt+Tab will reveal a panel showing icons for all open applications in all workspaces. Again, if we hold Ctrl+Alt and tap Tab we cycle through the icons of all opened applications.

Holding down the Super key (usually has a flying windows icon) we will get a screen overlay that lists all the keyboard shortcuts for Unity such as the two I have mentioned. Try pressing Alt+dead grave key and see what happens.

Another one to try is Super+W and then use the arrow keys to cycle through the application windows. And there is Shift+Super+W. 

It really is amazing what the developers have achieved with keyboard shortcuts in Unity.

Regards.

---

### Post by vasa1 on 2014-12-07
I think OP's scenario is this:
7 Firefox windows open
5 Writer windows open
6 File manager windows open

Then, assuming the application currently in focus is a Firefox window, OP doesn't want to tab through the remaining six to get to the (last used) Writer or (last used) File manager window. OP wants to go straight to the (last used) Writer or File manager window.

---

### Post by deadflowr on 2014-12-08
> **vasa1 said:**
> I think OP's scenario is this:
7 Firefox windows open
5 Writer windows open
6 File manager windows open

Then, assuming the application currently in focus is a Firefox window, OP doesn't want to tab through the remaining six to get to the (last used) Writer or (last used) File manager window. OP wants to go straight to the (last used) Writer or File manager window.

?
alt+tab only shows one app at a time, regardless of how many windows for that app are open.
If you have 10 firefox windows open, alt+tab will only show one, until you toggle the up/down/left/right arrows to reveal all the windows open of the app.

So in the above scenario, if you have several windows for firefox and writer open, then alt+tab will only have two apps in it. To access the extra windows you use the arrows and then swaddle through those.
And the last window for which ever one you want will be the default selection if you don't want to toggle through a bunch of them.

Or at least that's the scenario I've seen, forever...

The OP might look at the alt+tab sister keybindings "alt+~", if that is more to the liking.

Or even fore go the alt+tab, and set another switcher all together like ring switcher or whatever else you can choose(there are a couple)
in ccsm.

I don't know how helpful that is, as, like above posts, I don't understand what the OP is meaning...

---

### Post by dry crust on 2014-12-08
As a rough guide, you shouldn't be using Alt-Tab to move between running applications, this can lead to Repetative Strain Injury type problems with your hands. I would recommend you download a desktop that allows you to see the con-currently running applications and to select the next one with your mouse. As far as I can tell the intent of Unity is mostly meant for use with just one application at a time, which is why I think you change to another type of desktop. I use Ubuntu-Gnome, but there are other desktops as well, such as LXDE and Lubuntu, I think Kubuntu would also work, all of which should allow you to select the application you want to use by using the mouse. 
As I said, Alt-Tab should be a "last resort" method of changing between apps, not your first choice. I learnt the hard way. Look after your hands. 
I would recommend you look throught the different desktops available and chose one that looks like it lets you see the con-currently running applications and allows you to select the appropriate one with the mouse. Only use Alt-Tab if you absolutely must.

---

### Post by deadflowr on 2014-12-08
> **dry crust said:**
> As a rough guide, you shouldn't be using Alt-Tab to move between running applications, this can lead to Repetative Strain Injury type problems with your hands. I would recommend you download a desktop that allows you to see the con-currently running applications and to select the next one with your mouse. As far as I can tell the intent of Unity is mostly meant for use with just one application at a time, which is why I think you change to another type of desktop. I use Ubuntu-Gnome, but there are other desktops as well, such as LXDE and Lubuntu, I think Kubuntu would also work, all of which should allow you to select the application you want to use by using the mouse. 
As I said, Alt-Tab should be a "last resort" method of changing between apps, not your first choice. I learnt the hard way. Look after your hands. 
I would recommend you look throught the different desktops available and chose one that looks like it lets you see the con-currently running applications and allows you to select the appropriate one with the mouse. Only use Alt-Tab if you absolutely must.
 You don't need to use alt+tab on unity. You can switch between running apps by clicking on the apps icon in the launcher.
No need to switch if that is the concern. 
Only downside is it'll only allows you to switch between multiple windows of a single app in a single workspace. So if you have multiple gnome-terminal's open across multiple workspace, it'll only open the one you are currently on, if any are opened in that workspace. But upside, you can switch different apps across multiple workspaces.
Anyway, alt+tab is no different than having to shift + someletter to capitalize.
And as I posted, you can avoid it altogether and enable a different switcher. You can set whatever keybinds you want for it, as well.

Unity is not a one app at a time desktop. Far from it.
It's just designed differently.

---

### Post by mc4man on 2014-12-08
A lot of conjecture without any op reply so in that spirit - 
I never use the switcher but maybe it's that the default for alt+tab, tab, tab, ect. with multiple windows of one or more apps is a timed  switch to a spead on that app when pausing on the icon in the switcher
The timing is non-adjustable & pretty quick, seems slightly less than 1 sec. If you disable the timed live preview then only apps are shown/switched, choosing  one with multiple windows opens last  focused window of that app on top

(- here just use spread in it's various implementations (mouse & key bindings), fast, efficient & not unhealthy. 
The spread on window group on multiple workspaces has been broken for a couple of years but is do-able thru a keybinding/command/dbus setup

---

### Post by dry crust on 2014-12-08
Re "Anyway, alt+tab is no different than having to shift + someletter to capitalize."
Yes, you are correct, the correct way to Alt-Tab is to use two hands, just like you do when you capitalise a letter, but how many people do that? Is the two handed process what Ubuntu - Unity says you should do? I made the mistake of doing Alt-Tab with one hand. I did try to mimic how you would do it with two hands and it does seem you could do it with two hands, but you would need to make sure you are using the correct fingers (and not your thumb) to do it otherwise you could easily end up with damaged hands. 
I'm sorry, I have tried Unity from time to time, but I'm afraid it just doesn't work for me. I have no idea what the apps icon is, nor the launcher. Why not just have the con-currently running apps on display in a mostly unused part of the screen, e.g. the top or bottom of the screen, and then select the next one with the mouse?

---

### Post by vasa1 on 2014-12-08
> **deadflowr said:**
> ?
alt+tab only shows one app at a time, regardless of how many windows for that app are open.
...

Or at least that's the scenario I've seen, forever...

...
This alt-tab has three mousepad windows open :)

---

### Post by deadflowr on 2014-12-08
> **vasa1 said:**
> This alt-tab has three mousepad windows open :)

Unity or other?

---

### Post by vasa1 on 2014-12-08
> **deadflowr said:**
> Unity or other?
I haven't used Unity since 12.10. This alt-tab is with Openbox. I don't know what the other flavors do though I used Xubuntu for a while.

---

### Post by vasa1 on 2014-12-08
I use the procedure described [here]("http://ubuntuforums.org/showthread.php?t=2180156&p=12814007#post12814007") to switch between my most common open apps. I think it should be flavor-independent.

---

### Post by deadflowr on 2014-12-08
> **dry crust said:**
> 
I'm sorry, I have tried Unity from time to time, but I'm afraid it just doesn't work for me. I have no idea what the apps icon is, nor the launcher. Why not just have the con-currently running apps on display in a mostly unused part of the screen, e.g. the top or bottom of the screen, and then select the next one with the mouse?
No need to apologize, the heart wants what the heart wants. If you don't like unity it is totally alright to say so. Though I find it does not help to say something that simply is not true as a reason not to use it. And the launcher does exactly what you suggest, it shows you the currently running apps the are open by using indicator arrows, which you can then toggle through from one app to another just by simply clicking on it. I really do not know how you do not know what the launcher is, it is the most prominent feature of unity's desktop; it's the side bar on the leftside of the screen, which can hold an ever-growing number of app(application) icons; if you add more than the screen can hold the bottom app icons squeeze down like an accordion, which you can then expand when mousing over the area they are in; it's an interesting feature that no other desktop has.

> **vasa1 said:**
> I haven't used Unity since 12.10. This alt-tab is with Openbox. I don't know what the other flavors do though I used Xubuntu for a while.
Yeah, I think most alt+tab options run their own design per DE, unity's design is definitely different from how openbox runs.

---

### Post by mc4man on 2014-12-08
Unity has it's own alt-tab switcher 
compiz has 2 alt-tab switcher plugins, (application switcher & static application switcher),  but neither is used in an ubuntu session & shouldn't be.
There are 2 other switchers in compiz that aren't alt-tab - ring & shift

---

### Post by Giango42 on 2014-12-08
First of all, thanks for the many answers to my question:-)
Than, I have to say that I didn't express exactly what I meant, due to my lack of confidence with english language and, second but most important, because when I wrote the post I was working with Pure Data.
Pure Data has a problem: for every window you open you have 1 app more in the alt-tab switcher. So, yes, I was wrong (and stressed by some hour of patching): Ubuntu usually let you see 1 icon for 1 app. The problem is a sort of bug of the Pure Data application, and I (and you) cannot do anything for it.

BUT.

Let's leave the world of Pure Data. In everyday life, using Ubuntu, when I switch app with "alt-tab", instead of viewing ALL the windows open in that app, I see only the last window used.
So, let's say: 
1) I open 2 windows of Nautilus, 
    - 1 for "Documents"
    - 1 for "Downloads" 
2) Then I open Firefox. 
3) Then I switch back to Nautilus 
4) I see ONLY the window "Download".

Why? Is there a way to see ALL the windows whitout doing any other step?
Thank you very much!
G.

EDIT: I don't know if I was clear: when switching to Nautilus I'd want to see all the open windows. In the example case: both "Documents" and "Downloads". If I have, let's say, 348 windows open, when I switch to that app, I want to see *all* the 348 windows in just one shot. Is it possible? Am I the only one who need something like this? Or, am I the only one who don't know to obtain a similar behaviour? Forgive me, I'm NOOB.

---

### Post by CantankRus on 2014-12-08
Applications with multiple windows are shown with small arrows to the left the same as in the launcher.
After a slight pause these windows will be previewed where you can cycle through them by
continuing to hold down alt and hitting TAB.
You can also use ccsm to turn off this behaviour and only display the multiple windows preview
when hitting the tilde (~) key above TAB.

---

### Post by Giango42 on 2014-12-08
@CantankRus

Thank you for the answer. I noted the little arrows, but I disabled the window preview because it "spawn" when I don't want it: maybe I'm switching app and while doing it I'm thinking about some decision to take, etc. - and suddenly this preview appear!, and, no, that's no something I'm comfortable with. 
I have to say that it is no a super-crucial problem: maybe I modeled my "habits" during years working on os-x, so getting used to Unity behaviors could be just a matter of time.

But. But *if* there is a way to switch app and find *all* the windows of that app arranged like I left them, well, if there is a way I would be grateful to anyone who should tell me the secret :-)

---

### Post by CantankRus on 2014-12-08
Have you considered using a workspace just for a particular application.
That way you only need to switch back to that workspace to find it as you left it.

---

### Post by Giango42 on 2014-12-08
[COLOR=#000000]@CantankRus


Yeah. For example using workspace, as you suggest, could be a solution. And I bet it could be a very good solution, so good to became a new habit. But it would be a new habit. So, if there is a way to make alt-tab behave like I'd want, I will be happy to continue working as I always did. Otherwise, I will learn to use workspaces. And maybe in 2-3 month I will find myself returning in the forum to tell everybody how much is awesome working with workspaces. :-)
[/COLOR]
Thank you,
G.

---

### Post by mc4man on 2014-12-08
> **Giango42 said:**
> 

EDIT: I don't know if I was clear: when switching to Nautilus I'd want to see all the open windows. In the example case: both "Documents" and "Downloads". If I have, let's say, 348 windows open, when I switch to that app, I want to see *all* the 348 windows in just one shot. Is it possible? Am I the only one who need something like this? Or, am I the only one who don't know to obtain a similar behaviour? Forgive me, I'm NOOB.
In either of those cases 'scale' (spread) does that. I'm not going to open hundreds of windows but it should show them all or all per app. 
The more window the smaller what you see 
(- now "see" may mean 2 different things here??
Example in screen of 20 nautilus windows (this case only pulling to spread nautilus windows
Scale can do only 1 app or all open app windows

(- also possible this is not at all what you want to "see"

---

### Post by Giango42 on 2014-12-08
eheh. yes. "see", I guess, means that. but I meant to see "as I left them". Not as a preview. And in just one shot :-)
I think that CantankRus suggestion of using workspaces is something that goes near what I want. And, becoming clear that there is no way to obtain what I want (at this time I think I should have found a solution) I'm sure that what Unity offer is comfortable enough to not let anyone complain until now, so I will get use to this new way of managing my windows and I'm sure it will be fine.
Thank you very much @mac4man
G.

---

### Post by Giango42 on 2014-12-08
Anyway. This.

[https://www.youtube.com/watch?v=Dm_s-hnc9P8&feature=youtu.be](https://www.youtube.com/watch?v=Dm_s-hnc9P8&feature=youtu.be)

---

### Post by mc4man on 2014-12-08
After a while one gets pretty set in their setup ect. so I don't offhand see any way to do that now in compiz as not something I need.

What it appears to be is you'd like a way to raise all open windows of a group at once. The current is to keep the stacking order & raise only 1 window at a time. (whether using alt-tab or scale, same thing). So if the target group is under others they'll stay that way other than the one picked.
A quick look doesn't suggest a way to do that if that's what you mean..

Pre unity (compiz < 0.9.x) I see there was this plugin that did have that option but it's likely not usable with current compiz - 
[http://wiki.compiz.org/Plugins/Group](http://wiki.compiz.org/Plugins/Group) under group options..

---

### Post by Giango42 on 2014-12-08
Yes! The chance of grouping windows could be nice. But if no ubuntu user feel the need of it, there must be a reason. So, I hope to get confident with workspaces (maybe creating some shortcut) enough to obtain a similar effect. 

Now, what I want to say is that receiving all these answers and attempts to help me and in so little time has been the better "welcome" I could have wished to get in this community (and hope to have it said in an understandable English  :) ). 
Thanks!

---

