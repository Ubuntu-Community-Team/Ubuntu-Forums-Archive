---
title: "Monospace font in gnome terminal"
date: 2006-11-21
forum: Desktop Environments
---

### Post by utka on 2006-11-21
Dear, eh... ubuntus!

Running the latest Ubuntu 6.10. Starting xterm, looking good. Starting gnome terminal, looks terrible. Question: how do I make gnome-terminal use *exactly* the font used by xterm. And no, disabling antialiasing/hinting ain't the same coz it ain't the same font. Thanks!

- vumnaja vutka

---

### Post by utka on 2006-11-22
come on! does not anyone know?

---

### Post by 23meg on 2006-11-22
Set your default Monospace font to a size of 7.5px at 96DPI and it should come close.

---

### Post by utka on 2006-11-22
> **23meg said:**
> Set your default Monospace font to a size of 7.5px at 96DPI and it should come close.

Close yes, still it is not the same font. I need *exactly* the font used by xterm.

Does anyone know at least the name of the font used by xterm. I cannot seem to be able to find it in the standard font list :( ...

Thanks!

---

### Post by utka on 2006-11-22
Well this forum has been very helpful... not.

Anyways, I've found the solution. Run:

```
sudo dpkg-reconfigure fontconfig-config
```

in console, answer whatever you want to the series of questions, when asked if you want to turn on bitmapped fonts answer YES. You should now be able to select "Terminal" et al fonts in the fonts menu.

Q.E.D.

---

### Post by cpitchford on 2008-03-06
You're right.. there are often lots of unanswered questions on this forum, but thanks for posting your reply. Having just installed Ubuntu 7.10 on a laptop with a terribly tiny 1024x768 display I really needed the xterm fixed font.

sudo dpkg-reconfigure fontconfig-config
sudo fc-cache -fv

fixed the problem, fontconfig-config wasn't enough..

---

### Post by cpitchford on 2008-06-10
Actually this is bad.. enabling bitmapped fonts does allow gnome-terminal to use the fixed font some of use know and love but it has knock on problems for firefox and printing!

firefox will use bitmapped fonts if a document uses them by name.. an example appears to be on the ubuntu start page:

[http://start.ubuntu.com/8.04/](http://start.ubuntu.com/8.04/)

So, I've **disabled** bitmap fonts using the method above and then added a small patch file to enable JUST the fixed fonts:

cat /etc/fonts/conf.d/69-zzz_fixedfonts.conf 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!-- Enabled Fixed bitmap fonts -->
 <selectfont>
   <acceptfont>
     <pattern>
        <patelt name="family"><string>Fixed</string></patelt>
     </pattern>
   </acceptfont>
 </selectfont>
</fontconfig>  

That solved the problem for me AND ensured my other fonts looked nice under firefox..

For an example of the problem I was seeing, enable bitmap fonts then try to print the ubuntu start page!! nasty!! (use print to file PS / PDF to see the same result)

It seems bitmapped fonts cause problems.. this little file patch solved it nicely for me!

---

