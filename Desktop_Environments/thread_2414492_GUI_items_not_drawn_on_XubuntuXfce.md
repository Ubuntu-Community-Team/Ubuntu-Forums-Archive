---
title: "GUI items not drawn on Xubuntu/Xfce"
date: 2019-03-11
forum: Desktop Environments
---

### Post by standardblue on 2019-03-11
Hello folks,

I'm running Xubuntu 18.04 LTS pretty much out the box (and kept updated) on fairly old hardware, and have had this issue for the past few months:

On most applications and windows, a lot of the GUI items are not correctly drawn: text boxes, drop downs, tabs, buttons, etc don't have any borders on them - just the text they contain. I've added a screenshot below of the Software & Updates window to show generally how things appear. It only happens on one account (mine) and not any others on my system. 

[ATTACH=CONFIG]282749[/ATTACH]

I've googled, searched this forum and fiddled with various settings and config files in my homedir to try and solve this, but without any joy. (I know there's a similar issue with Firefox, but I don't think it's that, and this is more widespread across most other applications.) Part of the problem may be that I'm not searching using the right terms.

Has anyone seen this before, or know where I need to be looking to fix it please? I'm guessing something somewhere has got corrupted, but I can't find what!

Thanks,
Mark

---

### Post by &amp;KyT$0P# on 2019-03-11
Does your selected GTK theme (Settings > Appearance > Style) have a GTK 3 variant?
Do you have a custom [FONT=Courier New]~/.config/gtk-3.0/gtk.css[/FONT] or similar that could be interfering?

---

### Post by standardblue on 2019-03-16
Hi Halogen,

Thanks for your reply. 
I've tried several themes (all ones Xubuntu comes with) to no avail - all have the same result.

It appears that while I have the gtk-3.0 directory, I don't have a gtk.css at all! (Nor does the other user on my system.) Could that be the issue?

Using dpkg -l libgtk-3-0, GTK3.0 does appear to be installed, though.

Thanks,
Mark

---

### Post by again? on 2019-03-16
The default theme in Xubuntu is Greybird.
Check you are changing this in Appearance and not just Window Manger settings.
[ATTACH=CONFIG]282803[/ATTACH]

You can test with default xsettings by moving the config file...
```
mv ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml.bak
```
Logout.

No difference...move config file back...
```
mv ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml.bak ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
```
Logout.

Can also create a new user account and test.

---

### Post by him610 on 2019-03-16
Hello standardblue,
May we see your system specs? Please show the results, between the code tags, of*** inxi -f***

---

### Post by standardblue on 2019-03-20
Hello guber2,

Thanks, that's sorted it! - I've always used Window Manager settings as that's how I thought you changed the theme. Selecting Greybird in Appearance has fixed the issue. (The theme I was using, Raleigh, didn't have the colour blocks next to it, that may have been part of the problem?)

Hello him610,

Thanks for your help. Just for completeness, these are my (antiquated) system specs:


```
[COLOR=#295FCC]**CPU:      **[/COLOR][COLOR=#295FCC]**Dual core**[/COLOR][COLOR=#AAAAAA] AMD Athlon II X2 245 (-MCP-) [/COLOR][COLOR=#295FCC]**cache:**[/COLOR][COLOR=#AAAAAA] 2048 KB[/COLOR]
[COLOR=#295FCC]**clock speeds:**[/COLOR][COLOR=#295FCC]**max:**[/COLOR][COLOR=#AAAAAA] 2900 MHz [/COLOR][COLOR=#295FCC]**1:**[/COLOR][COLOR=#AAAAAA] 2900 MHz [/COLOR][COLOR=#295FCC]**2:**[/COLOR][COLOR=#AAAAAA] 2900 MHz[/COLOR]
[COLOR=#295FCC]**CPU Flags:**[/COLOR][COLOR=#AAAAAA] 3dnow 3dnowext 3dnowprefetch abm apic clflush cmov[/COLOR]
[COLOR=#AAAAAA] cmp_legacy constant_tsc cpuid cr8_legacy cx16 cx8 de extapic[/COLOR]
[COLOR=#AAAAAA] extd_apicid fpu fxsr fxsr_opt ht hw_pstate ibs lahf_lm lbrv lm mca[/COLOR]
[COLOR=#AAAAAA] mce misalignsse mmx mmxext monitor msr mtrr nonstop_tsc nopl npt[/COLOR]
[COLOR=#AAAAAA] nrip_save nx osvw pae pat pdpe1gb pge pni popcnt pse pse36 rdtscp[/COLOR]
[COLOR=#AAAAAA] rep_good sep skinit sse sse2 sse4a svm svm_lock syscall tsc vme[/COLOR]
[COLOR=#AAAAAA] vmmcall wdt

[/COLOR]
```

Thank you all for your help, appears to have been user error! I'll mark this thread solved now.

Mark

---

### Post by again? on 2019-03-20
In xfce, the Window manager sets title bar and border theme only.
I have a number of themes without the colour blocks that work.
I think not showing colour blocks is just due to changes in theme coding.

---

