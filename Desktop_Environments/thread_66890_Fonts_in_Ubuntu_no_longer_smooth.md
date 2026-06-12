---
title: "Fonts in Ubuntu no longer smooth"
date: 2005-09-18
forum: Desktop Environments
---

### Post by bcc on 2005-09-18
Hi,

I've been using Ubuntu for a couple of months now, and I like it. I also experimented with installing Kubuntu and Xfce in the computer. I currently have some problems with the fonts used.

I've noticed that some applications do not have smooth fonts, like what is shown in the a screenshot I attach (the one showing Opera, BOINC Manager, and Gimp). Opera and BOINC Manager have jagged fonts, while Gimp is rather smooth. The screenshot shows the windows in KDE, but the same fonts smoothing problem exists in Gnome as well. I didn't like this and searched for solutions to the problem.

Thinking that I was in the correct direction, I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=22232&highlight=font+smooth](http://ubuntuforums.org/showthread.php?t=22232&highlight=font+smooth)

Instead of getting smooth fonts, to my horror **all** the programs and even the panels in Ubuntu now have jagged fonts, like the second screenshot that I attach, the one showing Firefox, Thunderbird, and Gimp. The same thing happens even in KDE and Xfce.

Could anyone help me in solving the problem and make the fonts in most, if not all, programs smooth again?

I've tried switching on all font smoothing options in both KDE and Gnome, to no avail...

I've also noticed that the instructions I mentioned in the link above require me to change the GTK Settings under LookNFeel settings in KDE to "Qt". In my case, even after clicking OK, the setting would revert automatically to "Use my KDE style in GTK applications".

I believe I made some mistake here, because frankly I'm not quite sure what GTK and Qt are...


Thanks,

Hendri

---

### Post by Curlydave on 2005-09-18
I think somehow anti-aliasing has been turned off, and for some reason the Ubuntu fonts look really bad with it off. Personally I prefer un-antialiased clean fonts to begin with, but if you're going to use the Ubuntu fonts, make sure that AA's on.

---

### Post by bcc on 2005-09-19
[QUOTE=Curlydave]I think somehow anti-aliasing has been turned off, and for some reason the Ubuntu fonts look really bad with it off. Personally I prefer un-antialiased clean fonts to begin with, but if you're going to use the Ubuntu fonts, make sure that AA's on.[/QUOTE]

Thanks! But the problem is that I've activated anti-aliasing in both Gnome System Preferences and KDE Control Center... But the jagged font problem is still there.

I'm thinking of reformatting the entire system if it can't be helped...

Do you have any other suggestions?

Thanks. :)

Hendri

---

### Post by KaiO on 2005-09-30
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=4456]("http://www.ubuntuforums.org/showthread.php?t=4456")

---

