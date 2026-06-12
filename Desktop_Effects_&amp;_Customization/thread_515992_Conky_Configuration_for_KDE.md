---
title: "Conky Configuration for KDE"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by armware on 2007-08-02
As stated in the title, i'm running kde and trying to get conky to work properly.

Properly being:
1) transparent
2) no flickering
3) desktop icons don't disappear

i can only seem to get two out of three.

the closest i've gotten it so far is 1 and 3. i can get it to stop flickering by enabling double buffering (dbe is enabled in the xorg.conf, no errors in dmesg), but then my desktop icons disappear, unless i hover over them with the mouse, but then they hide again when conky refreshes.

i've tried all combinations of settings, i've loaded all kinds of conky config files and still can't come up with the solution.

so has ANYONE gotten conky to cooperate with kde?

until then, i guess i'll just deal with the flickering.

---

### Post by walkerk on 2007-08-02
> **armware said:**
> As stated in the title, i'm running kde and trying to get conky to work properly.

Properly being:
1) transparent
2) no flickering
3) desktop icons don't disappear

i can only seem to get two out of three.

the closest i've gotten it so far is 1 and 3. i can get it to stop flickering by enabling double buffering (dbe is enabled in the xorg.conf, no errors in dmesg), but then my desktop icons disappear, unless i hover over them with the mouse, but then they hide again when conky refreshes.

i've tried all combinations of settings, i've loaded all kinds of conky config files and still can't come up with the solution.

so has ANYONE gotten conky to cooperate with kde?

until then, i guess i'll just deal with the flickering.

for the flickering:
```
sudo gedit /etc/X11/xorg.conf
```

now add dbe (the bold bit):
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"[B]
	Load	"dbe"[/B]
EndSection
```

---

### Post by armware on 2007-08-02
thanks, but when i said, "dbe is enabled in the xorg.conf", that's what i meant.

i think double buffering IS working, but something about it causes my icons to hide. when it's double buffered conky refreshes are real smooth (which is why i'm sure it's working), but my icons hide.

---

### Post by kodoku on 2007-08-02
KDE with conky is a big pain, but it can be done, as shown [here]("http://briancarper.net/2006/08/25/transparent-conky-in-kde-part-2/")

---

