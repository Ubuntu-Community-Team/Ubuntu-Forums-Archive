---
title: "What is the 'Sans' font?"
date: 2007-12-28
forum: Desktop Environments
---

### Post by fearpi on 2007-12-28
What exactly is this font I see named 'Sans'? It looks exactly like Deja Vu Sans, which looks exactly like Bitstream Vera Sans. (In fact, there are a lot of fonts installed with Ubuntu that look exactly the same to me). Is 'Sans' defined by a symbolic link somewhere, or by some font settings file, to point to Deja Vu Sans? I'd like to change it if possible, since many programs use 'Sans' and in which it is not possible to change the font (e.g. several Compiz Fusion plugins).

Also, is there any way to see what the actual paths are of fonts in the font cache?

---

### Post by bonzodog on 2007-12-28
I believe that 'bitstream vera sans' and 'sans' are more or less the same font, although they have seperate font files. The generic 'sans' is officially just known as 'X11-Sans'.

However, i always do notice a difference between those and Deja-Vu Sans, which is completely seperate. 

However, personally, I actually prefer to use Liberation Sans, which is part of the redhat liberation font set, designed to replace the need for MS fonts on linux machines.

It also helps to have sub-pixel hinting enabled, and install the modified libs with Bytecode enabled.

This pic from last year shows how crisp and clear they are on my system:
[[img]http://xs216.xs.to/xs216/07240/OpenZen11.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs216&d=07240&f=OpenZen11.png)

---

### Post by fearpi on 2007-12-28
I appreciate the suggestion, but what I'm more interested are technical details. Some applications are hard-coded to use the Sans font, and I want these applications to use another font of my choosing in place of Sans.

---

### Post by marcaemus on 2008-02-19
What font is actually used for Sans is determined by fontconfig. It maps the generic 'Sans' name a font which is actually installed on the machine. Here's part of  /etc/fonts/conf.avail/40-generic.conf:

<!--
  Mark common families with their generics so we'll get
  something reasonable
-->

<!--
  Serif faces
 -->
	<alias>
		<family>Bitstream Vera Serif</family>
		<family>DejaVu Serif</family>
		<family>Times New Roman</family>
		<family>Times</family>
		<family>Nimbus Roman No9 L</family>
		<family>Luxi Serif</family>
		<family>Kochi Mincho</family>
		<family>AR PL SungtiL GB</family>
		<family>AR PL Mingti2L Big5</family>
		<family>&#65325;&#65331; &#26126;&#26397;</family>
		<family>Baekmuk Batang</family>
		<family>FreeSerif</family>
		<family>MgOpen Canonica</family>
		<default><family>serif</family></default>
	</alias>

---

### Post by fearpi on 2008-02-19
Aha, thanks a bunch. That's exactly what I needed.

---

