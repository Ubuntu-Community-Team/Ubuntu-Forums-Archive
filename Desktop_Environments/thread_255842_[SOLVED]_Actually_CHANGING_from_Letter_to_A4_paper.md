---
title: "[SOLVED] Actually CHANGING from Letter to A4 paper"
date: 2006-09-12
forum: Desktop Environments
---

### Post by siddartha on 2006-09-12
Hello,

I have an Okipage 14ex laser printer on USB. It used to work quite well untill the last updates (this summer I didn't work at home so I had not use the printer). Now... I can't print. It keeps showing me on the display - Letter paper request. I changed Letter to A4 in the printer menu. No luck. Checked the standard gnome printing menu also - the one that shows up when you try to print from Gedit.

I even went so far to edit by hand the defaults for all PPD files from letter to A4. Not a change! And there should be a way to set this up graphically. I went further and changed my language defaults from EN-US to EN-UK just in case it would work like some sort of locales.

My only hope is with Open Office. It has an extra menu for setting up the printer that shows up the Letter format. ONLY IN THIS menu I can change and make it work. Worse - there is some setting that messes everything up as I have to set this each time for each document and instance or it will just 'forget' that I want A4.

How can I print from Gnome as well?

Thanks,
Sidd

---

### Post by siddartha on 2007-01-28
The solution is within the file /etc/papersize
It was set to letter and I changed it to a4.

---

