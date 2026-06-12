---
title: "Best Way to Install Additional ttf Fonts"
date: 2005-06-02
forum: Desktop Environments
---

### Post by j_baer on 2005-06-02
What is the best way to install additional ttf fonts?  I am aware of the ".fonts" folder option but wanted them available globally.

I tried the how-to from the ubuntu guide but that didn't work for me.

Thanks ...

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=j_baer]What is the best way to install additional ttf fonts?  I am aware of the ".fonts" folder option but wanted them available globally.

I tried the how-to from the ubuntu guide but that didn't work for me.

Thanks ...[/QUOTE]
 Do you already have the font files (.ttf)? If so, copy them to some subdirectory of /usr/share/fonts/ 
and that should do it. (I usually create a subdirectrory /usr/share/fonts/local/ for all the fonts I install myself). You may also run 
fc-cache <directoryname> 
but it should not be necessary.

---

### Post by j_baer on 2005-06-02
Alexander,

That did the trick.

Thanks ...

---

### Post by Who on 2005-07-26
[QUOTE=Alexander Kirillov]Do you already have the font files (.ttf)? If so, copy them to some subdirectory of /usr/share/fonts/ 
and that should do it. (I usually create a subdirectrory /usr/share/fonts/local/ for all the fonts I install myself). You may also run 
fc-cache <directoryname> 
but it should not be necessary.[/QUOTE]
Doing this 'installed the font', but I couldn't get a bold version of it - I got sent the font by a windows user who _can_ get both with the same font, so I feel like it is not properly installed - is this the case?

---

### Post by Who on 2005-07-26
[QUOTE=Who]Doing this 'installed the font', but I couldn't get a bold version of it - I got sent the font by a windows user who _can_ get both with the same font, so I feel like it is not properly installed - is this the case?[/QUOTE]
Seems I was a bit 'post happy. After quite some googling (it takes a while to work  out what you're actually googling _for_ sometimes). As far as I can discern, many fonts don't actually have a bold or italic part to them and many programs 'fake' the bold or italic. The progrmas I was using apparently do no do this, so I am stuck with just the regular font. Can anyone confirm this, or prove me wrong by getting 'Papyrus' bold in inkscape...?

---

### Post by GTvulse on 2005-07-26
[quote=Who]Doing this 'installed the font', but I couldn't get a bold version of it - I got sent the font by a windows user who _can_ get both with the same font, so I feel like it is not properly installed - is this the case?[/quote]

No. Windows graphics subsystem (a.k.a. GDI/GDI+) can fake the bold face by emboldening the font outlines before printing them to the screen. X11 can't, yet.

BTW, besides running fc-cache, you also want to run mkfontscale and mkfontdir, in that order.

---

### Post by jpincheira on 2005-07-26
I think the best way is using what GNOME gives us: [SIZE=4]sudo nautilus fonts:///[/SIZE]

---

### Post by GTvulse on 2005-07-27
[QUOTE=jpincheira]I think the best way is using what GNOME gives us: [SIZE=4]sudo nautilus fonts:///[/SIZE][/QUOTE]
 Not quite, you have no control on where the fonts end up nor can you integrate them with other applications that do not use fontconfig. If that's all you want, IMO it would be better to install the fonts in your own home directory.

---

### Post by joanverde on 2005-10-14
Here's an example from real life.

I wanted to read [http://www.divaina.com/](http://www.divaina.com/)
therefore I installed the kaputa.ttf font in /usr/shared/fonts/local/
runned in terminal:

# fc-cache /usr/share/fonts/local/
# mkfontscale /usr/share/fonts/local/
# mkfontdir /usr/share/fonts/local/

tried to reload the page, but it didn't work so tried to copy the fonts to the font:/// folder but it doesn't seem to be copied no matter what I tried.

Question: what is the next step?

Thx for reading,
John

---

### Post by joanverde on 2005-10-14
ok,
now it works, maybe because i logged otu and in.

---

### Post by TristanMike on 2005-10-14
You may also want to create a "/home/<usrname>/.fonts" directory (take note of the period "." indicating a hidden file)  so you don't have to go mukking about in system directories you don't have to. *you may need to create "/.fonts" directory

---

