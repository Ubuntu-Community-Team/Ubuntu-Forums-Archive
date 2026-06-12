---
title: "Cannot install Xfce 4.12 on Xubuntu 14.04"
date: 2017-04-26
forum: Desktop Environments
---

### Post by ericmark4 on 2017-04-26
Is the xfce4-dev ppa for xfce 4.12 kaput? I am trying to install xfce 4.12 on a fresh install of Xubuntu 14.04.5 (x64). I gave up on 16.04 after too many problems. I know that Xubuntu Trusty went out of support earlier this month, but I plan to run it at least till 18.04 comes out. The base packages from Canonical are still supported. 

Anyway....last time I had 14.04 I upgraded xfce to 4.12 via ppa:xubuntu-dev/xfce-4.12. That ppa now seems to be gone. Does anyone know how to upgrade to 4.12 on Trusty? Please do not suggest that I upgrade to 16.04. I have tried that several times; it just does not suit me. If I have to I will live with the fully functional 4.10 but 4.12 worked like a charm when I used it.

Thanks.

---

### Post by &amp;KyT$0P# on 2017-04-26
Looks like [that PPA]("https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12") was deleted.

Do you have any working 14.04 machines with those packages installed?  If so, [FONT=Courier New]dpkg-repack[/FONT] might help you.  It's available in the standard repositories.

---

### Post by ericmark4 on 2017-04-26
Thanks, halogen 2. Alas I do not have a machine running Xubuntu 14.04 with xfce 4.12. I "upgraded" my desktop to 16.04 and spent months trying to make peace with its bugs and annoyances, till today when I could stand it no more. My laptop runs Mint 18.1. 

I will keep trying to get 4.12 somehow. I can live with 4.10 if I must. It's OK; but 4.12 is better. (Thunar and Settings improvements, etc.) Why must we scramble like this to make things "just work"?

---

### Post by mikodo on 2017-04-27
> **ericmark4 said:**
>  -snippet-

I will keep trying to get 4.12 somehow. 

Try this in an vm or test install then.

Copy source.list:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```
                        [FONT=Ubuntu][SIZE=2]Open sources.list:
[/SIZE][/FONT]
```
[FONT=Ubuntu][SIZE=2]sudo -[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]H mousepad[/SIZE][/FONT][FONT=Ubuntu][SIZE=2] /etc/apt/sources.list[/SIZE][/FONT]
```

[FONT=Ubuntu][SIZE=2]Replace 14.04 sources.list with 16.04 repos.
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Save and close [/SIZE][/FONT][FONT=Ubuntu][SIZE=2]sources.list.
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Open &#8216;Synaptic&#8217; package manager, (install if needed).
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Hit the &#8216;[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]refresh button&#8217; in synaptic.
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Click on the packages you want and then install them.
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Close synaptic.
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2](This can be done in a running system, because of the &#8216;start-stop daemon&#8217; in Debian/Ubuntu systems).
[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Copy your original &#8216;sources.list' from backup [/SIZE][/FONT][FONT=Ubuntu][SIZE=2]and replace to what was before editing and save.

```
sudo apt-get update && sudo apt-get dist-upgrade

```[/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2]Reboot.[/SIZE][/FONT]

---

### Post by Bucky Ball on 2017-04-28
A heads up that Xubuntu 14.04 LTS is no longer supported. Reached EOL not long ago. Upgrade to a supported release (Xubuntu 16.04 LTS perhaps, support to 2019) and no doubt you'll get the version of xfce4 you're after by default (or newer if there is one).

Xubuntu 14.04 end of life: April 17, 2017. [See here]("https://xubuntu.org/release/14-04/").

Just to remind that Xubuntu LTS (and Lubuntu) have three years support, not five.

While Mikodo's remedy may or may not work, why add a new sources list (from 16.04) or PPA to an EOL release (14.04)??? Doesn't make much sense. :-k

Perhaps a better idea would be to back up your data, install a supported release and be done with it. :) EOL releases get no updates/upgrades, and that includes security updates.

---

### Post by mörgæs on 2017-04-28
> **ericmark4 said:**
> I gave up on 16.04 after too many problems.

How does 17.04 work?

---

### Post by flocculant on 2017-04-28
> **ericmark4 said:**
> ... I gave up on 16.04 after too many problems. I know that Xubuntu Trusty went out of support earlier this month, but I plan to run it at least till 18.04 comes out....

 Please do not suggest that I upgrade to 16.04. I have tried that several times; it just does not suit me...

What problems where they? Can't seem to find any threads.

> **Bucky Ball said:**
> A heads up that Xubuntu 14.04 LTS is no longer supported. Reached EOL not long ago....

They know ;)

---

### Post by Bucky Ball on 2017-04-28
> **flocculant said:**
> They know ;)

In that case, might be a better idea to start posting about the problems they were having with 16.04, a supported release, rather than trying to nut out an unsupported one, no? That is a step in the wrong direction IMHO and even if it does get fixed, how long before the next EOL related issue, by which time they'll be even less support available for 14.04? :)

Anyhow, good luck with it. ;)

---

### Post by ericmark4 on 2017-05-02
> **Bucky Ball said:**
> In that case, might be a better idea to start posting about the problems they were having with 16.04, a supported release, rather than trying to nut out an unsupported one, no? That is a step in the wrong direction IMHO and even if it does get fixed, how long before the next EOL related issue, by which time they'll be even less support available for 14.04? :)

Anyhow, good luck with it. ;)

Thanks for the replies, if anyone is still out there. I was busy at work and installing 16.04 yet again. 

Yes, I bit the bullet and decided that xfce 4.12 plus security updates was worth the hassles. I've played with Xenial so much over the past year i learned how to deal with most of the issues and annoyances. 

Since you asked....(thread-jack alert but as OP I hope that's OK): The one issue I still have this time is that I cannot play embedded audio in .ppt/.pps files through WPS Office. That's the one program that does work for that purpose in Trusty, but in Xenial no luck lo the many times I have tried.

So I have to resort to Windows for that admittedly rare usage case. I do not like having to resort to Windows for anything.

Other issues I had, which might be somewhat specific to my wants and needs:

1. Abiword is unusable in 16.04. It works fine in 14.04. I like Abiword for simple word processing. I don't like not being able to use it. I don't like not being able to revert to the earlier version used in Trusty without wading through broken dependencies and such fun.

2. I am a tournament chessplayer and SCID, the chess database, works fine in Trusty but much less well in Xenial. It's not as bad as the total fail of Abiword but it's bad enough.

3. It took a long time to figure out how to restore the Filter box to synaptic, which is the main way I install programs. This is not well-documented at the Xubuntu site or on the main forums as far as I could see. Not sure why this useful feature was removed.

4. The xfce4-mixer plugin was pulled from the repos and at first there was no word on where to find it or what to use as an alternative. I eventually found a way to install the mixer plugin but after awhile it went belly-up. It took more surfing and sniffing around to find the pulse audio plugin---which works fine, but I would still prefer the mixer plugin if it worked. But it does not.

5. The mscore fonts do not always install correctly on Xenial. This is not a deal-breaker as there are OS alternative fonts---but it's frustrating to see the package listed as "installed" in synaptic---reinstall it repeatedly---but not be able to access the fonts in any word processor. This time around the mscore fonts did install. Much joy.

There are a few other nitpicks but those are the main and recurring issues. This time---based on trial-and-frustration the past year---I found ways to deal with all issues apart from the embedded audio in Powerpoint problem.

If nothing else goes south I will keep this install of 16.04. It is snappy and elegant in its simplicity---what I liked about Xubuntu from the start. (I found Linux around the time Xubuntu appeared.) But I will never get why it suddenly became harder to get stuff set up and get stuff done in Xenial, and why it's so hard for a moderately savvy Xubuntu veteran to find explanations/alternatives.

Thanks for asking. Enjoy.

---

### Post by &amp;KyT$0P# on 2017-05-02
For (1) and (2), have you tried getting the source code of the version you used on 14.04, and building/compiling it on 16.04?  When I upgraded from 14.04 to 16.04, I needed to do this for a couple softwares.  And it worked well for me.

For (3) sounds like you figured this out, but for other readers: just install [FONT=Courier New]apt-xapian-index[/FONT] then restart Synaptic once or twice.

And for (5) I followed this suggestion from howefield - [https://ubuntuforums.org/showthread.php?t=2349421&p=13594666&viewfull=1#post13594666]("https://ubuntuforums.org/showthread.php?t=2349421&p=13594666&viewfull=1#post13594666")

---

