---
title: "Odd output from conky 'mixer' variables"
date: 2010-03-29
forum: Desktop Environments
---

### Post by tgeer43 on 2010-03-29
Hi folks,

Was fooling around with my .conkyrc today. Whenever I output the values of any of the mixer variables, eg. mixer, mixerbar, mixerl, mixerlbar, mixerr, mixerrbar - the correct value is initially displayed but it only persists for one iteration of conky. As soon as conky refreshes (2 secs. in my case), the value goes to zero (0). I'd have to restart conky in order to get another reading until conky loops/refreshes again.

I'm sure that it's not normal behavior because nothing else in conky seems to work this way. Has anyone come across this? I couldn't find a mention of it anywhere.

Thanks,

tgeer

---

### Post by wannabegeek on 2010-03-30
similar problem here,  I don't get any value besides zero...

wbg

---

### Post by tgeer43 on 2010-03-31
Well, I guess it's a small consolation that this issue is not unique to me but apparently it's fairly rare considering that lack of responses here and nary a mention of it elsewhere on the net.

Perhaps some kind soul who has had experience with this will pop in and set us straight.

Additionally, I've subscibed and sent a message to the conky-users mailing list at sourceforge.

Other than that, I'm about out of ideas as to where to look to find a resolution. Thankfully it's a minor 'cosmetic' type issue and nothing that's hindering my day to day use of Ubuntu.

tgeer

---

### Post by wannabegeek on 2010-04-01
tgeer would you mind posting your conky code for me...

just curious....the usage I've seen is really simple:

TEXT
$mixer

and that should kick out a volume number

---

### Post by tgeer43 on 2010-04-11
Sorry it took so long to get back to this thread. Too much going on lately.

Yes. the syntax is as simple as it comes. Here's a snippet containing the relevant line of code:
```
${color #5EFFFF}Ping time to www.verizon.net: ${execi 180 ping -c2 verizon.net | tail -n1 | cut -d"/" -f5 | head -c-3}ms
**${color #5EFFFF}Volume: ${mixer}**
${color #5EFFFF}GPU: ${nvidia temp}°F  Mem: ${nvidia gpufreq}MHz Clk: ${nvidia memfreq}Mhz
```I've also tried using the optional *device* argument to specify various ALSA devices with the same result - an initial correct display until conky refreshes in 2 seconds after which time the variable returns zero (0).

Dunno about this one and the conky-users mailing list hasn't provided any clues yet either.

tgeer

---

### Post by luceerose on 2010-06-08
I was having the same problem it's taken me 3 straight days & nights to find a solution. The mixer command is useless in newer versions of conky & even the standard .sh scripts weren't working for me. Eventually, I found the only script anywhere on the internet that works.
Put the following code in a .sh file, (mine's called vol.sh);
```
#!/bin/bash
amixer get Master | awk -F'[]%[]' '/%/ {if ($7 == "off") { print "Master Mute" } else { print "Master",$2"%" }}'
```
Put that .sh file wherever you want on the harddrive.
Then refer to it in your conky file with an execution command.
Example;
${texeci 3 /PATHtoFILE/vol.sh}

---

