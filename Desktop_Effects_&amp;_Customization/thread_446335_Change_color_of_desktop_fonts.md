---
title: "Change color of desktop fonts?"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by jackmc on 2007-05-16
Hey,

I want to make my desktop fonts white, and remove the rectangle around them. How can I do this? Img 1 is what Mine look like, img 2 is what I want

let me know if you need clarification

Thanks :)

---

### Post by Ziox on 2007-05-16
go to System > Preference > Themes.  Select Clearlooks or some other theme, then hit customize on the side, and hit the color tab.  If you can't edit the colors tab, then you need switch to a different theme.

---

### Post by dxdemetriou on 2007-05-16
I had ~/.gtkrc-2.0 with something like:

> style "desktop-icon" {
     		#1 for activate
	NautilusIconContainer::frame_text = 1
      	text[NORMAL] = "blue"
	#base[NORMAL] = "white"
		#Transparency     
	NautilusIconContainer::normal_alpha = 35
}
#class "GtkWidget" style "desktop-icon"
widget_class "*DesktopIcon*" style "desktop-icon"


This worked well with Breezy/Dapper/Edgy, but not with Feisty
The problem is that I can't set the transparency.  All others works well
anybody knows if is there something like the "NautilusIconContainer::normal_alpha", that works on Feisty?
I prefer this method instead from themes

---

### Post by jackmc on 2007-05-17
This is what I tried too, but id did nothing for me. Changing theme isn't really what I want to do if I can avoid it.

---

### Post by notwen on 2007-05-17
I wouldn't mind knowing this as well.  Since I've modified my Gnome Panel text color by creating my own .gtkrc-2.0  Instead of the transparent BG for icon text I have black text over a white background.  Anyway to get text w/ no background?  Hope that makes sense. =p

---edit---
here's a [link]("http://ubuntuforums.org/showthread.php?p=2494544") to an older thread where I asked the same question w/ no response, really hope it's possible.

---

### Post by notwen on 2007-05-18
*bump*

---

### Post by jackmc on 2007-05-20
Bump

Still cant do it, someone must know how!

---

### Post by elchato on 2007-05-22
how can you change the font?

---

### Post by jackmc on 2007-05-22
System, preferences, font.

You cant change the color there though.

---

### Post by crimesaucer on 2007-05-23
You can modify your gtkrc file in which ever gtk-2.0 theme you are using, for the Human theme: /usr/share/themes/Human/gtk-2.0/gtkrc


....and then mess around with all of these settings, these are from the Human theme:

```

fg[NORMAL]        = "#101010"
fg[PRELIGHT]      = "#000000"
fg[ACTIVE]        = "#000000"
fg[SELECTED]      = "#ffffff"
fg[INSENSITIVE]   = "#B3AFAB"

``` 

and these:

```

text[NORMAL]      = "#000000"
text[PRELIGHT]    = "#000000"
text[ACTIVE]      = "#000000"
text[SELECTED]    = "#000000"
text[INSENSITIVE] = "#B3AFAB"

```

...but before you do this, make a back-up of the gtkrc file so you don't ruin the default Human gtkrc theme.

....you can even just use the terminal to copy it with a new name to your themes folder like this:

```

blah@blah-blah:~$ cd /usr/share/themes
blah@blah-blah:/usr/share/themes$ ls
Adept                          Keramik         Totem
AgingGorilla                   Kindaker        Trench
Agua                           Kleanux         Triviality
Agualemon                      Kokodi          Tubular
Alternate                      Koynacity       TUX
Amaranth                       LegacyHuman     Tyrex
Atlanta                        Linea           Variation
Atlanta2                       LineArt         Vicious Jet
B5                             Lush            Wallis
B6                             MagicChicken    Wasp
Basix                          Meenee          Waza
BBS                            Metabox         Wildbush
Beastie                        Microcurve      Xfce
Biz                            Microdeck       Xfce-4.0
Blackwall                      Microdeck2      Xfce-4.2
Bright                         Microdeck3      Xfce-b5
BrushedChrome                  Microgui        Xfce-bamboo
Buzz                           Mist            Xfce-basic
CleanIce                       Mofit           Xfce-cadmium
CleanIce-Dark                  Moheli          Xfce-chocolate
CleanIce-Debian                Next            Xfce-curve
Clearlooks                     Nuvola          Xfce-dawn
ClearlooksAlternative          Nuvola-old      Xfce-dusk
Coldsteel                      OkayishChicken  Xfce-glow
Coolclean                      Ops             Xfce-glow_gradient
CortlandChicken                Opta            Xfce-glow_gradient_b
Crux                           Oroborus        Xfce-glow_gradient_b2
Cruxish                        Outdoors        Xfce-glow_gradient_c
Curve                          Perl            Xfce-glow_orange
Daloa                          Pills           Xfce-glow_orange2
Default                        Piranha         Xfce-kde2
Default-4.0                    Platinum        Xfce-kolors
Default-4.2                    Prune           Xfce-light
Defcon-IV                      Quiet-purple    Xfce-milk
Eazel-blue                     Quinx           Xfce-mint
Elberg                         R9X             Xfce-newname
Emacs                          Raleigh         Xfce-orange
Esco                           Redmond         Xfce-purple_chrome
Exocet                         RedmondXP       Xfce-purple_chrome_b
Fbx                            Resilience      Xfce-purple_sage
G2                             Retro           Xfce-redmondxp
Galaxy                         Sassandra       Xfce-rusted
Gaudy                          Silicon         Xfce-rusted_fliped
Gelly                          Silverado       Xfce-rusted_gradient
Glider                         Simple          Xfce-rusted_silver
Glossy                         Slick           Xfce-rusty_charcoal
Gnububble                      Slimline        Xfce-rusty_charcoal_b
Gorilla                        Smallscreen     Xfce-rusty_milk
Gray                           Smoothwall      Xfce-rusty_milk_new
Gtk                            SphereCrystal   Xfce-rusty_milk_new2
HighContrastInverse            Stoneage        Xfce-rusty_new_b
HighContrastLargePrintInverse  Symphony        Xfce-rusty_new_c
Human                          Synthetic       Xfce-saltlake
Iceg                           Tabs            Xfce-silver_bw
Industrial                     Tgc             Xfce-silver_white
IndustrialTango                Tgc-large       Xfce-smooth
Katiola                        Therapy         Xfce-stellar
Kde                            ThinIce         Xfce-winter
Kde1                           Today
blah@blah-blah:/usr/share/themes$ sudo cp -r Human /usr/share/themes/Human2_new
Password:
blah@blah-blah:/usr/share/themes$ ls
Adept                          Kde1            Today
AgingGorilla                   Keramik         Totem
Agua                           Kindaker        Trench
Agualemon                      Kleanux         Triviality
Alternate                      Kokodi          Tubular
Amaranth                       Koynacity       TUX
Atlanta                        LegacyHuman     Tyrex
Atlanta2                       Linea           Variation
B5                             LineArt         Vicious Jet
B6                             Lush            Wallis
Basix                          MagicChicken    Wasp
BBS                            Meenee          Waza
Beastie                        Metabox         Wildbush
Biz                            Microcurve      Xfce
Blackwall                      Microdeck       Xfce-4.0
Bright                         Microdeck2      Xfce-4.2
BrushedChrome                  Microdeck3      Xfce-b5
Buzz                           Microgui        Xfce-bamboo
CleanIce                       Mist            Xfce-basic
CleanIce-Dark                  Mofit           Xfce-cadmium
CleanIce-Debian                Moheli          Xfce-chocolate
Clearlooks                     Next            Xfce-curve
ClearlooksAlternative          Nuvola          Xfce-dawn
Coldsteel                      Nuvola-old      Xfce-dusk
Coolclean                      OkayishChicken  Xfce-glow
CortlandChicken                Ops             Xfce-glow_gradient
Crux                           Opta            Xfce-glow_gradient_b
Cruxish                        Oroborus        Xfce-glow_gradient_b2
Curve                          Outdoors        Xfce-glow_gradient_c
Daloa                          Perl            Xfce-glow_orange
Default                        Pills           Xfce-glow_orange2
Default-4.0                    Piranha         Xfce-kde2
Default-4.2                    Platinum        Xfce-kolors
Defcon-IV                      Prune           Xfce-light
Eazel-blue                     Quiet-purple    Xfce-milk
Elberg                         Quinx           Xfce-mint
Emacs                          R9X             Xfce-newname
Esco                           Raleigh         Xfce-orange
Exocet                         Redmond         Xfce-purple_chrome
Fbx                            RedmondXP       Xfce-purple_chrome_b
G2                             Resilience      Xfce-purple_sage
Galaxy                         Retro           Xfce-redmondxp
Gaudy                          Sassandra       Xfce-rusted
Gelly                          Silicon         Xfce-rusted_fliped
Glider                         Silverado       Xfce-rusted_gradient
Glossy                         Simple          Xfce-rusted_silver
Gnububble                      Slick           Xfce-rusty_charcoal
Gorilla                        Slimline        Xfce-rusty_charcoal_b
Gray                           Smallscreen     Xfce-rusty_milk
Gtk                            Smoothwall      Xfce-rusty_milk_new
HighContrastInverse            SphereCrystal   Xfce-rusty_milk_new2
HighContrastLargePrintInverse  Stoneage        Xfce-rusty_new_b
Human                          Symphony        Xfce-rusty_new_c
Human2_new                     Synthetic       Xfce-saltlake
Iceg                           Tabs            Xfce-silver_bw
Industrial                     Tgc             Xfce-silver_white
IndustrialTango                Tgc-large       Xfce-smooth
Katiola                        Therapy         Xfce-stellar
Kde                            ThinIce         Xfce-winter
blah@blah-blah:/usr/share/themes$ 

```

...Now all I did was make a second copy of the default Human theme called Human2_new...so now all I have to do is play with the different hex color codes to change any font color for any part of my OS. I can switch between Human, and Huma2_new to compare my changes I make.

you can also install: thewidgetfactory

...from Synaptic, and then run:

```
twf
```

...in terminal to see where your changes take place. 

I usually just change a color of a text, or a widget's size on the gtkrc, and then save it, and quickly switch to a different theme so I can quickly switch back to see the changes I made for my new custom theme.

---

### Post by klato on 2007-05-23
what theme are you running there?

---

### Post by crimesaucer on 2007-05-23
Well, I use my own themes, they are all over in the Xfce section.

I just showed how to use the default Human theme, and showed the colors of the default Human theme because everybody has it installed in ubuntu and xubuntu. So it was an easy example.

This is my current theme that I made last night:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-9.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-8.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-8.png)

---

### Post by notwen on 2007-05-24
> **crimesaucer said:**
> You can modify your gtkrc file in which ever gtk-2.0 theme you are using, for the Human theme: /usr/share/themes/Human/gtk-2.0/gtkrc


....and then mess around with all of these settings, these are from the Human theme:

```

fg[NORMAL]        = "#101010"
fg[PRELIGHT]      = "#000000"
fg[ACTIVE]        = "#000000"
fg[SELECTED]      = "#ffffff"
fg[INSENSITIVE]   = "#B3AFAB"

``` 

and these:

```

text[NORMAL]      = "#000000"
text[PRELIGHT]    = "#000000"
text[ACTIVE]      = "#000000"
text[SELECTED]    = "#000000"
text[INSENSITIVE] = "#B3AFAB"

```



and this would affect only the icon text I presume? =]

---

### Post by ZipoTe on 2007-07-14
time since mi last post :P...

well i have the same problem. today I installed feisty fawn and modified the .gtkrc-2.0 to match the desktop fonts with the wallpaper but... as someone mentioned here it does not work at all, there is some mark around the icon that I can't set to "transparent" colour...

some help? 

thanks guys!!

---

### Post by ZipoTe on 2007-08-01
come on guys! :(

really nobody knows how to set transparent background instead this ugly white mark?

on edgy/dapper and my debian etch it works!! why not here ](*,)

---

