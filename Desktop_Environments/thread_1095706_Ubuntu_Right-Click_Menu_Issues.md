---
title: "Ubuntu Right-Click Menu Issues"
date: 2009-03-14
forum: Desktop Environments
---

### Post by Halfbrazilian on 2009-03-14
I don't know what happened just before it started but my right click menus are acting weird. If I click the right mouse button, the menu comes out and acts as if I immediately left clicked. Because the mouse it over the first entry of the menu when the menu comes up, the top entry of the list gets executed. The only way to access the other parts of the menu is to hold the right click button down and then release it over the desired option. This causes the option to be executed and new menu to appear at the new position of the cursor. I don't know why this happened but it is getting annoying FAST. Thanks for your time.

---

### Post by compnut41 on 2009-03-14
It may be your graphics conflicting. (Enabling certain Compiz fusion effects caused my computer to crash.) Right click on the desktop (I know bear with me) and get to the change desktop background item at the bottom. Click the Effects tab. I think it is on the far right. Try to dummy down your graphics a bit from there. It might just change things.

---

### Post by ugm6hr on 2009-03-14
This is a known bug in Firefox 3.

Lots of bug reports about it.

I use the Firegestures Firefox addon to resolve it.

---

### Post by Flake Remix on 2009-08-02
I experience the same problem but in gnome terminal. I do right click and whatever first menu item is being run. Any workaround on that?

---

### Post by irw on 2010-02-01
I am also getting this problem - anywhere in the system, not just Firefox.

Currently running 9.10; fancy graphics turned off (but seems to make no difference)

---

### Post by benmandude on 2010-02-02
I'm having the same issue. Right clicking is very tough. If I leave my mouse completely still, and right click it works and then I'm able to use the menu. However even the slightest movement while I'm right clicking and the menu either disappears or selects the item where the pointer is. I really wish I could find a cure for this. It makes things very difficult.

---

### Post by irw on 2010-02-03
Although another thing to note on my laptop, is that the touchpad buttons work fine, as do the trackpoint buttons (I have a thinkpad).
It is only the separate USB mouse that has this problem ...

---

### Post by benmarvin on 2010-04-11
Anyone have a fix for this? It's happening to my dad and he's driving me nuts with questions. Could it just be a hardware issue?

---

### Post by completely new on 2010-04-21
I have the same problem, mostly when I'm browsing folders if I right click on a file or empty space.

---

### Post by winxpuser on 2010-06-16
I am also having this same issue and not just in firefox but system wide. Has the problem been identified yet and better yet has a fix been created this issue is extremely annoying to say the least.

---

### Post by Szise on 2010-06-29
This solution worked for me at least for the moment, don't need to restart the PC, disabled and enabled "Use nautilus to draw desktop" (because was enabled by default). You can find "gtweakui" in Synaptic.  [http://ubuntuforums.org/showpost.php?p=1435048&postcount=5](http://ubuntuforums.org/showpost.php?p=1435048&postcount=5)

---

### Post by nerform on 2010-11-05
I got the same problem (system wide) on ubuntu 10.10

---

### Post by sirtales on 2010-12-13
The gtweakui trick didn't work for me.
I'm using Ubuntu 10.10

---

### Post by drz4007 on 2011-01-20
Me too (system wide). The gTweak didn't help. It all started unexpectedly and i cannot figure out why... (Ubuntu 10.10). Any progress?

---

### Post by drz4007 on 2011-01-20
Me too (system wide). The gTweak didn't help. It all started unexpectedly and i cannot figure out why... (Ubuntu 10.10). Any progress?

---

### Post by drz4007 on 2011-01-20
Me too (system wide). The gTweak didn't help. It all started unexpectedly and i cannot figure out why... (Ubuntu 10.10). Any progress?

---

### Post by drz4007 on 2011-01-20
Me too (system wide). The gTweak didn't help. It all started unexpectedly and i cannot figure out why... (Ubuntu 10.10). Any progress?

---

### Post by drz4007 on 2011-01-20
Me too (system wide). The gTweak didn't help. It all started unexpectedly and i cannot figure out why... (Ubuntu 10.10). Any progress?

---

### Post by fishyboy on 2011-02-17
Do you use a left-handed mouse? I ask because I have this problem, and I used to get around it by changing my mouse to be right-handed and then back again. I don't know why that worked.

Recently my workaround hasn't been working. Although the problem doesn't happen when my mouse is in right-handed mode. It's starting to annoy me.

---

### Post by khoma on 2011-02-18
Have the exact problem. Driving me crazy :/

---

### Post by fishyboy on 2011-02-21
After trying lots of seemingly random things, I found that disabling the Compiz "Mouse Polling Position" option helped.

See [http://ubuntuforums.org/showthread.php?t=1306508]("http://ubuntuforums.org/showthread.php?t=1306508")

I have still reproduced the problem since, but only a couple of times. I suppose that disabling Compiz altogether would also work.

Edit: update...

Drat. The problem returned after a while. Using Metacity instead of Compiz seems to help, but isn't a perfect solution. Running that program mentioned above to do with Nautilus also helps, but again the right-click returns eventually. I'm now using the xfce desktop environment instead (not Xubuntu) and that's working OK, although it includes some additional stuff that I don't really want. But at least I can right-click things.

Another thing. Starting Nautilus from within xfce causes the right-click problem to return, so I'd say the problem is to do with Nautilus, and probably not to do with Compiz.

---

### Post by sharq1 on 2011-03-16
Is there going to be fix for this?

---

### Post by surfdoc on 2011-03-23
I had this problem too, but only with chrome. When I read about issues with gesturing and firefox, I tried disabling gesturing in chrome - and it worked! 

PS. You can test if it's the button malfunctioning by running xev.

---

### Post by fishyboy on 2011-03-29
> **surfdoc said:**
> ... PS. You can test if it's the button malfunctioning by running xev.

I gave xev a try, and it kind of confirmed what I've been seeing.

When the mouse is in right-handed mode:
[LIST=1]
[*]Holding down the right mouse button produces one ButtonPress event.
[*]Releasing the right mouse button produces one BottonRelease event.
[*]Holding down the left mouse button produces many ButtonPress and ButtonRelease events in quick succession.
[/LIST]

When the mouse is in left-handed mode exactly the same occurs, and I think that is causing the problem. While the left mouse button is depressed, multiple button press and release events occur. These cause the context menu to be opened and the first item clicked. This continues while the button is held down.

Unfortunately I still don't know how to fix it.

---

### Post by fishyboy on 2011-03-30
> **fishyboy said:**
> I gave xev a try...

Following on from before, I tried using xev from within xfce, and also from Puppy Linux v5. There was no difference in the xev output.

Then I repeated all of the above with a different mouse, and this time the click events did not repeat for any button. This suggests it's probably a hardware problem, or maybe a driver problem - I don't know at what level xev works.

For what it's worth, I use a trackball - a logitech marble mouse. I don't know whether that's significant. The mouse that worked was a regular optical mouse (also logitech). I have another logitech marble mouse at work, so I will test that soon to see whether it gives the same problems.

---

### Post by owyn on 2011-04-01
I have the same problem with disappearing context menus. Sometimes it works a charm, other times I have to try right clicking several times before I can get the menu to stay up so I can select the option I want.

The problem is global, i.e. independent of any specific application.

Using Ubuntu 10.04 fully updated.

---

### Post by fishyboy on 2011-04-01
Right then, the good news is my mouse works now and I think I know what fixed it. The bad news is I'm not convinced my fix will help many people, but here it is...

My previous tests suggested that my mouse problem was a hardware problem, since xev shown it was independent of desktop environment and (Linux) operating system.

Therefore I decided to take apart my mouse - actually a trackball - using a screwdriver. I actually failed at this, because even when unscrewed I couldn't open up the mouse without forcing it (and I didn't want to risk breaking it until I'd tested my other identical mouse at work). 

So instead I gave the mouse a jolly good shake in the hope that maybe some dirt trapped inside might become dislodged, or something like that. Yes, that's the level of straw-grabbing I had resorted to. But it worked!

That's it. If xev reports repeated clicks while a mouse button is depressed, but other mice work OK, then try cleaning your mouse on the inside. It might not work, but it's worth a try.

---

### Post by fury94 on 2011-04-24
I have this bug too and it's driving me nuts.

Hardware: a simple Microsoft optical USB mouse.
OS: Lubuntu 10.10 (so it's using LXDE, OpenBox, PCManFM).

It is system wide. The only reason why it happens more in chromium than in firefox, according to me, is because the context menu in firefox pops a few pixels more to the bottom-right of the click ; thus, this is less prone to a mouse move to the right during the mousebuttonpress/mousebuttonrelease operation.

Anyone with more information on this? Let's kill that real turn-off.

---

### Post by earshot on 2011-05-09
Changing the desktop settings with Ubuntu tweaks fixed the problem for me. I changed several settings so I don't know which one did the trick. Could be Compiz menu effects.

---

### Post by kidknapp on 2011-06-29
This is rough, I know, but your sure bet is to go into Compiz Settings and click on the bottom left on 'Preferences'. Of the four buttons you can press 'reset to defaults'. Sadly you will have to start over with compiz but this gets you back to square one so you can figure out what plugin is doing it. You'll have to enable all the basic plugins like gnome, opengl, window decoration, move window, resize window, etc...:(

---

### Post by kidknapp on 2011-06-29
> **kidknapp said:**
> This is rough, I know, but your sure bet is to go into Compiz Settings and click on the bottom left on 'Preferences'. Of the four buttons you can press 'reset to defaults'. Sadly you will have to start over with compiz but this gets you back to square one so you can figure out what plugin is doing it. You'll have to enable all the basic plugins like gnome, opengl, window decoration, move window, resize window, etc...:(

For me its something about the rotate cube plugin...

---

### Post by kidknapp on 2011-06-29
> **kidknapp said:**
> For me its something about the rotate cube plugin...

It doesn't like when I set Initiate to button 3. This worked in previous distros(pre-natty) but I guess I'll be using ctrl-alt-button1 now...

---

### Post by glide on 2011-07-13
I have the same problem without compiz activated and driving me quite nut too.
I think Ubuntu devs should position the contextual menus at least 5 or 10 pixels away from the cursor.

---

### Post by ojow on 2011-08-09
Very annoying :( Tried a few compiz settings, no effect...

---

### Post by libiamo on 2011-08-16
I too have this problem system wide. The only moment it really bothers me is when I try to delete a bookmark in firefox. In Windows, I used to right click on that bookmark and then choose "delete". But in my Ubuntu 11.04, a right click on the bookmark opens that website just as a left click would do.

---

### Post by user-friendly on 2011-11-14
I appear to have fixed this problem on my system (so far) by disabling KDE/QT event loop in CompizConfig Settings in Natty Narwhal 11.04 :KS

---

### Post by Crownvic on 2012-01-26
I had this problem too and solve it by changing the theme. Right click the desktop > change desktop background and chose Theme. Ambiance (the standard) and Radiance are the only two themes that work for me. 

Hope this helps. When you test which themes work for you, remember to try a right click from all four corners as the problem only occurs from certain directions with some of the themes.

---

### Post by predato on 2012-07-25
The same problem here. I think I have to give up Gnome for KDE.

---

