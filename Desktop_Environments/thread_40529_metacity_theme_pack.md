---
title: "metacity theme pack"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Sav on 2005-06-09
Hi, I installed the metacity theme pack.
Where I can find the new themes?

---

### Post by bored2k on 2005-06-09
[http://gnomelook.org/](http://gnomelook.org/)
[http://art.gnome.org/](http://art.gnome.org/)

---

### Post by Sav on 2005-06-10
Thanks.
But there was a mistake.
I already installed the metacity themes pack, using synaptic.
But if I go to System->Preferences->Themes, I only found the default themes, that coming from the ubuntu installation.

---

### Post by TristanMike on 2005-08-18
Yes, me too, how do I access the metacity-themes that I installed from synaptic.
Please and Thank You

---

### Post by bored2k on 2005-08-18
[QUOTE=TristanMike]Yes, me too, how do I access the metacity-themes that I installed from synaptic.
Please and Thank You[/QUOTE]
```
square@box:~$ cd **/usr/share/themes/**
AgingGorilla/           Emacs/                  Redmond/
Atlanta/                Esco/                   Sandwish/
Bright/                 Glider/                 Simple/
Clearlooks/             Grand-Canyon/           Smokey/
Clearlooks-DeepSky/     Human/                  Smokey-Blue/
Clearlooks-Olive/       Industrial/             ThinIce/
Clearlooks-Quicksilver/ Metabox/                Traditional/
Crux/                   Mist/
Default/                Ocean-Dream/
```
/usr/share/themes/
Is the directory of your themes installed through sudo.

---

### Post by TristanMike on 2005-08-18
Thank you for such an amazingly quick response.  :)  Yes I see them there but they do not appear in my System->Preferences->Themes menu.```
tristan@ubuntu:/usr/share/themes$ ls
AgingGorilla            Grand-Canyon               OutlineHot
Alloy                   HeliX-Sweetpill-Crowberry  OutlineWinter
Atlanta                 Human                      quiet-purple
Bright                  Industrial                 Redmond
BrushedMetal            keramik-Gyellow            Sandwish
Clearlooks              mcblue                     Simple
Clearlooks-DeepSky      Metabox                    Smokey
Clearlooks-Olive        Mist                       Smokey-Blue
Clearlooks-Quicksilver  Ocean-Dream                ThinIce
Crux                    OutlineAsh                 Traditional
Default                 OutlineBeach               Urbicande
Emacs                   OutlineCoal                Watercolor
Esco                    OutlineCold
Glider                  OutlineFruity

```All that I see are Human, Clearlooks, Default, Glider, Grand Canyon, Ocean Dream, Simple, Smoke Blue, and Traditional, none of the others.  :???:

---

### Post by bored2k on 2005-08-18
[QUOTE=TristanMike]Thank you for such an amazingly quick response.  :)  Yes I see them there but they do not appear in my System->Preferences->Themes menu.```
tristan@ubuntu:/usr/share/themes$ ls
AgingGorilla            Grand-Canyon               OutlineHot
Alloy                   HeliX-Sweetpill-Crowberry  OutlineWinter
Atlanta                 Human                      quiet-purple
Bright                  Industrial                 Redmond
BrushedMetal            keramik-Gyellow            Sandwish
Clearlooks              mcblue                     Simple
Clearlooks-DeepSky      Metabox                    Smokey
Clearlooks-Olive        Mist                       Smokey-Blue
Clearlooks-Quicksilver  Ocean-Dream                ThinIce
Crux                    OutlineAsh                 Traditional
Default                 OutlineBeach               Urbicande
Emacs                   OutlineCoal                Watercolor
Esco                    OutlineCold
Glider                  OutlineFruity

```All that I see are Human, Clearlooks, Default, Glider, Grand Canyon, Ocean Dream, Simple, Smoke Blue, and Traditional, none of the others.  :???:[/QUOTE]
 Weird. Copy pasting them to your $HOME/.themes do any good ?

---

### Post by TristanMike on 2005-08-18
[QUOTE=bored2k]Weird. Copy pasting them to your $HOME/.themes do any good ?[/QUOTE]Wow, thanks, but a no go on that one too, if it matters there is an .xml file in with the png's

There was a "metacity-1" folder inside the BrushedMetal theme, so I moved that one to the .themes folder with no luck either, still lost.

---

### Post by TristanMike on 2005-08-18
Ok, solution. The problem is that the package listed in Synaptic is misleading. It says > Themes for the Gtk2 metacity window manager
This collection of themes for the metacity window manager.....Included Themes: Urbicande, OutlineHot, OutlineAsh, OutlineBeach, OutlineCoal, OutlineCold, OutlineFruity, OutlineWinter, keramik-Gyellow, mcblue, quiet-purple, BrushedMetal, Alloy, HeliX-Sweetpill-Crowberry, Watercolor,However, as it turns out, they are not "themes" at all, that is, not as I interpreted it. I assumed(that's a bad word) that they were Full Blown themes with icons and all that jazz and I'd be able to pick it from the Themes menu, sounded logical enough to me, when in fact they are actually just Window Boarder Themes so to access them you go to System->Preferences->Themes. Then from there, pick which ever theme you like but want a different Window Boarder and go to "Theme Details" on the right hand side, Pick the "Window Boarder" tab and you should see all of the "themes".

In retrospect, I should've known, as the are *themes for a window manager* specifically, rather than "themes" but chalk that one up to inexperience in terminology, but whatever, here it is for anyone else as perplexed as I was.

EDIT: Thanx to bored2k and bob2(from #Ubuntu) for helping with this solution.

---

