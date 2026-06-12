---
title: "Getting rid of ugly fonts: *Everywhere*?"
date: 2008-08-23
forum: Desktop Environments
---

### Post by tmic on 2008-08-23
Hello everyone!

I'm just trying to get nice, professionally looking fonts all over my Kubuntu-KDE desktop. What I have done so far is to copy some of the nicely bytecode-hinted TrueType fonts from my Windows partition to Linux (essentially the msttcorefonts and some others, such as Lucida and Tahoma). I set up KDE, Konqueror and Firefox to use them and it works fine apart from a couple of exceptions:

In Firefox, the menu fonts are still some other ugly fonts. In GNU emacs (the graphical X version), particularly the menu fonts are similarly ugly as the Firefox ones, and the text fonts are ok, but not perfect.

So my question is how to get rid of everything but a few selected fonts (namely the msttcorefonts) from the whole system. Can I define something like font aliases that redirect all applications asking for unwanted fonts to the msttcorefonts? If so, where can I define these aliases and how do I find out which fonts should be aliased?

Best Regards,

Michael

---

### Post by guinness1759 on 2008-08-23
Install Gnome. ;)

Really, I'm not sure. I've tried the same fonts I use in Gnome (which looks as nice as my Mac or Vista boxes (Calibri, Segoe UI (both from Vista/Office 2007), and VAG Round), and it still looks like a mismash, even with forcing my KDE fonts in FF. I just don't like how KDE renders them.

Here's my Gnome setup (Window title font is VAG Round, application font is Segoe UI, FF theme is Camifox (looks like Camino on OSX):
[[IMG]http://img225.imageshack.us/img225/1557/screenshot3fb0.th.png[/IMG]](http://img225.imageshack.us/my.php?image=screenshot3fb0.png)

And here is how it looks in KDE 3.5.9 (bleh):
[[IMG]http://img113.imageshack.us/img113/5031/snapshot5jj9.th.jpg[/IMG]](http://img113.imageshack.us/my.php?image=snapshot5jj9.jpg)

Maybe KDE 4 is better, but I couldn't stand it, and I never played with it too much.

---

### Post by AlanR8 on 2008-08-23
Been there and wondered the same thing. Here's what to do:

Go into System settings then GTK Styles and Fonts.
Check the box "Use my KDE  Fonts in GTK applications"

Apply the change and reboot the desktop Ctrl+Alt+Backspace.

You should now find your FF fonts on the menu bar etc are the same as elsewhere. :KS

---

### Post by tmic on 2008-08-24
Thanks Alan, setting GTK Fonts to the KDE styles did the trick for both firefox and GNU emacs (which apparently is GTK-based as well). For the record, I can add that in order to get the possibility to change GTK styles in the KDE system settings, I had to install gtk-qt-engine-kde4 first.

So I guess I should just hope that there will not be some odd X application coming up on my desktop some day that wants to use ugly fonts...

---

### Post by anupkshah on 2008-11-22
Hi,

Even though I had set the GTK font preferences from Kubuntu's system preferences, I still wasn't happy with GNOME fonts.

The following post got it back to how I used to have it on an older laptop:

[http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/](http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/)

Basically, from the post, save the following into ~/.fonts.conf
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Firefox fonts (and other GNOME apps) look beautiful again!

Hope it helps!

Anup

---

### Post by ellalan on 2008-11-22
Hi
How to make a directory in terminal(.fonts.conf)please, I am not sure how to do it. TIA.

---

### Post by oldos2er on 2008-11-22
.fonts.conf is a file, not a directory. Copy the "code" anupkshah posted, paste it into gedit (Text Editor), and save it as .fonts.conf

---

### Post by ellalan on 2008-11-22
I get this Error when I try to paste this code, what am I doing wrong?

---

### Post by oldos2er on 2008-11-22
You want to save it to your home directory, which would be /home/[yourusername]

---

### Post by ellalan on 2008-11-22
Thank you for the help, now I have saved it in my Home directory,how would I know what that made any difference to the appearance of my Fonts(bear with my ignorance).

---

### Post by ciscosurfer on 2008-11-22
> **ellalan said:**
> Thank you for the help, now I have saved it in my Home directory,how would I know what that made any difference to the appearance of my Fonts(bear with my ignorance).I suppose the first test would be to say to yourself, "Self, does it look better?"  Then you can go into your fonts settings and see if the changes you made actually took (System > Preferences > Appearance > Fonts tab).

---

### Post by ellalan on 2008-11-22
I am very sad to say that it hasn't made any difference at all, all my Fonts settings didn't change and they stay the same as prior to this editing.

---

### Post by llamakc on 2008-11-22
Log out, log back in.

---

### Post by ellalan on 2008-11-23
I have navigated to this .fonts.conf file and checked the contents then I get this notification at the top saying "This XML document ....."(Please view the attachment). I do like to see an improvement of my fonts, any suggestions please. Thanks llamakc I tried your suggestion.

---

### Post by ellalan on 2008-11-23
Sorry,I forgot the attachment,here it is.

---

### Post by anupkshah on 2008-11-23
ellalan,

This thread was about getting GNOME fonts looking decent if you are using Kubuntu.

From your screenshots it looks like you are using Ubuntu/GNOME already?

In that case, I don't know if these tips would apply to your situation.

---

### Post by ellalan on 2008-11-23
Thanks for the info.

---

### Post by oldos2er on 2008-11-23
You missed the

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

at the top of the file.

---

### Post by ellalan on 2008-11-23
> **oldos2er said:**
> You missed the

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

at the top of the file.
I did copied the whole thing in that quote box, I have tried second time as well but still for some reason these two lines keep missing.

---

### Post by anupkshah on 2008-11-24
Firefox won't show those things in the XML view. When you view source you should see it though.

---

### Post by pablo2525 on 2008-12-18
> **anupkshah said:**
> Hi,

[snipped]

Firefox fonts (and other GNOME apps) look beautiful again!

Hope it helps!

Anup

Howdy,

I'm looking at migrating from openSUSE 11 to kubuntu 8.10.  I have two machines.  One is currently running openSUSE and the other is running kubuntu.

After changing ~/.fonts.conf, the fonts on kubuntu are substantially better than the base system however they don't look as nice, yet, as on openSUSE.

Please see the attached .png.  You can see the difference between the two desktops - I vnc'd over to my laptop and scraped my screen.

Any ideas on what I can try?

Thank you.

---

### Post by anupkshah on 2008-12-22
Unfortunately I have no experience with openSUSE.

The attached screenshot: could it just be that remoting has lost font smoothing? I get that sometimes remoting to other boxes (but I have only remoted to Windows boxes so don't know for sure).

---

### Post by pablo2525 on 2008-12-22
> **anupkshah said:**
> 
The attached screenshot: could it just be that remoting has lost font smoothing? I get that sometimes remoting to other boxes (but I have only remoted to Windows boxes so don't know for sure).

Hi,

Thank you for your response.

No, the VNC'ing matched exactly what I'm seeing on the other machine.  I thought it was a nice side-by-side comparison.

For now, I think I'm going to stick with openSUSE 11.1  I'm _very_ close to having its fonts dialed in.  I'm very picky about having sharp and crisp fonts.

---

### Post by Zorael on 2008-12-23
I detailed the steps I take over on kubuntuforums.net. Link [here](http://kubuntuforums.net/forums/index.php?topic=3100304.msg162222#msg162222).

---

### Post by pablo2525 on 2008-12-23
Oh very nice ... okay, I'll burn down my openSUSE 11.1 and try kubuntu 8.10 with your instructions.  

Thank you for taking the time to respond to my post and to detail everything.

---

### Post by pablo2525 on 2008-12-23
Hi,

I burned down my openSUSE 11.1 environment and re-installed kubuntu 8.10.  I applied the `recipe'  The fonts look `okay', not crisp as I get them with openSUSE 11.1

They appear slightly smugdged.  Similar to before .. any other thoughts?

---

### Post by Zorael on 2008-12-23
Smudge or bloating usually means you have auto-hinting enabled, or lower hinting than full. Also, some fonts (Verdana) show up as fuzzy, hence why we're adding font substitutions to make Verdana show as DejaVu Sans/Kochi Gothic/Sazanami Gothic.

Could you perhaps provide a screenshot of that smudginess?

---

### Post by pablo2525 on 2008-12-23
Howdy,

I confirmed I have Hinting style set to `Full'

I'm attaching three sets of screenshots.

o The first set scrapes a web page.  You can see the `2' in `24 hours' has the `foot-point' missing in the `2' - the bottom pointy thing is what I'm calling the `foot-point'  :)

o The second set isn't a great side-by-side comparison but it does show how a small font (Tahoma) isn't being rendered as well on 8.10.  You can see `gkrellm' is running into itself ... or slightly blurry.  On the other hand, if you compare it to the time/date snip I include, you can see the small font is very clear on 11.0

o The third set compares the exact snippet from the same web page - I'll include this in a separate post as I'm limited to the number of attachments.

Thank you again for the assistance.

---

### Post by pablo2525 on 2008-12-23
and here is the third set:

---

### Post by Zorael on 2008-12-23
First of all, let me just say that I prefer the other set of screenshots with the smoother fonts. So every step so far has been on the road to getting just there. ;3

Are those bitmap fonts? Meaning, fonts defined pixel per pixel instead of vertex fonts (truetype) that are defined in mathematical shapes, much like normal bitmap pictures and vertex graphics. Bitmaps look great in lower sizes, but without any soft edges they quickly become blocky as they get larger. Vertex fonts look great in larger sizes, but as you get into the realm of the really small there's not enough pixels around to draw everything smooth and curvy, so stuff becomes an illegible blur. This is very noticeable when dealing with complex iconography like Asian characters. Hence, we enabled it in .fonts.conf and when dpkg-reconfiguring fontconfig-config.

Not all truetype fonts have bitmaps (again, mostly the Asian niche), but those that have usually display as bitmaps up to 16pt font size, at which point they're drawn as vertex characters. 

If I were you I'd:
[list][*]Try disabling antialiasing at this point and see what that gets you.
[*]Boot up into 11.0 and make note of what the font settings are. Is there a .fonts.conf? Make a backup of that one, or post its contents here.[/list]

In the last two attachments it's obvious that's two different fonts, likely because we made font substitutions in .fonts.conf (towards the end; that's probably Verdana).

---

### Post by pablo2525 on 2008-12-23
> **Zorael said:**
> 
If I were you I'd:
[list][*]Try disabling antialiasing at this point and see what that gets you.
[*]Boot up into 11.0 and make note of what the font settings are. Is there a .fonts.conf? Make a backup of that one, or post its contents here.[/list]

In the last two attachments it's obvious that's two different fonts, likely because we made font substitutions in .fonts.conf (towards the end; that's probably Verdana).

Aha!  I found the issue, I didn't have `Exclude Range' clicked on.  It wasn't clearly stated (to a dummy like me!) that I had to have it set.

I've left the default for now ... the small fonts look very sharp now.

Thank you.

---

### Post by Zorael on 2008-12-23
I just tried checking that and now my eyes bleed. Still, cheers. :3

---

### Post by pablo2525 on 2008-12-23
> **Zorael said:**
> I just tried checking that and now my eyes bleed. Still, cheers. :3

hah hah!  When I checked it, my fonts became very clear and the `2' was no longer clipped.

Thank you _very_ much for your help.

I'm still trying to decide between openSUSE and kubuntu.  I've been a long time openSUSE user so that's part of the `pain'; getting used to something new.

Take care.

---

