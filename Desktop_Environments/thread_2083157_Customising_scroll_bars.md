---
title: "Customising scroll bars ?"
date: 2012-11-11
forum: Desktop Environments
---

### Post by grey1beard on 2012-11-11
I would like to change the appearance of the scroll bars to make them more visible on my wife's laptop running 12.04, with Gnome, rather than Unity.

Her Ubuntu usage would be greatly enhanced if she could see them more easily.
Currently we are running the Radiance theme, where the scroll bars are 20% grey over a background of 30% grey(I'm guessing), so the contrast couldn't be much worse.

She also needs black lettering on a white backgound, so if anyone could suggest a change of theme that might improve matters, I'd be grateful.

I've had a search, but most screen shots seem to concentrate on the wallpaper, so progress is a bit slow in trying to find something suitable.

Thanks
John

---

### Post by vasa1 on 2012-11-11
Hi, there are quite a few threads here about customizing scrollbars. But you'll have to edit files to do so. There's one GUI-based program called GNOME Color Chooser that will allow the "click, click, click" approach but that's only for GTK2 apps, a gradually vanishing species.

I have customized all the scrollbars I come across, GTK2 or 3, but that has been with Unity, Xfce and Lubuntu. I have no experience with the Gnome DE.

---

### Post by grey1beard on 2012-11-12
Hi vasa1,
Thanks for your response.
Since my original post, I've found a page on the askubuntu.com site that offers various ideas.

I've done a preliminary read through of my gtk-3.widgets.css file, and found the code for the scroll bars.
Unfortunately for me the code appears on screen so widely laid out with line breaks that I'm having some difficulty in reading it. Also the scroll bar 'sliders' and troughs have gradients, so again, each line of code is somewhat extended.

When I'm feeling a little more confident, I'll see what a single change makes on my screen before changing SWMBO's laptop ;)

And I will make a backup copy before, I promise !

Regards
John

---

### Post by kansasnoob on 2012-11-12
Since you're talking about 12.04, which is supported until April 2017, you might find some of my notes here helpful:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I'll grant you that's written for the "classic (no effects)" session but those parts related to theming and the scrollbars should apply to Unity and Gnome Shell also.

Specifically regarding themes look here:

[http://ubuntuforums.org/showpost.php?p=11993655&postcount=70](http://ubuntuforums.org/showpost.php?p=11993655&postcount=70)

You'll notice the first section refers to default settings and how to determine the existing settings before changing anything. The rest focuses on the Zukitwo themes but there are other themes available from that source for 12.04:

[https://launchpad.net/~webupd8team/+archive/themes?field.series_filter=precise](https://launchpad.net/~webupd8team/+archive/themes?field.series_filter=precise)

[ATTACH]227072[/ATTACH]

Regarding scrollbars in general I'm a bit unsure if you're using the overlay scrollbars or not :confused:

In step #8 of that first link I describe how to drop the overlay scrollbars on a per-user basis, but you will notice that a few apps requiring root access will still display the overlay scrollbars. So they can be more **[COLOR="Red"]permanently removed[/COLOR]** like this:

[http://ubuntuforums.org/showpost.php?p=12180327&postcount=152](http://ubuntuforums.org/showpost.php?p=12180327&postcount=152)

Note: I highlighted "permanently" because getting the overlay scrollbars back is NOT as easy as just reinstalling the pkgs!!!!

**One final note**: It appears that the classic sessions are being deprecated altogether either in 13.04 or 13.10 so I highly recommend that classic DE users stick with 12.04 which is supported until April 2017. I strongly suspect that things will be hashed out one way or another by mid 2016 :)

---

### Post by vasa1 on 2012-11-12
> **kansasnoob said:**
> ...
Regarding scrollbars in general I'm a bit unsure if you're using the overlay scrollbars or not :confused:
...

From OP's second post it looks like it's the conventional scrollbars (IMO) since reference is made to sliders and troughs and gradients:
"[I]I've done a preliminary read through of my gtk-3.widgets.css file, and found the code for the scroll bars.
Unfortunately for me the code appears on screen so widely laid out with line breaks that I'm having some difficulty in reading it. Also the scroll bar 'sliders' and troughs have gradients, so again, each line of code is somewhat extended[/I]."

From what I've seen (in 12.04), the overlay scrollbar code is pretty brief.

---

### Post by kansasnoob on 2012-11-12
> **vasa1 said:**
> From OP's second post it looks like it's the conventional scrollbars (IMO) since reference is made to sliders and troughs and gradients:
"[I]I've done a preliminary read through of my gtk-3.widgets.css file, and found the code for the scroll bars.
Unfortunately for me the code appears on screen so widely laid out with line breaks that I'm having some difficulty in reading it. Also the scroll bar 'sliders' and troughs have gradients, so again, each line of code is somewhat extended[/I]."

From what I've seen (in 12.04), the overlay scrollbar code is pretty brief.

Thanks. I suspected that was the case but I always try to err on the side of caution :)

It is quite true that the standard scrollbar color "contrast" rather stinks with the standard themes.

Clearlooks/now Clearwaita is by far the best but I've tried Clearwaita from a couple of different sources and always encountered problems, so I chose the Zukitwo themes because they do seem to just work, and they have a slightly better color contrast :)

---

### Post by grey1beard on 2012-11-12
Hi  kansasnoob, and vasa1. 
Yes, it's the classic scroll bars we're using.
I found the overlays concept bizarre. I know they wanted to produce an uncluttered look, but that seemed a bit extreme, so I've disabled them, but not removed them.
You've given me a vast amount of reading to do, kansasnoob, so I'll return when I've got through it.
I'll also look at Zukitwo theme, as a new theme might be easier to impliment ;)
Regards
John

---

### Post by vasa1 on 2012-11-12
> **grey1beard said:**
> ... 
Yes, it's the classic scroll bars we're using....
John
BTW, which browser is being used?

---

### Post by grey1beard on 2012-11-12
Firefox 16.0.1

John

---

### Post by vasa1 on 2012-11-12
> **grey1beard said:**
> Firefox 16.0.1

John

If the scrollbars in Firefox are an issue, you could consider installing the [Stylish extension]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") and then add code to make at least the browser's scrollbars as contrasty as you like.

The advantage of that approach is that your Firefox scrollbars will be unaffected by changes in themes.

You can find a whole bunch of scrollbar styles @ userstyles.org.

---

### Post by grey1beard on 2012-11-12
vasa, that's brilliant.
It is the Firefox browser that is most used by my wife, in fact almost exclusively.
Thanks,
John

---

### Post by vasa1 on 2012-11-12
> **grey1beard said:**
> vasa, that's brilliant.
It is the Firefox browser that is most used by my wife, in fact almost exclusively.
Thanks,
John
You could even make your own style (once you've installed Stylish). This is the spartan code I use. Obviously, you can change whatever you want but the first line is essential:
```
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

scrollbar { -moz-appearance: none !important; background: #888 !important}
scrollbar[orient="vertical"] { width: 8px !important}
scrollbar[orient="horizontal"] { height: 8px !important}
scrollbar thumb {
-moz-appearance: none !important;
border-radius: 4px !important;
background: #003263 !important;
min-width: 8px !important;
max-width: 8px !important;
border: 1px !important;
}
scrollbar thumb:hover {
background: pink !important;
}
scrollbarbutton { display: none !important}

```

BTW, scrollbars can only be tweaked with the help of the Stylish extension, unlike a lot of other things that can be done via userContent.css and userChrome.css.

---

### Post by grey1beard on 2012-11-12
I've still got lots to learn re writing code.
Can you explain the significance of the > ! important entries.
And is the 'thumb' entry the movable part, and the 'button', the top and bottom single line movement controls ?

mtia
John 

PS I now have highly visible black controls on the scroll bar :)

---

### Post by grey1beard on 2012-11-12
OK, I've found out how to edit the colours, but not the shape of the ends of the slider.
Is it possible to get the ends rounded ? 
Is it the line 
> -moz-appearance: none !important;
or is it something new that I need to insert ?

John

---

### Post by SantaFe on 2012-11-12
You might also check out: NewScrollbars (aka NoiaScrollbars)  [https://addons.mozilla.org/en-US/firefox/addon/noiascrollbars/]("https://addons.mozilla.org/en-US/firefox/addon/noiascrollbars/")  It lets you adjust how the scrollbars look.  And has a rounded ends option.

---

### Post by vasa1 on 2012-11-12
> **SantaFe said:**
> You might also check out: NewScrollbars (aka NoiaScrollbars)  [https://addons.mozilla.org/en-US/firefox/addon/noiascrollbars/]("https://addons.mozilla.org/en-US/firefox/addon/noiascrollbars/")  It lets you adjust how the scrollbars look.  And has a rounded ends option.
The thing about Stylish is that it can be used for other things as well. To that extent, if I were to install an extension to tweak scrollbars, I'd prefer Stylish rather than one that's specific for the purpose.
Stylish also has a pretty active community.

---

### Post by vasa1 on 2012-11-12
@John:

**!important** ensures that the line containing it is implemented overriding preferences of the web site etc.

Here's a list of elements: [http://css-tricks.com/custom-scrollbars-in-webkit/](http://css-tricks.com/custom-scrollbars-in-webkit/)
(Even though it's for webkit browsers, the nomenclature is the same.)

The ends should be governed by the radius: In my example, it is this: 
border-radius: **4px** !important;
The higher the value, the more rounded. If you want absolutely flat ends, you could comment out (render non-functional) that line by using **/*** and ***/** to indicate a comment like so:
/*This is a comment*/

**-moz-appearance: none !important;** is a mantra that shouldn't be used loosely but it prevents certain (unwanted) default things from happening, AFAICT.

One more thing, to be sure that the changes take effect, exit Firefox completely (no pinned tabs, etc) and restart.

Edit: I added a bit to the previous code to allow for the "thumb" to appear colored differently when the mouse hovers over the thumb.

---

### Post by grey1beard on 2012-11-13
Hi SantaFe, and thanks for the link.

Vasa, I'm still having problems with rounding the ends of the 'thumb slider'.
It started with the border radius set to 15px, so I changed it to 5px first, and re started Firefox, but no change. I then pushed it to 25px, but it is still flat across the end.
Have attached a screen shot, taken after rebooting.
Any ideas ?
John

---

### Post by vasa1 on 2012-11-13
> **grey1beard said:**
> Hi SantaFe, and thanks for the link.

Vasa, I'm still having problems with rounding the ends of the 'thumb slider'.
It started with the border radius set to 15px, so I changed it to 5px first, and re started Firefox, but no change. I then pushed it to 25px, but it is still flat across the end.
Have attached a screen shot, taken after rebooting.
Any ideas ?
John
1: change** -moz-**border-radius to just border-radius
2: Next time you could just copy the code and paste it here between code (#) tags.

---

### Post by vasa1 on 2012-11-13
BTW, how old is that style you're using?
Just like everything else, it may be outdated ;)
IIRC, a few -moz prefixes have been "deprecated" and don't work anymore.


Edit: if it's this ([http://userstyles.org/styles/13601/scrollbars-colored-solid-combo-style-5](http://userstyles.org/styles/13601/scrollbars-colored-solid-combo-style-5)), it was last updated on Apr 7, 2011 and the "deprecation" took place later.

---

### Post by vasa1 on 2012-11-13
FYI, here's some reading on the -moz-border ... to just border:
> Note: Support for the prefixed version (-moz-border-radius) was removed in Gecko 13.0 (Firefox 13.0 / Thunderbird 13.0 / SeaMonkey 2.10).
from [https://developer.mozilla.org/en-US/docs/CSS/border-radius](https://developer.mozilla.org/en-US/docs/CSS/border-radius)

Edit: moral of the story is to stay with new styles or those being maintained regularly. You could also provide feedback on the page explaining the issue. "Barbie" used to be quite active some time ago. Maybe she still is?

---

### Post by grey1beard on 2012-11-13
So, it's not quite back to square 1 then. At least I'm learning !

Ijust picked the 'Solid Combo'style 5 as it was the first that I came to in the vast oceans of possibilities that mentioned changing the colour.
Barbie put it back up in 2011, but I'll have another explore on later dated styles.
I take your point about the feedback, so I'll have a go at that as well.
Many thanks for the help so far.
John

---

### Post by vasa1 on 2012-11-14
> **grey1beard said:**
> ...
She also needs black lettering on a white backgound, so if anyone could suggest a change of theme that might improve matters, I'd be grateful.
...
And what about this? If you have questions it maybe better to do it in a new thread. In that you could specify in which apps she needs black on white.

---

### Post by grey1beard on 2012-11-14
Good Morning vasa1.
In truth, I now realise she only uses Firefox, so just customising that will probably solve her needs.
It's me that spends too much time in front of the screen ;)

Regards
John

---

### Post by vasa1 on 2012-11-14
> **grey1beard said:**
> ...
In truth, I now realise she only uses Firefox, so just customising that will probably solve her needs.
...
Well, as I suggested, you could start a new thread on this with examples of sites that need to be "fixed".

At the outset, you should know that fiddling with colors could have "consequences" because some web designers use colors in ways that aren't really friendly to those certain preferences. For example, I prefer black text on a gray background and not a white background. As soon as I specify a background color, background images take a hit.

---

### Post by grey1beard on 2012-11-14
Good point, vasa1.
I do have a small experience of html coding, though it's been some time since I set up my own pages, w w w.fanmaker.co.uk , and a lot has changed since then !

I liked your signature links, by the way, so thanks for those as well.
I'm moving slowly from classical to folk, having started restoring a locally made old hammered dulcimer, but that's another story for another place.
Regards
John

---

