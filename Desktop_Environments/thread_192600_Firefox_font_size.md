---
title: "Firefox font size"
date: 2006-06-08
forum: Desktop Environments
---

### Post by reuben on 2006-06-08
Hey,

I'm running KDE/XGL/Compiz/Gnome-window-decorator. I have a fonts problem:

In most GTK programs (e.g. synaptic) the fonts are too small. I can increase them either by running gnome-font-preferences or from the appearances section in the KDE control panel. However, if I increase that font size, then the font in the menubar/toolbars of firefox get *too* big; i.e. it seems that they are a notch or two higher than the base GTK size.

Is there a way to bring the firefox fontsize down without affecting the general GTK font size?

Thanks

---

### Post by amunimanghi on 2006-06-09
Hold down Ctrl and Shift and press the hiphen (-) button. You can also go to view => text size => font size down. 

Hope this helps.

&#126;Amunimanghi

---

### Post by reuben on 2006-06-09
Thanks for the reply. However, this is the menubar/toolbar text, not the text within web pages. You'd imagine there'd be a firefox setting to change it, but I don't see it.

---

### Post by Zed on 2006-06-09
Go to Edit -> Preferences -> Content and there's a section on Fonts & Colors. Click 'Advanced' and you'll have control over your fonts (including whether it should always use your selections, or allow the web page to override them.)

---

### Post by reuben on 2006-06-09
Hi Zed,

I should be more explicit. I'm talking about the application fonts, i.e. the file /edit/view, etc, and the fonts in the toolbars (I use the webdeveloper toolbar). Firefox is not obeying the GTK font settings (or, at least, it is, but it is displaying 2 or 3 font sizes bigger than most other GTK apps seem to be)

---

### Post by Winblowz on 2006-06-09
I had the same problem a while back when I was using Gentoo. I solved the problem by going to System Settings -> Appearance -> GTK styles and fonts. You should be able to configure the font/size properties there.

Hope that helps you:D

---

### Post by oobuntoo on 2006-06-10
I had similar problem after I enabled XGL. All font settings for GTK apps through gtk-qt-engine were overided. All gtk apps fonts became smaller and use different font from before.

The way I solved this problem is to install and run "gnome-control-center" and change gtk font settings from there. I also ran "gnome-settings-daemon" on kde start up so that these setting will be applied everytime kde starts.

You can add "gnome-settings-daemon" to the compiz start-up script that you're already using right after "gconf-editor".

---

### Post by userundefine on 2006-06-10
Firefox's interface is XUL, and is controlled via CSS.  Whether or not you know CSS, you can customize any aspect of the UI with it.

In your profile, find the directory /chrome.  Inside, you'll probably have a file called userChrome-example.css.  Edit and rename this to userChrome.css.  Everything currently inside is commented out, but you can blank it if you want.  Place this code in the file:

```
* {
    font-size: 11pt !important;
}
```

And restart Firefox.  Only the font-sizes of your toolbars will be affected (menu bar, status bar, navigation bar, and any other toolbars of extensions).  Adjust as necessary until you're satisfied (you can even do font-size: 11.5pt !important if the difference between 11 and 12 is too much).

---

### Post by reuben on 2006-06-12
Excellent tip. Thanks

---

### Post by BeachBum on 2006-06-22
- userundefine

I have the same problem with the application fonts, and successfully created the CSS file for Swiftfox and Thunderbird.  The problem is that once I edit the CSS file, the fonts are resized to my liking, however upon reboot, Swiftfox and Thunderbird go back to their original settings.  The CSS file is still there and intact exactly as I last edited it, however I must delete the file and recreate it in order for either program to reapply my desired fonts.  Any ideas?

Thanks!

---

### Post by userundefine on 2006-06-22
BeachBum, that's pretty strange, I've never had that happen.  You might want to create a new profile and test it out again.  Failing that (and I don't see why it would), head on over to mozillazine.org forums -- the Firefox forums themselves.

---

### Post by BeachBum on 2006-06-24
I seem to have gotten things working now.  First, I was editing the wrong file (using the userContent.css in /etc), the correct file to edit is ~/.mozilla/firefox/(profile name, its just a bunch of random characters)/chrome.  I just did a filesystem search for "chrome" and looked in the wrong place ](*,)  

Then, I found out from here [http://www.mozilla.org/unix/dpi.html#CSS](http://www.mozilla.org/unix/dpi.html#CSS) that userChrome.css handles fonts for the application interface itself, while userContent handles the web interface.  So I inserted the text you provided below in userChrome.css for my Firefox profile, and in my Thunderbird profile (which can be found at ~/.mozilla-thunderbird/(profile name)/chrome), and now everything looks just right!

---

### Post by userundefine on 2006-06-25
I assumed people knew where their profile folder was, sorry.  I'm also embarrassed to see that I put userContent instead of chrome when I went on to mention "chrome", agh.  Glad you posted it.  Just for future lurkers:

Your Firefox profile is :

```
~/.mozilla/firefox/[randomly-generated-directory-name]/
```

---

