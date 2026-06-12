---
title: "Menu falls behind Flash Banner add on Firefox"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Barleyman on 2006-09-20
Hello All,

I have seen a few sites where a javascript menus will open behind a flash object (usually an ad or title) on Firefox on Ubuntu, but will be fine on Windows XP with firefox/IE.  

Here is screenshots similar to my problem.

[http://blogbeebe.blogspot.com/2006/03/annoyance-using-firefox-on-linux.html]("http://blogbeebe.blogspot.com/2006/03/annoyance-using-firefox-on-linux.html")

I am sure it is probably somesetting on flash a developer of the site forgot to add, but I can't change that.  Is there any workaround to this?  Because, I have to use the problem site every day, and I have to switch over to Windows everytime I need a menu item in the 2nd or 3rd position.

---

### Post by Barleyman on 2006-09-20
here is a site with the problem.

[http://www.ati.com]("http://www.ati.com")

---

### Post by pgilmon on 2006-11-14
I have the same problem, and there are lots of websites like that...

---

### Post by CatKiller on 2006-11-14
That's why you need to block Flash ads... or not install Flash in the first place, of course.

---

### Post by pgilmon on 2006-11-16
Well, flash is useful sometimes. Haven't you ever visited youtube?

---

### Post by WalmartSniperLX on 2006-11-16
What flash are you using? 

I had the same problem btw but I don't know if I still have it :S Right now I'm at school on Windoze. ](*,)

---

### Post by lazyart on 2006-11-16
Yeah, this happens on espn.com as well.

---

### Post by JairunCaloth on 2006-11-16
I have the same problem. It was occuring with the flash 7 and firefox 1.5, and now with flash 9 and firefox 2.0. Annother site with the problem is asus's website. Disabling flash is not an option for me.

---

### Post by CatKiller on 2006-11-16
There are tweaks that you can make to your userContent.css to not display images/Flash videos that are the same size as is commonly used for banner ads, or are called common banner ad names. And there's the Adblock extension for those that get through - or if you don't want to fiddle with your Firefox configuration. That's what I'd do if I were you.

Not that either of these are Linux things, of course. I did the same when I was using Windows.

---

### Post by Barleyman on 2006-11-16
It is not only a problem with ads, some sites use flash for the page titles as well.

fantasy football site.
[http://imgfly.com/files/161106_042725/fb.png](http://imgfly.com/files/161106_042725/fb.png)

adobes own site.
[http://imgfly.com/files/161106_042645/ad.png](http://imgfly.com/files/161106_042645/ad.png)

Not using flash is not an option for most people.  I have to use a specific fantasy football site because someone else chose it.  This is one little thing that continues not to work as well under Linux as it does in Windows.

---

### Post by Barleyman on 2006-11-16
I just found this posted on adobe's flash blog.

[http://blogs.adobe.com/penguin.swf/2006/11/chart_toppers.html](http://blogs.adobe.com/penguin.swf/2006/11/chart_toppers.html)

Check out point 2, it seems they are aware but have not time frame on a fix.

---

### Post by nyinge on 2007-01-19
> **Barleyman said:**
> I just found this posted on adobe's flash blog.

[http://blogs.adobe.com/penguin.swf/2006/11/chart_toppers.html](http://blogs.adobe.com/penguin.swf/2006/11/chart_toppers.html)

Check out point 2, it seems they are aware but have not time frame on a fix.

Yes, I'm having the same issue even with the latest Flash release, i.e. 9.0.31.0.  According to the blog (link in above quote), he/she is saying it has to do with Firefox.  However, I'm experiencing the same problem in Opera as well.  To test, just visit adobe.com, and hover your mouse over menus.

---

### Post by .adma on 2007-06-03
Did anyone find a fix for this...its driving me NUTS!

---

### Post by Barleyman on 2007-06-03
nope, 

Just go here if you want an example -> [http://www.adobe.com/](http://www.adobe.com/)

EDIT:  oops, should have read above.  My comment adds nothing.

---

### Post by azntfl on 2007-07-15
anyone find a fix for this yet??

---

### Post by WinterWeaver on 2007-07-15
I'm having the same problem atm... currently I'm just avoiding sites that has flash like this. Lately I've been thinking of installing a Flash Blocker for Firefox.

sorry, but I dont have any solution other than the flash blocker idea :P

WW

---

### Post by walkere on 2007-12-01
I've noticed this problem too.  It seems that a lot of the major retail websites like to use fancy Flash ads/headers right underneath their menus... and in the process make the menus unusable.

I tried re-installing Gnash to see if that would render it properly, but Gnash didn't render the flash videos at all (I checked Bestbuy.com and Walmart.com).

It seems to me that the problem would be in the way that the Flash plugin renders the video relative to other page elements... so is it possible that a future implementation of Gnash will fix the problem?

In the meantime, I thought I'd bump this in case anybody found a workaround (other than disabling flash) to get this to work.

- Walkere

---

### Post by pruss on 2008-03-12
It pretty annoying that this bug is there for more than 1.5 years and nothing happens:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613)
As more and more sites are providing video in flv it is a NOGO for Ubuntu.

Just my 2 cents,

Peter.

---

### Post by Leoncio on 2008-07-02
Word. It is definitely awkward to have such a huge bug like this for AGES and not a soul interested in fixing it (at least that's what it looks like).  I've just installed Flash Player 10 and I'm still having problems with **menus hiding under other objects** (**and, in some cases, flash banners covering the text**). This is definitely one of the things keeping me away from spreading Ubuntu to everyone I know.  Anyway, here's another couple of websites that show such problem, for debugging purposes:

[http://www.bovespa.com.br/]("http://www.bovespa.com.br/") (try the drop down menus)
[http://www.concursos.correioweb.com.br/]("http://www.concursos.correioweb.com.br/") (look for a rolling banner)

Cheers

---

### Post by iheartubuntu on 2008-07-02
Same problem for me. I started a thread below for help.

[http://ubuntuforums.org/showthread.php?t=847361](http://ubuntuforums.org/showthread.php?t=847361)

No answers. Im almost embarrassed now to all the people I got onto the Ubuntu/linux band wagon. So many websites are starting to use these pulldown menus.

Gnash didnt help me either.

---

### Post by MickS on 2008-07-02
I would suggest trying NoScript, seems to work for me.

Mick

---

