---
title: "Suggestions for better font?"
date: 2009-02-04
forum: General Help
---

### Post by tneva82 on 2009-02-04
Ubuntu default font is something I find hard to read. Also I seem to have trouble finding how to change the font in the programs main window(ie where I'm writing now). Anyway anybody have good suggestions for more eye-friendly fonts? I'm starting to get headache from the default ones :-/

---

### Post by mb_webguy on 2009-02-04
You can change the system font (used on the Gnome panels and menus) by going to System->Preferences->Appearance and clicking on the Font tab.  If you're using an LCD monitor, it may also help if click on Subpixel Smoothing under Rendering.

This won't change the font used in your web browser, however.  If you're using Firefox, you can change the default font by going to Edit->Preferences, clicking on the Content tab, and changing the setting for Default Font.  Generally, a sans-serif font is easier to read on a computer screen than a serif font (which tends to be easier to read on paper).

---

### Post by Therion on 2009-02-04
My own personal suggestion: Try using Verdana, 'bout 10pt or 11pt or thereabouts.  You can also try adjusting the settings in the Fonts section of the [Appearance Preferences](http://www.techotopia.com/images/4/46/Ubuntu_desktop_font_settings.jpg).  Full Hinting might help; check out the options under the "Details" button too.  

What looks best to you is going to be a matter of personal preference so you may just have to try playing around with the different options.  Often a font will look better at one resolution than it does at another as well.

Oh, and if you don't HAVE the MS fonts installed (like Verdana):```
sudo apt-get install msttcorefonts
```
Then refresh your font cache:```
sudo fc-cache -fv
```

---

### Post by Yashiro on 2009-02-04
> You can change the system font (used on the Gnome panels and menus) by going to System->Preferences->Appearance and clicking on the Font tab. If you're using an LCD monitor, it may also help if click on Subpixel Smoothing under Rendering.
Subpixel rendering and Slight Hinting works best on Linux.

You want to grab some nice sans fonts. If you have a copy of Windows try those fonts. You can download them too if you're lazy.
The same goes for Apple Mac Truetype fonts.

There is a free font called Liberation which is quite good. It's easy to find.

The best sans font I've seen running on Linux is called Segoe and is a Windows Media Center font.

---

### Post by jespdj on 2009-02-04
I like the [Liberation fonts](apt:ttf-liberation). They are open source (unlike the Microsoft msttcorefonts). See also [this for more info](http://en.wikipedia.org/wiki/Liberation_fonts) about the Liberation fonts.

---

### Post by tneva82 on 2009-02-04
Thanks. Sans serif suggested above is good for now. I'll look at the other suggestions later when I have time(this solved essential problem so now attention to higher priority issues).

Thanks!

---

