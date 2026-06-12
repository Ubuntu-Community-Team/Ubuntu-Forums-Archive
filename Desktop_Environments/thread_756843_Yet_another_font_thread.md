---
title: "Yet another font thread"
date: 2008-04-16
forum: Desktop Environments
---

### Post by melat0nin on 2008-04-16
Hi all

I've been playing around with my fonts, and I've found what I think is the best set-up for clear, smooth fonts.

Using 'sudo dpkg-reconfigure fontconfig-config' I set the settings to Native, Automatic and Yes.  This gives me really nice fonts when using the msttfcorefonts package (and other truetype fonts taken from my Windows installation).  All well and good.

The problem comes on certain webpages, which seem to use unusual fonts or something, but the upshot is the look _**awful**_ - almost unreadable.

Here's an example:

[IMG]http://i26.tinypic.com/2u7q13t.png[/IMG]

As you can see the interface fonts (main menu, firefox, verdana on the webpage etc) look great.  The main body of the blog looks utterly horrendous, however.

Any thoughts on how to get a level of consistency across all fonts on my system?  Help and suggestions much appreciated :)

---

### Post by hvthao on 2008-04-16
Maybe you can use Autohinter instead of Native.

---

### Post by erginemr on 2008-04-16
If you are into the font smoothing business, I suggest you to have a look at here:
[http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)

and try the config file given there. I have been using it with my regular (Ubuntu based) fonts and it looks pretty good.

---

### Post by melat0nin on 2008-04-16
> **erginemr said:**
> If you are into the font smoothing business, I suggest you to have a look at here:
[http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)

and try the config file given there. I have been using it with my regular (Ubuntu based) fonts and it looks pretty good.

I'm really not a fan of that effect, it makes my fonts looks fat and blurry.  Here is what they are like with that .fonts.conf file in my home folder:

[[IMG]http://img183.imageshack.us/img183/8573/withfontsconfas6.th.png[/IMG]](http://img183.imageshack.us/my.php?image=withfontsconfas6.png)

and without it (I just deleted it and logged out and back in):

[[IMG]http://img245.imageshack.us/img245/7710/withoutfontsconfjd7.th.png[/IMG]](http://img245.imageshack.us/my.php?image=withoutfontsconfjd7.png)

You can see a few differences.  The Ubuntu main menu font is slightly fatter, and seems less crisp in the first image. Also, the fonts in Firefox are far less crisp (on the tab, and all over the BBC News homepage - also, the example blog with the horrible font is not improved at all by that configuration).  Certain parts of letters are overly-weighted, too (like the uppercase S).


@ hvthao: I think the Autohinter is actually what the configuration suggested by erginemr switches on.  I also did plenty of experiments with fonts, checking the different configurations provided by fontconfig-config and setting it to Native instead of Autohinter helped the above blurriness in all cases.  

The only thing that it still problematic is the odd case of horrible fonts on sites such as [http://lockerbiecase.blogspot.com/](http://lockerbiecase.blogspot.com/) .

Thanks for your replies so far :)

---

### Post by melat0nin on 2008-05-08
Apologies for resurrecting this thread, but I'm on my mother's Ubuntu system (which is still running Feisty).  When I installed it I did one of the font hacks, and the fonts look fantastic:

Here's a screenshot of the same site on her machine:

[IMG]http://i30.tinypic.com/124ixco.png[/IMG]

It looks great, better than Windows, both the HTML fonts and the UI fonts.

Trouble is, I can't remember which font settings I changed/hacked.  I'm pretty sure there was replacement of files regarding hinting or something, though.

**With that in mind, which files relate to font display, and is it possible for me to copy them over to my Hardy installation on my own machine to get the same quality of fonts?**

---

### Post by erginemr on 2008-05-08
Really, great looking fonts. :shock:

Can you please try this to see if you can get the same effect:
[http://ubuntuforums.org/showpost.php?p=4049873&postcount=172](http://ubuntuforums.org/showpost.php?p=4049873&postcount=172)

---

### Post by melat0nin on 2008-05-08
> **erginemr said:**
> Really, great looking fonts. :shock:

Can you please try this to see if you can get the same effect:
[http://ubuntuforums.org/showpost.php?p=4049873&postcount=172](http://ubuntuforums.org/showpost.php?p=4049873&postcount=172)

I will be at my own machine tomorrow and I will try this then.  Thanks for the suggestion :)

---

