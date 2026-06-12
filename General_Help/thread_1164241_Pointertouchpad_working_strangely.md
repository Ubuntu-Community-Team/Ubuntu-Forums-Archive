---
title: "Pointer/touchpad working strangely"
date: 2009-05-19
forum: General Help
---

### Post by Seishuku on 2009-05-19
I did everything the General Multimedia Howto told me to, and when I restarted my screen went bonkers and said it had to boot in low-graphics. Then, I reset the configuration to default and restarted. Everything works fine now (so it didn't undo the work this howto did), but my pointer is working strangely. Instead of speeding up when I do long, fast strokes, it slows down! It also goes faster when I do small, slow strokes. How do I get it working normally and not backwards?

---

### Post by utnubuuser on 2009-05-19
Are you using "gsynaptics"?

---

### Post by Seishuku on 2009-05-19
> **utnubuuser said:**
> Are you using "gsynaptics"?

No, I'm not.  Should I?

---

### Post by Seishuku on 2009-05-20
How do I enable gsynaptics?  I keep getting an error message I don't know how to fix.

---

### Post by utnubuuser on 2009-05-20
Hi -- Cut and paste that error message: "... SHMConfig to "True...", and you'll find plenty of threads.  [http://ubuntuforums.org/showthread.php?t=942400]("http://ubuntuforums.org/showthread.php?t=942400")
On the last laptop I set up, I specifically had to make sure that the InputDevice section was a "Mouse" section, and not just touchpad.  I tried for hours to get it set up in a seperate section InputDevice  "Synaptics touchpad" and it wouldn't work.  Make sure to add the "Option SHMConfig "True" line in an actual InputDevice "ConfiguredMouse" section.
Here's such a section from my desktop.> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection
  You could probably copy and paste the xorg.conf input device section in the above link to your own xorg.conf file and try it.  If it doesn't work, try changing the Identifier line to:  'Identifier "Configured Mouse"' like it is in my xorg.conf file, and change the driver to synaptics.
I'm just pointing out that sometimes it works as "touchpad", and sometimes you have to call it a "Mouse".

---

### Post by Seishuku on 2009-05-21
Thanks for your help, I got gsynaptics working properly now...Although gsynaptics doesn't actually solve my problem.

---

