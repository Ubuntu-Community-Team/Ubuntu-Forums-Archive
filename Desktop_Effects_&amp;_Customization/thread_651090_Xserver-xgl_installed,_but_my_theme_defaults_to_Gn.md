---
title: "Xserver-xgl installed, but my theme defaults to Gnome."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by Alex Carroll on 2007-12-27
In an attempt to get compiz working on my computer, I installed the "xserver-xgl" package through Synaptic. This allowed me to use desktop effects, however my desktop theme and icons have gone back to the Gnome default.

I have tried changing the theme settings in the Appearance Preferences, but it makes no difference. My window options have not been affected by this, and can also be changed when I select the relevant option. My problem only affects the panels and icons. And fonts, it appears, as I have noticed while typing this.

Thanks for any help you have to offer.

---

### Post by Forlong on 2007-12-27
Run ```
gnome-settings-daemon
``` via [Alt]+[F2] and see if it helps.

---

### Post by jomann on 2007-12-27
hi, 

I had the same problem... what I did is this.. I went to synaptic installer and i downloaded compiz settings manager, after i did that i went to system ->prefrences-> and i saw an icon called gl desktop. i double clicked and enable compiz. after that you'll see a function called "use metacity theme" disable it and you are done... well I did

---

