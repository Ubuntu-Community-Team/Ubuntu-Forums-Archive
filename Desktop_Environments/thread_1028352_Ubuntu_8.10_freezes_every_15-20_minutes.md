---
title: "Ubuntu 8.10 freezes every 15-20 minutes"
date: 2009-01-02
forum: Desktop Environments
---

### Post by Jetlag1989 on 2009-01-02
Hello community,
just to introduce myself shortly: I'm a 19 year old student from Germany. I used Ubuntu for a long time, but over the last year i had to use win for work, so I just came back to ubuntu last week.
I installed Kubuntu 8.10 on my AMD PC (64bit Dual-Core). I'm using the actual nvidia drivers for my 8600 GT video card.

The problem:
My computer freezes every 10-15 minutes. Sometimes it even completely restarts (like i unplugged the power cord). I saw nothing special in the logfiles (var/log) and I also don't know what to look for.
RAM and CPU Temp are supervised and RAM is also checked, there is nothing wrong with it. 
The computer runs for days under windows.

Thanks for any ideas

---

### Post by AlanR8 on 2009-01-02
Are you running 64 bit or 32 bit Ubuntu?

From what I see and hear in these forums and elsewhere on the InterWeb, sometimes you get more stability running the 32 bit versions...

---

### Post by Jetlag1989 on 2009-01-02
Sorry, i use the 64 bit version!

---

### Post by AlanR8 on 2009-01-02
No need for an apology!

If you've just put Ubuntu back on you've probably got a fairly clean install right now.

Why don't you try the 32 bit version and see how it goes? Maybe a 64 bit guru will offer some more practical help but that's what I would do....

---

### Post by Jetlag1989 on 2009-01-02
Hello,
i also read something about KDE4-Features which lead to freezes, so i'll reinstall it using the 32bit version and try to deactivate those feature. Maybe that will help.

---

### Post by Jetlag1989 on 2009-01-04
Dear community, i now have reinstalled Ubuntu 8.10 as 32 Bit version, furthermore i haven't installed any nvidia drivers but the freezings continue.

Can anyone explain which error logs i should look through / post here?


Seconds before the computer shut down, those messages were displayed in /var/log/messages;

Jan  4 20:02:16 martin-desktop kernel: [ 2055.245987] __ratelimit: 12 callbacks suppressed
Jan  4 20:02:16 martin-desktop kernel: [ 2055.245997] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:16 martin-desktop kernel: [ 2055.252241] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:16 martin-desktop kernel: [ 2055.264736] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:16 martin-desktop kernel: [ 2055.270846] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:16 martin-desktop kernel: [ 2055.284884] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:16 martin-desktop kernel: [ 2055.297297] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:19 martin-desktop kernel: [ 2058.400424] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:19 martin-desktop kernel: [ 2058.407083] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:19 martin-desktop kernel: [ 2058.417663] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:19 martin-desktop kernel: [ 2058.424605] sky2 eth0: rx length error: status 0x4660100 length 598
Jan  4 20:02:23 martin-desktop kernel: [ 2062.614876] __ratelimit: 1 callbacks suppressed
Jan  4 20:02:23 martin-desktop kernel: [ 2062.614883] sky2 eth0: rx length error: status 0x4660100 length 598

maybe it helps.

---

### Post by Jetlag1989 on 2009-01-06
Hello guys,
i figured out that my sky2 network driver caused the errors in "messages", i now installed the closed source drivers from my card manufacturer but the freezes go on.

---

### Post by bunty on 2009-01-06
KDE4 is still far from finished. I would recommend 8.10-alternate that gives you 3.5

The big popular distros seem locked into the numbers game these days. This sadly means packages get included before they are really proven.

kde.org:

# General Information
# KDE 4.1 (recommended for early-adopting users)
# KDE 4.2 (Beta2) (recommended for beta testers and experienced users)
# KDE 3.5 (recommended for release for more conservative users)

I think we can all see what the "early-adopting users" euphormism means.
a.k.a. beta3  ;)

---

### Post by Jetlag1989 on 2009-01-08
Hello,

@bunty: Thanks, i already downgradet it.

@all:

I found out that the sky2 network driver for my Marvell network card is producing the errors posted above.
I have now searched for the original marvell drivers and have installed them. I told the driver to remove the sky2 driver but it still gets loaded (bug in installation tool maybe).
I see it listed by lsmod, but i can't unload it through modprobe, it says: unknown module.

I now tried to build my own kernel and exclude those sky2 drivers, but i can't get it compiled because my system crashes. (I think this is caused by the sky2 still getting loaded :/)

---

### Post by minisori on 2009-01-12
Yes those errors are around for more than 1 year now... no fix released yet. :S

Edit: sorry for more than 2 years, thanks to the crappy support Marvell is giving to linux and the crappy sky2 drivers :S

---

### Post by soulitude on 2010-07-05
Hi Guys,

@minisori : I agree to you, there are a huge amount of users troubled  with sky2. Unfortunately I am one among them too. You have any idea or  update on this? which driver could work for Marvell Yukon ethernet card?

@Jetlag1989 : I assume that your Wired net connection freezes every  often when you say "freezing", am i right? Cause I have the same issue,  but connections breaks every 5 seconds. 
I have a Sony Vaio laptop with "Marvell Technology Group Ltd. Device 4380(rev 10)" . It has sky2 driver to work for Ubuntu 9.10. I can see my eth0 in ifconfig and lsmod shows sky2 too.

I also tried sk98lin driver but that won't even load my eth0, won't show it in ifconfig. Can you please get back on your present status about this issue? Have you fixed it or any suggestions to carry out.

@AlanR8 : I hope you got an idea on this. Sky2 is driving me crazy and its been a month, i still can't get my cable modem working. I will appreciate if you can help me out. Thanks.

Thanks a lot guys for the help.;)

---

