---
title: "Ubuntu Font in Kubuntu rendering"
date: 2011-03-22
forum: Desktop Environments
---

### Post by tja on 2011-03-22
as long time ubuntu user (since 6.06), a bit dissatisfied with the current state of gnome in maverick (lack of functionality, bugs that never got fixed f.e. in gnome-panel etc) and uncertain of the future direction of ubuntu regarding unity (have a natty installation on a spare notebook) i decided to give kde a try and installed kubuntu-desktop on my fresh maverick installation.

so i played around a bit with kde then and tried to get a look-and-feel which would satisfy my needs.

kde by itself looks great and the features are promising - but i have a big issue with the font rendering.

in gnome i like the new ubuntu fonts for readabilty and never looked back. but the "ubuntu" font is rendered completely different in kde then in gnome, its thin and ugly IMO.
i wondered about that and did screenshots to compare the rendering in gnome and kde and the font really is different (see the attachements).

i tried to play around with antialiasing, hints, dpi etc., searched the forums but found no working solution.

has anybody out there a good idea ?

---

### Post by schnelle on 2011-03-23
Try with: "Use anti-aliasing" - "enabled", then click on configure and check "use sub-pixel rendering: "RGB".

---

### Post by tja on 2011-03-26
> **schnelle said:**
> Try with: "Use anti-aliasing" - "enabled", then click on configure and check "use sub-pixel rendering: "RGB".

thx.

i tried all combinations of antialiasing but still the font will stay thin. it only changes it to more or less bluriness and coloured edges.

i wonder that nobody else sees the difference but maybe nobody cares ...

---

### Post by SeijiSensei on 2011-03-26
Those of us using Kubuntu exclusively wouldn't see the difference because we have no basis of comparison!

Did you try other sans-serif choices like Lucida Sans or Liberation Sans?  You might prefer those instead.  You can also install the ttf-mscorefonts package to add the Microsoft "core fonts" like Arial and Tahoma.  Arial renders pretty well, I think.

---

### Post by tja on 2011-03-26
> **SeijiSensei said:**
> Those of us using Kubuntu exclusively wouldn't see the difference because we have no basis of comparison!

Did you try other sans-serif choices like Lucida Sans or Liberation Sans?  You might prefer those instead.  You can also install the ttf-mscorefonts package to add the Microsoft "core fonts" like Arial and Tahoma.  Arial renders pretty well, I think.

sure, pure kubuntus will not see this.
my "maybe nobody cares" wasnt meant negative, more as a fact.

i will install kubuntu on another box to be sure its not my main machine (and to prevent the kubuntu firefox mods from happening every time i start kubuntu ...).

---

### Post by ankspo71 on 2011-03-29
Hi Tja,
Being that I have used Ubuntu and Kubuntu I have been able to see the difference in the rendering of fonts between KDE and Gnome, but I didn't have anything useful to say about it until now.

I installed Kubuntu 11.04 (Alpha) 2 days ago for testing purposes, and I just this morning I realized the fonts look much better than in Kubuntu 10.10. I did have to adjust my QT fonts with qtconfig to get Google Earth to display fonts correctly yesterday, but I don't think that had anything to do with how well the KDE fonts are being displayed now. Anyways, the fonts are bolder and smoother in appearance now. Something to look forward to...

Btw, my Kubuntu 10.10 fonts still looks just as bad (if not worse) as your screenshot does.

Edited: Attached screenshot

---

### Post by tja on 2011-03-30
> **ankspo71 said:**
> Hi Tja,
Being that I have used Ubuntu and Kubuntu I have been able to see the difference in the rendering of fonts between KDE and Gnome, but I didn't have anything useful to say about it until now.

I installed Kubuntu 11.04 (Alpha) 2 days ago for testing purposes, and I just this morning I realized the fonts look much better than in Kubuntu 10.10. I did have to adjust my QT fonts with qtconfig to get Google Earth to display fonts correctly yesterday, but I don't think that had anything to do with how well the KDE fonts are being displayed now. Anyways, the fonts are bolder and smoother in appearance now. Something to look forward to...

Btw, my Kubuntu 10.10 fonts still looks just as bad (if not worse) as your screenshot does.

Edited: Attached screenshot
thx ankspo, thats good news. will try the alpha with kubuntu soon.

---

### Post by tja on 2011-03-30
just for the still interested.

i installed kubuntu-desktop on a second machine - the ubuntu font look a bit better there (but still too "hungry" :) for my taste)
the difference between the machines is the monitor, my main has a dual 28" tft setup with 1920x1200 each while the second machine is connected to a lonley 19" 1280x1024 tft.
so my guess is that one needs a big screen to see the difference in rendering between the (k)ubuntus ... at least with 10.10 as ankro wrote.

i logged into kubuntu on the main and played around with the font settings a bit and found that sub-pixel rendering with "slight" hints were at least acceptable on the desktop and most apps. still FF was a bit messy and OO was horrible, even after playing around with OO's own rendering settings.

anyway i tried to work a day with KDE but a couple of other issues made me switch back the other day. i decided to wait for 11.04 and then give it another try.

thx for all the helpful comments.

---

