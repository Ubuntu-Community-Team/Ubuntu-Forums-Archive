---
title: "Adding/removing fonts"
date: 2006-07-14
forum: Desktop Environments
---

### Post by mssever on 2006-07-14
How to you add and remove fonts--especially true type fonts? I have several true type fonts that I use all the time in Windows, and I need to install them in Linux. Also, there are a few currently installed fonts that I want to remove.

I can't seem to find a font confuguration tool for this. In my old Red Hat system I had to write a script to manage this using a rediculously complicated method. I don't want to mess with that method anymore (and I don't think that I have that script anymore, anyway).

---

### Post by Jagot on 2006-07-14
I have a directory on my Desktop called 'My Fonts' in which I have all the fonts I want to install.  Then I do this:

```
sudo mv ~/Desktop/My\ Fonts /usr/share/fonts/truetype/
```

Then, I have to get Ubuntu to recognise the fonts:

```
sudo fc-cache -f -v
```

---

### Post by bruce89 on 2006-07-14
You can install fonts with nautilus.  Press Control+L, and type fonts:/// .  You can then put fonts in this folder to install them.  If you want the common windows fonts (Times New Roman, arial etc.), then ```
sudo aptitude install msttcorefonts
``` will install them.  I don't think that removing existing fonts will work with this method.

---

### Post by coffeecat on 2006-07-14
If you've only got a few .ttf fonts to install there's a ridiculously easy method which seems to be little known. I only discovered it by chance on a forum somewhere and didn't believe it until I tried it.

On the Gnome desktop open System > Preferences > Fonts. You get the Font Preferences Windows. Click on the Details button, then on the 'Go to font folder' button. Drag and drop your .ttf fonts into the Fonts - File Browser Window. Now close all the windows and log out. When you restart the X-server your fonts will be installed.


Simple.

---

### Post by mssever on 2006-07-14
Thanks. Now, my question is, how come this is hidden? Why isn't there an obvious way to get to the fonts folder?

---

### Post by coffeecat on 2006-07-15
> **mssever said:**
> Thanks. Now, my question is, how come this is hidden? Why isn't there an obvious way to get to the fonts folder?

Good question. But I think bruce89's Nautilus > ctrl-L > fonts:/// gets you to the same place as the method I gave and is probably easier - if you can remember it! A question for the devs perhaps: adding fonts is a popular pastime; there's an easy way to do it; why is it so obscure?

With regard to Jagot's method, I've used that too, except that I've always put my .ttfs in one of the system font folders rather than creating one in my home directory. If you look in your /etc/X11/xorg.conf file you'll see a number of FontPaths. If you follow "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" you'll see that's a load of symlinks to directories under /usr/share/fonts. I suppose you could find the fonts you want to delete in those, delete them with a sudo command and run fc-cache. I haven't tried it myself, but I can't see why it wouldn't work.

---

### Post by mssever on 2006-07-17
> **coffeecat said:**
> I suppose you could find the fonts you want to delete in those, delete them with a sudo command and run fc-cache. I haven't tried it myself, but I can't see why it wouldn't work.

I've done that now, and it works--mostly.

In OpenOffice, the font Goudy Old Style displays some sort of italic. My church's logotype calls for this font in regular small caps. I don't know what's wrong. It looks OK in AbiWord, but AbiWord doesn't support small caps.

---

### Post by coffeecat on 2006-07-17
> **mssever said:**
> In OpenOffice, the font Goudy Old Style displays some sort of italic.

You're absolutely right. How odd. But I've found a solution. Here's what I did.

To see what you had found I dragged the three files GOUDOS.ttf GOUDOSB.ttf and GOUDOSI.ttf from C:\Windows\Fonts in my mounted Windows partition onto my Ubuntu desktop, and thence into the Ubuntu font folder as I described in my earlier post. This time I noticed that they did not appear in the font folder immediately - it was as though they hadn't 'taken' - but when I logged on again they were properly installed. And when I fired up OOWriter and Abiword I found exactly what you found.

So I deleted GOUDOSI.ttf from the font folder, and logged out and on again. Now Goudy Old Style appears as it should in Open Office Writer. You can still italicise it if you want to, but the italics don't look so good.

You're welcome! :wink:

---

### Post by Dubbayoo on 2006-07-17
I just put them in ~/.fonts

---

### Post by dolby on 2006-07-17
u can also:

   1. Go to "Preferences" menu and then "Font"
   2. Click on the "Details..." button.
   3. Click on "Go to font folder."

Now simply drag & drop your fonts into the "Fonts" window to add them. You may have to log out and log in again to see them actually show up in that folder.

If you have any programs open, you will need to close then and then open them again, to have the new fonts show up in those programs.

---

### Post by mssever on 2006-07-18
> **coffeecat said:**
> You're absolutely right. How odd. But I've found a solution.

Thanks for the workaround. It works for me, as well.

I've reported this as a bug. It's available here: [http://www.openoffice.org/issues/show_bug.cgi?id=67479](http://www.openoffice.org/issues/show_bug.cgi?id=67479). You can vote for the bug there.

---

### Post by evaldas on 2006-07-21
On Gnome I did the following, and everything works.

> sudo apt-get install msttcorefonts
sudo cp *.ttf /usr/share/fonts/truetype/msttcorefonts/
(for copying Tahoma font, cause it's not in the msttcorefonts package)
But I want to have Tahoma font as the default system font on Xubuntu (Xfce) and the above trick doesn't works :( I can't see any of ms fonts available in font selection list.

---

