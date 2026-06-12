---
title: "Custom Compiz color filter"
date: 2010-03-02
forum: Desktop Environments
---

### Post by lian1238 on 2010-03-02
Hi all!

I just wanted to share with the community a color filter for the Color Filter plugin in Compiz that I had thought of and made, by looking at the sample filters. I used to love the negative plugin, which inverts the colors of the screen. I use it in the nighttime when the screen is just too bright for reading text or for coding. I prefer white text on a black background and maybe that's just me. But for those of you use the Negative plugin for the same reason as I do, read on!

What I don't like about the Negative plugin is that it also inverts the colors and it makes it hard to recognize some icons, such is the status icons in your IM client (green for online, red for busy, etc). So I've made a plugin for the Color Filter plugin (not the Negative plugin) which inverts black and white but keeps the original color. Here is the code for the filter:

```

!!ARBfp1.0
TEMP temp, neg, red, green, blue;
TEX temp, fragment.texcoord[0], texture[0], RECT;
RCP neg.a, temp.a;
MAD temp.rgb, -neg.a , temp, 1.0;
MUL temp, temp.a, temp;
ADD green, temp.r, temp.b;
ADD red, temp.g, temp.b;
ADD blue, temp.r, temp.g;
MUL red, red, 0.5;
MUL green, green, 0.5;
MUL blue, blue, 0.5;
MOV temp.r, red;
MOV temp.b, blue;
MOV temp.g, green;
MUL temp, fragment.color, temp;
MOV result.color, temp;
END

```

To use this, run the following commands:
```

cd /usr/share/compiz/filters/
sudo gedit nightmode

```

Copy and paste the code for the filter into the text editor, save it and close it.

Now open ccsm (CompizConfig Settings Manager) and turn on the Color Filter. Set your preferred keybindings and click New. Find the filter file in /usr/share/compiz/filters.

That's it. :D

I have attached a screenshot of the result.

Please comment and tell me what you think and if you have better code to get the same result, let me know! After all, I didn't know what I was coding. It was trial-and-error and took me about 50 minutes to get this.

---

### Post by BionicSeahorse on 2010-04-07
Very cool! Thanks for sharing.

How did you figure out how to write it, though? I haven't found any documentation on the scripting language. :confused:

---

### Post by lian1238 on 2010-04-07
> **BionicSeahorse said:**
> Very cool! Thanks for sharing.

How did you figure out how to write it, though? I haven't found any documentation on the scripting language. :confused:

You're welcome!

I found this documentation:
[http://wiki.compiz.org/Plugins/Colorfilter](http://wiki.compiz.org/Plugins/Colorfilter)
which links to
[OpenGL Fragment Program]("http://oss.sgi.com/projects/ogl-sample/registry/ARB/fragment_program.txt"), the language used for the filters.

For the most part, it was trial-and-error. I looked at the negative filter and the "swapping colors" filters for reference.

---

### Post by baisong on 2010-04-15
How would one only invert non-menu elements of a window?

---

### Post by lian1238 on 2010-04-15
> **baisong said:**
> How would one only invert non-menu elements of a window?

It's not possible with this plugin. I'm not sure that it's even possible to do it with compiz.

---

### Post by lian1238 on 2010-04-15
I have made some changes to the filter. This new one has better contrast, and I've changed the way the color is calculated.

```
!!ARBfp1.0
TEMP temp, mean, diff;
TEX temp, fragment.texcoord[0], texture[0], RECT;
MUL mean, temp.r, 0.3;
MAD mean, temp.g, 0.59, mean;
MAD mean, temp.b, 0.11, mean;
MAD diff, -2.0, mean, 1.0;
ADD_SAT temp.r, temp.r, diff;
ADD_SAT temp.g, temp.g, diff;
ADD_SAT temp.b, temp.b, diff;
MUL temp, fragment.color, temp;
MOV result.color, temp;
END
```

*****Note: There is still a problem with filtering the window decorations, so please turn that off in the Color Filter plugin.** The alpha of the shadow from the window decoration seems to get flipped.

---

### Post by t1010011 on 2010-05-23
Anyone knows how to add the colorfilter to startup? So I wouldn't need to press <super>+d every time I turn the pc on?

---

### Post by t1010011 on 2010-05-24
Never mind solved adding to startup a scrip with the following code

```
#!/bin/bash

sleep 20s && dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/colorfilter/allscreens/toggle_screen_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'` &
```

I'm working with a fake RGBA color filter:
```
!!ARBfp1.0
TEMP texv, rep;
TEX texv, fragment.texcoord[0], texture[0], RECT;
MOV rep, {0.196078431, 0.196078431, 0.192156863};
SUB rep, rep, texv;
ABS rep, rep;
MAX rep.b, rep.b, rep.r;
MAX rep.b, rep.b, rep.g;
SUB rep.b, rep.b, 0.0001;
CMP rep.b, rep.b, 0.9, 1;
MUL texv, texv, rep.b;
MOV result.color, texv;
END

```
but I'd like to filter more than 1 color... Is there a way to load more than one filter at once in colorfilter? Or anyone knows how to change the code above to add more colors?

---

### Post by jsgoodall on 2010-05-28
Just to share a little bit as well I added two filters to my setup. Both of them are red based, very helpful for when you want to keep your night vision intact, like when you are out at sea and have the night watch. Of course they even work on my Windows XP VirtualBox so you would be able to use those win programs you might miss.

First one is night-vision-negative

```
!!ARBfp1.0
TEMP temp, neg;
TEX temp, fragment.texcoord[0], texture[0], RECT;
RCP neg.a, temp.a;
MAD temp.rgb, -neg.a, temp, 1.0;
MUL temp.rgb, temp.a, temp;
MUL temp, fragment.color, temp;
SUB temp.gb, temp, temp;
MOV result.color, temp;
END
```

Second one is just night-vision, it is slightly brighter
```
!!ARBfp1.0
TEMP temp, neg;
TEX temp, fragment.texcoord[0], texture[0], RECT;
RCP neg.a, temp.a;
MUL temp.rgb, temp.a, temp;
MUL temp, fragment.color, temp;
SUB temp.gb, temp, temp;
MOV result.color, temp;
END
```

Thanks Compiz guys, great code!!

---

### Post by yahooshua on 2010-09-30
Wow, the documentation on this is intense. 

I am looking for a filter that filters all blue light out. Kind like through a red or amber lense.

I am not sure if this coincides with night vision BUT when blue light hits your eyes it basically tells your brain not to produce melatonin. I have been using blue blockers sunglasses (remember those?) at night to use my computer to not mess up my sleep. The white in the text using the above filters has to much blue light in the white.

Any help would be great. Tried a few things.

The best seems to be the first one by jsgoodall. Thank you.

---

### Post by Michl0x07 on 2011-01-17
> **yahooshua said:**
> Wow, the documentation on this is intense. 
I am not sure if this coincides with night vision BUT when blue light hits your eyes it basically tells your brain not to produce melatonin. I have been using blue blockers sunglasses (remember those?) at night to use my computer to not mess up my sleep. The white in the text using the above filters has to much blue light in the white.


Exactly! I need it for the same purpose as you! :D

I experimented a bit, and here it is:

> !!ARBfp1.0
TEMP tex, temp;
TEX tex, fragment.texcoord[0], texture[0], RECT;
DP3 temp.r, tex, {0.9, 0, 0, 0};
DP3 temp.g, tex, {0, 0.9, 0, 0};
DP3 temp.b, tex, {0, 0, 0, 0};
MOV temp.a, tex.a;
MOV result.color, temp;
END

Melatonin, you can come! ;)

---

### Post by Nikles on 2011-01-21
Is there a way to conditionally use a negative filtered color only if the overall light intensity is lower than the original one?

[SIZE="4"]The Problem[/SIZE]
[[IMG]http://img5.imagebanana.com/img/z3861hoi/thumb/Workspace1_003.png[/IMG]](http://www.imagebanana.com/view/z3861hoi/Workspace1_003.png)
[[IMG]http://img5.imagebanana.com/img/gyk87j1w/thumb/Workspace1_004.png[/IMG]](http://www.imagebanana.com/view/gyk87j1w/Workspace1_004.png)
With a dark color scheme, the dark areas (which would be quite OK as they are...) becomes incredibly bright.
This is a nightmare for working up late at night.

[SIZE="4"]Shader Assembly Language (ARB/NV)[/SIZE]
I've found this link as a reference for creating filters: [http://www.renderguild.com/gpuguide.pdf](http://www.renderguild.com/gpuguide.pdf)

...but I really can't get mine working.

Possible solutions could involve:
```
Instruction   Output  Input     Description 
-----------   -----  ------     -----------
LIT           v       v         compute light coefficients
SGE           v       v,v       set on greater than or equal
SLT           v       v,v       set on less than
MAX           v       v,v       maximum 
MIN           v       v,v       minimu
```

I'll try again but if anyone else comes up with a viable solution... well... post it here please (maybe with screenshots too) :D

---

### Post by Nikles on 2011-02-06
Haven't found a solution yet.
Has anyone else tried to solve the issue?

---

### Post by oldarney on 2011-07-14
Thank you!

I'm working on a skin filter, to make skin only turn inverted. 

Edit: after alot a work, i found that inverting skin would ruin some text with anti alias.
so instead I made skin gray. you can find the filter here:

[http://malefreedom.blogspot.com/2011/07/skin-filter-for-linux-beta.html](http://malefreedom.blogspot.com/2011/07/skin-filter-for-linux-beta.html)

> **t1010011 said:**
> Never mind solved adding to startup a scrip with the following code

```
#!/bin/bash

sleep 20s && dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/colorfilter/allscreens/toggle_screen_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'` &
```I'm working with a fake RGBA color filter:
```
!!ARBfp1.0
TEMP texv, rep;
TEX texv, fragment.texcoord[0], texture[0], RECT;
MOV rep, {0.196078431, 0.196078431, 0.192156863};
SUB rep, rep, texv;
ABS rep, rep;
MAX rep.b, rep.b, rep.r;
MAX rep.b, rep.b, rep.g;
SUB rep.b, rep.b, 0.0001;
CMP rep.b, rep.b, 0.9, 1;
MUL texv, texv, rep.b;
MOV result.color, texv;
END

```but I'd like to filter more than 1 color... Is there a way to load more than one filter at once in colorfilter? Or anyone knows how to change the code above to add more colors?

---

### Post by oldarney on 2011-07-15
> **Michl0x07 said:**
> Exactly! I need it for the same purpose as you! :grin:

Melatonin, you can come! :wink:

I love the way you are thinking, however, that filter makes everything yellow lol.
Here is one that turns 85% of blue into other colors.

```

!!ARBfp1.0
TEMP tex, temp;
TEX tex, fragment.texcoord[0], texture[0], RECT;
DP3 temp.r, tex, {1, 0, 0, 0};
DP3 temp.g, tex, {0, 1, 0, 0};
DP3 temp.b, tex, {0.425, 0.425, 0.15, 0};
MOV temp.a, tex.a;
MOV result.color, temp;
END 

```

I also made the oposite, which makes every color bluer, except white. Its like sephia,
but for blue, and leaves colors.

```

!!ARBfp1.0
TEMP tex, temp;
TEX tex, fragment.texcoord[0], texture[0], RECT;
DP3 temp.r, tex, {1, 0, 0, 0};
DP3 temp.g, tex, {0, 1, 0, 0};
DP3 temp.b, tex, {0.5, 0.5, 1, 0};
MIN temp.b, temp.b, 1;
MOV temp.a, tex.a;
MOV result.color, temp;
END 

```

---

### Post by jpka on 2012-01-01
> **lian1238 said:**
>  and maybe that's just me
You're not alone! I was search for exactly this filter for many years. And now, using your solution, i can write big, bold and embossed final point in my journey. Armed with your code, i'm able now fight any non-human-friendly software like most professional CADs and development systems. I was use 'invert' plugin before, but it damage colours.
The only problem i found in your code (i mean first original code) is the colors not so intensive as must be. (But, it is *much* better than wrong colours). Ideally, we must invert image and then turn *hue* value by 180 degrees to get precisely correct colours, please see screenshots [here]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/659810"). 

Thank you very much for your work and for saving people's eyes! You rock! :KS :KS :KS :KS :KS

---

### Post by diethr on 2012-04-13
Hi,

I've recently been diagnosed with irlen syndrome, a sensitivity to certain wavelengths of light that makes reading very difficult. I'd like to make a color filter that changes the white to a light blue color. I'm not a programmer and so this along with my condition is making learning how to write filters very difficult. I'd really appreciate some help.

I've got some questions:
Are the color codes written in CSV?

I've annotated the color filter below (sepia) to show what I understand so far. Would you mind telling me if I'm wrong and mention anything that I'm missing.

!!ARBfp1.0

//sets temporary variables 'tex' and 'tem'
TEMP tex, temp; 

TEX tex, fragment.texcoord[0], texture[0], RECT;

//sets the color value for red
DP3 temp.r, tex, {0.393, 0.769, 0.189, 0};


//sets the color value for green
DP3 temp.g, tex, {0.349, 0.686, 0.168, 0};


//sets the color value for blue
DP3 temp.b, tex, {0.272, 0.534, 0.131, 0};

MOV temp.a, tex.a;
MOV result.color, temp;
END

How would I change the the white to a blue colour given the csv value {0.552500,0.719644, 0.947500, 0}?

Thanks for any help,

Ben.

---

### Post by jpka on 2012-07-05
Hi!
I suddenly did some research and probably find solution that can preserve colors more precisely than original inversion filter. It works perfectly with grays, blacks, whites, and saturated colors. But halftones may be a bit grayed or lighted. Please see comments in code. 

Use it and give to your friends. This filter will save your eyes, like lian1238's original filter.

```
!!ARBfp1.0
# Compiz Color Filter, negative but preserve colors v0.1
# Based on various ideas and examples.
# author of portions: jopka1@gmail.com, www.bdyssh.ru
# (select 'Ruby' in `gedit` for proper text highlight and show of keywords and comments)

TEMP temp, lightness, diff, saturation, delta, grayness;
TEX temp, fragment.texcoord[0], texture[0], RECT;

# saturation 0...1 - show how rich the colour.
#  i calculate it as max difference between r, g, b parts of colour.
#  it is linear operation, so it's incorrect for half-tones, see HSL color model.
# grayness = 1 - saturation. (it is 'anti-saturation').

MOV saturation, 0;
SUB delta, temp.r, temp.g;
MAX saturation, saturation, delta;
SUB delta, temp.g, temp.r;
MAX saturation, saturation, delta;

SUB delta, temp.r, temp.b;
MAX saturation, saturation, delta;
SUB delta, temp.b, temp.r;
MAX saturation, saturation, delta;

SUB delta, temp.g, temp.b;
MAX saturation, saturation, delta;
SUB delta, temp.b, temp.g;
MAX saturation, saturation, delta;

# simple method used... Not sure if it is precisely correct.
MUL lightness, temp.r, 0.333;
MAD lightness, temp.g, 0.333, lightness;
MAD lightness, temp.b, 0.333, lightness;

# -0.5 to 0.5 range and inverse
ADD lightness, -lightness, 0.5;

# -1 to 1 range
MUL lightness, lightness, 2.0; 

# inverse slope - calculate grayness, 1 = not coloured pixel, 0 = full saturation
SUB grayness, 1, saturation;

# here we invert pixels, and amount of inversion is inverse relative of saturation.
# so, black colour become white, white turns to black, but red remains red.
MUL diff, lightness, grayness;

ADD_SAT temp.r, temp.r, diff;
ADD_SAT temp.g, temp.g, diff;
ADD_SAT temp.b, temp.b, diff;

MUL temp, fragment.color, temp;
MOV result.color, temp;
END
```

---

### Post by jpka on 2012-12-09
Hi!
Ubuntu 12.10 lacks of **ColorFilter** plugin. Also **Neg** plugin kicked from mainstream, but installable as separate option via command line.
This plugin was main reason for me to vent from Windows to Ubuntu six yrs ago, and now, latest Ubuntu just can't be used at all, due to lack of it.
But don't let your eyes cry.
I take some weeks and find a way to modify Neg plugin so it can match my color filter processing. So, Ubuntu 12.10 *still* can be turn to useable. (I can't imagine what else can be worse in 13.04, but it becomes worse each new release, and blind to my bugreports.)

Well, here is the (pseudo-diff of the) code of neg.cpp. You will need to recompile Compiz. It is full of tricks, but doable by inexperienced people like me. Tip: **Never do '*make install*'**, else you need to reinstall complete system. Just take libneg.so after build and push it to /usr/lib/compiz/.

```
// read more at http://ubuntuforums.org/showthread.php?t=1419702&page=2
// was: Compiz Color Filter, negative but preserve colors v0.1
// Based on various ideas and examples.
// author of portions: jopka1@gmail.com, www.bdyssh.ru
static std::string fragment_function =
	"void neg_fragment () {; \n"
	"float lightness; \n"
	"float diff; \n"
	"float saturation; \n"
	"float delta; \n"
	"float grayness; \n"
	"vec3 temp; \n"
// saturation 0...1 - show how rich the colour.
// i calculate it as max difference between r, g, b parts of colour.
// it is linear operation, so it's incorrect for half-tones, see HSL color model.
// grayness = 1 - saturation. (it is 'anti-saturation').
	"saturation = 0.0; \n"
	"delta = abs (gl_FragColor.r - gl_FragColor.g); \n"
	"saturation = max (delta, saturation); \n"
	"delta = abs (gl_FragColor.r - gl_FragColor.b); \n"
	"saturation = max (delta, saturation); \n"
	"delta = abs (gl_FragColor.g - gl_FragColor.b); \n"
	"saturation = max (delta, saturation); \n"
// simple method used... Not sure if it is precisely correct.
	"lightness = gl_FragColor.r * 0.333 + gl_FragColor.g * 0.333 + gl_FragColor.b * 0.333; \n"
// # -0.5 to 0.5 range and inverse
	"lightness = 0.0 - lightness + 0.5 ; \n"
// -1 to 1 range
	"lightness = lightness * 2.0 ; \n"
// inverse slope - calculate grayness, 1 = not coloured pixel, 0 = full saturation
	"grayness = 1.0 - saturation; \n"
// here we invert pixels, and amount of inversion is inverse proportional of saturation.
// so, black colour become white, white turns to black, but red remains red.
	"diff = lightness * grayness; \n"
// WARNING. Originally ADD_SAT instead of ADD used.
// but i don't know its equivalent for fragment function,
// to prevent values run out of 0...1 boundaries. So just add (`plus`) functions used.
	"temp = vec3(gl_FragColor.r + diff, gl_FragColor.g + diff, gl_FragColor.b + diff); \n"
	"gl_FragColor = vec4(temp, gl_FragColor.a); \n"
	"} \n"
;

```

Hope it helps.

ADD: Please remember to change fonts antialiasing mode from rgb to grayscale via gnome-tweak-tool.

---

### Post by zombifier25 on 2012-12-09
Ya know, another option is to stick with 12.04 if you're really dependent on the feature. It has 5 years of support, so you can stick to it until Compiz got all the unsupported plugins sorted out

---

### Post by jpka on 2013-10-09
Hi! Unfortunately it is impossible to use this filter in Ubuntu 13.04 at all. So 13.04 unusable for professional[1] use. So i agree i need to fall back, or find other distro. When selecting Ubuntu for fallback, i take look at 10.04, it is one of latest which are truly professional[1], and latest professional with LTS. (I also try Xubuntu, etc). There is no any problem with color filtering in 10.04.

I also develop final version of filter: Now it has absolutely correct colors when inverted.
```
!!ARBfp1.0
TEMP temp, neg, YPbPr;
TEX temp, fragment.texcoord[0], texture[0], RECT;
RCP neg.a, temp.a;
MAD temp.rgb, -neg.a, temp, 1.0;
MUL temp.rgb, temp.a, temp;
MUL temp, fragment.color, temp;
DP3 YPbPr.x, temp, {0.333, 0.333, 0.333, 1};
SUB YPbPr.y, YPbPr.x, temp.b;
SUB YPbPr.z, YPbPr.x, temp.r;
ADD temp.r, YPbPr.x, YPbPr.z; 
ADD temp.b, YPbPr.x, YPbPr.y;
SUB temp.g, YPbPr.x, YPbPr.z; 
SUB temp.g, temp.g, YPbPr.y;

MOV result.color, temp;
END

# DO NOT MOVE LINE #2 (TEMP...) below, i.e. do not insert comments before it!
# do not insert comments before 'END' token: SOMETIMES not work!

# replace file /usr/share/compiz/filters/negative with this file.

#  Color filter: negative, but preserve colours. Tested on Ubuntu LTS 10.04.

# compiled from [1], [2] by jopka@kvidex.ru, www.bdyssh.ru
# [1] http://hronir.blogspot.com/2008/09/compiz-fusion-color-filter-for-hue.html
# [2] http://ubuntuforums.org/showthread.php?t=1419702

# add to line 15:  MUL temp.b, 0.5, temp.b;  - for warm/melatonine colors, or 
#  MUL temp.g, 0.5, temp.g;  - for cold colors.
```

-----
[1] Professional - means here: Intended to use many hours a day without eye damage.

---

### Post by kikazaru on 2014-02-15
jpka

Just what the doctor ordered!

Excellent.

Thanks.

---

### Post by lian1238 on 2014-02-21
I have found another (less extreme) alternative to the color filter: [f.lux]("http://justgetflux.com/linux.html")
It makes the screen warmer at sunset and back to normal at sunrise, attempting to keep your sleep pattern "normal."
Hope it is useful.

---

### Post by hellwoodfire on 2015-01-09
I'm new. In jan 2015, I don't find the Color Filter plugin on the Compiz Configuration Manager. 
How do I install it ?

---

### Post by CantankRus on 2015-01-09
As Unity is a plugin for compiz, Canonical has taken over the development of compiz
and some plugins are unsupported and cease to function as compiz develops.

You can install the **compiz-plugins** unsupported plugins package 
but this does not include a Color Filter plugin. 
There is a negative plugin to toggle windows negative as in pic.  
Some of the plugins provided by  **compiz-plugins** are cube, firepaint, opacify, scaleaddon.
Most of these still work.

---

