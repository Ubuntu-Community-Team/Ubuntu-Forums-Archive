---
title: "Transparent Menu Bar"
date: 2009-09-27
forum: Desktop Environments
---

### Post by MelDJ on 2009-09-27
hi there, i would like to make my menu bar transparent.. tried looking around google and found nothing. Anyone know how to do it?

---

### Post by grturner on 2009-09-27
in gnome, right click on the menu bar and select properties. Select the background tab at the top. Select the Solid Color and there you can mess around with the transparency.

---

### Post by MelDJ on 2009-09-27
i want to change the bar not the panel. in the screenshot is the thing i want transparent.
thanks anyway:)

---

### Post by grturner on 2009-09-27
taken from [HTML]http://d0od.blogspot.com/2009/03/make-your-gnome-menus-transparent.html[/HTML]

```
Firstly, make sure you have the ‘Compiz Configuration Settings Manager’ installed (CCSM). You can easily find this in synaptic if you don’t.

   1. Open CCSM
   2. Go to Accessibility
   3. Go to Tab - Opacity Settings

Enter the settings as follows: -

    * dock 67
    * Menu 90
    * DropdownMenu 92
    * popupmenu 93

Preview these settings and then tweak to your liking. 

```

I'm sure you could tweak those settings even more. I've not personally tested this because I don't use compiz. It does seem the most concise thought.

---

### Post by MelDJ on 2009-09-27
* dock 67
    * Menu 90
    * DropdownMenu 92
    * popupmenu 93

where do i type these in?

---

### Post by grturner on 2009-09-27
[http://wiki.compiz-fusion.org/CCSM#Changing_options](http://wiki.compiz-fusion.org/CCSM#Changing_options)

I'm sorry that I can't help you more. compiz slows down my machine, but have a look at that website. Hopefully it can help you out more.

---

### Post by MelDJ on 2009-09-27
now i have it half transparent by enabling transparent menu in ubuntu tweak. but i want it completely transparent. Anyone?
thanks to [grturner]("http://ubuntuforums.org/member.php?u=770399"). appreciated your help:)

---

### Post by fela on 2009-09-27
> **MelDJ said:**
> now i have it half transparent by enabling transparent menu in ubuntu tweak. but i want it completely transparent. Anyone?
thanks to [grturner]("http://ubuntuforums.org/member.php?u=770399"). appreciated your help:)

I think the compiz plugin is 'brightness and opacity', or something like that. Go in there and modify your settings for each window - there's lots of guides on google aswell.

---

### Post by MelDJ on 2009-09-27
there is brightness and saturation, as i said, google isn't really helping me out now:(

---

### Post by MelDJ on 2009-09-27
my way of editing in ubuntu tweak has made all the menu bars transparent. is there a way to only make the panel menu bar transparent?

---

### Post by fela on 2009-09-27
> **MelDJ said:**
> my way of editing in ubuntu tweak has made all the menu bars transparent. is there a way to only make the panel menu bar transparent?

Probably yes, I'm afraid you'll have to search for it as I don't know exactly how it's done. Googling is an art and you have to practise to get it right. You can't just search in google 'how do I do this' and expect the right answer to come - it requires a bit of effort.

What about [this]("http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion")? Also check out [this]("http://wiki.compiz-fusion.org/WindowMatching").

---

### Post by kaivalagi on 2009-09-27
> **fela said:**
> What about [this]("http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion")?.

A web page linked off of your posted link should suffice: [http://arstechnica.com/open-source/news/2007/11/configuring-conditional-window-transparency-in-compiz.ars](http://arstechnica.com/open-source/news/2007/11/configuring-conditional-window-transparency-in-compiz.ars)

The OP will need to find out the name for the panel based menu, if it differs from all others? A bit of trial and error might get him there...

[COLOR="Blue"]edit: Looks like you've found a better site link since I posted my reply :)[/COLOR]

---

### Post by MelDJ on 2009-09-27
reading this :[http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion](http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion) has made me really confused. the link says got to opacify but i only have opacity. and some of the options seem to be from an older version of ccsm:confused:

---

### Post by fela on 2009-09-27
> **MelDJ said:**
> reading this :[http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion](http://lifehacker.com/322513/make-menus-transparent-in-compiz-fusion) has made me really confused. the link says got to opacify but i only have opacity. and some of the options seem to be from an older version of ccsm:confused:

Look for the plugin that is most similar to 'opacity settings'.

---

### Post by MelDJ on 2009-09-27
i tried changing pidgin to gnome-panel and then menu_bar but both did not work. pretty stumped here:(
i mean i changed the pidgin here: 
class=Pidgin & !title=Buddy List

---

### Post by fela on 2009-09-27
> **MelDJ said:**
> i tried changing pidgin to gnome-panel and then menu_bar but both did not work. pretty stumped here:(
i mean i changed the pidgin here: 
class=Pidgin & !title=Buddy List

Just replace all of that with class=panel, or whatever. You don't need any pidgin stuff.

---

### Post by MelDJ on 2009-09-27
thats what i did. i just took the pidgin as an example. i tried class=panel, class=gnome-panel, class=gnome-panel, all to no avail..:(

---

### Post by kaivalagi on 2009-09-27
> **MelDJ said:**
> thats what i did. i just took the pidgin as an example. i tried class=panel, class=gnome-panel, class=gnome-panel, all to no avail..:(

I think it is case sensitive, try Gnome-panel

---

### Post by MelDJ on 2009-09-27
> **kaivalagi said:**
> I think it is case sensitive, try Gnome-panel

still nothing..

---

### Post by kaivalagi on 2009-09-27
> **MelDJ said:**
> still nothing..

Sounds like what you want isn't possible right now...anyone else got any ideas?

---

### Post by kelvin spratt on 2009-09-27
As already mentioned  its all done in Compiz setting manager in opacity in older versions,
opacity Brightness and Saturation in later versions. Under window specific settings, click on edit and enter your settings. 
This is mine,
 name=gnome-panel | type=Menu | tooltip |  PopupMenu | DropdownMenu  or you can enter them separately on different lines.

---

### Post by MelDJ on 2009-09-28
have i typed it right? please see the screenshot

---

### Post by MelDJ on 2009-09-28
bump

---

### Post by kaivalagi on 2009-09-28
> **MelDJ said:**
> have i typed it right? please see the screenshot

If it worked then yes, if it didn't then no...

You may be best asking if what you want is even possible (only affecting panel based menus and not others) on the IRC based #compiz channel, which resides at irc.freenode.net...I assume you know about IRC? If not read here: [http://en.wikipedia.org/wiki/Irc](http://en.wikipedia.org/wiki/Irc)

You can use Pidgin to access IRC in Ubuntu by adding an IRC protocol based account for irc.freenode.net. See attached screenshot for a brief howto...just pick a username to be known as...

---

### Post by MelDJ on 2009-09-29
okay. will try it. Thank you everyone for trying to help me out:)

---

### Post by fela on 2009-09-30
Just a thought, but try:

```
class=gnome-panel & (type=Menu | Tooltip | PopupMenu | DropDownMenu)
```

You could also use the 'grab window' feature to grab the gnome panel's class (select class, grab, click on the panel), and then add another parameter to the same rule, with the menus options, and make sure to give the whole of it an 'and' relationship to the 'gnome panel' parameter. Hope you get what I mean!

My only worry is that if you were to make the menus transparent with compiz, I think it also makes the text transparent - so you can't actually have full transparency and still see the text.

---

### Post by Kognit on 2010-04-02
Just enter the "!" without the quotes and this will apply to all aplications

---

