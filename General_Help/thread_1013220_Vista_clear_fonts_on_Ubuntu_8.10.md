---
title: "Vista clear fonts on Ubuntu 8.10 ????"
date: 2008-12-16
forum: General Help
---

### Post by Shadowness on 2008-12-16
Hi, all!
How can I get the vista clear type fonts on Ubuntu?
I tryed everything I know and I read here but I can't get the same good looking firefox from vista to ubuntu 8.10.The fonts are almost but not quite as vista's. I have ms fonts and vista fonts installed too.
Now I'm using for .confs.conf:
> <?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
It's pretty good at now but I really need my vista clear type fonts on ubuntu.
Can anybody help, please??? 

Thanks in advance!

---

### Post by yellowaeroplane on 2008-12-16
I'm sort of confused... do you need help actually installing the fonts?

If so, all you need to do is copy the fonts to your .fonts folder in your home directory.

---

### Post by Shadowness on 2008-12-17
> **yellowaeroplane said:**
> I'm sort of confused... do you need help actually installing the fonts?

If so, all you need to do is copy the fonts to your .fonts folder in your home directory.

I have the fonts installed.It's ok but I can't get them look like vista ones. I mean the smoothing and the hiting are not the same.I can't get the same clear type.

---

### Post by roger-k on 2009-03-04
Hi.
I have also the same problem. I have installed ubuntu 8.10 at three different PC's. None of PC's has clear fonts and I'm getting tired in my eyes after a short while.
I have also installed the same fons as in XP. It is a little bit better but not as crystal-clear as in XP.
I want to avoid to change back to XP, but I can't find any solution. Is there any of you who know about a recipe to fix this?

---

### Post by Vaphell on 2009-03-04
different font rendering engine - different results. Probably it's all about patents and engine used by OSS community can't mimic windows 100%.
I also noticed that MS fonts look different so i just found good looking open source ones (DejaVu in my case) and use them.

---

### Post by hashan17 on 2009-04-25
Hey in case in your fonts are not smooth enough or if you are using a LCD display, you can 
* System -> Preferences -> Apearence -> Fonts
* Select sub pixel smoothing (LCD)

---

### Post by pparks1 on 2009-04-25
Aside from the LCD font-smoothing option, I don't make any other changes ( I do install msttcorefonts).   Everything in Ubuntu for me is crystal clear and looks fantastic.   It's a little different than XP or Vista...but it isn't any better or worse.

---

