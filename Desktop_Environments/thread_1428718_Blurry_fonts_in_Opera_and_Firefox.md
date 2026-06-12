---
title: "Blurry fonts in Opera and Firefox"
date: 2010-03-13
forum: Desktop Environments
---

### Post by incus on 2010-03-13
Hello,

[http://img694.imageshack.us/img694/3839/compe.png](http://img694.imageshack.us/img694/3839/compe.png)

Could anyone tell my why fonts in Chrome and Opera/Firefox are so different, even though they're set the same (Arial and Times New Roman)?

For me, pages in Opera/Firefox are blurry and I'd prefer to make them look like those in Google Chrome.

How to do that? Especially in Opera?

Thanks

---

### Post by lukjad on 2010-03-13
First, try this:

Go to Applications->Accessories->Terminal and copy paste this:

```
sudo apt-get install msttcorefonts
```

This is to check you have the core fonts installed. Restart Firefox and Opera and if that fixes it, all is well.

Try this:
Create a file in your /home/[username]/ folder called .fonts.config and then add the code that I'll post below.

Then close and reopen all Firefox and Opera windows and restart them. This should fix it.

To do this, there are two ways of creating the file. Below are the two ways.

[SIZE="5"]**GUI Method**[/SIZE]

Go to *Places->Home Folder*. When Nautilus opens, Click *File->Create Document->Empty File*. Then name the file **.fonts.config**

Once you save it, the file will appear to disapear. The period in front of the file name marks it as a hidden file. To view it, just go to *View->Show Hidden Files* or press Ctrl+H. This will show you all the hidden files that are there. find the .fonts.config file you just created (just type .fonts.config and it should find it for you). Then double click the file and copy paste the code below. Save and close the file. Next close all Firefox and Opera windows and then open them again. This should fix your problems.

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```


[SIZE="5"]**CLI way**[/SIZE]

Open a terminal (*Applications->Accessories->Terminal*) and copy and paste this:

```
touch ~/.fonts.config
```

Next copy and paste this:

```
nano ~/.fonts.config
```

And paste the code below, then press Ctrl+O and Ctrl+X:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Next close all Firefox and Opera windows and then open them again. This should fix your problems.



[_***Source***_]("http://ubuntuforums.org/showpost.php?p=7544051&postcount=3")

---

### Post by incus on 2010-03-13
Thank you very much! It helped.

---

### Post by chazdg24 on 2011-02-02
This does help somewhat.  Fonts are better, but not nearly as clear as windows 7.

---

