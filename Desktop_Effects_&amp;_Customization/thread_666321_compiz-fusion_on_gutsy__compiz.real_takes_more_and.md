---
title: "compiz-fusion on gutsy : compiz.real takes more and more RAM &#8594; freeze"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by nico@nc on 2008-01-13
Hi,

I am using compiz-fusion on Gutsy with fusion-icon automaticaly loading when opening my session (with "loose binding" option).

When I'm normally using my computer (Firefox, Thunderbird...), compiz.real process takes more and more RAM (up to 300/500Mb), and when there is no more, everything freezes. If done quickly, Ctrl+Alt+Del can allow to come back to the login screen.

I found a workaround: reload compiz with fusion-icon *Reload window manager* option, and compiz.real immediately goes back to a more "normal" memory use (less than a hundred Mb).

I can check when to reload compiz with the system monitor :
[IMG]http://www.enregistrersous.com/images2/197939072120080108211048.png[/IMG]

When the dark green (programs) is over 70%, reload is needed, over 90% it is urgent to do it (and usually it starts to slow down).

And a *Reload window manager* effect : (it is often more spectacular)
[IMG]http://www.enregistrersous.com/images2/126051650020080108211043.png[/IMG]


Any idea to avoid to do this every 15 minutes?

Thanks! :)


PS : my configuration in a few words
> nVidia GeForce Go 6400 (with *nvidia-glx-new* driver)
2*512Mb RAM
1,73GHz Intel Pentium M processor

---

### Post by nico@nc on 2008-01-26
&#8594; [quote="Adamk from [Compiz Fusion forum](http://forum.compiz-fusion.org/showthread.php?p=46939#post46939)"]The nVidia drivers 100.14.19 and higher suffer from a memory leak that can cause compiz to gradually consume all your memory. nVidia is aware of the problem and is working on fixing it: [http://nvnews.net/vbulletin/showthread.php?t=100803](http://nvnews.net/vbulletin/showthread.php?t=100803)[/quote]

---

### Post by MONODA on 2008-02-06
you could try and write a script for it and register it in your crontab to run every 15 min or so

---

### Post by nico@nc on 2008-02-07
I prefer doing it manually, as if I don't minimize any window it can last one or two hours without problem.

Moreover, reloading compiz is not very transparent: it takes about 10 seconds, windows mustn't be maximize, if Firefox is open it crashes in 90% of cases, and in ~10% of cases Ubuntu completely freezes...

So I try not to minimize windows, and when I need something a bit more stable, I switch to Metacity with fusion-icon.

---

