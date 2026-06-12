---
title: "Installing Downloaded Themes"
date: 2008-09-14
forum: Desktop Environments
---

### Post by sjrlaw on 2008-09-14
I am trying to install Gnome themes into Hardy that I downloaded from the Net.  I download and extract the tarball, then run the theme installer.  I click the Install button and navigate to the folder where the theme is, but when I click the Open button, all it does is open the folder; it does not add the theme to the list of those that can be selected.  Am I missing something?

---

### Post by kostkon on 2008-09-14
> **sjrlaw said:**
> I am trying to install Gnome themes into Hardy that I downloaded from the Net.  I download and extract the tarball, then run the theme installer.  I click the Install button and navigate to the folder where the theme is, but when I click the Open button, all it does is open the folder; it does not add the theme to the list of those that can be selected.  Am I missing something?
You have to keep the tarballs, don't extract them. Then go to *System -> Preferences -> Appearance* to install them.

---

### Post by sjrlaw on 2008-09-15
That worked, thanks.  However, there are some tarballs that I am downloading from Gnome-look that give me an error when I try to install them.  It says that it "does not appear to be a valid theme."  Are these just defective themes I downloaded, or am I missing something?

---

### Post by Casper Hansen on 2008-09-15
After extracting the tarball just copy the folder to your /usr/share/themes.
- I think that will work for all downloaded themes.

```
sudo cp -R [foldername] /usr/share/themes
```

---

