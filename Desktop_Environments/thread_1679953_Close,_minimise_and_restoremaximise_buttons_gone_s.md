---
title: "Close, minimise and restore/maximise buttons gone sometimes"
date: 2011-02-01
forum: Desktop Environments
---

### Post by cblnchat on 2011-02-01
The close, minimise and restore/maximise buttons are randomly gone!  Its kinda irritating,  it seems to consistently happen with Open Office word processor.  So is there anything i can do about this?

Thanks

---

### Post by mwong8888 on 2011-02-02
Can you show a screenshot?  Have you tried to restart compiz?

---

### Post by cblnchat on 2011-02-03
> **mwong8888 said:**
> Can you show a screenshot?  Have you tried to restart compiz?

Ill try to get a screenshot.  It doesnt happen very often.  But whats compiz?

---

### Post by spydeyrch on 2011-02-03
If you go into the software center, do a search for the compiz icon. Install that.

Once it is installed, find it in your applications menu. Start the actual service and you should see that little icon appear in your system notification area.

If you right-click (I believe) on the icon in your sytem notification area, it will give you an option to restart your compiz or metacity windows managers.

This is how I have always fixed the issue.

You can even set the icon to start automatically every time you log in.

Hope that helps. :-)

-Spydey

---

### Post by cblnchat on 2011-02-05
That seemed to work perfectly.   Thanks so much.
Ive also found an application called Cairo-Dock.  Which looks like the dock on the Mac.  
I have a question about it.  Ive found out how to work it for the most part, but am i able to get rid of the original ubuntu bar on the left side of the screen?

Thanks

---

### Post by Copper Bezel on 2011-02-05
Not in the full version of the Netbook Edition desktop environment, no. You can switch to the Gnome environment, but if you're relatively new at this, I'd say that'll probably be more headache than it's worth.

I believe that if you're using Unity 2D, the lighter version of the Netbook environment, you can customize it a bit more, including removing the lefthand dock. I'd look into that, first.

I'd also say that to avoid other headaches, start with Avant Window Navigator, not Cairo-Dock. It's not quite as flashy, but it's a little simpler and its options are a hell of a lot easier to navigate.

---

### Post by cblnchat on 2011-02-05
Ill try out the Avant Window Navigator.  But how do i tell if i have Unity 2D?

Thanks

---

### Post by Copper Bezel on 2011-02-06
Unfortunately, I have zero experience with Unity. WebUpD8 posted on the 2D version mid-January, so you can see their install guide [here]("http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html"). As explained in [another article]("http://www.webupd8.org/2011/01/run-unity-qt-panel-or-launcher-in.html"), though, I guess doing it piecemeal is as involved as anything else, because you'd have to log into a Gnome Classic session, then launch the bits you want from the Unity desktop, then muck about with gconf-editor to remove the original Gnome panel....

In any case, if you want more customization, it's probably easiest to start with Gnome Classic (called Ubuntu Desktop Edition, found in the dropdown menu at the lower right in your login screen after you select your username) and start moving things around from there.

Hmm, remind me whether in the current version the left-hand dock in Unity auto-hides, or whether it's visible at all times?

---

### Post by cblnchat on 2011-02-06
Ill give that stuff a shot.  And on the netbook edition the dock stays at all times.  I cant even find any option for it anywhere.  
But itll take some time to get that stuff figured out, i am pretty new to ubuntu.  But especially new to the Unity interface.  Does the Desktop Edition also have it?

Btw, the Mozilla Firefox icon wont stop bouncing in the Avant Window Navagator...is that fixable?
Thanks

---

### Post by Copper Bezel on 2011-02-06
All the icon animations are adjustable. Just right-click any part of the dock, select "dock preferences", and change the "Icon Effects" setting. If you want different animations for different actions, select "custom" and then the "edit" button. 

Too bad about the auto-hide bit on the Unity launcher - I wasn't certain when that was supposed to be phased in. No, if you log in in the Desktop Edition, it's what we call the classic Gnome interface, which by default has two configurable panels that you can move around, add and remove stuff from, add and remove entirely, etc. 

Personally, I don't use them - I'm using Desktop Edition + Avant in a basically Unity-style arrangement: 

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Screenshot-7.png[/IMG]

Tweaking this stuff can become seriously addictive. = |

---

### Post by cblnchat on 2011-02-06
> **Copper Bezel said:**
> 
Tweaking this stuff can become seriously addictive. = |

I tried editing the quote, i hope it works.  And im finding that out quickly!  I NEVER could be able to do this with windows, which ive used my whole life.  Its nice, really nice, to find and be able to use something so different.  
And how did you change the bar on the top, that displays the time and all that?  So if i go into the desktop edition on the netbook edition i can change all this stuff...and then it will change how the netbook edition looks?
Nice background btw!  How did you get it?  Ive tried getting new backgrounds but it wont work right, their not the right size.  Or i try clicking on the get new backgrounds button in the appearance section and i still havent been able to figure out how to get them onto the computer properly, i even tried dragging and dropping into the appearance screen but that wont work.

Thanks so much for your help! :D

Edit: I just went into the desktop edition and couldnt figure out how to change anything at all.  Im not sure if its just cause im new or what, lol.  :confused:

---

### Post by Copper Bezel on 2011-02-06
Glad you're having fun! I'll try to answer each of your questions in order, here....

1. The bar on the top on my rig is actually being supplied by Avant. You can create a new panel, then adjust all of its settings (except the theme) individually. For instance, I have both of mine set to "Always Visible", but it's just as easy to, say, set the bottom dock to Intellihide.

To get rid of the panels that come with the classic Gnome environment (Desktop Edition), I used a settings program called gconf-editor, which provides a huge number of tweakable settings for the desktop environment. Edited like so:

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Screenshot-8.png[/IMG]

With that said, be careful with what you change in gconf-editor if you choose to go that route - a lot of stuff in there can really screw your system. Also note that getting rid of the panel means that the Alt+F2 run dialog doesn't work anymore, either - in my case, I replaced it with one from another desktop environment.

2. Changes to the Desktop Edition won't change the Unity panel or Launcher in Netbook Edition, which is a separate program from the Gnome Panel in Desktop Edition. Changes to Avant will stay no matter which you log into, because it's the same program run by the same user account. Whichever Edition you select will become your default for next time, and all of your program and personal settings will be unchanged. In short, if you just make the switch to Desktop Edition, you won't really notice the difference.

If you decide to install Unity-2D, then you can run the Unity top panel, or the Unity Launcher or both, in the Desktop Edition interface. You can add them to your startup applications, and they'll appear at boot just as in the Netbook Edition. Just note that these are still separate programs from the standard Unity Netbook Edition interface and what changes you can make to them won't translate over if you do decide, for whatever reason, to jump back to the Netbook Edition environment.

3. For the background, I'm a big fan of Deviantart.com, which is where I get most of mine, including this one. It's a general art sharing site, but there are categories for most popular desktop background genres, like vector, photography, landscape, etc. Save any file you want to your computer (probably in a folder under Pictures), and then you should be able to drag and drop it into your Background list in appearance preferences. If you're having trouble finding backdrops of the right dimensions, set "Style" to "Zoom." It'll scale and crop the image appropriately.

---

### Post by cblnchat on 2011-02-06
Thanks so much for all this help.  Its a lot to cover.  And i think ill change over to the Desktop version.  But i was reading that on the next release, (11.04 right?) they are gonna use the Unity interface for the desktop version too making the netbook version obsolete, whats that gonna mean if i do do all this...is the unity interface just gonna pop up in the desktop version?
And where do i get gconf-editor, im guessing the software center, but im asking just to make sure. lol.  
Other than the change in look i only have one other worry about changing to the desktop edition.  It seems to boot really slow from the log in screen.  Is that something i have to worry about or is it just cause im using a netbook for the desktop edition?
And thanks for the background website.

Thanks again for all this help

Edit:  Do you use Ubuntu exclusively?  And if you do do you have any pros or cons for switching?  Im thinking about doing that.

---

### Post by Copper Bezel on 2011-02-07
No problems!

1. No, upgrading won't remove the classic Gnome interface.

2. You can actually just install gconf-editor from the terminal by running this command: sudo apt-get install gconf-editor

3. Since I don't use Unity, I didn't realize it had a quicker login. If that's something you're concerned about, I could see that that might be a reason to stick with the Netbook Edition interface. On the other hand, of course, there's the tweakability factor here. = )

4. Yes, I'm using Ubuntu exclusively now, after briefly experimenting with Fedora. Switching seems pointless to me. It's roughly the same kernel and roughly the same selection of desktop environments and enduser applications no matter what Linux you're running, and Ubuntu has the broadest support base and gets quite a bit of preferential treatment. Because it's the most common distro, it's the most likely for any new application to have a build for. I never have to compile anything from source, which would be true on Ubuntu or Fedora but not many others. It seems like switching to a different desktop environment would have a larger effect on the user's experience than switching to a different OS that used the same desktop environment - for instance, take a look at XFCE or Gnome Shell. Simultaneously, there are any number of Ubuntu-derived distros out there designed toward specific goals or user bases.

---

### Post by cblnchat on 2011-02-07
I actually already had gconf-editor installed!  It took me a bit to find it but once i did i edited it like you showed on your screenshot.  But i didnt have time that night to change anything so i just shut down my computer, and once i restarted it both the bottom bar and the top bar was gone.  And its taken me a while to get it back but now im not sure how to change it or make another avant dock.
And ive been wanting to change from Windows to ubuntu for a while now.  A few years ago i started messing around with ubuntu 8.04 i think, but i had some big problems with it with my desktop.  But i still loved it.  Have you ever had any hardware problems?  Like plugging stuff into it and it just wont work? 

Thanks very much

---

### Post by Copper Bezel on 2011-02-07
Hmm, making that change didn't make Avant start at startup? It's basically telling the system to load Avant instead of Gnome Panel, the two bars that are present by default in the regular Gnome desktop.

Yeah, I've had some hardware compatibility problems, but there's almost always a solution, save for one #$%& annoying printer. (At the same time, I've also had occasion to work out compatibility problems I wouldn't have been able to on Windows, so it's kind of a wash.)

---

### Post by cblnchat on 2011-02-08
Nope it didnt work.  But ive kinda found a set up that works for me for now.  Its using the original gnome top bar and i have it smaller and autohiding.  Its working.  Eventually tho id like to change it.

Im also gonna include an attachment of a screenshot of one time i turned on ubuntu, everything is grey and its almost like i turned it on some kind of ultra low system requirements setting.

Thanks

---

### Post by Copper Bezel on 2011-02-08
Cool. = )

To fix that bug with everything coming up in that older default theme, open your preferences -> startup applications and add a new entry, with "gnome-settings-daemon" (without the quote marks) in the command box. The bug doesn't happen for everyone, but it's been coming up quite a bit, and the fix doesn't work for everyone, either, but it worked for me and I've heard positive things.

---

### Post by cblnchat on 2011-02-09
i think that worked.  But now i have another small problem.  Im trying to make it so the gnome panel stays now cause the avant wont work right when i enter it, but it wont stay as gnome panel.  And every time i turn off the computer i have to find and restart the gnome panel.  Its not much of a problem but its kinda annoying lol.

Thanks for all the help

---

### Post by Copper Bezel on 2011-02-10
No problem. I'm glad that seems to have worked.

This is actually solvable with startup applications, too. I'd just go ahead and add entries for gnome-panel and avant-window-navigator.

---

### Post by cblnchat on 2011-02-23
> **Copper Bezel said:**
> No problem. I'm glad that seems to have worked.

This is actually solvable with startup applications, too. I'd just go ahead and add entries for gnome-panel and avant-window-navigator.

Hey im not sure if your still watchng this thread.  But ive givin AWN another shot but directly from the wiki page.  And its still not working, although i have a different problem this time.  Ive changed the entry in gconf-editor from gnome panel to avant-window navigator then to avant-window-manager and when i changed it to manager i turned the computer back on and the gnome panel is still there but a strangely shaped something appeared before it.  And im not sure whats going on or how to get this to work.

Thanks!

---

### Post by Copper Bezel on 2011-02-23
Well, in any case, I apologize if I led you into a lot of confusion. Is there anything you're specifically trying to figure out at this point?

---

### Post by cblnchat on 2011-03-02
> **Copper Bezel said:**
> Well, in any case, I apologize if I led you into a lot of confusion. Is there anything you're specifically trying to figure out at this point?

Im actually just trying to figure out what i was doing before.  Putting a AWN panel where my GNOME panel is up top.  Im kinda learning to use the startup applications thing tho so is there anything special i would need to put in there?  Or just avant-window-manager or avant-window-navigator?

Thanks

---

### Post by Copper Bezel on 2011-03-02
Yeah, just avant-window-navigator in Startup Applications.  I don't know what caused it, but for a while, my AWN was showing up invisible - still there, still clickable, but completely invisible - at startup, and I would have to restart AWN. I wonder if you're experiencing something related to that same bug.

---

### Post by cblnchat on 2011-03-04
> **Copper Bezel said:**
> Yeah, just avant-window-navigator in Startup Applications. I don't know what caused it, but for a while, my AWN was showing up invisible - still there, still clickable, but completely invisible - at startup, and I would have to restart AWN. I wonder if you're experiencing something related to that same bug.
 
That could be.  What did you do to fix it?
Btw right now ive had a major problem with my computer and it wont work anymore.  It turns on but will restart itself at the starting screen.  Where it tells me to press F2 for the BIOS options.  But im about to make a post about it.  If your interested
 
Thanks

---

### Post by cblnchat on 2011-03-06
Ok so now i have full Ubuntu on my netbook.  And its ubuntu desktop, not desktop thru netbook edition.  And i just tried editing gconf-editor again to  avant-window-navigator and it didnt work again.  But this time it wont let me change it back to the gnome-panel.  It says that its not writable or something like that.  I cant get a screenshot if you want one.  Do you have anyideas whats wrong with it?

Thanks

---

