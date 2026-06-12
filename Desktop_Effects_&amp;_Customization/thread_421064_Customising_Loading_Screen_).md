---
title: "Customising Loading Screen? :)"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by kgriffin on 2007-04-24
Hi all,

I have installed Feisty, (the last version I installed was Slackware 10.2 about 3 years ago) and firstly want to say how stunned I was at the ease of use. Absolutely incredible! 

I (of course) went straight for some good old eye candy and have beryl emerald themes etc going a nice background and new login screen.

My question is how to change the "Loading" screens between the login screen and my desktop?

Is it down to the theme I used to add a new login screen?

Thanks in advance :)

---

### Post by Rinzwind on 2007-04-24
It's called 'splash screen'
If you add the package 'gnome art' you should have some more splash screens :)


BTW: 
I made custom ones based on the Bleach anime. From commandline: 

gconftool-2 -t str --set /apps/gnome-session/options/splash_image "/dir/to/image/image.jpg" 

changes your splash screen. I have a bash file with the last part in a variable and when I run the file it changes it :KS

---

### Post by kgriffin on 2007-04-24
Cheers,

Will try :)

---

### Post by reclusivemonkey on 2007-04-24
There's a program in Synaptic that will give you a GUI to install/preview splashscreens. Just search for "splashscreen" and you should be able to find it.

---

