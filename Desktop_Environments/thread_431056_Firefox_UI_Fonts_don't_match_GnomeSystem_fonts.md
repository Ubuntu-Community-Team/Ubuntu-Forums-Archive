---
title: "Firefox UI Fonts don't match Gnome/System fonts"
date: 2007-05-02
forum: Desktop Environments
---

### Post by hollywoodb on 2007-05-02
See screenshot section; neither Firefox's UI nor its page rendering are nearly as crisp as Gnome's (menu/panel and desktop icon text).

---

### Post by justinjstark on 2007-05-02
I just noticed this over the past few days.  I don't remember the firefox fonts being like this before but maybe I just never paid attention.

The fonts are kind of blurry compared to gnome fonts.

---

### Post by oomingmak on 2007-05-02
I've always had problems with the fonts in Firefox on Linux (no problems whatsoever with Firefox on Windows though).

Font rendering on Ubuntu is pretty ropey as it is, but by following certain tweak guides (and by substituting fonts like Segoe UI) I have managed to get mine looking acceptable (though still no where near as good as Windows).  

However, when it comes to Firefox on Ubuntu, the font rendering is truly revolting, and no matter what I do I just can't find a way to improve it. In fact it's so bad that I can't browse the web for any length of time because it really strains my eyes and gives me a headache.

On my particular Ubuntu setup, the system fonts are ok (after tweaking), but any fonts displayed *within *applications (e.g. Open Office, Gedit, Firefox etc) all seem to render really badly, with Firefox probably being the worst of them all.

---

### Post by justinjstark on 2007-05-02
Okay, this is driving me nuts.  Fonts were never like this before.

I found an old development shot of a website I was working on and the fonts were a lot crisper with the exact same settings.  So, this is a recent development for me.

Now, small text is extremely hard to read and the black on white text is really fuzzy.

---

### Post by LuisGMarine on 2007-05-02
> **justinjstark said:**
> Okay, this is driving me nuts.  Fonts were never like this before.

I found an old development shot of a website I was working on and the fonts were a lot crisper with the exact same settings.  So, this is a recent development for me.

Now, small text is extremely hard to read and the black on white text is really fuzzy.

What you just said is what I just got today.  The text got a lot blurrier and really small, man you read my thoughts!  You nailed this right on the head, I will deff be watching this thread to see the fixes.  I turned on my PC today and I got smaller texts in firefox, and everything just looks worst than it already was!

Good Luck

-LuisGMarine :guitar:

---

### Post by justinjstark on 2007-05-02
This is odd.  There haven't been any updates so why is this all of a sudden affecting everyone?

---

### Post by justinjstark on 2007-05-02
Go into synaptic and reload your packages.  I just had four updates that seem to have fixed the problem.

---

### Post by LuisGMarine on 2007-05-02
Try the guide blow, totally fixed my problems with text in general all around!

[Click Here!]("http://http://ubuntuforums.org/showthread.php?t=343670")

Good Luck

-LuisGMarine :guitar:

---

### Post by PrimoTurbo on 2007-05-02
Guide did not fix anything, my eye hurt from the small fonts used. Everything is messed up and I hate ubuntu fonts.

---

### Post by LuisGMarine on 2007-05-03
Read this thread below, this fixed worked for this person.

[Click Here!]("http://ubuntuforums.org/showthread.php?t=425579")

Good Luck

-LuisGMarine

---

### Post by hollywoodb on 2007-05-03
Renders fine in Fedora.... Compare to what I posted above.

---

### Post by dschaller on 2007-05-07
I had the same problem as the original poster. Solved it by installing the Microsoft core font package.

sudo apt-get install msttcorefonts

---

### Post by Iokua on 2007-05-07
I've spent months trying to find the "right" font configuration that makes Ubuntu's fonts in Firefox/OpenOffice tolerable. Unfortunately, I haven't met with the amount of success that I had originally hoped for. I have however found that the best solution for my tastes is to do the following:

[LIST=1]
[*]Install msttcorefonts package AND Tahoma (which is not part of msttcorefonts and must be installed separately). Use [this guide]("http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html") to complete the installation of Tahoma and its hints file. This allows Firefox to use fonts like Arial, Verdana, and Tahoma, which can greatly improve web readability. 

[*]Use the improved [subpixel font rendering package as described in this thread.]("http://ubuntuforums.org/showthread.php?t=343670") This really does make a difference.

[*]If you're on an LCD, as I am, don't use full hinting. It's far too blurry for my tastes. I set the hinting to Medium, or I use Best Shapes/Best Contrast.

[*]Use Deja Vu Sans/Serif or Bitstream Sans/Serif across the board.

[*]Make sure X is set to 96dpi. Go to the terminal and run: xdpyinfo | grep resolution. Unfortunately, I think there's a bug in Feisty (or maybe X) that prevents modification of xorg.conf to fix dpi. I have to resolve this one for Feisty, although it worked in Edgy.
[/LIST]

As with most font configurations, this is largely a matter of taste. I can't stand the jagged look of aliased fonts, but I also can't stand the uber-bold, fuzzy look of anti-aliased Ubuntu fonts. In my opinion, the standard "Linux fonts" are poorly designed, and no amount of hinting makes them look any better. They only look good at large font sizes. This is one area I wish Ubuntu would really invest in. Better fonts and font rendering doesn't seem like a small issue to me, but most people tend to brush this off for some reason.

To be honest, I think this is one area where Microsoft is leaps and bounds beyond Linux. Some may complain about patents, but that is no excuse. With time and money from the community, I have no doubt that Freetype and Linux fonts could exceed their patented rivals, but most people would rather spend their time on desktop effects and other more exciting features.

If fonts don't look good, laypeople won't adopt Linux. My brother refuses to run Linux for this very reason and I imagine he isn't alone.

---

### Post by img on 2007-05-07
I agree 100% with you. 

Instead try to do more stupid desktop effects, and trying to imitate MacOS or Vista Gui's we need to focus more in all those things that stop users from using linux, and font rendering is one of them. I did the subpixel font trick and now my ubuntu looks better than windows. It;s a shame OpenOffice looks so bad in linux, and developers running just to add more and more functions without fixing the SAME old bugs since StartOffice 5.2. And this goes all over linux. That's the main reason I left linux during the last year, even that my first OS was linux ( I started using computers on '93, with linux as my only OS). Today I come back to linux mainly due to Ubuntu and because I did miss linux, but not because I didn't like windows....

---

### Post by clevin on 2007-05-08
ok, my experience
I installed Kubuntu then uninstall it, after that my firefox's font didn't match gnome's font anymore. 

I solve the problem by** editing the ~/.font.conf** , there is a **hintxxxx,** change to the right string that fit your setting, (you probably are using "**hintfull**")

im guessing that mozilla's products are using font.conf, and when Kubuntu changed it, gnome then lost control of it.

---

### Post by hollywoodb on 2007-05-08
Yeah, I tried that.  Didn't help in my case.

If installing msttcorefonts is helping people with this issue I'd say it is pretty twisted that Ubuntu is set up to use Microsoft fonts to render properly.  I've never had to install those fonts in any other distro.

---

### Post by hollywoodb on 2007-05-08
Yeah, I tried messing with ~/.fonts.conf as well, even copying the font configuration from Fedora which has a normal-looking Firefox.  Didn't work.

I wouldn't worry about it, it isn't the first or even second time I've encountered difficult-to-explain difficult-to-fix breakages in ubuntu.

---

### Post by mannheim on 2007-05-08
> **hollywoodb said:**
> Renders fine in Fedora.... Compare to what I posted above.

In this Fedora screenshot, you have subpixel anti-aliasing enabled (not just in Firefox, but in the panel at the top). In the Ubuntu screenshot, you only have gray-scale anti-aliasing enabled.

---

