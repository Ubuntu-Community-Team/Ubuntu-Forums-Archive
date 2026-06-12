---
title: "Macromedia Adobe and linux?"
date: 2006-01-11
forum: General Help
---

### Post by jackdirt on 2006-01-11
I have been searching these forums and the internet for a week+ now trying to learn of alternatives for the two suites. I am a graphic and web designer and I *need* these apps but I am sick of windows bullshit.  

I have looked into crossover office and I can't run any of the new suites CS cs2 or mx2004. I ahve not tried installing flash mx but I hope it will work, that and I hear it will be buggy as all hell. That aside I have been looking into alternatives, alternatives I would be willing to pay for.

I have found a few good open source replacements for dreamweaver such as screem, nvu, and gPHPedit. All these will suffice. I sucessfully installed IE 6 and 5.5 yay!

so my web needs are covered, but my big hump is illustrator (reading ai files), and indesign , quark and getting all my windows fonts to work in linux. I still can't get pressure sensitivity on my wacom to work either.

I think pixel will work to replace photoshop, have not tried it yet. Xara looks promising? But I don't know anything about it any testimonials.  I am really looking for peoples experiences. 

Side question is it possible to install OS X apps on ubuntu on a pc?

Thanks in advance everybody!

---

### Post by 23meg on 2006-01-11
For an Illustrator counterpart look into Inkscape (not sure if it reads ai files). I heard they had plans to merge with Xara.

For Wacom pressure sensitivity (I'm assuming you're working with GIMP), did you set all your devices to "Screen" mode in the extended input device configuration (under Preferences)?

---

### Post by John Jason Jordan on 2006-01-11
[QUOTE=jackdirt]I have looked into crossover office and I can't run any of the new suites CS cs2 or mx2004. I ahve not tried installing flash mx but I hope it will work, that and I hear it will be buggy as all hell. That aside I have been looking into alternatives, alternatives I would be willing to pay for.[/QUOTE]
Unlike you, I do no web work at all. However, I'm heavily into book publishing, for which I use InDesign CS on a Windows 2000 computer. Everything I need is available on my Ubuntu-64 Breezy computer except InDesign CS. I checked into Crossover and it appears it won't run CS or CS2. However, it will run 2.0, if you can settle for that. (I need at least CS.)

I am more seriously looking at Scribus as an InDesign replacement. Development has been proceeding very fast. Nevertheless, it will be at least a year before it gets to the level of InDesign CS.

---

### Post by probe45 on 2006-01-12
inkscape reads and writes .ai files so no problem there I think.

---

### Post by Sef on 2006-01-12
> Side question is it possible to install OS X apps on ubuntu on a pc?

No, it's not possible to just put OS X apps on Ubuntu.  OS X based on BSD, which is LGPL.  Under LGPL, you don't have to release changes to the community at large as you have to under GPL.  Also apps may be propriertary, and thus the source code is not available.


Technical Note: Apple OS X is based on FreeBSD's Darwin.

---

### Post by jackdirt on 2006-01-12
[QUOTE=probe45]inkscape reads and writes .ai files so no problem there I think.[/QUOTE]

Tried opening my ai files in inkscape and I keep getting errors like```
Couldn't load Perl module Image::Magick.  Images will be skipped.
Can't locate Image/Magick.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 1.
BEGIN failed--compilation aborted at (eval 1) line 1.

Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 3.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 3.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 3.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 3.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 3.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 3.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 174.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 174.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 174.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 174.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 174.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 174.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 187.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 187.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 187.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 187.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 187.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 187.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 189.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 189.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 189.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 189.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 189.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 189.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 227.
Argument "M-^_^FM-D7^M-nM-@M-CM-gM-<|.M-H^]^DM-h^]/M-9M-eM-fM-wM-|..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 227.
Argument "^_^NlM-zM-^HM-4^OM-[M-tVR^^,M-e^EM-p\r^OM-^VtM-cI^GM-1M-a..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 227.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 227.
Argument "ZM-{M-^BUM-^KM-L6M-XM-Y^M-\\q\\XM-9M-(?M-?llM-\0OM-MM-MM-+..." isn't numeric in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 236.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 236.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 236.
Argument "M-L\r^RM-sM-CM-$u" isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 236.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 236.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 236.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 237.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 237.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 237.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 237.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 237.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 237.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 261.
Argument "A>^ZM-dM-^Qz!ZM-KFM-^\|M-DM-IE@.M-"gM->7M-rM-[M-^VM-\092..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 261.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 261.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 261.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 261.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 281.
Argument "M-1kM-jM--M-jM-kM-[kM-)M-bjj{#M-7M-5M-^VN&'^B^AM-WM-(gpM-X..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 281.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 281.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 281.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 281.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 303.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 303.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 303.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 303.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 303.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 303.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 331.
Argument "M-+^G^KM-M$Y^C" isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 331.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 331.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 331.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 331.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 338.
Argument "^HM-UM-3M-}M-6`M- jM-6^O<M-fM-jM-{M-g^]M-^OM-G^\M-OM-?kM-^..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 338.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 338.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 338.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 338.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 392.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 392.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 392.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 392.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 392.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 392.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 403.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 403.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 403.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 403.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 403.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 403.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 404.
Argument "AM-9M-mM-x^[M-\foYM-OM-_M-\fM-^^zM-^F^OM-]O^OW^G^N^VM-{>..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 404.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 404.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 404.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 404.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 417.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 417.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 417.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 417.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 417.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 417.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 425.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 425.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 425.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 425.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 425.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 425.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 441.
Argument "M-V+M-^QvM->^S=M-yAM-"V"M-el.M-^\^FM-bM-}M-9|M-nM-QM-^_x..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 441.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 441.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 441.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 441.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 447.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 447.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 447.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 447.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 447.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 447.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 459.
Argument "yM-YM-oM-w?<M-_M-C&w}M-7^Y6M-{M-M^]5JM-^UiM-^F^FM-'p-=M-e..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 459.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 459.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 459.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 459.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 461.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 461.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 461.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 461.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 461.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 461.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 465.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 465.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 465.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 465.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 465.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 465.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 471.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 471.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 471.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 471.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 471.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 471.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 476.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 476.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 476.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 476.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 476.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 476.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 478.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 478.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 478.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 478.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 478.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 478.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 479.
Argument "^?^Bdh^NM-jM-^DM-{2M-=M-@BM-Z"M-\rM-kM-`M--M-$M-^QM-^C0M-5..." isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 479.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 479.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 479.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 479.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 481.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 481.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 481.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 481.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 481.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 481.
Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 304, <> chunk 484.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 309, <> chunk 484.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 310, <> chunk 484.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 311, <> chunk 484.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 484.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 315, <> chunk 484.

```

no idea what any of that means as I am also 3 weeks into linuxland


but thank you everyone for your input

---

### Post by graphius on 2006-11-16
I too have a ton of Illustrator files I would love to read in Ubuntu.
I installed inkscape (I have used it before for smaller projects) but when I tried to open an ai file, it gave an error that perl ImageMagick wasn't installed. no problem, I installed the perl module. 
Now I get no error message, but the files will still not open. I just get a blank page. 
The files in question were created in Illustrator CS and CS2.

---

### Post by ser1alsn1per on 2006-11-17
I have both photoshop cs2 and the macromedia studio 8 installed on my edgy machine using wine

---

### Post by drphilngood on 2006-11-17
I use Xara Xtreme on Dapper and it works really well for me.
Don't know if that's what you were looking for but if you need anything more concrete, LMK.

---

### Post by Rodneyck on 2006-11-30
> **ser1alsn1per said:**
> I have both photoshop cs2 and the macromedia studio 8 installed on my edgy machine using wine

How did you do this?  I have tried and tried.  What version of Wine are you using?  ](*,)

---

