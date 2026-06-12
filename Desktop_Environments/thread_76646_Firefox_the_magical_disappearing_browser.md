---
title: "Firefox: the magical disappearing browser"
date: 2005-10-15
forum: Desktop Environments
---

### Post by poptones on 2005-10-15
From a newsforge review:

*I kept running up against this first release nature of Ubuntu. For instance, sometimes Firefox would randomly just disappear. I do not know whether this is a Firefox problem or a Ubuntu problem, but since it never happened to me in SUSE or Mandrake or even (gasp!) Windows, I suspect it's Ubuntu.*

I must say I am *totally* over this. I've been hoping it would be resolved in the next release, and yet it never seems to get addressed. I've evne downloaded the mozilla browser from mozilla.org and it STILL crashes when visiting certain URLs. (like [this one]("http://72.14.203.104/search?q=cache:c5IFtr5hg-oJ:web.mit.edu/ist/products/evolution/2.0/evolution.pdf+novell+evolution+change+colors&hl=en&client=firefox"). In fact, it seems Firefox in ubuntu is pretty much unable to use google's "view as hml" feature AT ALL.

I have tried the stock "nv" driver and I have tried the nvidia driver. It crashes on the OOTB 1.02 version of firefox and it crashes on the "new and improved" 1.07 version. It crashes when image loading is disabled, it crashes when IPV6 is disabled, it crashes when java and javascript are disabled. It crashes when NO PLUGINS are installed. It just crashes...

I'm am at my wits end with this. words cannot convey how aggravating it is to have the browser magically disappear simply from clicking a link. It isn't like this happens sometimes - it seems to happen several times A DAY, usually when I am most involved in a bit of resaerch on something - poof, there goes your work (and the history as well, so forget retracing your path).

This is turning into a showstopper for me. I hate the idea fo trying to run slackware on dialup because it will mean FOREVEr to do simple software upgrades, but if it means I can actually USE my computer as it is intended then, as they say, you gotta do what you gotta do.

BTW, using epiphany doesn't seem to fix this - I just get a more behaved crash on the same sites...

---

### Post by poptones on 2005-10-15
Aha! A clue! changing "browser.display.use_document_fonts" has stopped this!

I suspected a font problem. Is this perhaps related to the .so6 library used by default? Is there a way to change it?

---

### Post by blueturtl on 2005-11-04
I'd very much be interested in a solution to this as well.

> Aha! A clue! changing "browser.display.use_document_fonts" has stopped this!

How do you set this? Can it be done for Mozilla as well as Firefox?

I currently use Opera when I want to be sure nothing will go wrong, but Mozilla has better plugin support, so I'd prefer using it instead.

---

### Post by poptones on 2005-11-04
The flags are set by typing "about:config" in the URL bar. 

It's been several weeks now and no more crashes. Seems like disabling the document fonts did the trick. I can still see international characters, I guess that just disables the document from being able to change the font intself, not the encoding.

---

### Post by blueturtl on 2005-11-05
Thank you so much. I hope this does the trick. I assume the browser also remembers the setting so I won't have to reset it all the time.

---

### Post by linkunderscore on 2005-11-07
My firefox does this when I click a link that launches an external application. If I click a link that opens my pdf viewer--crash. If I click a link to open a document via OpenOffice--crash. 

Does anyone know how to fix this? It only crashes when an external program needs to be launched, but it doesn't do it every time--just randomly.

---

### Post by Biffy on 2006-04-27
[QUOTE=poptones]Aha! A clue! changing "browser.display.use_document_fonts" has stopped this![/QUOTE]

Change it to what? 1 or 0 ?

---

### Post by TitusDalwards on 2006-04-27
my value of "browser.display.use_document_fonts" is 1 and everything seems well

---

### Post by kolesarm on 2006-05-02
[QUOTE=TitusDalwards]my value of "browser.display.use_document_fonts" is 1 and everything seems well[/QUOTE]
mine's one too, but i got that problem with disappearing windows - sometimes they just vanish..didnt happpen on windows..

---

