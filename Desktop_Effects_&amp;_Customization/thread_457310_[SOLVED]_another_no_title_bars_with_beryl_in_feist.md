---
title: "[SOLVED] another no title bars with beryl in feisty..."
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by zachthejones on 2007-05-28
alrighty folks, I'm having the same problem as many people out there (at least from what I read in the forums): I don't have any title bars or anything around my windows!  I just installed feisty today, and installed beryl with no problems.  It was working great and I was playing with settings, when all of a sudden I realized I had no title bars.  The problem, it seemed, on other posts was this  portion of the /etc/X11/xorg.conf file:

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
[B]Option 			"RenderAccel" "True"
	Option 		"AllowGLXWithComposite" "True"
	Option 		"backingstore" "True"
	Option 		"TripleBuffer" "True"[/B]
	Option		"NoLogo"	"True"
EndSection

I am running an nVidia card...

the portion in bold was something suggested in one forum...which I added (though I forgot to line up that one "option" line - does that matter?) and rebooted with.  To no effect.

oh yeah, and I'm not even sure how to stop beryl so I can use the desktop as normal.

and I'm also not getting a little red diamond thingy in the corner representing the beryl manager, though beryl seems to be running fine (other than the missing titlebars) and I can access the beryl manager through Applications->system tools.

Any help would be wonderful.

---

### Post by dmoney on 2007-05-28
Open a terminal and type:

```
emerald --replace
```

and see what happens.

---

### Post by uthturn on 2007-05-29
thanks so much dmoney i was getting worried

---

### Post by zachthejones on 2007-06-08
Thanks!  I actually used the section of [this starter guide]("http://www.pcworld.com/article/id,130923/article.html") concerning beryl to fix the problem, I just ran the commands he suggested in the terminal, and when all was said and done, Beryl worked perfectly!

---

### Post by njwiley on 2007-06-19
In case others haven't resolved this after upgrading to Beryl 0.3, I fixed my issue by deleting my beryl settings (# mv ~/.beryl ~/.beryl.backup) and restarting beryl (# beryl-manager&).

---

