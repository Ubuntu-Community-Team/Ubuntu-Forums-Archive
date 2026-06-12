---
title: "Firefox Crashes When Pasting Into GMail"
date: 2009-04-24
forum: General Help
---

### Post by Phasmus on 2009-04-24
I just did a clean install to Jaunty.  It is pleasant.  But a strange and enraging new problem has arisen.

Using either the default Firefox 3.0.9 or the experimental Firefox 3.5 pre-beta 4 when I paste anything into a GMail compose-mail window the browser crashes hard.  

There is no output to the console when Firefox is launched from there.

Deleting my .mozilla folder and going in with a totally clean profile has no effect.

Changing GMail to use Plain Text instead of Rich Formatting lets me paste without crashing.

I am worried that GMail is not the only entry point for this crash, and that I will lose data by pasting into some other interface that causes the same problem.

I haven't seen anything like this in the forums/the googling.

Any ideas?

Thanks.

---

### Post by NWC on 2009-04-24
I just registered to this forum to ask for help with something very similar. I haven't written any emails yet with gmail, but if I type into they small search box in the upper right-hand corner, my browser immediately fades to dark for about 10 seconds, and then unless I exit the box immediately, it freezes again for 10 seconds until I manage to get the cursor out. The same thing happens when trying to fill out any search field(for instance, the search on the Mozilla support forums).

I'm on 9.04 as well using Firefox 3.0.9. I've never had any problems like this before with 8.10, but now firefox is unusable for me, I had to download another browser. I disabled all of my add-ons, but I don't know if there's anything else I should do to fix it or what's going on, but it doesn't look like a ton of people have this problem.

---

### Post by Unhban on 2009-04-27
I have a similar thing - using FF 3.0.9 and Ubuntu 9.04... Firefox will just suddenly disappear. Then I can restart it but it soon goes again. It does seem to happen with feature-rich pages....

The add-ons I'm running are AdBlock-Plus and ForecastFox - but no problems previously with U 8.10 and the previous FF.

Unh.

---

### Post by Phasmus on 2009-04-27
A mysterious twist...  I returned from the weekend thinking to test the effect of disabling Desktop Effects on this irk.  I re-enabled rich text on gmail and started pasting madly.  There was no crashing.  I have not restarted the system or installed any software or relevant updates since the symptoms were last observed.  I'll keep a wary eye on future developments...

---

### Post by Unhban on 2009-04-28
Interesting. I read elsewhere it may be down to the screensaver, so disabled that and all is well so far. Fingers crossed!

Unh.

---

### Post by mtthwbrnd on 2009-06-26
I am having a similar problem. Every time I reboot my machine the restart freezes with the hour glass mouse pointer. I have to restart and hold escape, and boot into the recovery mode root prompt.

I then have to mv /usr/local/lib/libz.so.1 /usr/local/lib/libz.so.1.hold

Then reboot succeeds. Some where along the line, I don't know how, that blasted libz.so.1 file get regenerated! When it does Firefox crashes when I paste into Gmail and Synaptic Package manager will not run.

The solution I found is to:
mv /usr/local/lib/libz.so.1 /usr/local/lib/libz.so.1.hold

Then it all starts working again. Is it something to to with Python? Why does Python need the version information and then stops everything from working when it cannot find it? I am not a fan of Python.

mb@mb-laptop:~$ synaptic 
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)
synaptic: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
mb@mb-laptop:~$ mv /usr/local/lib/libz.so.1 /usr/local/lib/libz.so.1.hold
mb@mb-laptop:~$ synaptic 
mb@mb-laptop:~$ 

Hope it helps.

---

### Post by o1e9 on 2009-08-01
The same problem, in my case it is Adobe Flash plugin.  Updating to the latest from Adobe Labs does not help.  The problem started few days ago.

Can you run FF 3.0/3.5 from xterm and say 'ulimit -c unlimited' before running it?  It may produce core file on crash, so stack trace may help to understand the source of the problem.

---

### Post by pgacv2 on 2009-12-03
Try pasting the text to some other app as an intermediary. For me, it was crashing when I pasted from jEdit to a tinyMCE textarea, but if I go from jEdit to gedit and then to Firefox, all is well. I saw on another forum that someone has the same problem and apparently it might be related to Java or Netbeans.

I never would've thought that just kind of program you use to copy-paste some text could have an effect on other programs that receive it.

---

