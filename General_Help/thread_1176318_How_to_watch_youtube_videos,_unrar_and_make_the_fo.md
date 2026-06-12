---
title: "How to watch youtube videos, unrar and make the font look better"
date: 2009-06-02
forum: General Help
---

### Post by ManosLinux on 2009-06-02
Hi all I have just installed Ubuntu 9.10. This is my first touch of Linux, I am total novice to this new Operating System and I have some questions. Firstly, How can I watch videos from Youtube and other video sites? How can I unrar  some .rar or .zip files I have? And I am facing a problem. I have installed my graphic card drivers and updated my Ubuntu and restarted pc. But in some sites fonts are really awfull. In some sites I can hardly understand the words. Am I missing some styles of fonts or something? How can i make fonts smoother? 

Thanks in advance.

---

### Post by Legace on 2009-06-02
Open Applications -> Accessories -> Terminal and type in:
```
sudo apt-get install unrar
```

Note, it will ask you for your password, and to to press Y (for yes) and Enter.
After you've installed it, you can right-click on .rar (and .zip) archives, and select "Extract here" :)


To install the Windows fonts, close Firefox and type in the following in Terminal:
```
sudo apt-get install msttcorefonts
```

Then, after you've installed the fonts, type in the following for Flash (which is required by YouTube):
```
sudo apt-get install flashplugin-nonfree
```

Then things should look better (restart PC if you see no changes)..

---

### Post by Therion on 2009-06-02
> **ManosLinux said:**
> How can i make fonts smoother? 
Go to System/Preferences/Appearance "Fonts" tab.

Try using a different "Rendering" method (there are buttons at the bottom for this) and/or click on the "Details" button for more options regarding font Hinting, DPI, and so forth.  If the problem is how fonts are rendering on web pages, try going into the Firefox configuration menu.

Edit/Preferences "Content" tab (Fonts and Colors section) "Advanced" button.  Try using a different font (I find sans-serif fonts render better in both Ubuntu and Firefox) and/or setting the "Minimum Font Size" to something reasonable like 14 or 16.  You might also want to clear the checkbox for allowing websites to choose their own fonts instead of using your chosen fonts.

---

### Post by ManosLinux on 2009-06-02
Thanks a lot both. Your posts was really helpful!

---

