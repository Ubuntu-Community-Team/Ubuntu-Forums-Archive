---
title: "Evince font rendering"
date: 2005-11-18
forum: Desktop Environments
---

### Post by marciano on 2005-11-18
Hi All,

I originally posted a message on this issue in the main Ubuntu Gnome forum, but realized that that was not the right forum for this kind of question. In any case, apologies for double-posting as a result. This message has further info though.

I just installed Breezy alongside my trusty "old" SuSE 10.0, and I must say I'm very impressed! Gnome seems /way/ faster in Ubuntu than in Suse.

However, I do have one issue. The Evince document viewer in Breezy renders PDF fonts quite poorly compared to the same viewer in SuSE. FYI, SuSE 10.0 uses Evince-0.4.0 and poppler-0.4.2, just like Ubuntu.

I have attached two screenshots to demonstrate the problem: the first (on the left) is from SuSE, and the second (on the right) is from Ubuntu. The document shown was produced by pdflatex, using type1 Computer Modern (i.e. standard TeX) fonts. It renders perfectly in Acrobat and, as I mentioned, Evince/Suse.

I also checked KPDF under both SuSE and (K)Ubuntu: same problem.

Any ideas? Thanks!

Marciano.

---

### Post by 23meg on 2005-11-18
Are you sure that your font settings are the same in both distros? The Ubuntu screenshot looks non-antialiased to me.

---

### Post by marciano on 2005-11-18
[QUOTE=23meg]Are you sure that your font settings are the same in both distros? The Ubuntu screenshot looks non-antialiased to me.[/QUOTE]

Yes, they are---sorry I should have mentioned this. I use the Freetype autohinter with the "hintmedium" setting and subpixel decimation with VBGR pixel arrangement---which, however, is irrelevant as far as Evince is concerned, because it only seems to use grayscale antialiasing under both SuSE and Ubuntu, as can be seen by magnifying either picture.

What's more, font settings in the Gnome font panel or the .fonts.conf configuration file do not seem to affect Evince rendering, at least under Ubuntu [they do affect system fonts, etc., of course].

M

---

### Post by Zwack on 2005-11-18
I haven't seen that myself, so you might want to check out the font settings...

System->Preferences->Font

You have four options for Font Rendering and you can select Details to get even more detailed settings.  I am using an LCD screen at work and am using SubPixel Smoothing, with Full Hinting.  At home I'm using a CRT with Best Shapes and Full Hinting.

Play with the options in there and find ones that look good.  You may well be able to get settings that look better.

You may also want to look into the fonts installed in Synaptic and add all of the fonts you can find.

Failing that can you provide a small sample PDF that other people can look at to see if we have the same issue or not.  If we don't then we can start looking into differences between the setups...

Z.

---

### Post by 23meg on 2005-11-18
marciano: I thought that would be the case as well; pdf is a world onto its own. I'll compare how my documents look in different distros/viewers and see if I can come up with anything useful. In the meantime, check how your document is rendered in xpdf under Ubuntu.

---

### Post by marciano on 2005-11-18
[QUOTE=Zwack]I haven't seen that myself, so you might want to check out the font settings...

System->Preferences->Font

You have four options for Font Rendering and you can select Details to get even more detailed settings.  I am using an LCD screen at work and am using SubPixel Smoothing, with Full Hinting.  At home I'm using a CRT with Best Shapes and Full Hinting.

Play with the options in there and find ones that look good.  You may well be able to get settings that look better.

You may also want to look into the fonts installed in Synaptic and add all of the fonts you can find.

Failing that can you provide a small sample PDF that other people can look at to see if we have the same issue or not.  If we don't then we can start looking into differences between the setups...

Z.[/QUOTE]

Maybe I wasn't clear. All application fonts work perfectly. The problem is only with PDF documents displayed within Evince (Poppler, actually, as that's what Evince uses for rendering). And as I've said, the setup is absolutely the same under both distributions.

As for installing additional fonts, this should be irrelevant, as pdflatex embeds all required fonts (or subsets thereof). Again, these are standard type1 CM fonts. [I also tried installing the latex-xft-fonts package, but that, as expected, did not change the results].

M

---

### Post by canadianwriterman on 2005-11-18
There are a couple of other PDF viewers you can install through Synaptic: gpdf and Acrobat Reader. You might want to install them and see if they render differently. As I recall, gpdf renders the same as evince, but Acrobat Reader is better.

---

### Post by marciano on 2005-11-18
[QUOTE=23meg]marciano: I thought that would be the case as well; pdf is a world onto its own. I'll compare how my documents look in different distros/viewers and see if I can come up with anything useful. In the meantime, check how your document is rendered in xpdf under Ubuntu.[/QUOTE]

I did. Under SuSE, I can see no difference between xpdf and Evince. Under Ubuntu, there is a difference---I'd say the output is closer to that under SuSE, although not identical (and not as good). But I'm now working under SuSE, so I can't double-check.

Thanks for the suggestions though...

M

---

### Post by ow50 on 2005-11-18
There's some PDF-specific problem in Evince. I have noticed that the same document with the same CM fonts is rendered significantly differently depending on whether it's PS or PDF. 

[[IMG]http://img292.imageshack.us/img292/2839/kuvakaappaus5lt.th.png[/IMG]](http://img292.imageshack.us/my.php?image=kuvakaappaus5lt.png)

---

### Post by marciano on 2005-11-19
[QUOTE=ow50]There's some PDF-specific problem in Evince. I have noticed that the same document with the same CM fonts is rendered significantly differently depending on whether it's PS or PDF. 

[[IMG]http://img292.imageshack.us/img292/2839/kuvakaappaus5lt.th.png[/IMG]](http://img292.imageshack.us/my.php?image=kuvakaappaus5lt.png)[/QUOTE]

Interesting. Your PDF output is similar to mine (but there are also some other font issues, with some characters being of a different height than others, which I have not noticed in my output). However, your PS output is very similar to my PDF output under SuSE! I assume you used dvips to generate it, and instructed it to embed the type1 CM fonts, right?

Perhaps I should make a bug report about it. Any thoughts? M

---

### Post by ow50 on 2005-11-19
[QUOTE=marciano]I assume you used dvips to generate it, and instructed it to embed the type1 CM fonts, right?[/QUOTE]
Actually, I just downloaded two files, lyhyt2e.ps and lyhyt2e.pdf, off the internet. However, the effect is the same with files I have made myself with latex, dvips, ps2pdf and pdflatex. PDF always renders worse in Evince than the corresponding PS.

You can compare Evince to Gnome Ghostview (ggv). At least for me ggv renders both PSs and PDFs properly.

---

### Post by chichilalescu on 2006-06-22
hello everyone... what i would like to find out, is how to make kghostview render pdf's like adobereader. (i have ubuntu/kubuntu 6.06; kpdf and document viewer all look like kghostview, documentviewer worst; xdivk looks great and has all the options, but it's just dvi's)
i attached a picture of kghostview next to the adobe reader.

---

