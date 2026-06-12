---
title: "Strange forum font"
date: 2007-05-18
forum: Forum Feedback &amp; Help
---

### Post by Ramses de Norre on 2007-05-18
What font are these forums using? Because it's quite unfriendly for my version of freetype... (2.3.4-1). All bold fonts look terrible because of wrong anti-aliasing...
I'm no font expert but I hope that you guys aren't using some windows ttf font on a linux forum... This seems to be the only website that has this problem and on my system (which uses DejaVu sans) all fonts look perfect.

---

### Post by bashologist on 2007-05-18
You could make font-weight: bold !important; in your firefox userContent file maybe? I've never tried it myself but it should work.

```
[COLOR="Gray"]# To add css to your userContent:[/COLOR]
for d in ~/.mozilla/firefox/*; do [ -d "$d" ] && nano "$d/chrome/userContent.css"; done

[COLOR="Gray"]# Then add whatever you'd like. For example:[/COLOR]
body {
        font-weight: normal;
}

```
[http://www.w3schools.com/css/pr_font_weight.asp](http://www.w3schools.com/css/pr_font_weight.asp)

---

### Post by Ramses de Norre on 2007-05-18
But I don't really want to change it... My fonts work perfect on all other sites... It's just ubuntuforums whose bold fonts behave bad.

---

### Post by bashologist on 2007-05-18
While looking for a solution to the problem I came across a nice Firefox Add-on that you might find useful for disabling or editing styles of individual web pages. Let us know if this'll help.

[https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)
[IMG]https://addons.mozilla.org/en-US/firefox/images/addon_preview/60/1[/IMG]

---

### Post by Ramses de Norre on 2007-05-20
It probably will, but I'm not really looking for a solution from my end... 
What I really want to know is whether these forums are using a windows ttf font and why they choose for a font that seems to be quite freetype-unfriendly...
It could be a problem with my version of freetype and if someone can confirm that (for instance by telling me which free font these forums are using) everything is fine and the freetype developers are to blame.

So this is an "ethical" (don't know a better word in english to express what I mean) problem rather than something I want to solve for me.

But thanks for trying to help me anyway, it's appreciated nonetheless ;)

---

### Post by kerry_s on 2007-05-20
Can you post a screen shot of what your talking about, so we can see it?
Mine looks fine and i'm not using ms fonts.

---

### Post by Ramses de Norre on 2007-05-20
Look at the "W" and "y" in my post, and look at bold fonts in for example the "Unanswered Posts" button and the" Forum Feedback & Help:" banner on top of the page.

---

### Post by trak87 on 2007-05-20
Your image didn't look that bad to me. You can look at this forum page's css file to see what fonts the page is referencing. Here's the link:

[http://ubuntuforums.org/clientscript/vbulletin_css/style-c9675613-00074.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-c9675613-00074.css)

It looks like they are referencing MS fonts: Tahoma, Arial, Trebuchet MS. These font definitions are just suggestions to the browser however. And when these fonts aren't available, the browser will choose one of the other fonts in the list. For example, the body tag shows this:

```
font: 12px Tahoma, Sans, Arial, Helvetica, sans-serif;
```

So when the browser renders the body area, if you don't have the Tahoma font, the system will looks for Sans, and then Arial, and then the next one, etc. If it can't find anything, it will use the brower's default font.

You might try adjusting the "font rendering" at System, Preferences, Font. Also click the Details  button. Those options might help as well.

You could also install the msttcorefonts package and see how it goes.

---

### Post by Ramses de Norre on 2007-05-20
> **trak87 said:**
> Your image didn't look that bad to me. You can look at this forum page's css file to see what fonts the page is referencing. Here's the link:

[http://ubuntuforums.org/clientscript/vbulletin_css/style-c9675613-00074.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-c9675613-00074.css)

It looks like they are referencing MS fonts: Tahoma, Arial, Trebuchet MS. These font definitions are just suggestions to the browser however. And when these fonts aren't available, the browser will choose one of the other fonts in the list. For example, the body tag shows this:

```
font: 12px Tahoma, Sans, Arial, Helvetica, sans-serif;
```

So when the browser renders the body area, if you don't have the Tahoma font, the system will looks for Sans, and then Arial, and then the next one, etc. If it can't find anything, it will use the brower's default font.

You might try adjusting the "font rendering" at System, Preferences, Font. Also click the Details  button. Those options might help as well.

You could also install the msttcorefonts package and see how it goes.

Tahoma was exactly the proprietary font I was afraid for...
I personally belief it should be replaced by a free font (DejaVu for instance) in the css... I belief the other fonts aren't free neither, are they? I think it's not totally correct to use such fonts on a linux forum, but I may be a little fanatic...
I'll take a look into why tahoma is rendered so bad here, thanks for all inputs.

---

### Post by kerry_s on 2007-05-20
Yeah, it's not the forum fonts, it's your specific font setup.

sudo dpkg-reconfigure fontconfig-config

I have autohinter, always, and no.

---

### Post by Ramses de Norre on 2007-05-20
> **kerry_s said:**
> Yeah, it's not the forum fonts, it's your specific font setup.

sudo dpkg-reconfigure fontconfig-config

I have autohinter, always, and no.

The forum is only using an ms licensed font...

But anyway it seems like my tahoma.ttf was a little borked anyway and I replaced it by another one from a windows install on another machine.

---

### Post by kerry_s on 2007-05-20
Your not getting it, fonts are a personal choice, unless you have this->

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33034&stc=1&d=1179689010[/IMG]

checked, the web sites will use the fonts you selected, but if you let them choose there own font, they will use the first one on there list that you have installed.

---

### Post by Ramses de Norre on 2007-05-20
I do get it, and these forums have their fonts set to tahoma... Of course you can override it but I think the principle of setting tahoma as this forums font is a little strange because of the nature of this forum (a support forum for a free and open source operating system).

PS: I didn't think of disabling that option, I now have ubuntu forums in DejaVu ;)

---

### Post by lithorus on 2007-05-21
Actually it IS the forum that is sorta wrong and our systems that are right now. Recently the Tahoma font was added to the msttfcorefonts on Gutsy. So now we have the right font (Tahoma) while we didn't have it before and it would fall back to Sans. Like someone also said it's a little wrong to depend on a MS specific font.

---

