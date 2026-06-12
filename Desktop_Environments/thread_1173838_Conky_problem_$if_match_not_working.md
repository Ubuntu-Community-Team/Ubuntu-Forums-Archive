---
title: "Conky problem: $if_match not working"
date: 2009-05-30
forum: Desktop Environments
---

### Post by SoundBloke on 2009-05-30
The following lines in .conkyrc

${if_match "A" == "A"} TRUE $endif
${if_match "A" == "B"} FALSE $endif

generate the output on the desktop

${if_match} TRUE
${if_match} FALSE

Do I have the syntax wrong or is this a bug? I cannot find any other information on this particular $if construct, though $if_existing...$endif works perfectly.

I am using conky version 1.6.1 on Jaunty if that makes any difference?

Thank you in advance for your help...

---

### Post by Fastjack77 on 2009-05-31
Hi SoundBloke,

I copied and pasted your code and it works on mine. I'm using a pre-release version of conky (Conky 1.7.1_rc4), which was configured with the "--enable-imlib2" option to enable IMLIB2 support at compile time. (e.g. ./configure --enable-imlib2).

Try this one and let me know how it went.

---

### Post by SoundBloke on 2009-06-01
Thanks fastjack77 for the reply.

I installed the pre-release version as requested (though for others' reference, the command "./configure --enable-imlib2" should read "./configure --enable-libimlib2"). Unfortunately this pre-release version of conky does not run at all and instead has generated the following terminal output with the .conkyrc file that worked in version 1.6.1 (other than the original $if_match problem):

Conky: unknown variable wireless_bitrate
Conky: unknown variable wireless_essid
Conky: unknown variable wireless_link_qual
Conky: unknown variable wireless_link_bar
Conky: desktop window (14000a9) is subwindow of root window (8c)
Conky: drawing to desktop window
Conky: drawing to double buffer
Conky: Could not open the file
Segmentation fault

I removed the $wireless... variables which in turn removed the respective errors - though this is obviously not a solution to the problem. The rest remains a mystery.

Hope you can help...

---

### Post by pauna on 2009-06-03
> **SoundBloke said:**
> The following lines in .conkyrc

${if_match "A" == "A"} TRUE $endif
${if_match "A" == "B"} FALSE $endif

generate the output on the desktop

${if_match} TRUE
${if_match} FALSE


It seems if_match has been added in conky v. 1.6.2 so jaunty's default conky doesn't recognize it. Displaying it is conky's default behaviour when it doesn't recognize something as a command.

[http://linux.softpedia.com/progChangelog/Conky-Changelog-8586.html](http://linux.softpedia.com/progChangelog/Conky-Changelog-8586.html)

---

### Post by SoundBloke on 2009-06-03
Thanks Pauna for pointing out my error. However, I am still stuck trying to install version 1.7 - what has happened to the $wireless... variables for instance?

---

### Post by Fastjack77 on 2009-06-03
Hi SoundBloke,

After playing with this version of conky, I think it's not accepting variables or aliases. I might be wrong, but I never was able to make them so far.

I'm sending my conkyrs with screenshot and other useful files; maybe it could help.

Here is my conky version details:
enigma@studio:~$ conky --version
Conky 1.7.1_rc4 compiled Sun May 31 00:00:58 PDT 2009 for Linux 2.6.28-11-generic (x86_64)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * config-output
  * IMLIB2
  * apcupsd
-----------------------------------

If nothing works, send me your conkyrs file and your error messages (copy/paste); I'll see what I can do.

To be honest, there is a great lack of documentation for conky out there. The wiki is empty, and the man page is cryptic. It took me a long time to make mine work. But it certainly was worth it. :popcorn:

Let me know if you were able to go further with this.

Fastjack




[QUOTE=SoundBloke]Hi Fastjack77,

Just to say I have posted the results of the experiment with conky 1.7 following your advice with my my problems using $if_match. Unfortunately i have different errors and am unable to see if the $if_match is working or not. Hopefully you can shed some more light on the issue...

Thank you for the help

SoundBloke[/QUOTE]

---

### Post by SoundBloke on 2009-06-03
Using the latest version, I stripped down my .conkyrc to the bare minimum such that the "segmentation fault" was removed. The simple $if_match test I first cited worked as expected and exactly as you reported.

However, when I add something useful such as:

${if_match ${battery BAT0} == "AC"} Mains Powered, Battery Charged $endif

then I get a "segmentation fault". In version 1.6.1, this line produced no such error (though of course the logic did not work).

For some reason, the $wireless... variables (such as $wireless_essid) produce faults that were not present in version 1.6.1. And I have also noticed that the $user_names function now repeats the user name twice - another added feature of the updated version.

I will keep you informed of progress and more than likely end up posting my conkyrc file in the near future for your analysis too - thank you!

---

### Post by Fastjack77 on 2009-06-04
Hi SoundBloke,

Try this out:
```

${if_existing /proc/acpi/ac_adapter/ADP1/state off-line}
	On battery: ${battery BAT0}.
${else}
	${if_existing /sys/class/power_supply/BAT0/present 1}
		Main power with battery: ${battery BAT0}.
	${else}
		Main power without no battery.		
	$endif
$endif

```
It's working for me. It was the only way I could find a way (using conky) to make a conditional statement to check the presence of an adapter and a battery. The path could be different from one system to another, but it's a start.

---

### Post by SoundBloke on 2009-06-04
Your code segment did work - thank you! Frustratingly though, I still don't know why my lines didn't ](*,)

More curiously, on pasting in your lines, the $user_names problem was also cured - temporarily. Now it's back, which is probably coincidental. Still no luck with the $wireless variables though...

Without needing $if_match, however, I think I might head back to version 1.6.1 where I know everything else works...

---

