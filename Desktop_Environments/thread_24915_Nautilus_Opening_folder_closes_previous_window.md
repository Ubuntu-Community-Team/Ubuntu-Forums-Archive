---
title: "Nautilus: Opening folder closes previous window"
date: 2005-04-08
forum: Desktop Environments
---

### Post by imnes on 2005-04-08
One of the recent updates to Hoary (pre-prelease) has caused Nautilus to change behavior.  It stills looks like it's browsing in spacial mode, but when I double-click on a folder with the left mouse button, it opens that folder in a new window (as expected) but immediately closes the previous window.  (I think that should be the behavior when you double-click with the middle mouse button).

Any ideas how to get the old behavior back?  (I want it to leave windows open unless I explicitly close them).

Nick

---

### Post by Novack on 2005-04-08
Open the GConf configuration editor (Applications -> System Tools -> Configuration Editor). Then browse to Apps/Nautilus/Preferences in the GConf editor and select the "no_ubuntu_spatial" -key.

---

### Post by taygan on 2005-04-08
and the middle button leaves the previous folders open, yes?

---

### Post by wxm505 on 2005-04-08
[QUOTE=Novack]Open the GConf configuration editor (Applications -> System Tools -> Configuration Editor). Then browse to Apps/Nautilus/Preferences in the GConf editor and select the "no_ubuntu_spatial" -key.[/QUOTE]
Problem solved . cheers

---

### Post by slux on 2005-04-09
Anyone actually *like* this behaviour? I think it just pretty much breaks the basic idea of going spatial (a folder equals a window and they stay in the places you leave them).

If the Ubuntu devs think spatial is not a good idea they should just make the browser windows default instead of making spatiality broken and effectively giving the worst of both worlds.

---

### Post by originil on 2005-04-10
Yeah, that was my thought. I actually liked the previous spatial quite a bit, it just worked for me, but this seems much, much worse. Every time I want to go to a folder I was using previously, I need to run through the whole directory structure. 

Is this the Hoary devs, though, or is it Gnome 2.10? Either way, it would be nice to see an option in preferences to specify this behavior.

Edit: ahh.. clearly, this is an Ubuntu thing, by the gconf key. Well, as long as I can change it in Gconf, that's good enough for me. I have my doubts as to whether this will sell spatial any more than the old way, though. Then again, I could be wrong!

Don't get me wrong, though, Hoary's great, and the work the devs are doing is fabulous! 

Thanks!

---

### Post by souki on 2005-04-10
[QUOTE=slux]Anyone actually *like* this behaviour? I think it just pretty much breaks the basic idea of going spatial (a folder equals a window and they stay in the places you leave them).

If the Ubuntu devs think spatial is not a good idea they should just make the browser windows default instead of making spatiality broken and effectively giving the worst of both worlds.[/QUOTE]
 I think the ubuntu_spatial mode is quiet disturbing, because it does not behave like the windows equivalent : the folder-window is resized or moved to the last visited state (and you see the parent-folder disapearing) instead of staying with your first size-and-position choice

---

### Post by imnes on 2005-04-10
I agree, please go back to Gnome's default behavior.  This new style is just annoying.

NIck

---

### Post by Dreamsmith on 2005-04-10
Hmm.  Yes, there are advantages and disadvantages to spatial mode vs. browser mode.  This new "Ubuntu spatial" seems designed to incorporate the disadvantages of both while discarding the advantages!  I'm utterly baffled...

---

### Post by c_dog on 2005-04-10
[QUOTE=taygan]and the middle button leaves the previous folders open, yes?[/QUOTE]

Which works just wonderful on laptop touchpads. snick... And oh yeah, I think I'll grow another arm or 10 inch fimgers to use the <shift-key click on the directory tree> method too. Having spactial set without a non-geek way of setting it to Gnome standard is a real stupid precidence on the SABDFL's part.

---

### Post by neighborlee on 2005-05-01
[QUOTE=Novack]Open the GConf configuration editor (Applications -> System Tools -> Configuration Editor). Then browse to Apps/Nautilus/Preferences in the GConf editor and select the "no_ubuntu_spatial" -key.[/QUOTE]
------------
gez you guys come ON lol..

you do all this in PREFS under nautilus > behavior tab then: 'open in browser window'

why make it l33t tricky when its right in your face ?LOL

cheers
neighbolree

---

### Post by Emrysk on 2005-05-01
He wasn't asking for browser windows.  He just wanted Gnome's normal spatial style back.  (Meaning: windows don't close every time you open a new one.)

---

### Post by condorloco on 2005-05-01
I said this before in another thread: I like the default gnome behaviour much better than the Ubuntu one. Changing the system config to revert to the normal gnome behaviour is quite easy, BUT if I use Nautilus with 'sudo' I still get the Ubuntu-style windows opening. I wished it would be changed back again in Breezy.

---

### Post by c_dog on 2005-05-01
[QUOTE=neighborlee]------------
gez you guys come ON lol..

you do all this in PREFS under nautilus > behavior tab then: 'open in browser window'

why make it l33t tricky when its right in your face ?LOL

cheers
neighbolree[/QUOTE]
 If you're going to get so arrogant with an answer, be sure you're even answering the right question... when it's right in your face.

---

### Post by neighborlee on 2005-05-02
[QUOTE=c_dog]If you're going to get so arrogant with an answer, be sure you're even answering the right question... when it's right in your face.[/QUOTE]
-----------------------
I always get a bit arrogant I suppose when I misread posts slightly :('my bad')...  deeply trenched l33t mentality I see too often which bit me that time as I just misread as I say the original post.  I stand by my post on its merits though that using gconf should be unnecessary in a world of easy-to-use systems of which ubuntu claims it is...gconf is just confusing imo and especially to the target user audience . If they are going to make 'changes' like that, they need to be 'undo' able from PREFS ;-).

cu
neighborlee

---

### Post by SKLP on 2005-05-19
Please, make the REAL spatial (no_ubuntu_spatial) default in breezy. Even the browser mode is a whole lot better than this crap. The whole point of spatial file management is ruined. 

Now my question is, who the hell really likes this IMHO stupid change?

---

### Post by SKLP on 2005-05-21
And if I may, if this IMHO dirty hack will be kept, at least make it somewhat consistent so that when u double-click a file (not a folder) in a nautilus window that nautilus window closes unless you shift-clicked (or middle clicked) the file.

Otherwise, this patch creates an unnecessary inconsistency between the behaviour when opening files and folders -- in other words we are not really spatial anymore and could just as well switch to browser mode by default...

---

### Post by Haegin on 2005-05-24
Thanks neighbolree, I actually prefer the browser window. If I'm tunneling down through 5 directories to copy one file up one directory I don't want to have to close 5 windows afterwards. The click to get focus on the window of the folder you are copying to could just as easily be spent clicking the "up" button.

Anyway, if you prefer spatial, use the gconf edit, if you prefer ubuntu spatial, leave it, if you prefer browser mode, change to browser mode in the preferences. And lets just hope that in breezy they just make it a selection in the prefs dialog.

---

### Post by MaX on 2005-05-24
[QUOTE=Human Prototype]Thanks neighbolree, I actually prefer the browser window. If I'm tunneling down through 5 directories to copy one file up one directory I don't want to have to close 5 windows afterwards. The click to get focus on the window of the folder you are copying to could just as easily be spent clicking the "up" button.

Anyway, if you prefer spatial, use the gconf edit, if you prefer ubuntu spatial, leave it, if you prefer browser mode, change to browser mode in the preferences. And lets just hope that in breezy they just make it a selection in the prefs dialog.[/QUOTE]
 Just thumb-click them (or middle click where ever you've got your third mousebutton)

---

### Post by MaX on 2005-05-24
[QUOTE=neighborlee]-----------------------
I always get a bit arrogant I suppose when I misread posts slightly :('my bad')...  deeply trenched l33t mentality I see too often which bit me that time as I just misread as I say the original post.  I stand by my post on its merits though that using gconf should be unnecessary in a world of easy-to-use systems of which ubuntu claims it is...gconf is just confusing imo and especially to the target user audience . If they are going to make 'changes' like that, they need to be 'undo' able from PREFS ;-).

cu
neighborlee[/QUOTE]
 And whats that ---------- it looks like you write everything in your signature.

---

### Post by Haegin on 2005-05-24
[QUOTE=MaX]Just thumb-click them (or middle click where ever you've got your third mousebutton)[/QUOTE]
actually - my mouse has 5 buttons (two normal, the scroll wheel/middle button, a "thumb" button  and another "thumb" button but on the other side (for left handed people). How do I get the two extra buttons working and what can I make them do? A terminal would probably be quite useful on one, or maybe force quit/quit.

Going back to the nautilus topic - it would take too long to learn to do it differently - may be easier and more natural but as I'm used to the "old" browser way its easier for me to just stick with that. Like the single mouse button on a mac - it may be easier for new users but I would just get annoyed by it I think.

Anyway - give everyone the option and people can change it when they want.

---

### Post by MaX on 2005-06-01
[QUOTE=Human Prototype]actually - my mouse has 5 buttons (two normal, the scroll wheel/middle button, a "thumb" button  and another "thumb" button but on the other side (for left handed people). How do I get the two extra buttons working and what can I make them do? A terminal would probably be quite useful on one, or maybe force quit/quit.

Going back to the nautilus topic - it would take too long to learn to do it differently - may be easier and more natural but as I'm used to the "old" browser way its easier for me to just stick with that. Like the single mouse button on a mac - it may be easier for new users but I would just get annoyed by it I think.

Anyway - give everyone the option and people can change it when they want.[/QUOTE]
 That's just lazy, I was all for the browser mode too, I got pretty upset over the new spatial thingy, but now I'm used to it, it took me what, 2 days. You can allways use close all parent windows if you don't want to thumb-click.

Your third is probably the mousewheel clicked then, it's the one which you can paste text with, you can add the other buttons in xorg.conf I think.

Gnome is not about options, it's about doing the most sensible thing and stick to it. KDE is for options.

---

### Post by Haegin on 2005-06-01
where can I find this xorg.conf and what kinda formatting do I use to add the buttons? Also if the spatial method had any benefits then yes I would switch over (like I did from windows to linux) but as its main benefits seem to be the way that it is easier to learn then switching would be counter productive - why spend time learning a new feature when its only purpose is to make it easier for people who aren't used to any way to pick up?

---

### Post by neighborlee on 2005-06-01
[QUOTE=MaX]That's just lazy, I was all for the browser mode too, I got pretty upset over the new spatial thingy, but now I'm used to it, it took me what, 2 days. You can allways use close all parent windows if you don't want to thumb-click.

Your third is probably the mousewheel clicked then, it's the one which you can paste text with, you can add the other buttons in xorg.conf I think.

Gnome is not about options, it's about doing the most sensible thing and stick to it. KDE is for options.[/QUOTE]

Where does it say that gnome is not about options, and that if you want options you should use kde ?LOL

I understand that kde is a bit bloated yes but gnome can't be about options like disabling a given mode 'in' nautilus PREFS instead of making someone do l33t things like changing it non ease of use places like gconf ?..I dont think so and if you do you dont deserve to be making apps for the rest of us that actuallly want to USE said apps instead of having to fiddle with them just to get a certain behavior. That is not good useabiliity design.

I am not the only one that believes it should be eaSier to go from one mode to the other easily , just look here:
----------------

I'm so used to the "normal" Spatial mode that I've re-enabled it on my Ubuntu machines. That's relatively easy to do via a hack in GConf (Gnome's somewhat Registry-like settings storehouse)--but before making such a big change in Nautilus, the Ubuntu gang should have provided a simple toggle for this new behavior in Nautilus's Preferences dialog. < which can be seen at: [http://www.pcworld.com/reviews/article/0,aid,120520,00.asp](http://www.pcworld.com/reviews/article/0,aid,120520,00.asp)

Ubuntu is about ease of use unless that no longer is the gangs core mentality....

cheers
nl

---

### Post by Haegin on 2005-06-01
i agree, one more vote in the bag...

---

### Post by Walker_P on 2005-06-05
[QUOTE=slux]Anyone actually *like* this behaviour? I think it just pretty much breaks the basic idea of going spatial (a folder equals a window and they stay in the places you leave them).

If the Ubuntu devs think spatial is not a good idea they should just make the browser windows default instead of making spatiality broken and effectively giving the worst of both worlds.[/QUOTE]
 I don't have this behaivior but I want it, how do I get It?

---

### Post by MaX on 2005-06-05
[QUOTE=Human Prototype]where can I find this xorg.conf and what kinda formatting do I use to add the buttons? Also if the spatial method had any benefits then yes I would switch over (like I did from windows to linux) but as its main benefits seem to be the way that it is easier to learn then switching would be counter productive - why spend time learning a new feature when its only purpose is to make it easier for people who aren't used to any way to pick up?[/QUOTE]
 /etc/X11/xorg.conf

The formating and syntax should be googelable. Since I only have Left,Right, "Middle" (wich is both my mousewheel and my thumbbutton), it works out of the box.

---

### Post by tiktok on 2005-06-12
Is there a way to adjust the ubuntu_spatial behavior? I don't want to turn it off since there is something I'd like to try. Sometimes I have to drill down 6 or more layers of folders. That's just how I personally organize things. Lots of subfolders. Sometimes I've got 10 levels of sub-folders open. 

I'd like an version of ubuntu_spatial where I'd be able to keep the last 2 previous folders open. 

For example:
As I drill down my  folders starting at Documents -> Work -> Apts -> 123 Main -> Contracts

When I open the 123 Main folder the Documents folder closes, but Work and Apts are still open. When I go down to Contracts, the Work folder closes, Apts and 123 Main remain open.

---

### Post by tranzndance on 2006-05-30
[QUOTE=neighborlee]------------
gez you guys come ON lol..

you do all this in PREFS under nautilus > behavior tab then: 'open in browser window'

why make it l33t tricky when its right in your face ?LOL

cheers
neighbolree[/QUOTE]
Even if your suggestion hadn't answered the original question, it answered mine. Thank you very much! Spatial mode was driving me nuts, and I wanted to make browser mode the default.

---

### Post by cyrano_says on 2007-01-07
it was driving me nuts too...

```
 Originally Posted by neighborlee
------------
gez you guys come ON lol..

you do all this in PREFS under nautilus > behavior tab then: 'open in browser window'

why make it l33t tricky when its right in your face ?LOL

cheers
neighbolree
```

This did the trick...

Thanks a bunch..

---

