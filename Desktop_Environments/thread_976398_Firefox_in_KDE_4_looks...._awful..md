---
title: "Firefox in KDE 4 looks.... awful."
date: 2008-11-09
forum: Desktop Environments
---

### Post by arizonagroovejet on 2008-11-09
On Intrepid, with default out of the box settings, is the attached how Firefox is supposed to look under KDE 4? Note how the text in the tabs is far too low down, the focused tab barely looks sensible, the unfocused tabs are a mess. Note also the big fugly grey squares around all the input elements on the Google home page.


Do other people see this or is there something wrong with my set up?

I have gtk-qt-engine-kde4 installed.

---

### Post by Vadi on 2008-11-09
No, that looks fine. I believe KDE was going to port Firefox from gtk to qt/kde, so this is the result...

---

### Post by PmDematagoda on 2008-11-09
> **Vadi said:**
> No, that looks fine. I believe KDE was going to port Firefox from gtk to qt/kde, so this is the result...

No, you got that wrong, it was actually ported by Nokia and Mozilla for Maemo, Firefox Qt has been released but I don't think it has been accepted either by Mozilla or KDE officially as of yet. So for now, I think Firefox uses Cairo.

At OP:- You may want to file that as a bug if you got this on a stock Intrepid install.

---

### Post by PmDematagoda on 2008-11-09
> **PmDematagoda said:**
> No, you got that wrong, it was actually ported by Nokia and Mozilla for Maemo, Firefox Qt has been released but I don't think it has been accepted either by Mozilla or KDE officially as of yet. So for now, I think Firefox uses Cairo.

At OP:- You may want to file that as a bug if you got this on a stock Intrepid install.

---

### Post by Vadi on 2008-11-09
Thank you for the correction. I just remember reading KDE people being overly happy about that, hence my ***-umption in this case.

---

### Post by GameManK on 2008-11-09
This isn't a port of firefox to qt or anything like that.  This is gtk-qt-engine-kde4 doing its thing, poorly.  Unfortunately it doesn't work too well with firefox even though it looks nice for most other GTK apps.  There are already several bugs filed about this.

---

### Post by jacksaff on 2008-11-10
Install the firefox theme Kde4+Firefox3
It looks a LOT nicer...

---

### Post by arizonagroovejet on 2008-11-10
> **jacksaff said:**
> Install the firefox theme Kde4+Firefox3
It looks a LOT nicer...

That theme does help a lot but the ugly grey boxes on input elements are still there.

Just have to wait for gtk-qt-engine-kde4 to get 'fixed' I guess.

---

### Post by kernelhaxor on 2008-11-10
Install a GTK theme like 'human' or something else ..
Then go to  K-menu -> System Settings -> Appearance -> GTK Styles and Fonts .. and choose 'Use another style' and select your GTK theme .. that worked well for me ..
my firefox on Kubuntu looks as good as on Gnome

---

### Post by mindo on 2008-11-21
Hi!

I bumped in the same problem and using kde4+firefox wasn't good enough because the first thing i change on my (k)ubuntu installs are the fonts. Searching around on gnome-look.org i found [Kde4 Oxigenstyle ]("http://kims-area.com/?q=node/63"). Just install the deb, follow kernelhaxor instructions and choose kde4-oxygen theme.
Now all your gtk2 apps look great on kde4.

Cheers


ps: don't forget to revert firefox theme to the default in case you were using kde4+firefox and restart any gtk application you had already open

---

### Post by utkjamie on 2008-12-06
> **mindo said:**
> Searching around on gnome-look.org i found [Kde4 Oxigenstyle ]("http://kims-area.com/?q=node/63"). Just install the deb, follow kernelhaxor instructions and choose kde4-oxygen theme.
Now all your gtk2 apps look great on kde4.

Thank you! The problem only started happening for me when I started fooling around with appearance settings in KDE a few days ago and I figured it was something I had done wrong. I was so frustrated that I was just about to fully remove Firefox from my system and then do a fresh install when I noticed that Miro was showing the same rubbish-looking inputs and figured it was probably another bug in 8.10. I hate that I was right.

Thanks for the fix!

---

### Post by utkjamie on 2008-12-08
The workaround is tolerable but not a real solution, unfortunately. The big problem is that Firefox is completely ignoring the CSS settings of individual web pages when it comes to input boxes. It means that input boxes will show at "normal" size, even if the page design requires that they be smaller. It means no rounded corners or colored backgrounds if that's what the designer intended.

It doesn't make sense to me why KDE simply can't leave Firefox alone to render inputs the way it has always done. This was never a problem for me until recently (weeks after upgrading to 8.10) so I'm not sure what exactly the cause of the problem is. There has got to be a way to restore Firefox to normal and avoid KDE4 screwing it up.

---

### Post by blazemore on 2008-12-08
I thought this was one of KDE4's new "features". They probably called it a "dynamic" and usable interface.

---

### Post by utkjamie on 2008-12-08
> **blazemore said:**
> I thought this was one of KDE4's new "features". They probably called it a "dynamic" and usable interface.

I hope not. I don't believe that a "feature" should interfere with the actual content of a web page, including its design and layout.

---

### Post by Dieseler on 2009-01-24
8.10 with kde4
This is the settings and Firefox theme I am using now.

[IMG]http://i45.photobucket.com/albums/f99/Dieselerpics/new.png?t=1232844154[/IMG]

It looks like this. Tabs look good, I'm happy.

[IMG]http://i45.photobucket.com/albums/f99/Dieselerpics/next.png?t=1232844615[/IMG]

---

### Post by maigret on 2009-02-28
Right! Changing the theme to Strata resolved this bad looking problem easily :) Thank you very much for the simple but clever tip.

---

