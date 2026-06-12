---
title: "X-server gets wrong dpi info, upsets font sizes"
date: 2005-05-15
forum: Desktop Environments
---

### Post by britbrian on 2005-05-15
I just installed Kubuntu on my Ubuntu partition and I like both environments equally, so now I want all app's fonts to be consistent in both DEs.

In GNOME sessions 10pt fonts look great but in KDE sessions, 10pt fonts look like 7.5pt fonts & are unreadable. In KDE sessions, kinfocenter->X-server reports my 19" monitor as 25" !! & as 75dpi instead of expected ~100dpi.

Can I tell /etc/X11/xorg.conf file to not query the monitor or force it to use only 100dpi ?. How does GNOME get the dpi right & KDE get it wrong ?

Meanwhile my workaround is to startup X-server & KDE with a 17" monitor that can report 100dpi then I switch back to the 19".  Changing font defaults  to / from 10 / 12pts  just to switch sessions is not on.

Thanks for any ideas

---

### Post by britbrian on 2005-05-17
I found my xorg.conf answer in this howto on installing MS fonts & setting the dpi !!!

[http://www.ubuntuforums.org/showthread.php?t=20976&highlight=pixel](http://www.ubuntuforums.org/showthread.php?t=20976&highlight=pixel)

Locate Section "Monitor" and add the following lines before EndSection:
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi

Now KDE looks as good as GNOME

---

