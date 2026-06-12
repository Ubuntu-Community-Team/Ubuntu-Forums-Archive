---
title: "[SOLVED] fonts.conf &amp;quot;not well formed&amp;quot;"
date: 2008-12-18
forum: General Help
---

### Post by aheckler on 2008-12-18
I downloaded a new .fonts.conf file yesterday to help smooth out my screen fonts, but now sometimes when I run things from the command line I get this error:

```
Fontconfig error: "~/.fonts.conf", line 1: not well-formed (invalid token)
```

Here's my .fonts.conf:

```
< ?xml version="1.0"?>  
< !DOCTYPE fontconfig SYSTEM "fonts.dtd">  
<fontconfig>  
  
 <match target="font" >  
    <edit mode="assign" name="rgba" >  
     <const>rgb</const>  
    </edit>  
 </match>  
  
 <match target="font" >  
    <edit mode="assign" name="hinting">  
     <bool>true</bool>  
    </edit>  
 </match>  
  
 <match target="font" >  
    <edit mode="assign" name="hintstyle">  
     <const>hintfull</const>  
    </edit>  
 </match>  
  
 <match target="font" >  
    <edit mode="assign" name="antialias">  
     <bool>true</bool>  
    </edit>  
 </match>  
  
 <match target="pattern" >  
    <edit mode="assign" name="autohint">  
     <bool>true</bool>  
    </edit>  
 </match>  
  
 <dir>~/.fonts</dir>  
</fontconfig> 
```

---

### Post by oldos2er on 2008-12-18
Try removing the spaces in the first two lines. From this:

< ?xml version="1.0"?>
< !DOCTYPE fontconfig SYSTEM "fonts.dtd"> 

 to this:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

---

### Post by aheckler on 2008-12-18
Did it! Thanks!

---

