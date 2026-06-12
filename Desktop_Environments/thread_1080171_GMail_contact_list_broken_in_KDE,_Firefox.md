---
title: "GMail contact list broken in KDE, Firefox"
date: 2009-02-25
forum: Desktop Environments
---

### Post by jackhab on 2009-02-25
I just switched from Ububtu to Kubuntu 8.1 KDE 4.1 and I have a problem with GMail contact list in Firefox 3.0.6 - it's completely unreadable like if the rows overlap each other. See attached picture.
I tried switching Firefox themes and GTK engines but the problem persists. The only way for me to see the contacts is to enlarge the page to enormous size which makes it unusable.

Any ideas?

Thanks.

---

### Post by giarca on 2009-02-25
Some days ago I found a thread who talk about the little buggy visualization of Firefox on Kde and give an example of this bad behaviour with Gmail too.
It's all about GTK style, so I bet you have enabled on System Setting --> Appearance --> GTK Styiles and Fonts --> Use my KDE style in GTK applications like everyone else.
Try that: install kde-style-qtcurve and gtk2-engines-qtcurve packages and then go to the config and select Use another style: QtCurve.
It looks better.
Hope you solve that problem.

---

### Post by jackhab on 2009-02-25
Yep, I've tried with and without QtCurve - it's all the same.

---

### Post by giarca on 2009-02-25
So it's not a problem related to buggy rendering of Firefox...
Have you tried to change font setting? Let all the page choose own fonts with a minimum size naturally!
I don't know what cause the problem only in Firefox.

---

### Post by jackhab on 2009-02-26
I played with the fonts settings also. The strange thing is that Gmail contact list is the only Web page (unfotunately very important one) I came accross this problem.

---

### Post by jetpeach on 2009-03-03
i have the same problem, if you find a fix. i haven't tried the fix. it only happens on my amd64 bit machine.

---

### Post by yther on 2009-03-03
Interestingly, I had the same problem, though I hadn't gone into my Contacts until I saw this thread!  Sure enough, all the contacts were squished together vertically and I couldn't read any of them properly.  I went to Appearance > GTK Styles & Fonts and told it to use QtCurve and keep my KDE fonts.  Then I restarted Firefox, and not only are my Contacts legible now, but my Inbox looks correct instead of having huge checkboxes that I can only see 50% of!

I'm using Firefox 3.0.6 with KDE 4.2 and QtCurve 0.59.3-xx, where the "xx" is a different suffix for **kde-style-qtcurve** and **kde4-style-qtcurve**.  To be safe, I had installed *all* of the packages with "qtcurve" in the name, so I don't know which one provided the fix for FF.

Oh yes, x64 here also, Intrepid.  :)

---

### Post by jackhab on 2009-03-03
"...installed *all* of the packages..."

That's the trick! The problem I installed QtCurve by sudo apt-get install gtk2-engines-qtcurve.
Only now, after I installed:

kde-style-qtcurve
kde4-style-qtcurve
kde4-style-qtcurve-kdeconfig
qtcurve

I have a perfect Firefox display. Thanks a lot, yther.

---

