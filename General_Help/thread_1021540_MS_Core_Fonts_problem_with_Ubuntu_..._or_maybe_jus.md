---
title: "MS Core Fonts problem with Ubuntu ... or maybe just Firefox?"
date: 2008-12-25
forum: General Help
---

### Post by majabl on 2008-12-25
Happy Christmas, everyone.

My laptop has developed a bit of a font problem today.  I've had the Microsoft Core Fonts package installed for months now and it has been working without any problems.  Today, for some reason, none of the Microsoft fonts display in Firefox.  They do, however, work in Open Office Writer, so I'm not sure whether the problem lies with my Ubuntu installation or whether there's something in Firefox that's gone awry.

The attached screenshot should show what's going on - as I mentioned, I'm able to use the fonts without problem in Open Office, but in the background Firefox window the font displayed should be (and has been up until some time earlier this evening) Georgia.

The only thing I'm aware of having changed today is having installed Wine to run an Amstrad CPC emulator.  I wouldn't have thought that this should affect my font settings!

What have I done, and how do I get things back to how they were?

Thanks in advance!

---

### Post by kerry_s on 2008-12-25
try setting all the fonts again, move them to a different font, then back.

i can't tell from your screen shot what part your talking about.

---

### Post by majabl on 2008-12-25
Thanks for your response.  I've tried your suggestion but no joy, I'm afraid.

To clarify the bit of the screen that I'm referring to, I *think* that the Gnome-controlled parts are showing correctly (I've set them to 8-point Arial because this takes up much less space than the standard Gnome typeface), but the Serif font in Firefox ('mselves into something not quite so ludicrous.  Maybe.' and onwards) should be Georgia.  This is something that should be set either by a stylesheet or by the page directly.

I have the same problem with other websites.  For instance, BBC News - it should be rendered in Verdana (I think), but instead uses the nearest 'default' font provided with Ubuntu, which is a bit bigger and fatter.

---

### Post by Zorael on 2008-12-25
You could try defining what fonts make up Sans, Sans-serif and Monotype; that may just help. That's done in your **~/.fonts.conf** file. I have mine pasted [here](http://kubuntuforums.net/forums/index.php?topic=3100304.msg162222#msg162222) for reference.

---

### Post by kerry_s on 2008-12-25
> **majabl said:**
> Thanks for your response.  I've tried your suggestion but no joy, I'm afraid.

To clarify the bit of the screen that I'm referring to, I *think* that the Gnome-controlled parts are showing correctly (I've set them to 8-point Arial because this takes up much less space than the standard Gnome typeface), but the Serif font in Firefox ('mselves into something not quite so ludicrous.  Maybe.' and onwards) should be Georgia.  This is something that should be set either by a stylesheet or by the page directly.

I have the same problem with other websites.  For instance, BBC News - it should be rendered in Verdana (I think), but instead uses the nearest 'default' font provided with Ubuntu, which is a bit bigger and fatter.

sounds like you have it set to let the web site choose the font.

---

### Post by majabl on 2008-12-25
Yes, I have the setting to allow the website to define the font, but that's what I want and how I've always had that setting.  In the example I posted, the site is defining the font as Georgia, but Firefox isn't displaying Georgia.  This is despite me having the Georgia font on my computer and it working just fine in other applications, such as Open Office.

I'm stumped!

---

### Post by majabl on 2008-12-25
OK - I'm not very techy as far as Linux goes, so I'm going to need a little how-to help here! :-)

In my Home folder I have no .fonts.conf file but I do have a I have a hidden folder called .fontconfig.  Is this what you mean?

---

### Post by kerry_s on 2008-12-25
> **majabl said:**
> OK - I'm not very techy as far as Linux goes, so I'm going to need a little how-to help here! :-)

In my Home folder I have no .fonts.conf file but I do have a I have a hidden folder called .fontconfig.  Is this what you mean?

no, ".fontconfig" is the user font cache, it helps them display faster.

".fonts.conf" you create yourself.

---

### Post by majabl on 2008-12-25
Development: I've been fiddling with the 'Fonts' tab under System >> Preferences >> Appearance.

What I've found is that my Firefox font problem arises only with Subpixel smoothing enabled.  Using any of the other settings makes the fonts display as they should, though with the rest of the display looking rough around the edges.

See screenshots below - the first is set to Monochrome (fonts are correct but they look rubbish), and the second to Subpixel smoothing (fonts are wrong but they look better).

---

### Post by kerry_s on 2008-12-25
i don't know it looks correct to me.

---

### Post by majabl on 2008-12-26
Open up the last three pictures in this thread in a new Firefox window and maximise them, and then ctrl+tab between them.  In the one from my computer with subpixel smoothing set, Firefox is definitely not displaying the Georgia font specified by the webpage as it should.

---

### Post by majabl on 2008-12-26
*bump*

:)

(Happy Boxing Day, everyone!)

---

### Post by kerry_s on 2008-12-26
that is definitely georgia, you can tell by the numbers.

---

### Post by majabl on 2008-12-26
Looking back I think you're right, it is Georgia.  But it's definitely not being displayed as it should be, nor are other fonts in Firefox.  They're all either too big (BBC News or Wikipedia, for instance) or too small (most of LiveJournal, for instance), unless I switch away from subpixel smoothing, in which case they display as they should.

---

