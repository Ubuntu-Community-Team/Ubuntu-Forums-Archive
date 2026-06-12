---
title: "[SOLVED] Adobe Reader Font Fixed"
date: 2008-12-09
forum: General Help
---

### Post by MrFSL on 2008-12-09
**[SIZE="4"]32bit Hardy Install[/SIZE]**

I searched the forum and could not find an answer to this problem so I am posting it here. Hopefully it helps some people.

I use the adobe reader 8.1.3 package for pdf files:
Located ***_[Here]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")_***

I have noticed that often I get errors saying that a certain font cannot be displayed. This happens frequently with Microsoft fonts like Arial,Bold or Arial,Narrow. In the reader these fonts come out as little black dots instead.

I simply could not find a fix here nor on the Adobe forums. After some hacking though I have a solution:

First install the msttcorefonts package (if you haven't already)
```
sudo apt-get install msttcorefonts
```
Next edit the the reader's startup file:
```
sudo gedit /opt/Adobe/Reader8/bin/acroread
```
And uncomment these two lines:
```
ACRO_ENABLE_FONT_CONFIG=1
export ACRO_ENABLE_FONT_CONFIG
```

Now reader acts as should be expected.

---

### Post by kendoori on 2010-02-23
I was having issues with Arial displaying in a document, even though I'd already had the fonts installed for use with WINE. Uncommenting these settings solved the problem for me.

---

### Post by kyriacosxk on 2011-02-20
Dear friend

What do you mean uncomment these two lines? I have gedit acroread9 but I don't know what to do? My English are not very good. Please help with more explanation. how to uncomment these two lines?

thank you

---

### Post by kendoori on 2011-02-20
Just modify the command line input to the following

```

sudo gedit /opt/Adobe/Reader9/bin/acroread

```

Then remove the # from the following lines

```

# Enable this if you donot want Adobe Reader to cache Font-config fonts 
# ACRO_DISABLE_FONT_CONFIG=1
# export ACRO_DISABLE_FONT_CONFIG

```

When complete it should look like this

```

# Enable this if you donot want Adobe Reader to cache Font-config fonts
ACRO_DISABLE_FONT_CONFIG=1
export ACRO_DISABLE_FONT_CONFIG

```

---

