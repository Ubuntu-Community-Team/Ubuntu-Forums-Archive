---
title: "truncate filenames in nautilus windows?"
date: 2007-02-23
forum: Desktop Environments
---

### Post by LilYoda on 2007-02-23
Hello

Is there any way to have nautilus windows truncate long filenames?  When browsing directories with long filenames, I end up having only 1 line of icons in my windows, because the long filenames end up strecthing every icon row too much.

Any ideas?  Did a bit of searching on this, but didn't find any config anywhere

Alternatively, is there a replacement to nautilus, that would do this, and integrate well in Ubuntu? (I have Ubuntu only, no KDE, I prefer gnome interface)

Thanks y'all

---

### Post by metnik on 2007-02-25
me too.. try to see on bugs.gnome.org even if I'm sure that somebody else already opened a bug for it

---

### Post by LilYoda on 2007-02-27
You're right, it's there

[http://bugzilla.gnome.org/show_bug.cgi?id=84390](http://bugzilla.gnome.org/show_bug.cgi?id=84390)

And it's been going on for 5 years.  I doubt we'll have resolution soon :(

---

### Post by turezky on 2007-11-22
So, any recent developments on this topic?
This issue really sucks, and I don't want to believe that guys in gnome just seat there for 5 yrs and do nothing about it..
Well, would be tremendously thankful if anyone gives the solution.

---

### Post by LilYoda on 2007-11-23
I personally gave up on Nautilus, and use Thunar.  There is a script somewhere on the forums to make thunar the default browser.

EDIT: the thread to make thunar the defautl manager is here: [http://ubuntuforums.org/showthread.php?t=299927](http://ubuntuforums.org/showthread.php?t=299927)

---

### Post by sambehera on 2008-01-03
this is ridiculous... 5 years and no resolution to long filenames..? we've worked on making brilliant effects on compiz fusion but haven't made gnome truncate long file names? ... KDE has been truncating long filenames for quite some time now...

---

### Post by markg85 on 2008-03-08
Sorry for "reviving" a nearly 6 months old topic.

I think this part needs extra attention. Recently this bug report on gnome got some more attention and it's now possible to make truncated filenames with pango (and that had to take 5.5 years!!!!). Now it just needs a patch and than gnome finally has what it should have had when the bug was opened (in 2002).

I don't think this will make it's way in Gnome 2.22 because that's already in RC state but if some smart coders start writing a nice decent patch for the filename truncation than it might get into Gnome 2.24. I will give it a try as well but i am far from a professional c coder..

My idea is (just like windows actually)
Normal is: 2 lines max ending in "..." when it was exceeding the 2 lines to indicate that there is more text

Selected/hover = All text visible and should go over any icon below it (not push it away)

Lets start making a patch for this.

---

### Post by LilYoda on 2008-03-09
I wish I could help coding it, but I Iknow nothing of coding :-(

---

### Post by markg85 on 2008-03-09
Well i submitted my first patch to nautilus when i had near to no c experience (still have nearly none) and that patch got accepted (nearly completely rewritten, but it got in). So don't think you can't write a patch. it's possible :)

---

### Post by BilliShere on 2008-04-24
sorry for reviving this thread again. but i also think this is a highly important feature that must be implemented. 

for lack of better words. nautilus sucks at drawing icons. thunar on the other hand uses less resources AND also draws aligned icons in a grid, with truncated filenames, and similar sized thumbnails. 

running thunar along side nautilus using the defaultthunar.sh script is not an option for me unless i get rid of nautilus completely. its really annoying to use thunar while nautilus is still drawing the desktop sucking up 128 mb of memory. also thunar doesnt really have a very good search option...i mean come on..who wants to use catfish *additionally* to give you search capability in thunar.(yes i do organize my files perfectly and know where they are). 

furthermore, its really annoying to rerun that script every now and then when an update is released and all kinds of wierd things start happening with awn stacks starting to have issues and what not. 

somebody? please help? lets fix these icon drawing problems in nautilus? come on?
its about time we get to use nautilus with grid aligned, truncated icons and correct thumbnail sizes to go along with the icons sizes?

---

### Post by markg85 on 2008-05-03
> somebody? please help? lets fix these icon drawing problems in nautilus? come on?
its about time we get to use nautilus with grid aligned, truncated icons and correct thumbnail sizes to go along with the icons sizes?

Well that quite a wish list..
To sum it up in a readable way:
- Nautilus with proper grid support
- Truncate filenames
- Correct thumbnail sizes to go along with the icon sizes

That last point is in nautilus
press ALT+F2 and type: gconf-editor
then go to: **/apps/nautilus/icon_view/thumbnail_size**
That value is by default 96 and the default icon size is 48. So change this one to 48 and you have that problem fixed.

I also just DON'T understand why gnome made the strange decisions to have those 2 in different sizes..

As for the rest..
I personally think that nautilus is a lost case..
it does:
- Desktop handling
- File manager stuff

And if i where part of gnome i would split it up in a program that draws the desktop and a program that manages files. Both might just use the same backend but the frontend must be either splitted in those 2 mentioned or made extremely well.

---

### Post by BilliShere on 2008-05-18
Thank you. That did the trick for having the same sized thumbnails as icons. Now no matter what the zoom in level the thumbnails have the same size.


The only things we have to fix up now is the ability to truncate filenames and grid support. Ive checked out some other settings under gconf-editor but no luck. i heard building nautilus from source may allow us to have access to include grid support or enable truncating filenames. but im sure its gonna be a pain to build nautilus everytime there is an update.

---

