---
title: "Is it a virus?!!?"
date: 2010-06-30
forum: Desktop Environments
---

### Post by manolomanolo on 2010-06-30
Hi to all.

Suddenly my desktop environement has turned this way:

[IMG]http://img196.imageshack.us/img196/692/screenshotjba.png[/IMG]

Actually the defefct started with gradual bad visualization of Firefox web pages and menu. Same defevt on Thunderbird. So I closed both Firefox and Thunderbird and the defect affected my desktop menu, icons and panel.

This is in turn how my desktop appears after restarting the system:

[IMG]http://img413.imageshack.us/img413/2617/screenshot1xd.png[/IMG]

Please take a look at the shadow border on the upper panel of the two screenshots and please notice that there's no defect on the desktop background. Also I noticed no defect when opening images, despite all the menu items and icon names were unreadable.

Any suggestion, please?

Thanks.

---

### Post by 3Miro on 2010-06-30
This not a virus, the only thing that is wrong is the font. Somehow FireFox messes up your fonts. You can what settings you have in FF and Ubuntu about languages and fonts. However, I am not sure what the exact problem can be.

---

### Post by celldweller1591 on 2010-06-30
No need to worry..its just a font problem..easy to sort out. Head to "languages and fonts" and select appropriate language and it should work !

---

### Post by Pitazboras on 2010-07-01
Hello,

I have something that seems to be a similar problem. Generally, it's about totally messed up rendering of some pages. It started with Qt web page ([http://qt.nokia.com](http://qt.nokia.com)), which looks like this any time I open it:
[IMG]http://i50.tinypic.com/xcw0b6.png[/IMG]
At first I ignored this since it was the only page with such problems but recently I encountered some other ones. However, Qt web page is the only one in which I can reproduce this glitch 100% times and where it appears right after entering the page (on the others the glitch shows after quite long time using the page).

**Some additional information:**

[LIST]
[*]The glitch is present on both Firefox from repository (3.6.3) and Mozilla Developer Preview 3.7a5.
[*]I'm using Kubuntu 10.04 with KDE 4.4.2 (maybe some Qt & GTK conflict?).
[*]IIRC the glitch occurs since I switched to 64bit system. I haven't had any problem like this before and I'm using Kubuntu since 6.06 or so (and Firefox since ~0.10).
[*]The glitch seems to "propagate" to other parts of Firefox - as you can see from screen above, there are some font rendering problems (similar to the one from manolomanolo's screen shot) on Firefox UI as well as on other pages. All of them start after entering that Qt website. However, I haven't experienced this problem on any other part of the desktop (unlike manolomanolo).
[*]Turning off CSS (View -> Page Style -> No Style) seems to solve all rendering problems. Unfortunately, most pages are terrible to use without styles ;)
[*]I tried disabling all Firefox extensions, including Ubuntu Firefox Modification (which, as I understand, is installed by default on Kubuntu) but it haven't solved the problem.
[/LIST]
Thanks in advance for any idea how to solve this problem (and sorry for any mistakes, I'm not English native speaker)!

---

### Post by 3Miro on 2010-07-01
@Pitazboras: this is not the same issue. I believe it is flash related, especially since it only appeared after you switched to 64-bit. The solutions that I can think of are:

1. Install Swiftfox + 32-bit flash, which is an optimized version of FireFox and it is 32-bit (hence you can use 32-bit flash).

2. Install the beta version of 64-bit flash (google or search the forum for 64-bit flash)

If you have any more questions, please start a new thread, since this is a separate issue, it would be rude to hijack this thread.

---

