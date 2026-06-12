---
title: "problem with gnome panels"
date: 2008-08-25
forum: Desktop Environments
---

### Post by crazyone on 2008-08-25
Hi i ahve a compaq 750us and i use ot be able to have 2 panels at the top of my screen on my old laptop taht was running linux but when i try to do it with this laptop. and then i log out after what ever amount of time it wont keep the order of the bars where the bar with menus is on top and the new panel is under taht. they keep fliping on every log in. any help on this would be great. thanks in advance

---

### Post by crazyone on 2008-08-25
anyone have this problem to cuase it is so odd.

---

### Post by Cammy on 2008-10-28
I might as well bump this because I'm having the same exact problem.  To make matters worse, when I launch apps the app comes up with the titlebar behind the upper panel.

Any suggestions?

---

### Post by hictio on 2008-10-29
> **crazyone said:**
> Hi i ahve a compaq 750us and i use ot be able to have 2 panels at the top of my screen on my old laptop taht was running linux but when i try to do it with this laptop. and then i log out after what ever amount of time it wont keep the order of the bars where the bar with menus is on top and the new panel is under taht. they keep fliping on every log in. any help on this would be great. thanks in advance

Sorry, I don't understand... You have 2 Gnome Panels, stacked, on the top of your screen, right?
And when you logout & login again, the 2 panels are flipped? That is, the one that you placed on top of the 2 Panels, is now on the bottom, beneath the one that, used to be below originally.

Is that so? Can you post a screenshot?

---

### Post by Cammy on 2008-10-29
> **hictio said:**
> Sorry, I don't understand... You have 2 Gnome Panels, stacked, on the top of your screen, right?
And when you logout & login again, the 2 panels are flipped? That is, the one that you placed on top of the 2 Panels, is now on the bottom, beneath the one that, used to be below originally.

For me this is correct.  I'll post a screenshot tonight when I get home from work.

---

### Post by Cammy on 2008-10-29
Ok, finally got the screen shots.

Here's how my panels are set up:
[IMG]http://i152.photobucket.com/albums/s171/rabidbeotch/before.png[/IMG]

Here's how they look after a reboot.  Noticed that the top panels have reversed their order.  This was never a problem in Feisty, but it is in Hardy.
[IMG]http://i152.photobucket.com/albums/s171/rabidbeotch/after.png[/IMG]

And here's what happens when I launch an app.  Notice how it's partially hidden behind the top panels.
[IMG]http://i152.photobucket.com/albums/s171/rabidbeotch/hidden.png[/IMG]

If anyone has any clue as to how to fix this, I'm all ears.

---

### Post by icodeme on 2008-10-29
Try to right click on the lower panel and click "Properties"
Set Orientation to Bottom:popcorn:

---

### Post by Cammy on 2008-10-29
> **icodeme said:**
> Try to right click on the lower panel and click "Properties"
Set Orientation to Bottom:popcorn:

But I don't want it on the bottom.  I want it on top, the way it is in the first pic.

And even when it's on the bottom (where it is now, until I solve this problem), the apps still get hidden under the top panel.

---

### Post by hictio on 2008-10-29
Thanks for the screenshot, I know, this is not what you want to hear, but, really, I have to ask, so...
Why do you setup the Panels like that? Do you use the second one, the one that should be on the bottom of the two, for only running a "Window List" applet?

---

### Post by icodeme on 2008-10-29
> **Cammy said:**
> But I don't want it on the bottom.  I want it on top, the way it is in the first pic.

And even when it's on the bottom (where it is now, until I solve this problem), the apps still get hidden under the top panel.

i hope this isn't a driver issue. I am experiencing a problem with my cursor being lost and until now, Im waiting for an update bout it.
Sorry bro got nothin' on this prob.:confused:

---

### Post by hictio on 2008-10-29
I just did a test on my box, with a setup like yours, with 2 Panel up there, and logout and login again, they did not change/ flip, nor they "block" the apps that I start...

The 3 things that I can think that are different than in your setup, so you can test those?
- My Panels were not transparent (they were the default grey of the Theme I'm using "Human Murrine"),
- The second panel, the one underneath the main one, only had the "Window List" applet.
- I dont run GDM, my box boots onto the CLI, and I start Gnome with the command 'startx', when I get out to Gnome, I go back to the CLI.
(not sure if you do this, but, I guess don't)

Anyways, at least there is something to test :D

(I still don't like having 2 Panels stacked like that, but now, I can say that I have tried :P :D )

---

### Post by Cammy on 2008-10-30
> **hictio said:**
> Thanks for the screenshot, I know, this is not what you want to hear, but, really, I have to ask, so...
Why do you setup the Panels like that? Do you use the second one, the one that should be on the bottom of the two, for only running a "Window List" applet?

I set the panels up that way because I want everything in one place.  I don't like looking up, then down, then up, then down, and it gets too crowded to stick everything on one panel.

It worked in 6.06.  It worked in 7.04.  It currently works on my laptop in 7.10.  It just doesn't work since I updated the 7.04 to 8.04.

So it seems that either:

1) There is something with Hardy that causes this, or
2) Something happened when I upgraded.

In my new install, I went with separate partitions for / and /home.  My 7.04 wasn't like that.  So when I installed 8.04 (on a new HD) I used a new username.  Then I copied my old /home/user directory onto the new machine from my old HD.  Then I logged out and back in under my previous name, and deleted the new user.

Maybe you can't copy stuff like that, but I didn't want to have to reinstall the world over again.


I think I'm going to try creating a new user, logging in as them,  stacking my panels, and seeing how that behaves.  Thanks for your other tips too.  I'll test those first.

---

### Post by hictio on 2008-10-30
> 
I set the panels up that way because I want everything in one place. I don't like looking up, then down, then up, then down, and it gets too crowded to stick everything on one panel.


Just a suggestion, as I don't like that either, but, also, I hate wasting screen real state with 2 Panels... Can you add what you are running on the second one (the one giving all this trouble) to the main one?
I do that, or at least, snuff the one on the bottom the minute I finish installing Ubuntu, because I hate it :D

---

### Post by XanTrax on 2008-10-30
All you need to do is right click both the panels, stacked how you want, and click on "lock" or whatever references to locking the bar.  This will keep them in the same place.  I can tell you dont have them locked because I can see the bar on the left that handles the resizing and stuff.

---

### Post by Cammy on 2008-10-30
> **hictio said:**
> Can you add what you are running on the second one (the one giving all this trouble) to the main one?
Well like I said, there's an awful lot of stuff to stuff onto the one panel, but if I can't fix this, I may have to do that.

I also need to figure out why apps show up with their title bar hidden under the top panel.


> **XanTrax said:**
> All you need to do is right click both the panels, stacked how you want, and click on "lock" or whatever references to locking the bar.  This will keep them in the same place.  I can tell you dont have them locked because I can see the bar on the left that handles the resizing and stuff.
That was the first thing I tried, and it doesn't work at all.  But after the reboot, it does successfully lock them in the wrong order, so that ends up being one more step I have to take to fix them.

I've even tried locking one but not the other.  Still no help.

---

### Post by mattgif on 2008-10-30
If you don't plan on changing your panels (or don't mind some extra hassle when you do), you can use the gconf-editor to put the panels into "lockdown," which prevents changes in a stronger way than the right-click lock does.  

This solved a problem I had a while ago of panels moving around.

Here's how:

1. In the run application (alt+F2), type 'gconf-editor' and hit Run

2. Go to: Apps > Panel > Global

3. Click the 'lock_down' box  

4. Restart gnome (ctrl+alt+backspace)

If this doesn't solve your problem, or you decide you want to change something after you've locked the panels down, simply go back to gconf-editor, remove the check mark, and restart gnome.

---

### Post by Cammy on 2008-10-30
Thanks matt. I just tried that, and it still doesn't work.  It was good info though, as although I had tried gconf-editor to lock the panels down, I wasn't aware of the global option.  Thanks.

I've also tried using system colors, but no luck there either.

For now I have everything stuffed into one panel.

As for the other problem, I think that's compiz-related, because when I switch to the Metacity Window manager, the problem doesn't occur.  I'll probably hit the compiz forums for help with that.

Thanks everyone.

---

### Post by Cammy on 2008-10-30
Ok, just FYI, I got the problem with the apps being behind the title bar solved.  It's a compiz plugin setting - place windows.  If that's enabled, the apps seem to appear properly.  I've found that the "cascade" setting works best for me.

---

