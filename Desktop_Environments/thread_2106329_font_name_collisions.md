---
title: "font name collisions?"
date: 2013-01-18
forum: Desktop Environments
---

### Post by monkblah on 2013-01-18
Hi, using Kubuntu 12.04. I wanted a Garamond font on my system, so I went to [http://www.fontsquirrel.com/fonts/eb-garamond](http://www.fontsquirrel.com/fonts/eb-garamond) and downloaded the fonts zip file. It contains two OpenType font files, EBGaramond.otf and EBGaramondSC.otf. One file is the basic Garamond font, the other the Small Caps Garamond font.

Went to System Settings, then Font Management, clicked on 'Add.' Chose the first file (EBGaramond.otf). Added it to my Personal Fonts. So far, no problem. The font was added successfully and applications can use it.

When I went to add EBGaramondSC.otf, however, I get a dialog box with the message:

```
Error
file://home/myusername/Downloads/EBGaramondSC.otf 
contains the font EB Garamond, Regular which is 
already installed on your system.
[Cancel Button]
```

If I uninstall the first font, I can then install the second (small caps) font. Applications then recognize it, under the name EB Garamond, same as the first font; now the displayed font is small caps.

Obviously there is some sort of name collision going on here. I am not familiar with the details of how fonts names work or are handled in Kubuntu, but presumably, each font has its own name, or possibly, some fonts have the same name but different 'styles,' eg small caps, italics, etc could possibly be seperate fonts (please correct me if I'm misunderstanding something).

Why isn't kubuntu handling these fonts as I would expect? It seems I should certainly be able to install both of them, and select between EB Garamond and EB Garamond SC in my applications. Or, perhaps the applications should show only EB Garamond and use the EBGaramondSC if small caps style is selected.

I suppose it is possible there is some problem with the .otf files...but I suspect the problem is more of a deficiency with kubunutu, since I have had similar font name collision issues in the past.

Does anyone know how to fix this issue, or can you refer me to whoever is in charge of font handling in kubuntu/kde so I can ask them?

---

### Post by McDuff on 2013-03-29
Hi monkblah,
I&#8217;ve just stumbled upon this post by accident. The version of EB Garamond which is served by the squirrel is very outdated. The problem may be in the font itself. Please download  a current version here: [https://bitbucket.org/georgd/eb-garamond/downloads](https://bitbucket.org/georgd/eb-garamond/downloads)

---

