---
title: "No joke, I need Internet Explorer, or equivalent. :("
date: 2006-07-29
forum: Desktop Environments
---

### Post by newagelink on 2006-07-29
[quote=https://addons.mozilla.org/firefox/1419/]IE Tab [Firefox Extension] is not available for Linux.[/quote]
Specifically, I need an Internet Explorer (or equivalent) that will incorrectly render some code at  [http://www.mtsu.edu/%7Ephys2010/Lectures/Part_1__L1_-_L5/Lecture_1/Metric_System/body_metric_system.html](http://www.mtsu.edu/%7Ephys2010/Lectures/Part_1__L1_-_L5/Lecture_1/Metric_System/body_metric_system.html) ... Believe me, I would must rather use Firefox.

I'm taking an online course at [http://www.mtsu.edu/%7Ephys2010/](http://www.mtsu.edu/%7Ephys2010/) The professor used a website designer program to put the site together, which, of course, raped the HTML. The program based itself off Internet Explorer's crappiness, and uses ```
<SPAN STYLE="font-family: Symbol,serif; font-size: medium;">m</SPAN>
``` for what apparently should be ```
&micro;
```... "millimeter" versus "micrometer," etc. There are other symbols used as well... but in Firefox, Konqueror, Opera, and Epiphany web browser, they all show it as 'm'.

I've told him about it, and the only thing he did was add "This site should be viewed using a Windows Internet Explorer browser." to the front page as a warning to users such as myself, and tell me to "swallow my pride and use Internet Explorer."

Do you know of a workaround to show this crappy HTML in Firefox, or a web browser for Linux that's as shoddy as IE?

---

### Post by Ziox on 2006-07-29
have you tried ies4linux? best IE under wine...

what should the site look like?

can you provide a screenshot of how it looks for you?

---

### Post by Gentist on 2006-07-29
I haven't really had this problem thus far, so I haven't really looked at the alternatives, but when I design websites, I usually run IE through Wine ([http://www.winehq.com](http://www.winehq.com)). If that's not an option, perhaps you can make use of the greasemonkey extension for Firefox, and rewrite the buggy parts if it's just a rendering (code) "bug" ([http://greasemonkey.mozdev.org/](http://greasemonkey.mozdev.org/)). Note though that I have never used greasemonkey myself, so I don't know how useful it is.

---

### Post by newagelink on 2006-07-29
I'm trying to update wine now. I'm guessing either the [Wine User Guide]("http://www.winehq.com/site/docs/wineusr-guide/index") will tell me what to do, or else I just download [an] [Internet Explorer]("http://www.microsoft.com/windows/ie/default.mspx") [executable?] and try to open it with wine ...

---

### Post by fragos on 2006-07-29
Strangely this came up with Comcast and AT&T DSL registration.  Both these braindead companies told me I had to buy Windows to use the Internet.  I managed to register with Comcast running IE with Crossover Office.  The need was only to register and I haven't needed IE and always use Firefox.  Occassional I'll run into a problem getting a download I've purchased.  Some vendors of Palm OS software only provide downloads as Windows exe's or Mac sit's.  These vendors have always been willing to email file formats Linux will work with.  I've rarely had problems browsing.  The issue is rare and relate to Active-X which is MS proprietary.  I haven't IE running on my Linux system for a number of years.

---

### Post by Gentist on 2006-07-30
Just trying to install Internet Explorer through Wine may not work.

[http://www.frankscorner.org/index.php?p=ie6](http://www.frankscorner.org/index.php?p=ie6) might be outdated, so I don't know how well it works. You might also want to take a look at [http://appdb.winehq.org/appview.php?iVersionId=469](http://appdb.winehq.org/appview.php?iVersionId=469) if you run into problems.

---

### Post by newagelink on 2006-07-30
Ugh, this is frustrating. I think I've installed wine, but I'm not sure. [The winecfg command]("http://www.winehq.com/site/docs/wineusr-guide/config-wine-main#USING-WINECFG") works in the terminal, at least.

But it seems I have to configure stuff, then try to install /home/daniel/Programs/IE7BETA3.exe in a pretend Windows installation, which seems like a lot of work. I might as well just restart in Windows, then restart in Linux when I'm done. This sucks.

... and, ironically, Windows is the only OS [required by MTSU to use Clean Access Agent]("http://www.mtsu.edu/~itdsupp/techxpress/#7") - a program that monitors your internet activity, and forces you to update virus scanning software, and it quarantines your computer if it suspects a virus at your IP address ...

---

### Post by newagelink on 2006-07-30
> **Ziox said:**
> what should the site look like?

can you provide a screenshot of how it looks for you?Well, in Firefox and every other web browser I've tried except for IE and AOL Explorer (based on IE), you see two 'm's at that webpage. You're supposed to see one 'm' for milli, and then a kind of u -- &micro;, I believe is the coding for it -- for 'micro'.

I think it's wonderful that he made that website, free Physics lessons, but the HTML isn't so great ...

---

### Post by patrickfromspain on 2006-07-30
Ies4linux is what you need:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by linuksamiko on 2006-07-30
I use Konqueror and everything seams to be fine

it shows the "Mu" how it should look like. But I have the same problem like you with firefox. Maybe you should try it with konqueror.

But if you want to know how the Mu looks like: [http://en.wikipedia.org/wiki/Mu_(letter](http://en.wikipedia.org/wiki/Mu_(letter))

---

### Post by newagelink on 2006-07-30
> **linuksamiko said:**
> I use Konqueror and everything seams to be fineWhat character encoding are you using? I just installed Konqueror 3.5.2 and it's showing the same thing it shows in Firefox, the m, and then the m of a slightly different length, and I've tried forcing several different character encodings ... How is your Konqueror setup different from the default (or, at least, the 3.5.2. I installed through Synaptic Package Manager -- the Add/Remove Applications didn't have Konqueror listed, although it had Epiphany.)

---

### Post by linuksamiko on 2006-07-31
Here are my font and coding setup in konqueror (3.5.3):

font: FreeSans
coding:  ISO 8859-1

But you said that you had some letter that looked like an "m" with with a different length. I gues that this was the greek letter Mu that you have seen and that is exactly the right letter how micro is described in the metric system. 

I attached a picture of the Mu to this post.
For exammple if you have a micro-gram it would be: this greek letter mu + g (µg)

Even if I don't think that it has something to do with the version (you use 3.5.2 and I have 3.5.3) I give you the repository where you can download the latest version:
deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main

---

### Post by hugmenot on 2006-07-31
The Symbol font maps greek letters onto the latin alphabet. So the small m is the small mu on screen. Not very semantic but I think once you get Symbol this particular problem is gone.

---

### Post by newagelink on 2006-07-31
> **hugmenot said:**
> The Symbol font maps greek letters onto the latin alphabet. So the small m is the small mu on screen. Not very semantic but I think once you get Symbol this particular problem is gone.So how d'you get the Symbol font ...? Can I append it to Firefox or something?

---

### Post by az on 2006-07-31
Isn't there a firefox extension that allows you to view pages as though they were rendered incorrectly by IE?
EDIT:  Maybe this:
[https://addons.mozilla.org/firefox/35/](https://addons.mozilla.org/firefox/35/)

---

### Post by msandersen on 2006-07-31
On Windows when testing web pages I use a Firefox extension to switch the rendering engine between Gecko and IE by clicking an icon. The Netscape 7 browser, which I haven't tried, is based on ForeFox but also has licensed the IE engine, so you can use either. Could be Windows-only for all I know, but would be interesting if it was on Linux as well.

---

### Post by jimmygoon on 2006-07-31
Theres no chance that Opera does it is there? Otherwise use the sidenet config and install wine/ie6 it works fine

---

### Post by HunterPro on 2006-07-31
> **azz said:**
> Isn't there a firefox extension that allows you to view pages as though they were rendered incorrectly by IE?
EDIT:  Maybe this:
[https://addons.mozilla.org/firefox/35/](https://addons.mozilla.org/firefox/35/)not really - those Firefox plugins are just ActiveX IE objects within Firefox. So that plugin simply loads IE without any eyecandy and fits it neatly into a tab.

For linux there is only one serious option: [IEs4Linux](http://www.tatanka.com.br/ies4linux/index-en.html). Easy, Smart, Simple. It takes less time to install then it takes to take the trash outside ;)

---

### Post by mightyteegar on 2006-07-31
I also recommend IEs4Linux.  Not only does it install IE6, it gives you the option to also install IE5.5 and 5.0 if you really need compatibility that far backward.  And at least on my machine it runs faster than it ever did on XP.

---

### Post by hugmenot on 2006-07-31
Just look at your snippet. It asks for Symbol to render the letter "m". If Symbol is present a mu will be displayed because that´s what the m looks like in that font.

```
<SPAN STYLE="font-family: Symbol,serif; font-size: medium;">m</SPAN>
```

If it´s not present then a generic "serif" font is used.

You just need to get symbol.ttf or something and copy that into your .fonts folder.

Don´t know why you want to jump through hoops here.

---

### Post by newagelink on 2006-08-04
> **hugmenot said:**
> Just look at your snippet. It asks for Symbol to render the letter "m". If Symbol is present a mu will be displayed because that´s what the m looks like in that font.
```
<SPAN STYLE="font-family: Symbol,serif; font-size: medium;">m</SPAN>
```If it´s not present then a generic "serif" font is used.

You just need to get symbol.ttf or something and copy that into your .fonts folder.

Don´t know why you want to jump through hoops here.Wow, I wasn't aware it was that simple!

I downloaded the font from [http://www.webpagepublicity.com/free-fonts-s10.html#Free%20Fonts](http://www.webpagepublicity.com/free-fonts-s10.html#Free%20Fonts). Can you tell me where the .fonts folder is? It seems that the Search function in Nautilus only searches for files.

---

### Post by Jagot on 2006-08-04
/usr/share/fonts/

---

### Post by newagelink on 2006-08-04
> **HunterPro, quoting the suggestion to use the IE Tab Firefox Extension said:**
> not really - those Firefox plugins are just ActiveX IE objects within Firefox. So that plugin simply loads IE without any eyecandy and fits it neatly into a tab.I dunno how it works, but it doesn't seem to. I right click [http://www.mtsu.edu/%7Ephys2010/](http://www.mtsu.edu/%7Ephys2010/) > "Open in IE Tab":

Alert - Unable to find Internet Explorer

---

### Post by newagelink on 2006-08-04
> **Jagot said:**
> /usr/share/fonts/I just downloaded [the Symbol font]("http://www.webpagepublicity.com/free-fonts/s/Symbol.ttf") from [http://www.webpagepublicity.com/free-fonts-s10.html#Free%20Fonts](http://www.webpagepublicity.com/free-fonts-s10.html#Free%20Fonts), and I put it in /usr/share/fonts

Firefox and Konqueror both still show it as a different 'm' ... Do I need to restart my computer? (If so, then maybe it'll work tomorrow. G'night.)

---

### Post by Jagot on 2006-08-05
> **newagelink said:**
> Firefox and Konqueror both still show it as a different 'm' ... Do I need to restart my computer? (If so, then maybe it'll work tomorrow. G'night.)

You may need to run this command to get Ubuntu to recognise them:

```
sudo fc-cache -f -v
```

---

### Post by LKRaider on 2006-08-05
The best way to install fonts is open Nautilus, browse (CTRL+L) to **fonts:///** and drop the font file there.

---

### Post by mozillamike on 2006-08-05
When I first saw your post title, I thought you were one of those (insert explicative)'s that loves IE. 

But, I've totally had this problem re-designing a highschool's website. If you have jedit, or pspad (which I think is pc only), you can find and replace uneccesary code that appears repeatedly, that is if you don't need to see it with it's css, or form (which I believe you do).. otherwise, I would find a browser, maybe IE tab could eventually be implemented into other os's... I lack the coding abilities. Anyhow, good luck, and sorry your professor doesn't know how to code....

---

### Post by hugmenot on 2006-08-05
> **LKRaider said:**
> The best way to install fonts is open Nautilus, browse (CTRL+L) to **fonts:///** and drop the font file there.

Ah, interesting. Nautilus can aggregate system and user fonts.

What I meant was jsut to drop the font file into /home/<user>/.fonts
I should appear immediately.

---

### Post by tturrisi on 2006-08-05
Actually, the code he is using is OK, that it does not render in FF is a bug w/ FF, which is also an incomplete browser that is not 100% W3C standards compliant.
These are the real errors in the html code on the page in question:
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.mtsu.edu%2F%257Ephys2010%2FLectures%2FPart_1__L1_-_L5%2FLecture_1%2FMetric_System%2Fbody_metric_system.html](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.mtsu.edu%2F%257Ephys2010%2FLectures%2FPart_1__L1_-_L5%2FLecture_1%2FMetric_System%2Fbody_metric_system.html)

---

### Post by newagelink on 2006-08-05
> **LKRaider said:**
> The best way to install fonts is open Nautilus, browse (CTRL+L) to **fonts:///** and drop the font file there.Aha! That makes more sense; I didn't see any other fonts listed in the /usr/share/fonts folder, although that seemed like an aptly-named place for them to be... Now to see if it's had any effect on either Firefox or Konqueror.

---

### Post by newagelink on 2006-08-05
> **tturrisi said:**
> Actually, the code he is using is OK, that it does not render in FF is a bug w/ FF, which is also an incomplete browser that is not 100% W3C standards compliant.
These are the real errors in the html code on the page in question:
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.mtsu.edu%2F%257Ephys2010%2FLectures%2FPart_1__L1_-_L5%2FLecture_1%2FMetric_System%2Fbody_metric_system.html](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.mtsu.edu%2F%257Ephys2010%2FLectures%2FPart_1__L1_-_L5%2FLecture_1%2FMetric_System%2Fbody_metric_system.html)
I don't know if you can really call it a bug with Firefox. Even if it's legitimate to demand a user to have a specific font, is it not better to simply rely upon the UTF-8 encoding? (I think that's what &micro; is, anyway, unless that's just basic HTML.)

---

### Post by newagelink on 2006-08-05
Where is the Fonts:/// folder located?

I moved the Symbol font to that folder as root, and it seems to have not had any effect at all. A screenshot is attached of what I see.

---

### Post by hugmenot on 2006-08-06
Does it appear when you copy the font to the ".fonts" folder in your Home directory? If you have it open in Nautilus you need to hit Ctrl+H to unhide the dotted folders.
Check some font selection window to check whether it&#8217;s available.
Also open the font by double click and check whether the letters are indeed greek and you have the right Symbol font.

---

### Post by tturrisi on 2006-08-06
> **newagelink said:**
> I don't know if you can really call it a bug with Firefox. Even if it's legitimate to demand a user to have a specific font, is it not better to simply rely upon the UTF-8 encoding? (I think that's what &micro; is, anyway, unless that's just basic HTML.)
correct, it's not really a bug but more of a 'function not yet supported".  Unfortunately, the majority of www content is coded non-standard, thus browsers have been forced to "become smarter" to render content.  The built in rendering capabilities of browsers often conflict with w3c standards or result in minor rendering quirks.

---

### Post by newagelink on 2006-08-08
> **hugmenot said:**
> Does it appear when you copy the font to the ".fonts" folder in your Home directory? If you have it open in Nautilus you need to hit Ctrl+H to unhide the dotted folders.Oh, so *that's* where the .fonts folder is ... Yeah, it's there, /home/daniel/.fonts/Symbol.ttf
> **hugmenot said:**
> Check some font selection window to check whether it’s available. Also open the font by double click and check whether the letters are indeed greek and you have the right Symbol font.
The font works in OpenOffice.org Writer, and Font Viewer shows it ... [Metric System](http://www.mtsu.edu/%7Ephys2010/Lectures/Part_1__L1_-_L5/Lecture_1/Metric_System/body_metric_system.html) in Firefox still doesn't use the font, though.
Is it a problem with Firefox, then? Should I take it to [Firefox Support](http://forums.mozillazine.org/viewforum.php?f=38)? Well, no, 'cause it's not just Firefox -- Konqueror also doesn't use the Symbol font...

---

