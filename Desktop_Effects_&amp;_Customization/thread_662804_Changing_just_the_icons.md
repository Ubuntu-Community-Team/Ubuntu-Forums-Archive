---
title: "Changing just the icons"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by Rubruquis on 2008-01-09
I've read topics about changing the icons in the desktop but they were either too old or did not solve the issue.

I want to keep the theme and just change the icons (for folders, my computer, etc) with the custom icons i've downloaded from internet.

How can I do it?

---

### Post by FuturePilot on 2008-01-09
System>Preferences>Appearance. Click the Customize button and then click the Icons tab.

---

### Post by kbless7 on 2008-01-09
Go to system preferences and then appearances. Click the install button and choose the tar.gz file you downloaded. After that you can click on customize for the theme you want and under the icons tab you should be able to select the one you just install. Thats all, but don't forget to save it.

---

### Post by santiagoward2000 on 2008-01-09
Hi!
You can find some icons themes installing the **gnome-extra-icons** package from Synaptic. Then, just select the ones you want like FuturePilot said.

---

### Post by Rubruquis on 2008-01-09
> **FuturePilot said:**
> System>Preferences>Appearance. Click the Customize button and then click the Icons tab.

It doesn't let me choose the custom icon I want, it just shows me a selection of theme icons already installed (Human, Tangerine, etc..) But I want to install the icons I've downloaded from internet (which are in .png format)

And there is no tar.gz file to choose because I don't want to install a theme, I just want to change the icons.

---

### Post by FuturePilot on 2008-01-09
I don't think what you want to do is possible. You can change individual icons but say you wanted all the folders a certain icon. You would have to manually change every single folder icon which would be almost an impossible task. The easiest way to change the icons is to use an icon theme.

---

### Post by CarpKing on 2008-01-09
You could always take your favorite icon theme and replace its folders with the ones you downloaded.  Just open up the tar.gz and poke around a bit (you might have to resize the new folders).

---

### Post by rune0077 on 2008-01-09
> **Rubruquis said:**
> It doesn't let me choose the custom icon I want, it just shows me a selection of theme icons already installed (Human, Tangerine, etc..) But I want to install the icons I've downloaded from internet (which are in .png format)

And there is no tar.gz file to choose because I don't want to install a theme, I just want to change the icons.

What you want to do is possible, but extremely tedious, because it requires you to manually change every single icon, which means a lot of copy/pasting and a lot of renaming, but it is definitely possible. So you need to locate your currently used icons (probably in /usr/share/icons), then you need to copy/paste the new icons into their respective folders, being sure they have the *exact* same name as the icon you want to replace them with, then select "yes" when asked if you want to replace it. Then you need to do this with every single icon, which is a very slow process to say the least. 

This will also mess up your default icons (since they'll be replaced by your new ones and hence deleted from the system), so don't do this if you want to be able to go back to some of the default icon-themes later on.

You'll probably be better off figuring out how to make your own icon-themes and then make a whole new theme with the png's you got.

---

### Post by Rubruquis on 2008-01-09
Yeah, I guess I will learn how to make a theme then.
Thanks a lot everybody.

---

### Post by Sisedi on 2008-01-09
I have a related question, where is the .icons directory where I am supposed to put in a couple icon themes I downloaded from gnome-look, does anyone know where that folder is?

---

### Post by FuturePilot on 2008-01-09
It's in your Home folder. Press Ctrl+H to show the hidden files in your home folder.

---

