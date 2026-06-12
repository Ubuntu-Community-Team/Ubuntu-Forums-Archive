---
title: "Can not set solid color as backround image GNOME 3.34.1"
date: 2019-10-26
forum: Desktop Environments
---

### Post by setonic on 2019-10-26
Can not set solid color as backround image in GNOME 3.34.1. I know how to do that, but it just does not work. I think it's a bug.

---

### Post by cruzer001 on 2019-10-28
I am also running 3.34.1 and willing to give it a try if you would please post how you done this.

---

### Post by setonic on 2019-10-29
I did this:

gsettings set org.gnome.desktop.background primary-color '#000000'
gsettings set org.gnome.desktop.background secondary-color '#000000'
gsettings set org.gnome.desktop.background color-shading-type 'solid'

But no changes: I believe I need to set the picture-uri value to an empty string, but I don't know how to do that.

What does mean "picture-uri"?

---

### Post by yetimon_64 on 2019-10-29
I am not on gnome or even ubuntu at the moment but my current install here has the dconf settings for gnome and the next code blanked out the picture-uri setting for me...

```
gsettings set org.gnome.desktop.background picture-uri ""
```

> What does mean "picture-uri"?         
A "URI" is "Universal Resource Identifier" as far as I'm aware. Just another name for "address" or "location" of the image being set as the background image.

Hope it works for you. Cheers, yeti.

---

### Post by setonic on 2019-10-30
> **yetimon_64 said:**
> I am not on gnome or even ubuntu at the moment but my current install here has the dconf settings for gnome and the next code blanked out the picture-uri setting for me...

```
gsettings set org.gnome.desktop.background picture-uri ""
```

         
A "URI" is "Universal Resource Identifier" as far as I'm aware. Just another name for "address" or "location" of the image being set as the background image.

Hope it works for you. Cheers, yeti.

Thanks. It is supposed to work, but it did not. But I was able to make ot work via dconf-editor.

---

### Post by setonic on 2019-10-30
> **cruzer001 said:**
> I am also running 3.34.1 and willing to give it a try if you would please post how you done this.

It should be pretty easy: just click on the image (where my pointer on screenshot) and you have to have an option replace it with color, but when I click nothing happens.

---

### Post by Skaperen on 2019-10-30
i don't know how close to this GNOME is, but in Xfce, right-click on the background and select "Desktop Settings".  see if GNOME has something there.

---

### Post by setonic on 2019-10-30
I finally did it via dconf-editor.

---

### Post by slickymaster on 2019-10-30
Threads merged

---

