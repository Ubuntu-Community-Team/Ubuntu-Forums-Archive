---
title: "[Hardy] Fonts like Gutsy for KDE apps and gnome-terminal"
date: 2008-06-12
forum: Desktop Environments
---

### Post by trapperjohn on 2008-06-12
After upgrading from Gutsy to Hardy, the fonts of gnome-terminal and any Qt (=KDE) app like Kile were blurry, as if they had the wrong antialiasing setting. Gnome's font settings were correct, as everything else worked as expected.

After a little bit of google-searching and trying things from the Ubuntu wiki, the following solution worked for me:

Install kde-systemsettings: "sudo apt-get install kde-systemsettings"
Start it: "systemsettings"
Go to "Appearance"->"Fonts"

Select "Enabled" at "Use anti-aliasing" and go to "Configure..."
Enable "Use sub-pixel hinting" and select (works best for me..) "Vertical RGB"
Set "Hinting style" to "Full".

Now apply all settings and restart the terminal or any KDE application. 
I think, it is a little weird, kde-settings has an influence on gnome-terminal ... ;)

See the attachment for an example screenshot (you have to click it again to see it fullscreen, else its also blurry ...).

---

### Post by Dodominyk on 2008-07-25
Thanks, I was looking for that as well.

I see you are using Kile. What pdf viewer do you use with it if you use any? I used to be on Fedora and I used kpdf, but I know just installed ubuntu 8.04, and the rendering of the fonts in kpdf or okular is ugly. I'm forced to use evince, which unfortunately doesn't yet automatically reload the pdf files after they are modified.

---

### Post by trapperjohn on 2008-07-26
I use Evince (and sometimes Acrobat) - Evince reloads the PDF when you press the "ViewPDF" button in Kile (instead of starting a new instance of Evince). So if I want to build and view my LaTeX document, I just press the "PDFLaTeX" button twice and "ViewPDF" once (without waiting between clicking!). Works fine for me!

---

