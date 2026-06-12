---
title: "Epiphany &amp; FF download PDF's instead of opening them in the browser?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by kayas80 on 2006-06-09
Epiphany and Firefox are downloading PDF's instead of opening them in the browser window. Breezy didn't do this, it started since I upgraded to Dapper. 

Its really annoying when reading a PDF eBook - when I click to open a new page it gets downloaded and needs manually opening in Acrobat Reader instead of opening embedded within the browser.

Any ideas how this can be overcome?

Thanks

---

### Post by musicinmybrain on 2006-06-09
[Here's a thread]("http://www.ubuntuforums.org/showthread.php?t=25685") from the days of Hoary Hedgehog that tells how to do this with mozplugger. I haven't tried it, but it seems like it would still work.

---

### Post by patrickfromspain on 2006-06-09
in epiphany I think you have to install epiphany-extensions, which is in the repos.

---

### Post by kayas80 on 2006-06-09
[quote=patrickfromspain]in epiphany I think you have to install epiphany-extensions, which is in the repos.[/quote]

I can't see which extension would do the job - unless I'm missing it.

---

### Post by reinouts on 2006-06-24
[QUOTE=kayas80]Its really annoying when reading a PDF eBook - when I click to open a new page it gets downloaded and needs manually opening in Acrobat Reader instead of opening embedded within the browser.
[/QUOTE]
First, start using evince :) Then associate PDF files with evince by right clicking a PDF file > Properties > Open with. Next time when you download a PDF, evince will open it automatically. Much better than viewing PDFs inside a browser window...

---

### Post by dpm on 2006-06-24
[quote=patrickfromspain]in epiphany I think you have to install epiphany-extensions, which is in the repos.[/quote] 
You don't need epiphany-extensions for that. The package you need is called **mozilla-acroread**, which will allow you to open pdfs with acroread embedded in epiphany.

Although this seemed to work in Breezy for me, it does not work anymore in my Dapper installation. Your mileage may vary. There is a bug about this:

[https://launchpad.net/bugs/43655]("https://launchpad.net/bugs/43655")

Otherwise, if you want to use Evince for viewing pdfs within the browser instead of acroread, I would recommend you to have a look a the link *musicinmybrain* posted on how to use **mozplugger**. That's what I'm using at the moment, and although is not really optimal ([https://launchpad.net/bugs/46017)]("https://launchpad.net/bugs/46017%29"), it does the trick.

Cheers.

---

### Post by Kuraboy on 2006-06-24
Hi!

I have a simillar problem...

I have muzplugger installed with the following code for pdf:

```
repeat noisy swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
```

when I open in Firefox nothing happens.

If I take away the space between +9000+9000 and +useFrontEndProgram I get the pdf in a new small acroread window... why?!

and when I tryed to install mozilla-acroread, it wanted me to uninstall muzplugger... and I dont want that because then I wont see movies...

evince worked fine, but it is buggy, when I put it in fullscreen, I cant reach top menu because it dissapears when the mouse comes near it... 

the point is, why do muzplugger och mozilla-acroread conflict? Because then acroread cant embed inside firefox right?!

thnx for any help :)
/Kuraboy

---

### Post by dpm on 2006-06-24
[quote=Kuraboy]

I have muzplugger installed with the following code for pdf:

```
repeat noisy swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
``` 
when I open in Firefox nothing happens.

[/quote] 
If you want to use acroread with Firefox, I'd use the **mozilla-acroread** plugin instead of **mozplugger**. I find mozplugger to be extremely buggy.

[quote=Kuraboy]
and when I tryed to install mozilla-acroread, it wanted me to uninstall muzplugger... and I dont want that because then I wont see movies...
[/quote] 
Why are you using mozplugger to embed the video player? What video player are you using? I'm sure there is a firefox plugin for embedding your video player already. AFAIK, I've never used mozplugger for viewing videos (someone correct me if I'm wrong). I'm using mplayer through the **mozilla-mplayer** plugin.

---

