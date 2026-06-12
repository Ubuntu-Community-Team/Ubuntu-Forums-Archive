---
title: "Cant install themes"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by s_raghu20 on 2007-06-22
Hi,

I looked for themes for my newly installed ubuntu feisty. I tried to install two themes.. but both times I received the same error message...

Theme file format is invalid...

here's how the theme file look like..
```
[X-GNOME-Metatheme]
Name=Leopard
Comment=Leopard look for Gnome
Encoding=UTF-8
GtkTheme=leopard
MetacityTheme=leopard
IconTheme=leopard-icon
```

Can anybody help.. please..
May be I am doing something wrong.. 

regards
raghav..

---

### Post by NeoLithium on 2007-06-22
How did you try to install them? There's a few ways possible, one is to move the extracted folders to /home/YOUR_USERNAME/.themes or you can go to System -> Preferences -> Themes and drag and drop them into that window.

---

### Post by s_raghu20 on 2007-06-22
well, I extracted the files in some folder somewhere.
And then I opened System -> Preferences -> Themes
And chose install theme from that panel.... 

is that the wrong way ?

After reading ur post, i extracted the files in ~/.themes also.. but it did not pick up...
or how should it pick up /??

i am still trying to read the docs... u c. not there yet..

thanks already... would appreciate if u could help..

regards
raghav..

---

### Post by NeoLithium on 2007-06-22
Well, just because I'm lazy, when I download something for a theme from gnome-look, I download the file (Defaulted to the desktop with firefox) then open up the Themes menu, and drag and drop that .tar.gz onto the window, it will work for a second or so and say the theme is installed correctly, and give me options to use it or keep the current theme.

Or, say I download example to the desktop, I just go:
```
mv /home/USERNAME/example.tar.gz /home/USERNAME/.themes
then
cd /home/USERNAME/.themes
tar -xvzf example.tar.gz

```

Little more work but it does the same thing.  Depending on WHAT theme you grabbed though, you might not see it off the bat, such as going to CUSTOMIZE, it may be in the Window Borders, or Controls tabs. GTK+ themes fall into Controls and the Metacity themes fall into your Window Borders.

---

### Post by s_raghu20 on 2007-06-23
thanks. I dont know what was wrong there, but ur suggestion of drag and drop worked just fine.

thanks again.
regards
raghav..

---

### Post by avik on 2007-06-23
You don't need to extract the theme.  Just choose the .tar.gz archive when you choose it during installation from the Theme window.

---

