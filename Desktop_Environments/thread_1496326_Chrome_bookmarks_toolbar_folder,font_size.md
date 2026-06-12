---
title: "Chrome bookmarks toolbar folder,font size"
date: 2010-05-29
forum: Desktop Environments
---

### Post by Experimental on 2010-05-29
The fontsize of the bookmarks in the toolbar are huge. I want to make them smaller. How can I do that ? I use latest chrome

---

### Post by Experimental on 2010-05-29
upup

---

### Post by Experimental on 2010-05-29
:s

---

### Post by Experimental on 2010-05-30
The bookmark's font size in the bookmarks toolbar are so big. I want to small them how can I do that

---

### Post by lovinglinux on 2010-05-30
Creating [multiple threads](http://ubuntuforums.org/showthread.php?t=1496326) and bumping them all the time won't help to get a response. Is not consider polite to do that. Please wait a t least 24 hrs to bump your thread.

I tried to find your answer, but this what I have found:

[http://www.google.com/support/forum/p/Chrome/thread?tid=0125470386276403&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=0125470386276403&hl=en)

[http://sites.google.com/a/chromium.org/dev/developers/design-documents/accessibility#Chrome_toolbar](http://sites.google.com/a/chromium.org/dev/developers/design-documents/accessibility#Chrome_toolbar)

I don't use Chrome, so I could be wrong, but I think you can't do what you want.

If you are looking for customization, then stick with Firefox. Chrome customization capability is a joke.

---

### Post by rykel on 2010-05-30
I noticed the big bookmark fonts too, and believe it is a Linux thing. You will find that the fonts in Windows Chrome looks really sweet, tiny and neat, especially if Clear Type is used.

---

### Post by cariboo on 2010-05-30
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Experimental on 2010-06-02
I am so sorry about that. It wont happen again. I've edited font-sizes in tree.css bmm.css but it didin't work

---

### Post by cKGunslinger on 2010-08-21
I realized I was running a months-old version of Chrome Beta, so I updated to the latest today, only to see my Bookmarks Toolbar font size become gigantic as well (like 16 or 18pt font.)

Still haven't found a solution or setting to fix this.  I did notice that when I played-around with the DPI settings in my font menu, teh Bookmark Toolbar Text did not change at all when raising/lowering the value (default 96dpi.)  Maybe Chrome is ignoring this setting?

---

Google Chrome	6.0.472.36 (Official Build 55963) beta
WebKit	534.3
V8	2.2.24.14
User Agent	Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.3 (KHTML, like Gecko) Chrome/6.0.472.36 Safari/534.3
Command Line	 /opt/google/chrome/google-chrome --enable-extensions --enable-plugins

---

### Post by the_mouse on 2010-09-03
That problem has been bugging me too for the last couple of months :(

---

### Post by Experimental on 2010-09-07
Still it is too big. Any ideas ?

---

### Post by the_mouse on 2011-02-20
Well, I guess it's a bug in Chrome, since it presented itself after an update between versions of the browser :(. I'm still struggling with larger font-size on my bookmarks bar in Chrome 10 beta.

---

### Post by rcolonia on 2011-04-14
I have the same problem. Chrome should use the system theme and DPI configuration... any solution?):P

---

### Post by the_mouse on 2011-04-18
Nope, same thing on Chrome 11 beta.

---

### Post by andyvy on 2011-10-02
Same issue here. Huge font in Bookmarks bar.

Only thing close to a solution I've come across is changing Font Rendering and even that doesn't make the font small enough, and usually breaks fonts else where in the OS. (Like my XChat looks terrible after changing Font Rendering...)

Change Font Render:

Click System > Preferences > Appearance >

In Appearance Preferences Window:

Click Fonts tab > Click Details button > 

Under "Hinting" section select "Full" instead of "Slight".

Check not just Bookmarks in Chrome but other font around your OS, make sure it's still readable. 

If anyone else finds a better solution, not a temporary one please post.

---

### Post by Copper Bezel on 2011-10-02
I don't think there is one. The bookmarks toolbar is a skinned element and doesn't depend on GTK settings. The rest of the interface can be skinned however you like by creating a custom theme extension, but that doesn't seem to apply to the bookmarks toolbar.

---

