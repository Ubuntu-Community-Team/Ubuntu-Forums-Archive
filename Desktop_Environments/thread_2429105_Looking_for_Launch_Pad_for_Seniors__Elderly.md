---
title: "Looking for Launch Pad for Seniors / Elderly"
date: 2019-10-13
forum: Desktop Environments
---

### Post by vitomacdoc on 2019-10-13
Hello,

I am looking for a Launch Pad type App or Theme that will let me isolate a few icons.  Something that doesn't disappear or go away.
My mother is in her 80s and although has been using a PC for 20 years, she keeps losing or hiding her email and social media pages.

There are a few computer makers out there that have all-in-one PCs with this feature, I am thinking they are just revised Linux boxes.
I already have a capable PC.

Thank you.

---

### Post by TheFu on 2019-10-13
LXDE can be configured with a left-side launch bar and locked.  Used this with my 75+ yr old relatives.  It was around 2010 when I set this up, so don't know about 18.04 LXDE. All versions after that are LXQt. I have zero clue about Qt stuff.  

Back in 2010, it worked well on a Pentium4 with 1G of RAM.  We swapped in a Core i7, and while faster, it really didn't matter to the user. ;)

---

### Post by SeijiSensei on 2019-10-14
I'm not sure I understand the problem.  Are you worried your mom will accidentally delete an icon?  If so, the easiest solution is to make the icon file read-only.  On my KDE system they are files with .desktop extensions in the Desktop folder in my home directory. I think that's true for other flavors as well. 

Open a terminal, then
```

cd ~/Desktop
chmod ugo-w *.desktop

```

If you really want to freeze them, you can make them "[immutable]("https://www.tecmint.com/chattr-command-examples/")."  Then even the root user cannot delete them.

```

cd ~/Desktop
sudo chattr +i *.desktop

```

Changing attributes requires root privileges, hence the need for sudo.

---

### Post by vitomacdoc on 2019-10-15
Hello and thanks for the input.

My goals to show a window with limited icons that can be chosen.  Similar to a kiosk.
Not much worried about deleting the icons.  If my mom has 4 icons to click, she can always go back to these icons easily.  Everything else is hidden and she wont be able to click outside the panel.

---

### Post by SeijiSensei on 2019-10-16
Maybe one of these might suit your needs: [https://www.omgubuntu.co.uk/2019/08/best-app-launcher-for-ubuntu-linux](https://www.omgubuntu.co.uk/2019/08/best-app-launcher-for-ubuntu-linux)

---

