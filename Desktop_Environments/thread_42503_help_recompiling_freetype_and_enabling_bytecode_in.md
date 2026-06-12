---
title: "help recompiling freetype and enabling bytecode interpreter?"
date: 2005-06-17
forum: Desktop Environments
---

### Post by Loungefly on 2005-06-17
Hi all, 

I was just wondering if anyone here had any experience recompiling freetype to enable the bytecode interpreter.

I did this ages ago with SUSE and it made a HUGE improvement in the font rendering on my particular setup (as opposed to the native autohinting that freetype uses by default which I know seems to work better for some people).  Since then I've switched to Kubuntu and I'd like to do the same with the BCI in  Kubuntu. I've lost the step by step instructions I originally used to recompile freetype and enable the BCI. I've googled a bit and can't find any straightforward easy-to-understand instructions for doing it again.

I've got all my settings tweaked and adjusted exactly the way I want them in Kubuntu and I'm loving it :) . The font rendering is the only real stumbling block left that's keeping me from ditching Windows altogether.

If anyone could point me in the right direction for some clear concise instructions on recompiling freetype and enabling the BCI I'd be eternally grateful :)

---

### Post by intangible on 2005-06-18
[QUOTE=Loungefly]Hi all, 

I was just wondering if anyone here had any experience recompiling freetype to enable the bytecode interpreter.

I did this ages ago with SUSE and it made a HUGE improvement in the font rendering on my particular setup (as opposed to the native autohinting that freetype uses by default which I know seems to work better for some people).  Since then I've switched to Kubuntu and I'd like to do the same with the BCI in  Kubuntu. I've lost the step by step instructions I originally used to recompile freetype and enable the BCI. I've googled a bit and can't find any straightforward easy-to-understand instructions for doing it again.

I've got all my settings tweaked and adjusted exactly the way I want them in Kubuntu and I'm loving it :) . The font rendering is the only real stumbling block left that's keeping me from ditching Windows altogether.

If anyone could point me in the right direction for some clear concise instructions on recompiling freetype and enabling the BCI I'd be eternally grateful :)[/QUOTE]
 Try this for some improvement: **sudo dpkg-reconfigure fontconfig**  Then install the MS fonts **sudo apt-get install msttcorefonts**

---

### Post by Loungefly on 2005-06-18
Yep, I've tried that. I already have MS fonts installed etc. I pretty much tried everything else I've come across in various forums with no real improvement. It took a while before I resorted to fooling with the BCI, mainly I because I had read several threads in other forums where others said it didn't really help much.  After trying everything else without any success I figured what the heck, gave it a shot, and low and behold  it worked wonders for me.  I was just hoping someone out there could point me to a good tutorial on recompiling, enabling etc since I no longer have the instructions I used previously and I haven't been able to find them again when googling.

---

### Post by santo on 2005-09-07
Hi,

if you're still looking for some clear instructions about enabling the bytecode interpreter, you may take a look at the following url:

[http://www.susewiki.org/index.php?title=Font_Setup](http://www.susewiki.org/index.php?title=Font_Setup)

I know it's for SUSE, but maybe you can get enough information out of it to try it with Ubuntu.

---

### Post by skoal on 2005-09-07
Hmm, I could download the freetype2 lib source and check it out, but I'm pretty sure that it's built in with the bytecode interpreter already enabled.  I'd be surprised if it weren't...

\\//_

---

### Post by skoal on 2005-09-07
```
skoal@morpheus:///tmp/freetype-2.1.7/debian/patches $ cat 030-bytecode-interpreter.diff 
--- freetype-2.1.7~/include/freetype/config/ftoption.h  2003-08-19 02:24:06.000000000 +0800
+++ freetype-2.1.7/include/freetype/config/ftoption.h   2003-08-28 20:40:55.000000000 +0800
@@ -399,7 +399,7 @@
   /*   Do not #undef this macro here, since the build system might         */
   /*   define it for certain configurations only.                          */
   /*                                                                       */
-/* #define  TT_CONFIG_OPTION_BYTECODE_INTERPRETER */
[COLOR=DarkRed]+#define TT_CONFIG_OPTION_BYTECODE_INTERPRETER[/COLOR]
 
 
   /*************************************************************************/

```
Booyah!

and...
```
skoal@morpheus:///tmp/freetype-2.1.7/debian $ grep -i bytecode rules
        # Turn on bytecode interpreter, but use unpatented hinting
        [COLOR=DarkRed]patch -p0 -i $(patchdir)/030-bytecode-interpreter.diff[/COLOR]
```
Double Booyah!

\\//_

---

### Post by aveline on 2005-09-07
[QUOTE=skoal]```
skoal@morpheus:///tmp/freetype-2.1.7/debian/patches $ cat 030-bytecode-interpreter.diff 
--- freetype-2.1.7~/include/freetype/config/ftoption.h  2003-08-19 02:24:06.000000000 +0800
+++ freetype-2.1.7/include/freetype/config/ftoption.h   2003-08-28 20:40:55.000000000 +0800
@@ -399,7 +399,7 @@
   /*   Do not #undef this macro here, since the build system might         */
   /*   define it for certain configurations only.                          */
   /*                                                                       */
-/* #define  TT_CONFIG_OPTION_BYTECODE_INTERPRETER */
[COLOR=DarkRed]+#define TT_CONFIG_OPTION_BYTECODE_INTERPRETER[/COLOR]
 
 
   /*************************************************************************/

```
Booyah!

and...
```
skoal@morpheus:///tmp/freetype-2.1.7/debian $ grep -i bytecode rules
        # Turn on bytecode interpreter, but use unpatented hinting
        [COLOR=DarkRed]patch -p0 -i $(patchdir)/030-bytecode-interpreter.diff[/COLOR]
```
Double Booyah!

\\//_[/QUOTE]
 ok so what did you do?  pasting the codes cool but doesn't help me if i wanna retrace your steps. :)  

plus I'm curious what the improvement is?  Friend of mine whos used linux for years had only this to say about your entrerprise:

<Tuxy> it should [improve the fonts/looks] a little bit.. and the fonts actually render better in linux but its just some of the proggies dont take advantage of it.. 

so if thats true... what is the advantage of doing this really?

aveline

---

### Post by skoal on 2005-09-07
oops. Sorry about that.  I was just trying to show that the patch for the bytecode interpreter was already enabled in libfreetype2.  *You need not do anything. It's already in there*.  My apologies.  I made a drive by post.  It won't happen again.  I offer my severed typing fingers on a silver platter as compensation...

\\//_

---

### Post by gpremuda on 2006-07-16
The bytecode interpreter is enabled, but it uses an algorithm that avoids patent issues but doesn't render very well.

---

### Post by rubengs on 2006-09-01
It's easy to recompile the freetype package with these simple instructions:

[http://ubuntuforums.org/showthread.p...ght=openoffice](http://ubuntuforums.org/showthread.p...ght=openoffice)

Change version numbers to match dapper package an thats all.

apt-build is the debian way.

---

### Post by the_mouse on 2006-10-08
I'm sorry but the link opens the forum index, can you link me again?

---

### Post by gentoofrm on 2006-11-23
1) sudo dpkg-reconfigure fontconfig

then choose "native",
then choose "automatic",
then choose "yes".

2) (Gnome Panel) System -> Preferences -> Font -> Details

Smoothing (none)
Hinting (full)

3) log out & log in

[http://www.linuxjournal.com/article/9166](http://www.linuxjournal.com/article/9166)

---

### Post by temcat on 2006-11-24
> **gentoofrm said:**
> 1) sudo dpkg-reconfigure fontconfig

then choose "native",
then choose "automatic",
then choose "yes".

2) (Gnome Panel) System -> Preferences -> Font -> Details

Smoothing (none)
Hinting (full)

3) log out & log in

[http://www.linuxjournal.com/article/9166](http://www.linuxjournal.com/article/9166)

Hi, dpkg-reconfigure didn't present any dialogs to me, even when I explicitly ordered Gnome frontend (-fgnome) and low priority questions (-plow)...

---

