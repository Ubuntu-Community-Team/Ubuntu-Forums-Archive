---
title: "Tibetan Unicode fonts/keyboard--Help!"
date: 2009-06-20
forum: General Help
---

### Post by ECS on 2009-06-20
Hello all. So I'm not a complete beginner to Ubuntu (been using/loving it just over a year), but I am completely foreign to using Unicode fonts and installing new keyboard layouts.

The past few days I've been trying with no avail to install a unicode font/keyboard for Tibetan based on tutorials from the [Tibetan & Himalayan Library (THL)]("http://www.thlib.org/tools/#wiki=/access/wiki/site/26a34146-33a6-48ce-001e-f16ce7908a6a/using%20tibetan%20in%20linux.html")

I've got the TibMachUni-1.901b.ttf font, which i put in /usr/share/fonts/
I also installed the uim, uim-m17nlib, scim, and scim-m17n packages.

From here, however, I have no idea what to do. SCIM added a little switcher to my panel, and Tibetan Machine Uni appears in my list of fonts in OOo. I also tried another rout, which was to go System-->Admin-->Language Support and enable support for both Tibetan and Dzongkha. Still nothing. Am I missing a simple step? Did I perhaps install components out of order? 

And in case it's relevant, I'm still using Ibex with OOo 2.4. (I know, I know...)

Help would be much appreciated.

-Evan

---

### Post by Chuck Glenn on 2009-07-08
I have done this on Windows, and as a recent convert to Ubuntu, I will be trying to get things done there too.  First, the obvious: Try Jaunty, and OO 3.1.  After that, I bet the real problem is the keyboard input, and having some way to generate the unicode you want.

For what I did, I didn't even use a keyboard.  I used something called BabelPad in Windows.  I could paste in extended wylie (English letters), then hit babelpads "translate / tibetan / extended wylie to unicode", then past the result into OO Writer.  Tedious, I know, but it did work.  I'd prefer to do that instead of learning some variation of a Tibetan keyboard.

I've heard that WinE will run BabelPad, so I may try this route myself.  Hopefully one can cut and paste between native Ubuntu apps and WinE apps.  I plan to install WineHQ (the Ubuntu/Debian packaging, I guess) sometime soon and try BabelPad.

On a semi-related note, I found a font that I liked much better than the "tibetan machine" ones.  Google "Jomolhari".  It seems to do character spacing better, and I think it's better looking.

I hope this helps somewhat.  If I find something new and exciting in my own efforts, I will post here.

-- Chuck Glenn

---

### Post by Chuck Glenn on 2009-07-08
For a video on that, check out my YouTube video:

[http://www.youtube.com/watch?v=ydyLwHY_0oE](http://www.youtube.com/watch?v=ydyLwHY_0oE)

Maybe the next one will be how to do this in Ubuntu...

---

### Post by Chuck Glenn on 2009-07-09
Well Evan, I have had decent success using BabelPad on Ubuntu (via Wine) to translate Extended Wylie to Tibetan Unicode.  Here is the video:

[http://www.youtube.com/watch?v=vJZYV2EQbqM](http://www.youtube.com/watch?v=vJZYV2EQbqM)

Note that I did go into "languages", and install Tibetan. I have no idea if that part was necessary.

Good luck!

-- Chuck

---

### Post by Chuck Glenn on 2009-07-09
Argh... The thought plickens...

In Windows XP, there is something called usp10.dll that renders characters.  This is apparently used by bablepad (and lots of other applications using the text-memo-area API).  I noticed when trying to translate "rtsa", I got the full-size "ra" character on top of a "tsa", instead of just the subtle ra-go flag.  I tried this on BabelPad on my work PC running WinXP -- same thing.  

I did a little googling, and identified the above DLL as part of the problem.  I ran across this page: [http://www.wazu.jp/gallery/Fonts_Tibetan.html](http://www.wazu.jp/gallery/Fonts_Tibetan.html)  and then searched my machine for another version of the dll.  Luckily, Office 2003 comes with one that is 1.47+.  I copied this into the same directory as babelpad.exe (on the WinXP machine), and VIOLA, "rtsa" rendered correctly.

So, the unicode that BabelPad creates is probably correct, but the Windows API bits simply don't render it correctly.

I will see if I can move usp10.dll to my ubuntu machine tonight, and convince WINE to recognize and/or use it.  I'll post my results here.

BTW, telling WINE to run BabelPad as "windows vista" instead of "windows xp" didn't fix this.

-- Chuck

---

### Post by scot on 2009-08-04
Hi Chuck

It's nice to read about your progress and I'm writing to ask if you have any recent developments to report.

Thanks for your help and hopefully more can join you in this search soon.

Scot

---

### Post by B9 hummingbird hovering on 2009-08-19
[COLOR=RoyalBlue]> **Chuck Glenn said:**
> Well Evan, I have had decent success using BabelPad on Ubuntu (via Wine) to translate Extended Wylie to Tibetan Unicode.  Here is the video:

[http://www.youtube.com/watch?v=vJZYV2EQbqM](http://www.youtube.com/watch?v=vJZYV2EQbqM)

Note that I did go into "languages", and install Tibetan. I have no idea if that part was necessary.

Good luck!

-- Chuck[/COLOR]     
----------------------------------------------------------
I have installed fonts and Tibetan text is visible through Firefox. I have tweaked Open Office 3.0 now I would just like to be able to input Tibetan through an extended Wylie system, is there such a functionality? I can't seem to install a Tibetan keyboard layout in Ubuntu, any advice? I was using TISE hapily but have left the dark side. Do I really need Wine? Is Wine and TISE an option? Is there a better way? :P Any assistance is really appreciated.

---

