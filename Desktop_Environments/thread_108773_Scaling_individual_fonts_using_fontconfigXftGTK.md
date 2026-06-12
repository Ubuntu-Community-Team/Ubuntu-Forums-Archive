---
title: "Scaling individual fonts using fontconfig/Xft/GTK"
date: 2005-12-27
forum: Desktop Environments
---

### Post by singamayya on 2005-12-27
Hello,

On my Ubuntu system, there is a TrueType font called "Pothana2000" that is used to render Unicode text for the Telugu language. This font comes with the **ttf-indic-fonts** package which  is also available on Debian systems.

My problem is that, in all GTK programs that use Xft (and therefore also use fontconfig), this Pothana2000 font appears much smaller than all other fonts at the same point-size. For example, see this screenshot [img]http://people.ucsc.edu/~skurapat/pub/tmp/Screenshot-gedit-good.png[/img] 
and notice how the English words "Link" and "Mouse" (near the bottom of the picture) appear much bigger than the surrounding Telugu text.

To solve this problem, I have tried to force scaling of this font using a fontconfig configuration file, but was unsuccessful. Here is the configuration file I have tried (~/.fonts.conf):
```

<?xml version="1.0"?>
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
 <!-- ~/.fonts.conf for per-user font configuration -->
 <fontconfig>
         <match target="font">
                 <test name="family">
                         <string>Pothana2000</string>
                 </test>
                 <edit name="scale" mode="assign_replace" binding="strong">
                         <double>10</double>
                 </edit>
         </match>
 </fontconfig>

```

Is it possible to use something like fontconfig to specify that a particular font should have a larger default size than others? Maybe by specifying a larger DPI for that particular font? For example, if all fonts on my system are made for 75 DPI, can I configure fontconfig/Xft/GTK/whatever to render Pothana2000 text at a higher DPI?

I would really appreciate any thoughts or comments on this problem. It has been annoying me for two years now. :cry: 

Thanks.

---

### Post by singamayya on 2007-12-06
The solution to this problem is to enlarge the font file itself.

This article shows you how: [http://rassmalog.rubyforge.org/blog/2006-12-11-a-guide-to-telugu-on-ubuntu-gnu-linux.html#Enlarging-Telugu-text]("http://rassmalog.rubyforge.org/blog/2006-12-11-a-guide-to-telugu-on-ubuntu-gnu-linux.html#Enlarging-Telugu-text")

---

