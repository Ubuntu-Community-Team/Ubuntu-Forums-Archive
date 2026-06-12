---
title: "Screen Resolution help"
date: 2009-01-14
forum: General Help
---

### Post by TCSnyder on 2009-01-14
I tried to plug in my Ubuntu system into a projector via a s-video port, i went to screen resolutions and when i extended my screen to the projector it asked something about making a virtual screen resolution, i accepted and put in my password and now my screen is messed up, when i log in i can see all of my screenlets, which are suppose to be in a widget layer, and my background, no panels or desktop icons, i can alt+f2 and run "gnome
 -display-properties" and it looks normal, but i press apply, and everything is fixed except my widgets, anyone had this problem or know how to help?

---

### Post by TCSnyder on 2009-01-14
bump.

---

### Post by TCSnyder on 2009-01-14
ok i fixed it and I am posting the answer for future lost people. in my /etc/X11/org.conf was an extra monitor, 

*~*~FIRST MAKE A BACKUP OF xorg.conf~*~*
i just opened it in the vi editor and deleted the new section,

i knew it was the right one because it had a subsection that said

	SubSection "Display"
		Virtual	2464 900
	EndSubSection


so i knew it was a virtual screen resolution, 
Good luck with any problems

---

