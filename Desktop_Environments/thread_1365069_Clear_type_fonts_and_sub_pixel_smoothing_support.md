---
title: "Clear type fonts and sub pixel smoothing support"
date: 2009-12-26
forum: Desktop Environments
---

### Post by sinistertim101 on 2009-12-26
I used to take great font support for granted before MS threated to sue anyone who used hinting for font rendering.

I have a laptop and I am trying to enable MacOSX/Windows font support for my lcd screen. Whenever I enable subpixel smoothing in the appearance control panel it does not render fully like Windows does and its unselected whenever I close the font tab.

I feel fontconfig is not using the byte code interpreter method of rendering.

In past versions of Ubuntu, I would just do a "sudo dpkg-reconfigure fontconfig-config". But this does not work anymore and I can not select native vs bytecode hinting anymore.

Also Netbeans (and any java app) does not use the font settings in gnome like it does in Windows and MacOSX and has no cleartype support as well which is an eye sore. Is there a way to have X enable it?

---

### Post by puckskraper on 2010-01-12
Bump

"sudo dpkg-reconfigure fontconfig-config" no longer brings up the option to select bytecode hinting in Karmic

---

### Post by Zorael on 2010-01-12
Tagging thread for interest.

Hmm.
[quote=Kriston Rehberg]Per the Freetype.org developers the "bytecode interpreter" is not to be used by any distribution because of the TrueType patents held by Microsoft and Apple.[/quote]
From [this launchpad report](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/14310).

The followup, however, says it's no longer an issue.
[quote=Alexander Sack]this doesnt apply to current fontconfig anymore from what i see. let me know if thats wrong.[/quote]

I'm ignorant to the different kinds of rendering (outside of levels of hinting), so I don't know any details. Perhaps the freetype libraries have been compiled without this support because of said patent/licensing issues. If so, you may be able to recompile them yourself. (Do report back with your results if you do this.)

And yeah, fontconfig-config has had its configuration window removed, likely in favor of instead manually making symlinks of files in **/etc/fonts/conf.avail** into **/etc/fonts/conf.d**.


**edit:** Looking at the Karmic freetype source, it seems there are patches there disabling the unpatented hinting and enabling the bytecode interpreter.
```
zorael@lethe:~/src/freetype/freetype-2.3.9/debian/patches-freetype$ ls
331-hmtx-no-shorts.diff           enable-subpixel-rendering.patch        **[COLOR="Green"]freetype-bytecode-interpreter.patch[/COLOR]**
CVE-2009-0946.patch               freetype-2.1.7-backwards.compat.patch  proper-armel-asm-declaration.patch
**[COLOR="Green"]enable-full-bytecode-interpreter[/COLOR]**  freetype-bdflib-large-encodings.patch  series
```
Those two disable '**TT_CONFIG_OPTION_UNPATENTED_HINTING**' and enable '**TT_CONFIG_OPTION_BYTECODE_INTERPRETER**' respectively.

Perhaps you need to enable autohinting for it to take effect?

---

### Post by cathalcummins on 2010-01-19
I am unhappy with the way the fonts and that are rendered on my Ubuntu Desktop. The screen dimensions seems to be fine - I'm using a HP 1955 monitor. I don't like seeing the rough edges on the characters. Is it my cheap graphics card that's causing the trouble?

Resolution:     85x86 dots per inch
Depth:          24
Dimensions:     1280x960 pixels (382x283 millimeters)
GPU:            GeForce 6150SE nForce 430
Display:        HP L1955 
Driver Version: 185.18.36

---

### Post by Zorael on 2010-01-19
My netbook has a small (and crisp) 1024x600 screen, and the only issues I have with regards to fonts is that Chromium doesn't honor fontconfig settings.

I have set up X to force a dpi of 96, as that is the de facto "standard" for screens otherwise. Antialiasing enabled and hinting set to full.

Since the screen itself is small, I use low font sizes for UI elements to conserve screen budget - but I'm not altering the dpi.

---

### Post by jejones3141 on 2010-07-20
Apple's patents on TrueType hinting have expired; see [http://freetype.sourceforge.net/patents.html]("http://freetype.sourceforge.net/patents.html"). I hope this means the freetype packages that were updated this morning for Lucid have the bytecode interpreter enabled.

---

### Post by hugmenot on 2010-07-20
jones, it’s been available all the time. but the default is autohinter with slight hinting.

there have been loads of discussions about this over the years. and polls and flamewars, and duplicate bugs fighting for changing the default setting.

it’s over. the default is what’s most compatible and best looking for the majority.

---

### Post by dasnk on 2010-07-29
Alright fair enough don't make it default.

But "sudo dpkg-reconfigure fontconfig-config" was an *option* that has been removed, that didn't affect the majority (or anybody on earth at all).

So now the insignificant minority of us have to go through sheer **hell** to achieve decent fonts on Ubuntu. I guess it's our own fault for not having your smugly satisfied and contented eyes.

---

### Post by hugmenot on 2010-07-29
yes, I’m satisfied. the lobby work was hard enough and having achieved the best looking fonts of all desktop platforms by default is to be celebrated.

at least you can achieve your preferred look with simple configuration changes. set autohint to false in fontconfig. that’s it. the hell you refer to stems from only a subset of fonts having the necessary qualified truetype instructions. so for the rest you need to make convoluted fontconfig setups to deal with all the rest and special case fonts. the current default avoids all of that. it works decently with most fonts at most sizes and it works properly with lcd filtering and it works well with scalable canvasses (like pdf readers, cairo, etc.)

removing debconf option had to do with debian wanting to move away from it. not related to fonts or their defaults per se.

---

