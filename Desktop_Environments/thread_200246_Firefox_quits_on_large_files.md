---
title: "Firefox quits on large files"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Peepsalot on 2006-06-20
I have a particularly large file that I would like to view in firefox. ([http://us2.php.net/get/php_manual_en.html.gz/from/a/mirror](http://us2.php.net/get/php_manual_en.html.gz/from/a/mirror))
The problem is everytime I try to open it, firefox loads much of it, but then suddenly closes itself.  I know it is a ridiculously large html file(~14mb uncompressed), but I figured 1gb of ram(not to mention swap space) could handle the displaying of that.

This is definitely repeatable on my computer, but I don't know about others.  Is this a built in(intentional or not) size limit for firefox?

I know there is a version of the documentation that is in separate files, but I would like to be able to open this one, and make a print a large selection from it.  Doing this from the separate files is a pain.

---

### Post by bionnaki on 2006-06-20
right-click
and "save links as"

---

### Post by Peepsalot on 2006-06-20
Um ok.  I've already tried that.  I still need to open the file after saving it.

---

### Post by nanotube on 2006-06-20
[QUOTE=Peepsalot]Um ok.  I've already tried that.  I still need to open the file after saving it.[/QUOTE]
what's your firefox version?
running this with 1.5.0.4, the official mozilla release (as opposed to the ubuntu repositories version), on breezy, it works just fine for me. if you are using something different, i would suggest getting the official mozilla release (there is an automatic script to do that that you can find in the first link in my sig, under the "install firefox 1.5" section)
another thing you could try (if you don't want to install the official mozilla 1504 release), is to disable your extensions, maybe?

---

### Post by aysiu on 2006-06-20
I've downloaded 700 MB ISO files through Firefox. There's no built-in size limit.

Maybe you have a corrupt profile? Try [this](http://www.ubuntuforums.org/showthread.php?t=103930) and see if it makes a difference.

---

### Post by nanotube on 2006-06-20
[QUOTE=aysiu]I've downloaded 700 MB ISO files through Firefox. There's no built-in size limit.
[/quote]
well, we are talking about something different here, not just downloading a large file with firefox, but /opening/ a large file with firefox. but...
> 
Maybe you have a corrupt profile? Try [this](http://www.ubuntuforums.org/showthread.php?t=103930) and see if it makes a difference.
... your idea about corrupt profile is a good one. certainly something worth trying before resorting installing another copy of firefox.

---

### Post by Peepsalot on 2006-06-25
Well, I'm running Firefox 1.5.0.4.  I tried clearing the profile, but that didn't help.  I tried the script from the link in your sig to install the official mozilla release, but still have the error.  I tried it in swiftfox and the same thing happens.

Are you sure you were able to load the entire document in your browser?  On my computer, the document takes so long to load(about a minute before it crashes), that if you just look at the top of the page you'd think it is loaded, but if you scroll to the bottom, you see it is still rendering.

---

### Post by Stirling on 2006-06-25
I am able to view that in Swiftfox just fine.  I verified that it finished loading too.  I assume since you cleared your profile that means you tried viewing the page with no extensions installed?

---

### Post by Peepsalot on 2006-06-25
Yep, no extensions and it still crashes on my computer.

---

### Post by nanotube on 2006-06-25
[QUOTE=Peepsalot]Well, I'm running Firefox 1.5.0.4.  I tried clearing the profile, but that didn't help.  I tried the script from the link in your sig to install the official mozilla release, but still have the error.  I tried it in swiftfox and the same thing happens.

Are you sure you were able to load the entire document in your browser?  On my computer, the document takes so long to load(about a minute before it crashes), that if you just look at the top of the page you'd think it is loaded, but if you scroll to the bottom, you see it is still rendering.[/QUOTE]

yes, i am sure. the document loaded completely (i scrolled to the end). 
well, if firefox doesn't do it, you could try a text-mode browser, like w3m or elinks. :)

but really, iam not sure what's going on with firefox. you could try contacting the firefox devs with this.

---

### Post by Peepsalot on 2006-06-25
I let it crash and submitted a report with the built-in talkback or whatever it is called.  I left my email address and tried to explain the problem.

Should I do anything else like submit it to bugzilla as well?  I'd hate to pester the devs more than necessary.

---

### Post by Peepsalot on 2006-06-25
Agh. I loaded it in Opera, but when I go to print selection, I got 7 pages of completely unformatted text.  Not a single line break, totally illegible.

Does anyone just sell a hardcopy of this documentation?

---

