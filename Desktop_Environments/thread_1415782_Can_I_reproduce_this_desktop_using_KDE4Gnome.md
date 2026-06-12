---
title: "Can I reproduce this desktop using KDE4/Gnome ?"
date: 2010-02-25
forum: Desktop Environments
---

### Post by realn on 2010-02-25
I am pressed by life to change what I've been using for years now : KDE3.
I won't detail why, the reasons are more or less obvious: 
- poor (IMHO) KDE support in Ubuntu ( I never understood - I didn't look too much, either - why Gnome is THE DE of Ubuntu. Why there is such a thing as Kubuntu and why not Gubuntu?;
- even poorer support of KDE3 in latest releases(I know about the pearson repository, I thank him with this occasion, he was quite helpful. But still it's not enough - my KK with KDE3 is pretty unstable).
First I have to mention that I've taken a look at latest KDE4 - its lack of customization is UNBELIEVABLE (or if it's possible to customize as I want - which I didn't manage - then it's the lack of friendliness which is unbelievable).

 I have two choices ( I think) - KDE4 and Gnome.

 What I want to keep is my desktop with its settings: it took me so long to get to what I need/like, that I would really like to keep the EXACT same settings. I attach a screen shot of it and I'll detail below what I want:

Panels:
1) Multiple panels with custom position and size
2) Transparent panel without composition. I don't care if it's fake transparency or not, I just want to see the desktop picture underneath the panel. I don't care if I cannot see a window underneath the panel, I just want the Desktop to look smooth and not waste resources
3) Panel that behaves like a quick launch bar = icons on a panel that I can click on to launch applications

Windows decoration:
1) Custom colors/fonts for windows title bars - active/inactive
2) Custom colors/effects for windows buttons - close/minimize/maximize

Panel applets
1) System tray - please note that I use Kdocker to put anything I want in the system tray. The only customization i need on the system tray is to select icons for hiding
2) Task bar with custom fonts and colors and with NO border for each task in the task bar - see KDE4. If I can have the option to display only the icons/text/both of the tasks, so much better
3) System monitor applet for the panel and NOT on the desktop. Custom colors and fonts, also. Look at how neat the Kima applet looks on my desktop
4) Time/date applet for the panel - custom colors/fonts/style
5) Weather applet for the panel

Desktop
1) Custom icon settings - custom size, custom font color and size.

3D effects
1) No effects - I came to the conclusion that it's nice to look nice, but it's even better if you can do the job without being nice.

 These are the main specs I can think of now and I would  need. In my opinion they should be part of a minimum a DE can offer.

 My question is: can anyone help me in reproducing these settings using something else than KDE3? If I can make the exact (almost) look and feel on anything else than KDE3, then I'll go for it. Otherwise, I guess I'll downgrade to HH and stick to it until the end.

 Thank you so much !

---

### Post by Silent Warrior on 2010-02-25
Your screenshot was in such a low resolution I couldn't make out what was exactly what, but I think it's quite possible to tailor a Gnome/KDE4-desktop to your criteria.

KDE4:
The dock on the side could be a panel, with STasks or Smooth Tasks applets installed to it (and nothing else) and not set to maximize. The bottom panel I couldn't read in your screenshot, but the only point of concern is the notification area/systray; as far as I know, anyway, take it as you will. Icons are of course freely placeable, or you could set up a folder-view - I can't tell what those icons are supposed to launch. I'm not familiar with KDE4's system monitors, but you can get A set of monitors - I doubt they'll look like that, though. Maybe there are some variants of conky?

Gnome:
The panel on the side is mostly the same story - add a panel and move it to that side, set it to full transparency, add Dockbar or Talika, deactivate the option to unfold (maximize). There's no folder-view plasmoid to use, but that might not be an issue as icons/links can be made and placed freely. Panel backgrounds can be set any way you like. Though you'll have to come to terms with Gnome's different (= requires more space) menu-policies or use Gnomenu. You can set the clock/calendar to display weather, as long as you specify your location.

Should only be a matter of time to just sit down and take the time to set the DE up, really.

What applets are you using now, anyway?

---

### Post by realn on 2010-02-25
Hi, thanks for the quick reply. The things I mentioned are the things I am currently using and I would like to port to KDE4/Gnome.
 For instance, I looked quite a bit of time and didn't find out how to do in KDE4:
 - custom colors/fonts for title bars and buttons;
 - custom colors/fonts for tasks in the taskbar.

Which info sources do you recommend for getting to know better KDE4/Gnome? The KDE forum is pretty much dead - it only now occured to me - maybe there is a KDE4 special one?
 I'll try to reattach the jpeg in better(in fact worse) resolution.

---

### Post by Silent Warrior on 2010-02-26
Just remembered I saw a package in Synaptic that was meant for migrating KDE3-settings to KDE4. Something for you? I'm not sure about the name, but if you search for the description, it'll mention this migration.

Panels: 1 and 3 are easily set in both DEs. I'm not sure about composition-less transparency in KDE4, but you can set panel transparency in Gnome by right-clicking said panel.

Window-decorations: These might depend on the decorator itself, not KDE/Gnome. I'm in fact looking at deKorator's settings module right now, and it seems to provide what you're looking for. Aurorae might as well. I haven't used the others much, so I can't comment for sure about those. I haven't poked Gnome enough to discover how to do this there - I don't have your particular tastes. :p

Panel-applets: 1 should be possible with KDE4's notification area. I can't comment on Gnome's capabilities in this. 2 is more likely an option in KDE4, maybe not in Gnome (AFAIK). Though to get only the icons, there are STasks and Smooth Tasks in KDE, Dockbar/DockbarX and Talika in Gnome - you'll have to browse Gnome-look for the Gnome-applets, in KDE you might find them through their vaunted 'Get hot new stuff'-interface. But that's another story.
3 I really don't know anything about. It might be an option in KDE, though the one I've tried doesn't quite seem to behave as you expect. Have someone else know this for you. 4 and 5 are easy enough in both DEs, though in Gnome you can have a weather-report through the time/date-applet if you set it so. It's icons will depend on the icon-theme in use, colors on Gtk-theming. I'm not sure if you can have it as a panel-applet in KDE - I only ever tried it on the desktop, not that it worked entirely to my satisfaction (didn't manage to set it for my location) - but it shouldn't be impossible. Whether it's themable likely depend on what plasmoid you pick for this. I think you have more than one customizable weather-plasmoid to try.

You can always have a look at the DEs' home forums - I think [www.gnome.org](www.gnome.org) and [www.kde.org](www.kde.org) are what you're looking for, as far as forums go.

---

### Post by realn on 2010-02-26
Thanks a lot for the reply. Yes, I took a look at the KDE3 import settings. 
 The bottom line is in fact that for the moment it seems quite improbable that I can meet all my needs with KDE4/Gnome. Come on, I looked in KDE4 for half an hour for a custom color text in the title bar, I didn't find it. In KDE3 it was just a "couple of clicks away", as they say.
  If someone can help me with these settings, I will be mighty grateful, because I am about to fallback to HH.

 I just stumbled on this: here is how decisions are made in the KDE world. 
[http://aseigo.blogspot.com/2009/03/decision-trees.html]("http://aseigo.blogspot.com/2009/03/decision-trees.html")
Sad, but true. I would like to have transparent panel without composition. I understand what I ask - a piece of code that doesn't fit at all in the main picture. Is it really not good for me or rather for him? 
 "Pure cosmetic" for me are all those objects floating around on my desktop, tilted at various angles and completely useless (IMHO). I insist on IMO - A. Seigo might be the father of KDE4, but after all his sole decision impacts so many users, and after all, it's only his point of view. He cannot simply decide what the users want. It doesn't make sense.

---

### Post by realn on 2010-06-16
I just solved the problem:

[https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid](https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid)

---

### Post by realn on 2010-07-20
The above mentioned solution is quite unstable and there are missing packages from the trinity repositories. Fallback to HH.

---

