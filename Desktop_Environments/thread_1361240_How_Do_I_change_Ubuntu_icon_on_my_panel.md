---
title: "How Do I change Ubuntu icon on my panel??"
date: 2009-12-21
forum: Desktop Environments
---

### Post by bix15 on 2009-12-21
Hey guys!
I have a question regarding how to change the default ubuntu icon on my panel....

Notice how on the attached thumbnail down below of my desktop, in the bottom left corner, There sits the same old, boring ubuntu logo =(

however in this link, this fella knows how to do it right!

[http://gnome-look.org/CONTENT/content-pre1/79463-1.jpg](http://gnome-look.org/CONTENT/content-pre1/79463-1.jpg)

I'm not saying I want a replica but I would like to know how I can change that logo. I haven't been able to do that with any themes I install or anything of the sort. 

Can anybody help me??

Oh and by the way Im running Ubuntu Karmic if that helps at all.....

---

### Post by itang sanjana on 2009-12-21
*"Following these instructions, you can put any image you want in that space .."* See tip #2: [https://help.ubuntu.com/community/QuickTips](https://help.ubuntu.com/community/QuickTips) .. HTH

---

### Post by bix15 on 2009-12-21
sorry, no luck =(

---

### Post by mzhou on 2009-12-21
Launch gconf-editor, then open apps>panel>objects on the left pane. Locate the object that says "menu_object" next to object_type (on the right pane). Then select "use custom icon". Under "custom icon", type in the path of the icon you wish to use.

Alternatively, you could use Gnomenu and set a custom icon.

Hope this helps!

---

### Post by spiderbatdad on 2009-12-21
yeah those are a little outdated. You have to actually know where the icon is located now...and I'm not sure, but you might try changing the icon of /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
the logo you use will need to be .png and 48x48 in size, also need to be named distributor-logo.png

---

### Post by drs305 on 2009-12-21
This works in Karmic:

Open gconf-editor and do a search for "menu-object" (note spelling).

Arrow down the "/apps/panel/objects" entries found in the lower panel. In the upper right panel, look for the menu_path of "applications:/"

Enable "use_custom_icon" and put the path/name of your desired image in the "custom_icon" entry.

Added: If you want to change the "Main Menu" icon added elsewhere on the panel, do the same thing and look for the "tooltip" "Main Menu" entry in the right panel.

---

### Post by mzhou on 2009-12-21
> **spiderbatdad said:**
> yeah those are a little outdated. You have to actually know where the icon is located now...and I'm not sure, but you might try changing the icon of /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
the logo you use will need to be .png and 48x48 in size, also need to be named distributor-logo.png

The gconf-editor method works fine on Karmic and doesn't require you to dig for the distributor-logo icon or to use a .png file of that size - I just tried it out with a huge jpeg image just for kicks and it actually worked.

---

### Post by spiderbatdad on 2009-12-21
> **mzhou said:**
> The gconf-editor method works fine on Karmic and doesn't require you to dig for the distributor-logo icon or to use a .png file of that size - I just tried it out with a huge jpeg image just for kicks and it actually worked.

Thanks for this info.

---

### Post by hariks0 on 2009-12-22
You can do this graphically using Ubuntu-tweak. BTW, how do you have the media controls [Previous, play/pause,Next]in your panel?:lolflag:

---

### Post by bix15 on 2009-12-26
thanks bro! It works!! XD
And it's a heck of a lot easier to use than the other methods!

And to answer your question about the [Play/pause] buttons on my panel, That is a program, or rather a panel app, that allows me to control my media player at the touch of a button =)
It's called Panflute.....  [https://launchpad.net/~kuliniew/+archive/ppa](https://launchpad.net/~kuliniew/+archive/ppa)
just copy/paste the PPA into your software sources list, find "panflute" in synaptic. Once you have installed it from synaptic, right-click on your panel>Add To Panel>Panflute Applet....
You have the option to link it to a number of different media players....I chose rythmbox =)
Enjoy! and thanks again!!!

---

### Post by hariks0 on 2009-12-27
> **bix15 said:**
> The [Play/pause] buttons on my panel is a program, or rather a panel app, that allows me to control my media player at the touch of a button =)
It's called Panflute.....  [https://launchpad.net/~kuliniew/+archive/ppa](https://launchpad.net/~kuliniew/+archive/ppa)
just copy/paste the PPA into your software sources list, find "panflute" in synaptic. Once you have installed it from synaptic, right-click on your panel>Add To Panel>Panflute Applet....
You have the option to link it to a number of different media players....I chose rythmbox =)
Enjoy! and thanks again!!!

Welcome and thank you for panflute. A smal correction though, the line I had to add into the sources is ***ppa:kuliniew/ppa***

---

### Post by phillychease on 2009-12-27
> **hariks0 said:**
> You can do this graphically using Ubuntu-tweak. BTW, how do you have the media controls [Previous, play/pause,Next]in your panel?:lolflag:
[http://www.kuliniewicz.org/music-applet/](http://www.kuliniewicz.org/music-applet/)
awesome isnt it? :popcorn:

---

