---
title: "firefox missing window"
date: 2008-05-07
forum: Desktop Environments
---

### Post by DoorGunner on 2008-05-07
Hi 

I have a minor issue with firefox. I am missing the window that normally goes around it. I have the window on all other gui's and applications. Just not firefox. 

Thank you

---

### Post by CoolGoose on 2008-05-07
Can you add a screen shot please and tell us what Ubuntu version are you using ? Also are you using compiz ?

---

### Post by Newbuntuguy on 2008-05-22
I am also missing my window frame in Firefox. This has just occurred in Hardy Herring. I noticed that after the upgrade to Hardy Herring that my Emerald window decorations were not operating correctly. That is they weren't what I had before so I opened the Emerald Theme Manager and selected a different theme. This should change the themes just when it is clicked. At that time, nothing noticeable happened. Then when I launched Firefox, I noticed that it began to flicker and the frame is gone. Below is a screenshot.

[IMG]http://farm3.static.flickr.com/2349/2513866064_12409235b3_b.jpg[/IMG]

---

### Post by High Roller on 2008-05-28
Here's how to replicate the bug.  You need to have Ubuntu's "Visual Effects" enabled to trigger this.

1.  Open a single instance of Firefox with no tabs open.
2.  Go to [http://www.htmlgoodies.com/legacy/beyond/javascript/bigsmall.html]("http://www.htmlgoodies.com/legacy/beyond/javascript/bigsmall.html")
3.  Click the "Maximize" link located at the top left of this webpage.
4.  Close Firefox.
5.  Re-open Firefox.
6.  Now the titlebar for Firefox and upper/lower panels should be missing.

You will also notice that the "Edit--> Preferences" will open under the browser instead of on top as well as the "Downloads" window.

To get Firefox back to "normal" you need to:

1.  Press "F-11" twice.
2.  Click the "Maximize" button at the top right of you Firefox Window.
3.  Notice that your top panel disappears but the bottom one remains present.
4.  Right click on the Firefox process within your bottom panel and click "Move"
5.  With your mouse, drag the window down a bit so that you can manually resize it to your ideals.
6.  Hit the "Maximize" button again and it should be back to "normal".

Can anyone indicate of a bug report before I go ahead and form one?
I'm pretty sure this is a compiz/window manager bug brought on by the behavior of Firefox.  But I'm not a developer so I haven't a clue about where the real problem exists.

---

### Post by cireg on 2008-09-07
I am experiencing the same problem in my Fedora environment:
Linux heloderma 2.6.25.14-108.fc9.i686 #1 SMP Mon Aug 4 14:08:11 EDT 2008 i686 athlon i386 GNU/Linux

compiz.i386                              0.7.6-2.fc9            installed 
emerald.i386                             0.7.6-1.fc9            installed
firefox.i386                             3.0.1-1.fc9            installed

---

### Post by MoebusNet on 2008-09-25
FF3.0.2 on all web pages. Followed your fix; it worked. Thanks Highroller!! I would add a Thanks to your count, but don't know how.

---

