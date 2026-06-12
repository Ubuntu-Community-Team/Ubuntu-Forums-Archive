---
title: "Problems with Japanese in LaTeX"
date: 2009-01-18
forum: General Help
---

### Post by orchidfire on 2009-01-18
Hi everyone.

I'm getting really frustrated with trying to input Japanese in LaTeX&#8212;I'd really like to make some PDFs with Japanese in them, but nothing seems to work.

I've tried this tutorial and followed it exactly: [http://www-alg.ist.hokudai.ac.jp/~jan/japfonts.html](http://www-alg.ist.hokudai.ac.jp/~jan/japfonts.html)

This is my test document:

> \documentclass{article}
\usepackage{CJK}
\begin{document}
\begin{CJK}{JIS}{ipam}
&#24859;&#12375;&#12390;&#12427;
\end{CJK}
\end{document}

However, Terminal says this:

> ! Package CJK Error: Invalid character code.

See the CJK package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.119 
        &#65533;&#12375;&#12390;&#12427;
? h
The second byte of the CJK code is out of range.
Do you use the right encoding scheme?

Did I do something wrong with the files?  Is my input not in EUC?  According to SCIM, I'm using Anthy to input Japanese, and the dictionary is in EUC-JP.

I'm also a real beginner to Ubuntu, so detailing every step, especially with notes that should be obvious (such as where the files *are* in the first place&#8212;it took me forever to find ttfonts.map because I didn't know I had to install the other package, and I didn't know where to look for anything), would be especially helpful.

Additionally, I have tried this tutorial: [http://www.fsfe.org/en/fellows/ciaran/ciaran_s_free_software_notes/using_latex_to_make_pdf_documents_with_japanese_characters](http://www.fsfe.org/en/fellows/ciaran/ciaran_s_free_software_notes/using_latex_to_make_pdf_documents_with_japanese_characters)

The files it provides are running through pdfLaTeX fine, but, when I opened them, the encoding they're in seem to be different than just typing Japanese straight into LaTeX.

I got halfway through this tutorial: [http://ubuntuforums.org/archive/index.php/t-695479.html](http://ubuntuforums.org/archive/index.php/t-695479.html)

However, the Cyberbit stuff just looked far too confusing for me, and the first tutorial I tried seems to be the most straightforward.

Thanks in advance.  This thing has been frustrating me to no end.

---

### Post by hugmenot on 2009-01-19
Why not use XeTeX? You can edit in plain Unicode and choose a Japanese font of your liking. An Example:
```
\documentclass{article}
\usepackage{fontspec} 
\setmainfont{Kochi Mincho}
\begin{document}

&#24859;&#12375;&#12390;&#12427;

\end{document}
```

You need to process this with "xelatex filename.tex". You can find out what fonts on your system provide Japanese with:
```
fc-list :lang=ja
```

---

### Post by orchidfire on 2009-01-19
Wow, thanks so much!  This works so beautifully; it's unbelievable how ridiculously easy that was.

I just have one more question&#8212;my document is primarily in English and just contains examples in Japanese.  Can I change fonts within the document (for just my few words in Japanese) instead of setting the entire document to the Japanese font?  The Japanese looks good, but the font is a bit awkward for English.

Using the commands found [here]("http://www.ee.iitb.ac.in/~trivedi/LatexHelp/latexfont.htm") work for the English portion of my assignment, but not the Japanese.  The problem with this is that it means I have to change font for the majority of my document instead of for the smaller Japanese portions, which seems a bit inconvenient.  Does that make sense?

---

### Post by hugmenot on 2009-01-19
Be aware that regarding Latex help on the web there is a huge amount of really ancient cruft around. Tex and Latex are very old but they have come a long way. Still, obsolete solutions swamp Google searches with -- let&#8217;s call it -- noise.

I have two suggestions. One is to switch to the Japanese font only for Japanese words. That should be easy. It uses the great userfriendliness of «fontspec».

```
\documentclass{article}
\usepackage{fontspec} 
\setmainfont{URW Palladio L}
\newfontfamily\jap[Scale=0.8]{Kochi Mincho}  % here we simply define a new font switch
\begin{document}

I don&#8217;t know what {\jap &#24859;&#12375;&#12390;&#12427; } means ...

\end{document}
```

So, you just em-brace your Japanese and switch the font inside using your new font macro. For many more nice options read «fontspec.pdf».


My second suggestion would be to use «[polyglossia]("http://www.ctan.org/tex-archive/macros/xetex/latex/polyglossia/")». This is a modern alternative to «babel». With it you can switch actual languages, with their proper hyphenation and all that. Possibly overkill for you.

Thirdly, there are nice fonts that have good looking and matching latin in them. Microsoft has this new development, Meiryo. Perhaps you can find it.

---

### Post by hugmenot on 2009-01-19
Mh, I think for suggestion two, you would even need to supply the japanese definition file [from here]("http://www2.math.kyushu-u.ac.jp/user/index.php?cmd=read&page=iwase%2Fitoniki&word=xetex"). Seems no Japanese support is shipped with polyglossia.

---

### Post by orchidfire on 2009-01-19
This works beautifully; thanks!  All this is so easy I could cry; I spent hours the other day trying to work with the other solutions, and they just refused to work.

One last minor quibble&#8212;when I have quotes, `', in my file, they're not rendered as the nice, curved quotes, &#8216;&#8217;, which regular LaTeX does just fine.  Is this a XeTeX thing?  How would I get my curved quotes back?

**Edit:** Ignore that last bit&#8212;I forgot that, since I can just input those quotes directly, I don't have to fiddle with that formatting.  Awesome.

---

### Post by hugmenot on 2009-01-19
Oh, right. You should also add
```
\usepackage{xltxtra}
``` 
for some automatic goodness. And for the good old typographic quotes you need to specify this mapping once:

```
\defaultfontfeatures{Mapping=tex-text}
```

---

### Post by orchidfire on 2009-01-19
Thanks!

Another question that probably seems really trivial but has been bugging me—how do I bold these Asian fonts?  I've noticed that \bf and \textbf don't seem to apply to Japanese and Chinese characters.  However, I would like to have the capacity to bold things, mainly to make my documents easier to read.

Do the fonts lack the capacity to be bolded, or do I need to add some sort of workaround?

---

### Post by hugmenot on 2009-01-20
Ok. You may know that there is some software that is able to give you a « faux bold » version of a font if there is no proper bold version of this font installed. Similarly some software can algorithmically slant a font if there is no true italic around. But of course both of these are a poor man&#8217;s version of real bold and italic faces.

XeTeX simply doesn&#8217;t do that. You have to find a font that has a true bold face, and then you can use \textbf regularly.

Check again what « fc-list :lang=ja » returns. If it doesn&#8217;t list « Bold » anywhere, then you need to install a font that has it.

---

### Post by Angus77 on 2009-03-03
Okay, I have:

```
Mona:style=Regular
KanjiStrokeOrders:style=Medium
Sazanami Mincho,&#12373;&#12374;&#12394;&#12415;&#26126;&#26397;:style=Mincho-Regular,Regular
WenQuanYi Zen Hei,&#25991;&#27849;&#39515;&#27491;&#40657;,&#25991;&#27849;&#39551;&#27491;&#40657;:style=Medium,&#20013;&#31561;
Kochi Gothic,&#26481;&#39080;&#12468;&#12471;&#12483;&#12463;:style=Regular,&#27161;&#28310;
Kochi Mincho,&#26481;&#39080;&#26126;&#26397;:style=Regular,&#27161;&#28310;
VL PGothic,VL P&#12468;&#12471;&#12483;&#12463;:style=regular
Sazanami Gothic,&#12373;&#12374;&#12394;&#12415;&#12468;&#12471;&#12483;&#12463;:style=Gothic-Regular,Regular
KonatuTohaba:style=Regular
kiloji \- B,&#12365;&#12429;&#23383; \- B:style=Regular
kiloji \- D,&#12365;&#12429;&#23383; \- D:style=Regular
kiloji \- P,&#12365;&#12429;&#23383; \- P:style=Regular
unifont:style=Medium
kiloji,&#12365;&#12429;&#23383;:style=Regular
Konatu:style=Regular
VL Gothic,VL &#12468;&#12471;&#12483;&#12463;:style=regular
```

none of which has bold or italics.

Does anyone know a good, free CJK font that has these features?

The problem I'm finding is that with many of these fonts I can't even bold the Roman characters.

---

### Post by Pro-reason on 2009-03-23
> **Angus77 said:**
> Okay, I have:

...

none of which has bold or italics.

Does anyone know a good, free CJK font that has these features?

The problem I'm finding is that with many of these fonts I can't even bold the Roman characters.

The thing is, italics and bold are features of the Roman alphabet, not Han characters.  It is right that these fonts don't bother with them.

Either use fake bold and slanted characters, or abstain from using them.  For bold/italic Roman characters, use a Western font.

---

