---
title: "How do you restart the KDE4 panel?"
date: 2009-09-12
forum: Desktop Environments
---

### Post by ireneshusband on 2009-09-12
If you are working in KDE4 and your panel goes down for whatever reason, how do you restart it? In Gnome the equivalent is simply to enter "gnome-panel".

The reason I need to know is that I am troubleshooting something and sometimes have to kill the KDE panel, but because of other bugs I can only relaunch my KDE session by rebooting the machine.

---

### Post by Raboch on 2009-09-12
"plasma-desktop" should do it, assuming that when the panel goes down all of plasma goes down with it.

---

### Post by jacksaff on 2009-09-12
Alt-F2 will hopefully still bring up a run-command box at which you can enter "plasma-desktop" as per the above post.

---

### Post by tubasoldier on 2009-09-12
alt-F2
killall plasma

alt-F2
plasma


that should do it.

---

### Post by ireneshusband on 2009-09-13
> **tubasoldier said:**
> alt-F2
killall plasma

alt-F2
plasma


that should do it.

Indeed it does. Entering "killall plasma && plasma" at the c(k)onsole also works.

Many thanks to everybody for your replies.

---

### Post by Mr.Goose on 2009-11-21
Just thought I'd mention that in KDE v4.3 as shipped with(K)Ubuntu 9.10 the commands have changed.

```
killall plasma-desktop
plasma-desktop
```

I must add, I feel it is a tad disappointing that KDE is still so buggy that one needs to do this in the first place! Let's hope it's sorted in KDE 4.4 - the version that will be used in the next LTS (long term support) edition of Kubuntu (10.04).

As it stands, whilst it is very pretty - great for geeks and tinkerers to play with - and a lot more things work than did in version KDE v4.2 - IMHO KDE v4.3 is still not of sufficient quality for general use and is therefore unfit for use in a production environment.

Best wishes, G.

---

### Post by Zorael on 2009-11-22
> **Mr.Goose said:**
> I must add, I feel it is a tad disappointing that KDE is still so buggy that one needs to do this in the first place! Let's hope it's sorted in KDE 4.4 - the version that will be used in the next LTS (long term support) edition of Kubuntu (10.04).
In its defense, in this case the original poster needed to manually kill the process in nondescript troubleshooting purposes. :3

On a related note, the plasma binary for the netbook shell is **plasma-netbook**.

I'm not sure if there's a difference, but there's also a **kquitapp** command you can use to send a dbus command to make the program neatly shut itself down, instead of sending a TERM signal. Do apps still undergo their shutdown procedures if terminated via signals?

So far I haven't had any real issues with 4.3 since its release, and nothing that strikes me as a production environment-stopper than what's plaguing Linux as a whole.

---

### Post by Mr.Goose on 2009-11-22
Fair point about the O/P's situation. However I suspect that many other readers stumbling across this forum via their favourite search engine will do so because they have experienced one of KDE 4.x's many little idiosyncrasies. E.g. random crashes, compositing stopping working for no apparent reason, the panel disappearing for no good reason, screen gradually slowing up and eventually locking up and a variety of other "nuisance" behaviour. 

Whilst these things might not faze experienced users or died-in-the-wool KDE fans, they make the current version of KDE entirely inappropriate for inexperienced users or for those used to the stability of the Gnome desktop. I feel that whilst KDE 4.3 is a great improvement on 4.2, it would be more accurate if it had been called "*4.0 beta*" - because that's where it is both in terms of stability and usability for the average user, IMHO.

I'm a KDE fan and I have the greatest respect for all those who are working so hard to make it a really good product. But there's no way I'd install it for a customer *at the moment* unless (s)he specifically requested it. Or put it another way. My elderly mother uses Ubuntu 9.10 c/w Gnome & the *New-Wave* skin. She is delighted with it and so far, it's never let her down. But I am quite certain the various annoyments I witnessed over the last few weeks with KDE4.3 would have her on the blower, cursing and begging for her old Windows box back, pronto!

Meantime, my G/F actually did try KDE 4.0 with Kubuntu 8.10 shortly after it came out. However, it's bizarrely random behavior, early-alpha-like usability and all the stuff that simply didn't work at all, literally had her in tears - no joke! Heck, not even Vista did that! Fortunately I made a Remastersys backup of her KDE 3.5-based Kubuntu 8.04 LTS, c/w a copy of all her KDE 3.5 settings files from her home folder. So I was able to restore her trusty Lenovo lappy to its former glory - and get into her *good books *again! Now she steadfastly refuses to budge from this setup until KDE 4.x is *truly* stable. She is adamant that pretty as they are, none of my various KDE 4.2 or 4.3 testbeds have persuaded her to abandon the stability and usability of her current virtual surroundings. 

Like I said, I sincerely hope the next LTS Kubuntu will change all that. But I'm not holding my breath. :)

Best wishes, G.

**P.S. Apologies to the o/p for drifting off topic.**
P.P.S @ Zorael, thanks for the **kquitapp** tip. I will look into that.

---

### Post by Zorael on 2009-11-23
Riding the tangent, 4.0 was awful. I used KDE4 on my test machine by 4.1, and on my main by 4.2. The only issues I have with 4.3 is with other apps (Kopete not having an autoconnect plugin, darnit), and with linux itself.

---

### Post by DJ_Peng on 2010-07-09
> **jacksaff said:**
> Alt-F2 will hopefully still bring up a run-command box at which you can enter "plasma-desktop" as per the above post.
Thanks for this. I'm giving KDE a shot on my Ubuntu box and Plasma seems to crash pretty often on me. Now I know how to restart it without logging all the way out.

> **tubasoldier said:**
> alt-F2
killall plasma

alt-F2
plasma


that should do it.
I'll remember this. Thankee.

> **Zorael said:**
> <snip>

I'm not sure if there's a difference, but there's also a **kquitapp** command you can use to send a dbus command to make the program neatly shut itself down, instead of sending a TERM signal. Do apps still undergo their shutdown procedures if terminated via signals?

<snip>
Nice! I'll look into this to see exactly how to use it and all.

---

