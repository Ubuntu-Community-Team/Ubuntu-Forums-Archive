---
title: "Tahoma font anti-aliasing at various sizes"
date: 2012-02-16
forum: Desktop Environments
---

### Post by flemur13013 on 2012-02-16
Hi 

On my machine (ubuntu 10.04/64/gnome w/fluxbox) the Tahoma font is anti-aliased with sizes 10,14,18 and larger, but NOT anti-aliased with sizes 12,13,16. ?!?! (Happens with fluxbox and gnome - it's mostly a browser display problem; an example is the "Fonts" and "Size" buttons in the posting GUI in this forum: they're NOT anti-aliased at default size, but ARE anti-aliased if bigger or smaller!)

I'd like Tahoma to be anti-aliased at all font sizes.

I've fiddled with any number of .conf files, "fc-cache -f -v" and nothing seems to do anything. 

My ~/.fonts.conf file is:
 
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font"> <edit mode="assign" name="rgba">           <const>rgb</const> 		</edit> </match>
<match target="font"> <edit mode="assign" name="antialias">      <bool>true</bool>  		</edit> </match>
<match target="font"> <edit mode="assign" name="autohint">       <bool>false</bool> 		</edit> </match>
<match target="font"> <edit mode="assign" name="hinting">        <bool>true</bool>  		</edit> </match>
<match target="font"> <edit mode="assign" name="hintstyle">      <const>hintfull</const> 	</edit> </match>
<match target="font"> <edit mode="assign" name="embeddedbitmap"> <bool>false</bool> 		</edit> </match>
</fontconfig>
```

It had no effect ((sudo)fc-cache, reboot, log in/out). The embeddedbitmap entry is supposed to disable using built-in bitmaps in some fonts (? I'm not an expert by any means).

Any ideas?

---

