---
title: "Can't get widescreen screen resolution"
date: 2006-05-28
forum: Desktop Environments
---

### Post by Stex on 2006-05-28
I just installed the Release Candidate onto my widescreen laptop. And have been given the wrong screen resolution. The choises I have through "Screen Resolution Preferences" are 1024x768, 800x600 and 600x400.

I searched around and picked up the keyword xorg.conf. I open that up but find that already all the values are my desired 1280x800. But I'm seeing a streached 1024x768. What gives?

Every entry (though with a different depth) was already this:
> 	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
Is there anyone that can help? Greatfulness will come to those that try :)

---

### Post by hw-tph on 2006-05-28
You will need a ModeLine entry in the Monitor section of your xorg.conf:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
```


Håkan

---

### Post by kanzelsberger on 2006-05-28
I remember there was an utility called 855resolution and that one was able to replace some unused resolutions like 2048x1024 to 1024x600 and 1280x800. It helped me on such laptop with Intel i915 chipset.

---

### Post by Stex on 2006-05-28
I've put in that modeline and restarted the computer (for lack of knowing what needs restarting) but nothing has changed.

Are you sure it's "1280x800@60" rather than "1280x800_60.00" like the form in the [howto]("http://www.ubuntuforums.org/showthread.php?t=83973")?

I don't know really... I am running at 60Hz refresh rate but other than that I'm pretty ignorant as to my specifications.


kanzelsberger:
I tried 915resolution (presumable the updated version of what you had) but it just didn't detect anything. Thanks for the tip though

---

### Post by Stex on 2006-05-29
Ok, scrap that. I turned my laptop on this morning and it's the right resolution o_O

Very strange... ohwell. It works at least and I'm very happy with the rest of ubuntu

---

