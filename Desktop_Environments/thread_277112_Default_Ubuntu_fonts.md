---
title: "Default Ubuntu fonts?"
date: 2006-10-14
forum: Desktop Environments
---

### Post by klato on 2006-10-14
I just installed the msttcorefonts from the terminal, but after looking at the fonts on my other user's desktop (which is default), I decided I preferred that look more.  How do I revert to those default Dapper fonts?  I really have no idea where to start.

(Also, how do I get my fonts to look like this? [http://www.ubuntuforums.org/attachment.php?attachmentid=17348&d=1160579990](http://www.ubuntuforums.org/attachment.php?attachmentid=17348&d=1160579990))


Thanks!

---

### Post by dagnabit dang doohickey on 2006-10-14
You should keep the msttcorefonts as the fonts in that package are pretty much an unofficial web standard.

To make your fonts look better, give [this]("http://ubuntuforums.org/showpost.php?p=1608934&postcount=5") a shot.

---

### Post by klato on 2006-10-14
dagnabit:

Thanks for the reply.  I've put the msttcorefonts back on, but it looks like everything in Ubuntu now uses these fonts for everything.  Is there any way to sort of select the font theme that was used when Ubuntu was first installed?

I'm going to try that link right now too, thanks.

Update: Ok I've tried that link, but things still looks the same over here. Everything looks like msttcorefonts. Thanks for any insight!

---

### Post by dagnabit dang doohickey on 2006-10-14
I'm not sure what you mean by "Ubuntu now uses these fonts for everything" because there are many differnt fonts in that package. It's essentially a package of all the MS default fonts such as Arial, Verdana, Times New Roman, etc.

You can change your system fonts by going to:

Ubuntu Menu > System > Preferences > Font

and then change the settings as you wish.


I've attached a screenshot of my Font Preferences.

---

### Post by klato on 2006-10-14
What I mean is that since installing the msttcorefonts, everything in Ubuntu looks like it's using those fonts (Firefox, the panels, everything) and they look very different from the default.

I've compared my font settings to yours, but the only difference I could see was that I had Subpixel smoothing on; other than that everything is the same.  And your fonts look way smoother than mine too...

Any other tips would be most appreciated :)

Here's a screenshot of mine:

---

### Post by dagnabit dang doohickey on 2006-10-14
If you were to change all your Font preferences to say, Times New Roman, do you now see Times New Roman all over the place?

Edit: I see that you use a custom theme. What happens if you change the theme back to the human theme?

---

### Post by klato on 2006-10-14
I just changed back to the Human theme, but the fonts remained the same.

I also changed my fonts to Times New Roman and yep, all the fonts change to Times New Roman.

Thanks for your replies btw, I know this is sort of nitpicking, but I'd really like things to look nice :)

---

### Post by dagnabit dang doohickey on 2006-10-14
Now change them back to Sans, Sans Bold & Monospace like you originally had them and see what happens.

---

### Post by klato on 2006-10-14
Ok now they all changed back to Sans, etc.

---

### Post by dagnabit dang doohickey on 2006-10-14
Save the following code as local.conf and put it in /etc/fonts directory.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>serif</family>
        <prefer>
            <family>Bitstream Vera Serif</family>
        </prefer>
    </alias>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>Bitstream Vera Sans</family>
        </prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer>
            <family>Bitstream Vera Sans Mono</family>
        </prefer>
    </alias>
</fontconfig>

```

Then update fonts cache with
```
fc-cache -fv
```

---

### Post by klato on 2006-10-14
Sweet!  That worked.  I restarted gnome and logged back in, but for some reason my mouse stopped working (??), restarted again, but then I got stuck at some command prompt...rebooted with ctrl+alt+del, and things seem to be working now.

I just can't believe it's that difficult to change fonts in Ubuntu!

I'm kind of wondering...what exactly was the problem?

Anyways, thanks for your help!

---

### Post by dagnabit dang doohickey on 2006-10-14
*Somebody please correct me if I'm explaining this wrong.*

Sans and Monospace (and Serif as well) are not fonts, they are links to fonts. So, when it became apparent that there was nothing strange about your Font Preference settings, it seemed as though those links might have been pointing to some undesirable fonts.

Another way to solve your problem would have been to select the appropriate Bitstream Vera fonts (Sans, Sans Mono, etc.) directly in the Font Preferences panel, but that seems more like a work-around than a fix. So, by doing what you did with local.conf, you fixed the links to point to the appropriate Bitstream font. And, by the way, you can point those links to any font you desire.

Why this happened to you, I have no idea. But, I guess it happens. ;)

---

