---
title: "bad quality with cups-pdf"
date: 2009-05-09
forum: General Help
---

### Post by soyouzz on 2009-05-09
So this morning I just reinstalled Cups-pdf (it worked fine with Intrepid on my computer) but now with Jaunty, the pdf quality is really poor and I really don't now why. Here is what I get when i "print" a good pdf:
[[IMG]http://img530.imageshack.us/img530/626/capturel.th.png[/IMG]](http://img530.imageshack.us/my.php?image=capturel.png)
What should I do?

---

### Post by nikgare on 2009-05-09
You don't need to use cups-pdf anymore, you just select "print to file" from the print dialogue box, then select pdf

---

### Post by soyouzz on 2009-05-09
Actually "print to file" is not available in every  print dialogue box and in acrobat reader, I have to print it firts into a .ps file then convert it into a .pdf file which is pretty annoying.

---

### Post by nikgare on 2009-05-09
Didn't realise that, sorry.
In the System->Printing maybe you need to change the settings of the cups-pdf printer - it looks like the image is set to draft?

---

### Post by HumbleGod on 2009-05-13
I'm having the same problem. I've tried upping the dpi, but documents still come out looking really awful. Is there some other thing we should be adjusting?

---

### Post by Go_Bucks on 2009-05-15
Same problem here... I use it on a daily basis, and am screwed now that this has happened. CUPS-PDF is converting fonts to graphics, and that is part of the problem. There is nothing in settings to fix this behavior. What did they mess with this when it was working fine?

---

### Post by Slim Odds on 2009-05-15
Looks like a font problem.

Are there some fonts that aren't installed now that were with Intrepid?

---

### Post by Go_Bucks on 2009-05-15
> **Slim Odds said:**
> Looks like a font problem.

Are there some fonts that aren't installed now that were with Intrepid?

I don't think it is a font problem. I have all of the same fonts that I have always had. I produce a PDF on this computer with cups-pdf, view it on this same computer, and it looks like hell on this computer or any other I view it on. Documents are NOT being encoded with fonts, though. They are being converted to an image and then to a PDF, which also makes for larger file sizes. This means that the PDF's produced by cups are not searchable and you can not copy and paste text.

I did some research. Saw a lot of people complaining and no solutions. I also discovered that apparently ghostscript is used by cups to create the PDF... don't know if that is the problem.

---

### Post by HumbleGod on 2009-05-17
Did this only start showing up in Jaunty with cups-pdf 2.5.0? I never used Intrepid, so I don't know how long this has been going on.

The cups-pdf changelog doesn't show anything that jumps out at me as explaining the difference since Hardy's version (2.4.6). That said, I am not a programmer by any stretch, so maybe something here can explain whether one of these changes makes the difference:

```
2009-01-25 : 2.5.0
  - new option to truncate long filenames
  - spoolfile is purged on errors
  - failed chmod() on output is treated as non-fatal
  - updates and additions to the documentation
  - removed additional changelog from source code
#

2008-06-22 : 2.4.8
  - fixed too small allocation of postprocessing string
  - corrected typo in the config file documentation
  - update for the SELinux .te-file in contrib/
#

2008-03-24 : 2.4.7
  - corrected the exit codes to match CUPS' specifications
  - original username passed to PostProcessing as 3rd arg
  - made PPD file auto-selectable via IEEE-1284 device id
```

I also checked cups-pdf 2.4.6 on my Hardy desktop, and it also depends on Ghostscript, for what it's worth. In fact, the dependencies are largely the same (aside from Hardy relying on cupsys 1.1.15 and cupsys-client, whereas Jaunty relies on cups 1.1.15 and cups-client - I'm presuming these aren't really different packages). The only noticeable difference is that Jaunty's cups-pdf depends on an older version of libc6 (>=2.4, whereas Hardy's cups-pdf depends on libc6 >=2.7-1).

I wish I knew what to do with this information; I'm hoping with more programming knowledge is equally irritated and checks this out.

---

### Post by HumbleGod on 2009-05-17
This problem has a launchpad page: [https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/366949](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/366949)

---

### Post by JohnnyVW on 2009-05-24
Probably a silly question...

Is there a way to install an older version that works?

Maybe there is a gs option that is missing?

---

### Post by DeMus on 2009-05-24
> **soyouzz said:**
> Actually "print to file" is not available in every  print dialogue box and in acrobat reader, I have to print it firts into a .ps file then convert it into a .pdf file which is pretty annoying.

In Acrobat reader, which is a pdf reader, you print to ps and then convert to pdf?
Why would you do a thing like that when you have a pdf file already, the one you are reading in Acrobat reader?

---

### Post by kaibob on 2009-05-26
Just upgraded to Jaunty, and I'm not experiencing the poor print quality, although I find that the text is not selectable or searchable. I printed a gedit text document with cups-pdf and this has always been searchable in the past but isn't any longer. I checked the cups-pdf configuration file and the ghostscript defaults are unchanged. I also opened some old PDF documents in Evince, and the text could be selected, so this is not an Evince issue. I hope this is fixed soon.

---

### Post by NoOp on 2009-05-29
> **HumbleGod said:**
> This problem has a launchpad page: [https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/366949](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/366949)

I found that jaunty cups-pdf does not embed the fonts from the original document. Tested with hardy - no problem, tested with intrepid - no problem, tested with jaunty - no fonts. I filed a bug before noticing your reference, see:
[https://bugs.launchpad.net/bugs/381788](https://bugs.launchpad.net/bugs/381788)
[[jaunty] cups-pdf no longer embeds fonts in pdf file
] I've included two pdf's, one printed w/hardy and one printed with jaunty.

---

