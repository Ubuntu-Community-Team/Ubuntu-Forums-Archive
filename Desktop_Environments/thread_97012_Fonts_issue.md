---
title: "Fonts issue"
date: 2005-11-30
forum: Desktop Environments
---

### Post by zeeone on 2005-11-30
I just installed Ubuntu 5.10 on my laptop and so far I'm getting a very positive vibe. I have configured the font smoothing to "None" and the hinting to "Slight". Can I somehow specify which fonts and sizes I want smoothed out and which ones not? I'd like to keep the small fonts, like the ones used in the menus and icon names not smooth and the bigger ones smoothed. 
Any help would be greatly appreciated.

---

### Post by 23meg on 2005-11-30
Create a ~/.fonts.conf file if you don't have one and put the following into it.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>**X**</double>
 </test>
 <edit name="autohint" mode="assign" >
  <bool>true</bool>
 </edit>
</match>
</fontconfig>
```

Substitute the X in the "<double>**X**</double>" line with the font size limit for smoothing. Anything smaller than X won't be smoothed.

---

### Post by zeeone on 2005-11-30
Didn't do it ...

Here is my .fonts.conf file:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>12</double>
 </test>
 <edit name="autohint" mode="assign" >
  <bool>true</bool>
 </edit>
</match>
</fontconfig>

```

And here is a partial screen shot of my browser:

---

### Post by 23meg on 2005-11-30
Opera may be overriding these settings. See if they're in effect in other browsers and elsewhere.

---

### Post by zeeone on 2005-11-30
Looks even worse in FireFox...
I've set the smoothing to "none" and hinting to "slight" in the Preferences -> Font dialog.

**UPDATE:**

Based on what you suggested and after reading man fonts.conf, I changed my .fonts.conf file to the following:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
  <test compare="more" name="pixelsize" qual="any">
  <double>12</double>
  </test>
  <edit mode="assign" name="antialias" >
    <bool>true</bool>
  </edit>
</match>
</fontconfig>

```

Everything works beautifully. It's like I'm seeing Windows.

---

### Post by 23meg on 2005-11-30
I think what I posted would only work if you were using the autohinter module; I forgot to tell that. Glad you got it working.

---

### Post by Burgresso on 2006-03-22
Where would I put/find the fonts.conf file?

Thanks!
:)

---

### Post by Zeroedout on 2006-03-22
[quote=Burgresso]Where would I put/find the fonts.conf file?

Thanks!
:)[/quote]

Well, 23meg said ~/.fonts . In linux ~/  is the user's home directry, and .fonts  is the file. Anything with a . at the beginning of the name is hidden, so if you are in nautilus and want to see all your hidden files, hit ctrl+h OR View------>Show hidden files OR In a terminal, type, ls -a

---

