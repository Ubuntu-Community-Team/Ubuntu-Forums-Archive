---
title: "Gnome desktop layout"
date: 2005-09-12
forum: Desktop Environments
---

### Post by impeteperry on 2005-09-12
I have been using the Fedora KDE desktop for several years, but this Gnome looks so great I thought I would like to try it for a while. In "KDE" I could move the "X" from the right end of the title bar to the Left end away from the STUPID position next to the size button that Bill G came up with.

Any comments?

---

### Post by banjobacon on 2005-09-12
[QUOTE=impeteperry]I have been using the Fedora KDE desktop for several years, but this Gnome looks so great I thought I would like to try it for a while. In "KDE" I could move the "X" from the right end of the title bar to the Left end away from the STUPID position next to the size button that Bill G came up with.

Any comments?[/QUOTE]
 Go to Apps > System Tools > Config Editor.

Then apps > metacity > general, and edit the value "button_layout".

I just found this out a few days ago. It should really be more easily visible.

---

### Post by impeteperry on 2005-09-13
Thanks, but I was refering to the Gnome desktop. I have been using it in the KDE desktop for a couple of years. 
I installed Ubuntu  and added the KDE functionality so I have both Gnome  & KDE. Installing KubuntuI directly fell short of what I wanted.
I found the Gnome desktop appealing and would like  to use it if I could get the damm "X" moved.

I will agree the setup should be more obvious, actually it should be the default!!

---

### Post by banjobacon on 2005-09-13
[QUOTE=impeteperry]
I found the Gnome desktop appealing and would like  to use it if I could get the damm "X" moved.[/QUOTE]

Did you try what I suggested? That's how it's done.

---

### Post by rwabel on 2005-09-14
[QUOTE=banjobacon]Did you try what I suggested? That's how it's done.[/QUOTE]
 it's working, but kinda problem with the theme. it moves the 3 buttons to the left, but the theme is made for beeing right positioned and not left. and least the one I'm using. Then it looks kinda strange. It all depends on the theme. I guess the OSX one should work fine

---

### Post by impeteperry on 2005-09-15
[QUOTE=rwabel]it's working, but kinda problem with the theme. it moves the 3 buttons to the left, but the theme is made for beeing right positioned and not left. and least the one I'm using. Then it looks kinda strange. It all depends on the theme. I guess the OSX one should work fine[/QUOTE]
If you select "laptop" for the Windows decoration it moves the "X" automatically to the left

---

### Post by rwabel on 2005-09-15
[QUOTE=impeteperry]If you select "laptop" for the Windows decoration it moves the "X" automatically to the left[/QUOTE]
 where do you select laptop for the windows decoration?

---

### Post by impeteperry on 2005-09-15
1. In the KDE desktop go to click on "LookNFeel"
2. Click on "Window Decorations"
3. click on "Buttons"
4. Check "Use custom title bar button positions"
5. In the top window, drag the "X" to the position you want on the title bar
6. It will be display in the second window.
7. If it is what you want, click on "Apply"

.                                             -or-

3. Select "Laptop" as the "Window Decoration" and it is done for you.

If I could do that with the "Gnome" desktop, that ia what I would use.

---

### Post by rwabel on 2005-09-15
[QUOTE=impeteperry]1. In the KDE desktop go to click on "LookNFeel"
2. Click on "Window Decorations"
3. click on "Buttons"
4. Check "Use custom title bar button positions"
5. In the top window, drag the "X" to the position you want on the title bar
6. It will be display in the second window.
7. If it is what you want, click on "Apply"

.                                             -or-

3. Select "Laptop" as the "Window Decoration" and it is done for you.

If I could do that with the "Gnome" desktop, that ia what I would use.[/QUOTE]
 ah okay I see. your laptop was referenced to kde. I'm on gnome and was looking for it :-)

I've no idea if that's possible though

---

### Post by banjobacon on 2005-09-15
[QUOTE=rwabel]it's working, but kinda problem with the theme. it moves the 3 buttons to the left, but the theme is made for beeing right positioned and not left. and least the one I'm using. Then it looks kinda strange. It all depends on the theme. I guess the OSX one should work fine[/QUOTE]

What window theme are you trying to use which doesn't work?

Not that I'd know how to fix it, I'm just curious.

---

### Post by rwabel on 2005-09-15
[QUOTE=banjobacon]What window theme are you trying to use which doesn't work?

Not that I'd know how to fix it, I'm just curious.[/QUOTE]
 for example longhorn inspirat. It's not that its not working, but the problem is:
it moves the 3 button from top right to top left, but as the theme is desined (as several others) to have th button on the top right, it only moves a part of it. the 3 symboles are moved but the 3 boxes still stay on the top right.

---

### Post by Ptero-4 on 2005-09-15
[QUOTE=rwabel]for example longhorn inspirat. It's not that its not working, but the problem is:
it moves the 3 button from top right to top left, but as the theme is desined (as several others) to have th button on the top right, it only moves a part of it. the 3 symboles are moved but the 3 boxes still stay on the top right.[/QUOTE]
 That's easy to fix. go to ~/.themes , look for the longhorn inspirat theme folder, then locate the titlebar pixmap (should be something like titlebar.png or somesuch) and gimp out the boxes.

---

### Post by rwabel on 2005-09-16
[QUOTE=Ptero-4]That's easy to fix. go to ~/.themes , look for the longhorn inspirat theme folder, then locate the titlebar pixmap (should be something like titlebar.png or somesuch) and gimp out the boxes.[/QUOTE]
 yes sure when you change the theme you can do alot :-)
but that is not the solution and well easy it won't be to alter the image that it looks the way you want it.

I guess, they normaly make the theme to have the 3 buttons on top right. If you want it left you need to do it yourself. It will only work with themes which don't look different on top left and right expect the 3 buttons.

---

