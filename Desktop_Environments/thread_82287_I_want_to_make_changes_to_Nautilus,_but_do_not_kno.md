---
title: "I want to make changes to Nautilus, but do not know how"
date: 2005-10-26
forum: Desktop Environments
---

### Post by magnusbb on 2005-10-26
Hello

In an earlier thread I complained about Nautilus not zooming text properly in "Icon view". I have a visual handicap and it really irritates me that it's only the icons being zoomed and not the whole label. It worked in 2.10, but in 2.12 there was a change.

Well, I want to change it. I've downloaded the complete source archive of Nautilus from the GNOME FTP server and found the lines of code needed:

It's in the **libnautilus-private** directory, in the file **nautilus-icon-container.c**. Here's the right code: 

> details->font_size_table[NAUTILUS_ZOOM_LEVEL_SMALLEST] = -3 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_SMALLER] = -3 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_SMALL] = -2 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_STANDARD] = 0 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_LARGE] = 2 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_LARGER] = 4 * PANGO_SCALE;
        details->font_size_table[NAUTILUS_ZOOM_LEVEL_LARGEST] = 4 * PANGO_SCALE;

But I've really no idea now, what to do to get this "edited" version of Nautilus work on my Ubuntu Breezy installation. Is there perhaps some sort of "source packages" for Breezy that I need to edit, compile and install, or what?

I would be most thankful for any help on this issue.

---

### Post by fabiand on 2005-10-26
Hey,

well you just pulled the whole nautilus source code .. well done .. but not very usefull ... you will have to build your own binaries to use "your" nautilus ...

a better solution would be to use the Font-Settings dialog in your Preferences Menu ...

Have a look at it maybe it already does what you are trying to do ..

- fabiand

---

### Post by psychicdragon on 2005-10-26
I think that you should probably get the the Nautilus source from the Breezy repositories not from the Gnome FTP. There were probably some Ubuntu specific changes made and it may just be easier to build.

You can grab it using this command:
```
sudo apt-get source nautilus
```

Make your changes.
Then go back to ~/nautilus-2.12.1

You need at least this package to build Nautilus, possibly others but I'm not sure.
```
sudo apt-get install build-essential
```

These are the basic steps to build and install most software:
```
./configure
make
sudo make install
```

I'm sure that there are probably a ton of dev packages that you're going to need to successfully build Nautilus. If you don't have them ./configure will fail and tell you what you're missing; apt-get install it and then try again 'till you've got them all. Once ./configure finishes successfully the hard part is over. Type 'make' then have yourself a beer and relax, it's going to take a while. 

Hopefully this is enough info to get you started. I can't actually try any of this because I don't actually Gnome or Nautilus on my system. Post any problems you're having here and I'll do my best to help you out though.

This kind of thing is a good learning experience. ;)

---

### Post by David Marrs on 2005-10-26
You should send them a bug report as well, because obviously they need to fix a  problem like that.

---

### Post by GeneralZod on 2005-10-26
[QUOTE=psychicdragon]

I'm sure that there are probably a ton of dev packages that you're going to need to successfully build Nautilus. If you don't have them ./configure will fail and tell you what you're missing
[/QUOTE]

Or, use:

```

sudo apt-get build-dep nautilus

```

Debian is awesome :)

---

### Post by psychicdragon on 2005-10-26
[QUOTE=GeneralZod]Or, use:

```

sudo apt-get build-dep nautilus

```

Debian is awesome :)[/QUOTE]
Cool, you learn something new every day. That could have saved me some time when I built xfce4 from svn. :rolleyes:

---

### Post by magnusbb on 2005-10-26
Thanks to all of you! YES, it worked. Now I'm tweaking it to my wishes. Using checkinstall is the safest way of course.

BTW, Nautilus took just 3 minutes to build.

---

