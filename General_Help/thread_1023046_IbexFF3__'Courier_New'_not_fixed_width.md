---
title: "Ibex/FF3 : 'Courier New' not fixed width"
date: 2008-12-27
forum: General Help
---

### Post by d1291 on 2008-12-27
Hello,

I've got xubuntu (intrepid ibex, xfce 4.4.2) and firefox 3.0.5. When I visit a website with something like the following:

```
<span style="font-family:courier new">This should be fixed width.</span>
```

It displays in variable width for me. I've tried all I can find here, my **~/.fonts.conf** inlcudes (and I've made sure it's included in /etc/fonts/fonts.conf too)

```
<match target="pattern">
	<test qual="any" name="family"><string>courier new</string></test>
	<edit name="family" mode="assign"><string>Bitstream Vera Sans Mono</string></edit>
</match>

```

and indeed, **fc-match** shows:
```
~$ fc-match "courier new"
VeraMono.ttf: "Bitstream Vera Sans Mono" "Roman"
```

I've tried rebooting and updating fc-cache ... no luck. What am I missing?

Note: I want to replace Courier (New) by Bitstream Vera Sans Mono, *not* install mscorefonts and use the real Courier.

---

