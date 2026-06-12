---
title: "make activity button show the list of recently used apps"
date: 2013-05-22
forum: Desktop Environments
---

### Post by amivaleo on 2013-05-22
hi everybody!
i use gnome shell 3.8 as my DE.
i was wondering... is there a way to make the "activities" button directly show "recently used apps" without having to click on the (let me say) stippled button on the dock?
by default, it show the list of all opened windows, which is not the way i want it to work.

can you help me? :)

thanks in advance for you answers ;)

---

### Post by dino99 on 2013-05-23
you can add them to the "favorites" , by right clicking their opened icon ; or use dconf (dconf-tool) to tweak the default list

---

### Post by amivaleo on 2013-05-23
that's not what i asked for at all... ^^

---

### Post by grahammechanical on 2013-05-23
There are a lot of things in life that I want. But I rarely get them. What makes you think that the people here know all the answers and are just waiting for to you to make an appearance?

---

### Post by amivaleo on 2013-05-24
nothing. infact I just _asked_ for help, I have _not claimed_ to receive it

then... I realized that the problem here is not the way I put myself (actually I had no doubt about that), but your lack of desire to help.
but that's ok, no one's forcing you as i said.
farewell -.-

---

### Post by Iowan on 2013-05-25
> **grahammechanical said:**
> ... What makes you think that the people here know all the answers and are just waiting for to you to make an appearance?Be nice... Considering our userbase, someone MIGHT have the answer.
> **Ziel van Brand said:**
> that's not what i asked for at all... ^^Gotta admit - probably not the best way to elicit  a response.

---

### Post by amivaleo on 2013-05-25
> **Iowan said:**
> [...]
Gotta admit - probably not the best way to elicit  a response.
probably the problem is that i'm not an english native speaker. so i may not be gentle; that's not because i'm rude, but because i do not know enough the language to be able to distinguish between a polite behaviour from a rude one.
infact, i'm always afraid to explain everything badly :(

so... sorry dino99 if i appeared rude to you.
all i wanted to say is: i'm looking for something different from what you said :)

---

### Post by markbl on 2013-05-25
> **Ziel van Brand said:**
> 
all i wanted to say is: i'm looking for something different from what you said :)
It's not much different though. He suggested a sensible solution which is is completely standard GNOME Shell functionality and pretty close to what you seem to want to do.

---

### Post by amivaleo on 2013-05-26
well... it looks quite different to me, instead :) let me say why:
my goal is to definitively hide the dash. but, if i do that without changing anything else first, i'll hide the "stippled" button too, which is the _only_ one that shows the list of all apps.
that's why i'm looking for a way to make the activities button work differently. in particular: i'd like to make it show the list of all (recently used) apps.
let me say what i mean in a different way:
when clicked, activities button shows this: [http://worldofgnome.org/uploads/2012/11/overview-picker.png](http://worldofgnome.org/uploads/2012/11/overview-picker.png)
if you click on the stippled button on the dash, you'll get this: [http://2.bp.blogspot.com/-I0g6Tq22gv8/UTN8mrSDhfI/AAAAAAAAOVE/vU79Ekd5_WM/s1600/gnome-3.8-beta-frequent.png](http://2.bp.blogspot.com/-I0g6Tq22gv8/UTN8mrSDhfI/AAAAAAAAOVE/vU79Ekd5_WM/s1600/gnome-3.8-beta-frequent.png)
what i want is to make the activities button shows directly the latter image.

what dino suggests would be a good solution if my purpose were to have a quicker access to the recently used apps. but my goal is more... aestethic :)

---

### Post by Frogs Hair on 2013-05-26
There is a recent items extension for the Gnome Shell that opens from the panel. . This extension displays files only and also requires Zeitgeist. Ubuntu already uses Zeitgeist  to display recently used files and applications  . In other words, Unity already uses a similar  feature to what you are seeking to add to the Gnome Shell, but opening dash still required. I see no extensions for recent applications though and 3.8 compatibility is unknown. 


[https://extensions.gnome.org/extension/72/recent-items/](https://extensions.gnome.org/extension/72/recent-items/)

---

### Post by amivaleo on 2013-05-26
uhm... you know, the point is that i want the activities button to work as a "menu button". by default, it opens the overview, where you can switch workspace, you can see all open windows, etc... on the other hand, the "stippled" button on the dash works exactly as a menu button: it shows the list of your installed apps.
i already use that extension after all. it's nice for browsing recently used files, but i've never seen an application there o.O

what makes me a bit... -let's say- disappointed, is that this extension [https://extensions.gnome.org/extension/584/taskbar/](https://extensions.gnome.org/extension/584/taskbar/) more or less reaches the goal: actually it shows a button (which is, ironically, a stippled button :D) on the top black panel, next to the activities button, which opens the recently used apps >.<
so it must be easy to do, maybe I'll just need to interchange some few lines of code :(

---

### Post by amivaleo on 2013-05-26
wow! found it :D
here it is: [https://extensions.gnome.org/extension/608/gnomenu/](https://extensions.gnome.org/extension/608/gnomenu/)
this extension replace the activities button with 3 other buttons. one of these is an "apps" button which does exactly want i want :D (and i can hide the other two buttons).
it's a bit rough (it makes the panel a bit taller than how it should be, and it doesn't have the hot corner), but i think that i can say i'm satisfied :)

thanks to all of you
and... i repeat my apologies for the little squabble at the beginning of the thread

---

