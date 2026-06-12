---
title: "how to install a theme in xubuntu natty??"
date: 2011-05-26
forum: Desktop Environments
---

### Post by kaparthy on 2011-05-26
hi
i jus started using xubuntu 11.04 on my low powered toshiba satellite. i was wondering how to installl themes on the box? i know that there are themes available in xfce-look.org but how to install them? i found many posts but all are outdated, nothing related to natty. plz help. and also explain how to use compiz ( i loved it on ubuntu, that wobbly windows etc.) on xubuntu or redirect me to some place so that i can make compiz work on xubuntu. thank you! :)

---

### Post by Joe of loath on 2011-05-26
If you have a low-end box, I wouldn't try Compiz. It'll destroy all the performance advantages of XFCE and then some.

---

### Post by Toz on 2011-05-26
> **kaparthy said:**
> hi
i jus started using xubuntu 11.04 on my low powered toshiba satellite. i was wondering how to installl themes on the box? i know that there are themes available in xfce-look.org but how to install them? i found many posts but all are outdated, nothing related to natty. plz help. and also explain how to use compiz ( i loved it on ubuntu, that wobbly windows etc.) on xubuntu or redirect me to some place so that i can make compiz work on xubuntu. thank you! :)

Here's a quick HowTo on installing the axiom/axiomd theme (one of my favs) from xfce-look.org:

1. Go to the Axiom Theme page at: ```
http://xfce-look.org/content/show.php/axiom?content=90145
```

2. Click the Download button and save the file to your computer.

3. Find the file using the file manager (Thunar), right-click the file and select "Extract Here".

4. If you don't already have one, you need to create a .themes file in your home directory. Follow either 4a or 4b depending on whether you want to use the command prompt or the gui (Thunar).
4a. Using the command prompt, type in ```
mkdir ~/.themes
```
4b. Or, using Thunar, first make sure that "Show hidden files" is selected from the View menu, then from your home directory, right-click the Thunar background and select "Create folder", call it .themes, and click on "Create".

5. Copy the extracted theme directory to ~/.themes 
5a. Command prompt: ```
mv 90145-axiom ~/.themes
```
5b. Or Thunar: right-click 90145-axiom, select Cut, goto .themes directory, Paste.

6. Most xfce themes come with two components: the gtk theme (gtk-2.0 subfolder) and window manager theme (xfwm4 folder)
NOTE: this particular theme file (axiom) comes with 2 separate themes (axiom & axiomd)

7. To change the gtk2 theme, go to Appearance in Settings Manager and select axiom or axiomd

8. To change the xfwm theme, go to Window Manager in Settings Manager and select axiom or aximod

Hope this helps.

---

### Post by galacticaboy on 2011-05-26
Be careful, when I tried to install a theme on Xubuntu 11.04, I somehow got rid of all of my Windows Decorations... it was annoying.

---

### Post by lemmon on 2011-10-07
@Toz:
many thanks mate! im most gratefull.
kudos!

---

