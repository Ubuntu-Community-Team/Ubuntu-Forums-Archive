---
title: "awn-trunk on ubuntu...gnomenu bug"
date: 2011-02-05
forum: Desktop Environments
---

### Post by rvchari on 2011-02-05
gnomenu applet in awn trunk fails to load many a time.
i usually used to click on the applet to restart and things would b fine. yesterday i changed the desktop theme to LC3 with clearlooksOSX / LC3 icon set.
now when i activate awn (i dont activate auto start up, i activate after desktop is loaded) the gnomenu applet crashes and takes me to bug report.

gnomenu app has been giving me irritation with awn. wonder if its awn problem or gnome applet problem, any clue ?

---

### Post by kerry_s on 2011-02-05
gnomenu has always been iffy, every time i've tried it something was broke.

---

### Post by Copper Bezel on 2011-02-06
Which one are you using? There are three, and none of them are specifically called Gnomenu Applet. I use Cairo Main Menu and have zero problems with it, except that it's the last applet to load by a second or two.

---

### Post by kerry_s on 2011-02-06
> **Copper Bezel said:**
> Which one are you using? There are three, and none of them are specifically called Gnomenu Applet. I use Cairo Main Menu and have zero problems with it, except that it's the last applet to load by a second or two.

it's not a standard menu.
[http://gtk-apps.org/content/show.php?content=93056](http://gtk-apps.org/content/show.php?content=93056)

you get it through ppa:
[https://launchpad.net/~gnomenu-team/+archive/ppa](https://launchpad.net/~gnomenu-team/+archive/ppa)

i use cardapio from ppa, see pic


i'll try gnomenu again & get back.

---

### Post by kerry_s on 2011-02-06
got it installed, seems to be running fine, it does crash when changing themes, but a simple click reload & it's all good.

i logged in & out a few times, no problems there.

my awn is set to auto load as i don't use gnome-panels.

is it a particular theme your using?

i settled on the kde theme.

---

### Post by rvchari on 2011-02-06
any ppa for cardapio ? by the way, copper bezel....
you r right, gnomenu was installed from the ppa and it runs fine when kept on panel. it behaves funny with awn... and yes, that was the last to load in awn !!!

any idea where and how i install cardapio ? sometimes its easer to type on the search bar than browse thru the main menu !!!

i tried both the options of ppa i got after i googled... ppa doesnt seem to get loaded !!!

---

### Post by rvchari on 2011-02-06
i finally installed cardapio following this link and instructions...
=> [http://www.ubuntuvibes.com/2010/08/cardapio-is-maverick-ready.html](http://www.ubuntuvibes.com/2010/08/cardapio-is-maverick-ready.html)

the problem is cardapio also fails to sit on awn dock !!! the applet crashes !!!:confused:

---

### Post by kerry_s on 2011-02-06
> **rvchari said:**
> i finally installed cardapio following this link and instructions...
=> [http://www.ubuntuvibes.com/2010/08/cardapio-is-maverick-ready.html](http://www.ubuntuvibes.com/2010/08/cardapio-is-maverick-ready.html)

the problem is cardapio also fails to sit on awn dock !!! the applet crashes !!!:confused:

i had no crashes.
did you install cardapio-awn ?

---

### Post by Copper Bezel on 2011-02-06
> any ppa for cardapio ? by the way, copper bezel....
you r right, gnomenu was installed from the ppa and it runs fine when kept on panel. it behaves funny with awn... and yes, that was the last to load in awn !!!

I didn't know what y'all were talking about, which meant that I didn't know what I was talking about. I'd never seen GnoMenu before. I didn't realize that there was a carbon copy of the Vista start menu for the Gnome environment.

By the looks of it, yes, Cardapio + the Cardapio-AWN wrapper would be a reasonable alternative, and it has a lot of very nice features, but be warned that it does strange things if it's used on a bottom-edge dock, and it's still always the last applet to load. I personally don't use it as a main menu, but it can be called by keyboard shortcut as well.

The PPA is ppa:cardapio-team/unstable .

---

### Post by rvchari on 2011-02-07
thankx copper bezel,
i was away all day and just installed cardapio-awn.
ppa cardapio/unstable didnt work here, had to google as mentioned in my prev post with the link on how to for meerkat.
now cardapio is functioning good, seems to be light weight compared to gnomenu.
one thing is common, both loads last (gnomenu when it was working fine was the last to load too !!!)
thanks once again.
let me see how i can customizr it...
cardapio takes up the desktop theme looks by default. gnomenu had its own theme.

by the look and feel,(cardapio is lighter in comparision to gnomenu) i think cardapio will stay and gnomenu will make an exit...

---

### Post by kerry_s on 2011-02-07
:lolflag: i went the otherway, kept gnomenu & got rid of cardapio.

i been using cardapio for a long while now, so i think i just want a change. as long as gnomenu still mostly works, i'll keep it for awhile.

---

### Post by Copper Bezel on 2011-02-07
[QUOTE=rvchari]let me see how i can customizr it...
cardapio takes up the desktop theme looks by default. gnomenu had its own theme.

by the look and feel,(cardapio is lighter in comparision to gnomenu) i think cardapio will stay and gnomenu will make an exit...[/QUOTE]

Here's something I liked, then.

If you're using Compiz, put this in the window decoration matching field.

(any) & !(name=CardapioAwnWrapper.py)

That'll force Cardapio to draw as without decorations, like a menu, instead of having the redundant title bar and non-functional buttons. = )

---

### Post by rvchari on 2011-02-07
ya,
this way cardapio looks better and stripped off the unnecessary buttons !!! minimalistic ? !

---

### Post by rvchari on 2011-02-07
> **kerry_s said:**
> :lolflag: i went the otherway, kept gnomenu & got rid of cardapio.

i been using cardapio for a long while now, so i think i just want a change. as long as gnomenu still mostly works, i'll keep it for awhile.


hahaha...
its natural to change i was bored with gnomenu anyways and i got irritated after i saw the funny applet crash behaviour every now and then, i ll keep cardapio till something funny pops up and tries my patience to force me to search for an option !!!

---

### Post by tvst on 2011-02-12
Hi, I am one of the Cardapio developers. I just wanted to comment on a couple of things:

1) **Start-up speed:** If you don't use the Software Center plugin, just remove it and Cardapio will load several seconds faster. It will also consume some 30MB less memory :)

2) **Cardapio not launching with AWN**: This was a bug that was introduced a couple of weeks ago, but has been since been fixed. 
[https://bugs.launchpad.net/cardapio/+bug/716744](https://bugs.launchpad.net/cardapio/+bug/716744)

3) **Redundant title bar:** Actually, the title bar was added because several people complained that Cardapio looked out of place without it. If you feel otherwise, please open a bug report, and we'll let people give their 2 cents on this issue :)
[https://bugs.launchpad.net/cardapio](https://bugs.launchpad.net/cardapio)

Cheers

- Thiago

---

### Post by Frogs Hair on 2011-02-12
I've  been using the Awn testing PPA and the Gnomenu PPA for months without problems . This is the first time I have heard of Cardapio  .  I will have to check it out.

---

### Post by rvchari on 2011-02-12
> **tvst said:**
> Hi, I am one of the Cardapio developers. I just wanted to comment on a couple of things:

1) **Start-up speed:** **If you don't use the Software Center plugin, just remove it and Cardapio will load several seconds faster. It will also consume some 30MB less memory **:)

2) **Cardapio not launching with AWN**: This was a bug that was introduced a couple of weeks ago, but has been since been fixed. 
[https://bugs.launchpad.net/cardapio/+bug/716744](https://bugs.launchpad.net/cardapio/+bug/716744)

3) **Redundant title bar:** Actually, the title bar was added because several people complained that Cardapio looked out of place without it. If you feel otherwise, please open a bug report, and we'll let people give their 2 cents on this issue :)
[https://bugs.launchpad.net/cardapio](https://bugs.launchpad.net/cardapio)

Cheers

- Thiago
can u elaborate on how to remove the plugin? i love ubuntu and i learnt it myself (so to say i am not a programming guy.. i just love linux and learn more and more of its awesome ability).... its since last few months that i m on this forum and i love to learn...

---

### Post by tvst on 2011-02-12
Sure, here's how:
1) Right-click on Cardapio and choose "Properties".
2) A new window will pop up, entitled "Cardapio Properties". On that window, click on the "Plugins" tab.
3) Uncheck the box for the "Software Center" plugin.

That's it! 

Now close that window and try searching anything in Cardapio. You'll notice that the "Available software" section doesn't appear anymore, because the Software Center plugin has been disabled :)

---

### Post by Copper Bezel on 2011-02-12
tvst, 

Thanks for dropping in with that information! And I didn't mean to complain about the title bar - I can see how that's really a matter of preference.

I also noticed that the bug I mentioned with its "doing weird things" when attached to a bottom panel was also specific to the release I'd happened to download (and probably other factors on my machine,) because plugging it into AWN now, I don't have that problem anymore.

Thanks for the tip about the Software Center plugin!

---

### Post by kerry_s on 2011-02-12
i've gone back to the standard menu after gnomenu started doing weird things, like doubling the menus. i find i really don't use the menu all that much, so no since in having a custom 1.

---

### Post by Copper Bezel on 2011-02-12
Ugh, does anyone else use that thing? I don't understand the tiled menu. It takes at least one more click and a lot more mouse navigation to get to anything with that over the main Gnome menu. I use xfrun4, my pinned apps, and Cardapio (not the AWN version, but called by keystroke) more than the main menu, but I still find it comforting to have one, and since I use Cairo Main Menu, it comes with a Places icon, too, which I *do* use constantly.

I guess that's two questions. 1., am I crazy to need the security blanket of a main menu despite all the other options? And 2., am I crazy to think that the tiled menu is an awful idea?

---

### Post by tvst on 2011-02-12
Copper Bezel: No problem!

---

### Post by rvchari on 2011-02-12
> **tvst said:**
> Sure, here's how:
**1) Right-click on Cardapio and choose "Properties".**
2) A new window will pop up, entitled "Cardapio Properties". On that window, click on the "Plugins" tab.
3) Uncheck the box for the "Software Center" plugin.

That's it! 

Now close that window and try searching anything in Cardapio. You'll notice that the "Available software" section doesn't appear anymore, because the Software Center plugin has been disabled :)

i am attaching a screen shot of what is displayed when i right clik on the applet (which is sitting on awn dock) when i select preferences or edit , nothing happens....
when i was using gnomenu, i used to get those properties menu...

---

