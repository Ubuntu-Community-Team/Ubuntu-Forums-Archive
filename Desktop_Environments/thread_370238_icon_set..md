---
title: "icon set."
date: 2007-02-25
forum: Desktop Environments
---

### Post by BlaineM on 2007-02-25
Im looking for a minimalistic complete grey icon theme for gnome... all of the ones that I get from gnome-look or gnome art are either not complete, or using icons that I dont care for.

If anyone has any icon themes that are like human, but grey in color... could I have them?

If not, I guess I can try to make an icon theme that I like.  But who needs to reinvent the wheel right?

thanks,
Blaine

---

### Post by disturbedite on 2007-02-25
i have monochrome installed in kde.  i haven't really tried it out, so i can't tell you if it is complete or not, but you might wanna try that out.

---

### Post by g8m on 2007-02-26
Difficult. Icons. There is no one is best set. It's like asking which color is best.
Some like red, others blue, and ubuntu likes earth-colors.

I've set my to tango-noir.

---

### Post by Kateikyoushi on 2007-02-26
I think with a little work you could convert the icons you need to gray from the human theme.
I did a few for myself like Thunderbird because I liked that envelope.

---

### Post by ComplexNumber on 2007-02-26
> **BlaineM said:**
> Im looking for a minimalistic complete grey icon theme for gnome... all of the ones that I get from gnome-look or gnome art are either not complete, or using icons that I dont care for.

If anyone has any icon themes that are like human, but grey in color... could I have them?

If not, I guess I can try to make an icon theme that I like.  But who needs to reinvent the wheel right?

thanks,
Blaine
human-ultra-grey and human-grey ([click]("http://gnome-look.org/content/show.php?content=46010"))


both 'inherit' the main human theme, so you are advised to have that installed too for consistency.

---

### Post by kanha on 2007-02-26
try locating glass icons in gnomelook.org
they are great

---

### Post by ComplexNumber on 2007-02-26
> **kanha said:**
> try locating glass icons in gnomelook.org
they are great
but they're not very complete. i had to change the index.theme file so that they inherit a similar iconset. by default, they inherit gnome...which makes them look like a complete mish mash.
btw when i say "inherit", i mean that when the icon theme hasn't got a particular icon, it will use the icons from the inherited theme that is stated in the index.theme file instead. i changed the "Inherits=" from gnome to snowish so the the start of the index.theme looks like this:


> [Icon Theme]
Name=Glass Icons
Comment=Glass Icons
Inherits=SnowIsh
Directories=scalable/apps,scalable/filesystems,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/stock
Example=gnome-theme-preview.svg
the first screenshot show them when they inherit gnome, and the 2nd one shows them what  they look like when they inherit snowish. notice the difference ;)

---

### Post by BlaineM on 2007-04-01
I started building one myself just a while ago, but with school I havent had alot of time to finish what I started... so when I get it all done, I will post it on gnome-look, or gnome art.

Yeah the human grey is nice, I had seen it before, but I am looking for something even a bit simpler than that now.

Yeah that inherit line is a killer for some of the icon sets that are out there.

Blaine

---

### Post by ComplexNumber on 2007-04-01
> **BlaineM said:**
> I started building one myself just a while ago, but with school I havent had alot of time to finish what I started... so when I get it all done, I will post it on gnome-look, or gnome art.

Yeah the human grey is nice, I had seen it before, but I am looking for something even a bit simpler than that now.

Yeah that inherit line is a killer for some of the icon sets that are out there.

Blaine
what exactly do you mean by simple? would g-flat appeal to you ([click]("http://gnome-look.org/content/preview.php?preview=1&id=14932&file1=14932-1.jpg&file2=&file3=&name=Flat+SVG+for+GNOME")). they're also very complete. [here ]("http://art.gnome.org/themes/icon/1281")is a link to the icons.

---

### Post by BlaineM on 2007-04-11
yeah... actually I've been using gflat for the last while... I like that theme.  I just changed the trash icons and the terminal icons to ones that I like... but yes, that is what I have been using.

---

### Post by ComplexNumber on 2007-04-11
> **BlaineM said:**
> yeah... actually I've been using gflat for the last while... I like that theme.  I just changed the trash icons and the terminal icons to ones that I like... but yes, that is what I have been using.
please note that the g-flat theme available in the link above on art-gnome is much more complete than the one available on gnome-look. i don't know why that is.

---

### Post by BlaineM on 2007-04-11
I guess I have never compared the two... but thanks for that though

---

