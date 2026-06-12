---
title: "X-Server bug ? Mouse focus getting &quot;trapped&quot;"
date: 2009-11-23
forum: Desktop Environments
---

### Post by Jethro_uk on 2009-11-23
hi guys,

I've posted with an experience with 9.04 which I originally thought was a mouse driver issue. However a recent incident has caused me to suspect a misdiagnosis which may be why I have't gotten any answers.

The problem is intermittent (the worst kind) and revolves around the mouse. My system is dual-boot with XP, and XP works flawlessly, so we can eliminate the mouse hardware. However, it's a Labtec USB wireless (with keyboard).

The problem manifests itself by mouse clicks not working. Initial thoughts are the clicks are being ignored, as the pointer moves around the screen. However, a more detailed inspection of the situation reveals that it's not that the mouse clicks are being ignored. It's that the system appears to have "trapped" the mouse focus, as moving the mouse over buttons no longer causes a highlight. In firefox (for example) hyperlinks no longer cause the cursor to change to a hand.

The problem seems application independent ... happens in Nautilus, Firefox, NXClient (that ones a killer as it gets trapped in the NXClient window, and you cannot break out of it).

When the problem happens Alt-Tab also stops working, so you can't switch windows.

At first I suspected (obviously) a mouse/USB problem. However, on Friday, my Linux-expert brother had caused to VNC into the machine, and the problem happened to him. Which pretty much lets the hardware of the hook.

At his suggestion, I switched from GNOME to KDE, but the problem still happened, which narrows things down to the X-Server ?

(Notice the question mark - I'm a Windows programmer, so the intricacies of Linux/X-Server/Desktop environments is all a bit of a dark science to me).

Moving on from here, I have noticed one set of circumstances which appear to guarentee the fault happening, and which may explain the intermittent nature of the fault.

It seems to happen when the mouse focus passes into a list control (NOT a drop down list). I noticed this after opening the LogFile Viewer, and realised that the mouse focus was getting stick in the LH pane, which lists the available log files. Once it is stuck in there, it won't allow clicking anywhere. However, interestingly enough, if I hover the mouse over the right hand side (the contents of the logfile) I can hold the mouse button down and highlight text - so clearly the system is "getting" the mouse click. However moving the mouse to the "Close" button and clicking does nothing - no highlight, no click.

For those of you that know the "Blueman" app (for bluetooth) I also noticed it here ... when I click the icon the app comes up, and works fine, except if I click in the list of plug-ins. Then the mouse gets trapped ....

So there you have it ... This problem is occuring on two 9.04 installs, one an upgrade, and one a fresh install. The fresh install is my sons "mess-around" copy, so yesterday I decided to upgrade to 9.10 and see what happens. 

In the meantime my system is still unstable :frown: 

So there you have it. The most detailed analysis I could pen. Ideally someone will step up and say "Ah! That's ....." and give me a fix. Failing that, if someone could point me into the direction of somehow enabling some debug, and a file to look into to see what is happening, I'd be eternally grateful.

For any Win32 heads out there, the best way I can picture this bug is that once the mouse focus moves over a certain graphical object, then the message handler somehow manages to crash and mouse click events are not forwarded down the chain. However my brother (who is also not an X-server expert) claims Linux handles events differently to Win32 ...

---

### Post by Jethro_uk on 2009-11-25
Seems this issue is a perennial one ...

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

---

### Post by TaxAlien on 2009-11-30
I have exactly the same problem but with different hardware. 

Symptoms are ignored mouse clicks, sometimes the odd one, sometimes you can click like mad, nothing happens and then suddenly it realises you wanted some attention. It makes it a totally lousy desktop experience.

I troubleshooted this by going into an xterm session and there is no problem with the hardware or the X server it seems. It is something to do with Gnome itself. What that is is anyone's guess.

TA

---

### Post by Jethro_uk on 2009-12-01
> **TaxAlien said:**
> I have exactly the same problem but with different hardware. 

Symptoms are ignored mouse clicks, sometimes the odd one, sometimes you can click like mad, nothing happens and then suddenly it realises you wanted some attention. It makes it a totally lousy desktop experience.

I troubleshooted this by going into an xterm session and there is no problem with the hardware or the X server it seems. It is something to do with Gnome itself. What that is is anyone's guess.

TA

The problem I have occured under KDE as well as GNOME. It is definitely an X-server bug.

---

### Post by Jethro_uk on 2009-12-02
After a while playing with this problem, I have got it down to be an annoyance, rather than a showstopper.

Not being a Linux guru, my opinions are of limited value, but I firmly believe this is an X-Server/XOrg problem. I've seen it happen under GNOME and KDE, and with all combinations of window managers, and decorators.

There appears to be a connection with ALT-TAB ... as soon as the mouse focus issue happens, you lose ALT-TAB.

Anyway, I have discovered that if I activate ALT-TAB as soon as I login, it seems to "protect" my system, and I don't seem to lose mouse focus.

I have also discovered, that CTL-ALT-D (show desktop) seems to recover mouse focus ... once all windows are minimised to the taskbar, then ALT-TAB seems to work again, and mouse focus is restored. Hopefully this workaround will prove useful to people, and can remove the need to logout/login again, or to restart the machine with the loss of data that implies.

---

### Post by Jethro_uk on 2009-12-23
Having lived with this problem for a few weeks now, I believe I can have a stab at suggesting what is going on, and the intermittent nature of the bug.

I *think* that when GDM starts (after I login), some process somewhere starts up, and creates a window. I have read various reports that it's possible to create a window which does not appear in the panel area. This window then steals focus. Because it's hidden, you can't switch to it to close it. From that point on, you're stiffed.

I've read a lot about the modified behaviour of the update manager/notifier, and I would like to propose this as the app which is killing mouse focus.

I'm researching ways to kill it so it never starts ...

---

### Post by louvann on 2009-12-24
I can confirm this behaviour. My laptop running 9.04 has the same problem whether using a USB mouse or the eraser-head. I initially have full functionality as you do. The trigger which you speak of may well be the cause, but I do not know what that element is.
 My mouse impairment is more selective than your case. the right mouse click seems to be mostly responsive, but the left is can only highlight a link in a browser. I have learned when in this mode, to use a <rtn> to simulate the left click.
The top most window is the only accessable window in my case. I need to dismiss a window to get to a 'lowered' window with <alt><F4>. None functions of the task bar are functional by the left mouse button

---

### Post by pjcdawkins on 2010-01-10
I have the same problem in KDE/Kubuntu 9.10 except everything other than mouse events (e.g. Alt-Tab) still works fine. The workaround is "kwin --replace".

I've just reported it here:
https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/505494

---

### Post by codedr on 2010-08-10
I found this bug report when I was searching for a fix for a similar issue.
In my case all  you have to do is move a window and then immediately click in another window.
There may be other ways to reproduce this.
Investigating the issue I found this patch:
     [http://cgit.freedesktop.org/xorg/xserver/patch/?id=1884db430a5680e37e94726dff46686e2218d525](http://cgit.freedesktop.org/xorg/xserver/patch/?id=1884db430a5680e37e94726dff46686e2218d525)
     Subject: Revert "dix: use the event mask of the grab for TryClientEvents."
 
I am using xorg-server-1.8.0 and found the issue was introduced in
xorg-server-1.6.3.  The patch fix appears in xorg-server-1.8.2 and later

---

### Post by Elyotna on 2010-10-28
Hi folks,

I'm having the exact same issue as louvann here. I also agree that this bug is not distribution/desktop environment/driver dependant.

(tested with Ubuntu/fedora/archlinux/gnome/kde/nvidia-binary/nouveau)

However, could you all post your hardware (mouse&graphic card) used ?

Because my solution to fix this bug (temporaly though, only for 1 week) is weird : 

I need to unplug my computer from power source, unplug my nvidia 9600GT for 2~3 minutes, plug everything back.

And then I can enjoy my linux for one week without this bug.

There's another way of fixing it, but only for your session : go to tty1 and restart the X server (using a "sudo service gdm restart" for example)

But it really looks like this bug is related to my 9600GT (or the way it's handled by some unknown layer in the system...), as it is the component I need to unplug.

Also my mouse is a logitech Cordless Click! plus.

I know I should post this on the bug report, but from what I've seen here lot of ppl have lot of different versions... (for some the mouse click does work sometimes, etc..).

But louvann is the first guy I see describing my exact same problem.

Anyway, if you have any headsup on this issue, I'd glad to hear them..

---

### Post by Elyotna on 2010-10-28
Hi folks,

I'm having the exact same issue as louvann here. I also agree that this bug is not distribution/desktop environment/driver dependant.

(tested with Ubuntu/fedora/archlinux/gnome/kde/nvidia-binary/nouveau)

However, could you all post your hardware (mouse&graphic card) used ?

Because my solution to fix this bug (temporaly though, only for 1 week) is weird : 

I need to unplug my computer from power source, unplug my nvidia 9600GT for 2~3 minutes, plug everything back.

And then I can enjoy my linux for one week without this bug.

But it really looks like this bug is related to my 9600GT (or the way it's handled by some unknown layer in the system...), as it is the component I need to unplug.

Also my mouse is a logitech Cordless Click! plus.

I know I should post this on the bug report, but from what I've seen here lot of ppl have lot of different versions... (for some the mouse click does work sometimes, etc..).

But louvann is the first guy I see describing my exact same problem.

Anyway, if you have any headsup on this issue, I'd glad to hear them..

---

### Post by Elyotna on 2010-10-28
Hi folks,

I'm having the exact same issue as louvann here. I also agree that this bug is not distribution/desktop environment/driver dependant.

(tested with Ubuntu/fedora/archlinux/gnome/kde/nvidia-binary/nouveau)

However, could you all post your hardware (mouse&graphic card) used ?

Because my solution to fix this bug (temporaly though, only for 1 week) is weird : 

I need to unplug my computer from power source, unplug my nvidia 9600GT for 2~3 minutes, plug everything back.

And then I can enjoy my linux for one week without this bug.

But it really looks like this bug is related to my 9600GT (or the way it's handled by some unknown layer in the system...), as it is the component I need to unplug.

Also my mouse is a logitech Cordless Click! plus.

I know I should post this on the bug report, but from what I've seen here lot of ppl have lot of different versions... (for some the mouse click does work sometimes, etc..).

But louvann is the first guy I see describing my exact same problem.

Anyway, if you have any headsup on this issue, I'd glad to hear them..

---

### Post by Elyotna on 2010-10-28
Hi folks,

I'm having the exact same issue as louvann here. I also agree that this bug is not distribution/desktop environment/driver dependant.

(tested with Ubuntu/fedora/archlinux/gnome/kde/nvidia-binary/nouveau)

However, could you all post your hardware (mouse&graphic card) used ?

Because my solution to fix this bug (temporaly though, only for 1 week) is weird : 

I need to unplug my computer from power source, unplug my nvidia 9600GT for 2~3 minutes, plug everything back.

And then I can enjoy my linux for one week without this bug.

But it really looks like this bug is related to my 9600GT (or the way it's handled by some unknown layer in the system...), as it is the component I need to unplug.

Also my mouse is a logitech Cordless Click! plus.

I know I should post this on the bug report, but from what I've seen here lot of ppl have lot of different versions... (for some the mouse click does work sometimes, etc..).

But louvann is the first guy I see describing my exact same problem.

Anyway, if you have any headsup on this issue, I'd glad to hear them..

---

### Post by Elyotna on 2010-10-28
Hi folks,

I'm having the exact same issue as louvann here. I also agree that this bug is not distribution/desktop environment/driver dependant.

(tested with Ubuntu/fedora/archlinux/gnome/kde/nvidia-binary/nouveau)

However, could you all post your hardware (mouse&graphic card) used ?

Because my solution to fix this bug (temporaly though, only for 1 week) is weird : 

I need to unplug my computer from power source, unplug my nvidia 9600GT for 2~3 minutes, plug everything back.

And then I can enjoy my linux for one week without this bug.

But it really looks like this bug is related to my 9600GT (or the way it's handled by some unknown layer in the system...), as it is the component I need to unplug.

Also my mouse is a logitech Cordless Click! plus.

I know I should post this on the bug report, but from what I've seen here lot of ppl have lot of different versions... (for some the mouse click does work sometimes, etc..).

But louvann is the first guy I see describing my exact same problem.

Anyway, if you have any headsup on this issue, I'd glad to hear them..

---

### Post by Elyotna on 2010-10-28
Sry about this quad-post... My browser hang and I thought the message didn't go, so.. well. And since there's no double-post protection and we can't delete them... :(

---

### Post by Jethro_uk on 2010-10-28
wow - such an old post to get replies.

I no longer use Ubuntu on my desktop - I just couldn't be doing with this bug, which seems to have poersisted through 3 new releases now. Before I gave up, I was doing the TTY1 restart gdm trick. But it was a PITA as I lost all my documents, webpages etc.

I still use ubuntu on my file/media server. I connect in from a windows machine, using NX, and that's worked fine for 18 months.

There is absolutely no doubt this is an Ubuntu-centric fault. The same machine, same hardware runs XP without a glitch. On the basis it only seems to happen with wireless mice, my guess is there is some very very subtle bug in the USB handling, which has to multiplex keyboard and mouse signals onto one port. I haven't experienced the issue with a hard-wired USB mouse ....

---

### Post by Elyotna on 2010-10-28
Thanks Jethro for your answer.

If I can't find any other solution to this bug, I guess I'll have to consider buying a wired mouse...

And like you say, I also run vista in dual boot, and everything is smooth in vista.

Could you please post your graphics hardware ? I wanna know whether my nvidia 9600GT is guilty or not.

Thanks in advance,

Elyotna.

---

### Post by EnsignR on 2010-10-30
@Elyotna
I am using a wired ps2 mouse, thats not the issue.

> seems to have persisted through 3 new releases now
Yes its tad disconcerting isn't it. This bug was initially reported back in 2006.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

---

### Post by Jethro_uk on 2010-11-04
> **Elyotna said:**
> Thanks Jethro for your answer.

If I can't find any other solution to this bug, I guess I'll have to consider buying a wired mouse...

And like you say, I also run vista in dual boot, and everything is smooth in vista.

Could you please post your graphics hardware ? I wanna know whether my nvidia 9600GT is guilty or not.

Thanks in advance,

Elyotna.

I will get back when I next have the machine on ... I use my work laptop more noawadays, since a promotion, so haven't had the machine on for a while. It *is* an nvidia GEFORCE IIRC

---

### Post by flyboy on 2010-12-04
This problem is not ubuntu specific - I am experiencing what appears to be a similar issue on gentoo, with kde and with gnome. The trick of dropping to an alternative terminal fixes the problem and it doesn't come back until the computer is rebooted. I am trying to find a combination of xorg-server, hal, udev and kernel settings to try and resolve where the bug actually resides, but so far I haven't isolated it.

I intend to keep trying ;)

---

### Post by Jethro_uk on 2010-12-07
> **flyboy said:**
> This problem is not ubuntu specific - I am experiencing what appears to be a similar issue on gentoo, with kde and with gnome. The trick of dropping to an alternative terminal fixes the problem and it doesn't come back until the computer is rebooted. I am trying to find a combination of xorg-server, hal, udev and kernel settings to try and resolve where the bug actually resides, but so far I haven't isolated it.

I intend to keep trying ;)

Hi Flyboy ...

the only clue, is that it's a bug which appears to have been introduced, with an upgrade. I have forgotten what version now (it'll be at the start of the post) as I was using Ubuntu quite happily for months beforehand.

Oh, the other clue is it appears to be a *wireless* mouse issue, possibily restricted to the USB port.

I personally believe that when alls said and done, we'll discover that some process somewhere, was creating an "invisible" window, which captured the mouse button focus. Not sure if the Linux message pump works the same as Win32, but my guess is someone subclassed the mouse button messages, and the forgot to call the default handler, to pass it down the chain. I say that, because I have written a few Win32 apps which used the same trick to ignore mouse clicks (google "subclassing" if you want a riveting read).

---

### Post by johansson on 2011-01-03
I've had this same exact problem, and I'm not sure I'm shedding any new light here, but I think I have two minor differences.  

1) While for some users this problem seems to be fairly intermittent, for me it is fairly predictable.  It ALWAYS happens. 

2) it never used to happen.  I ran 8.10, 9.04, and until recently 9.10 without issue.  What Changed?  I accidentally shocked my computer through the mouse and keyboard with static.  I thought I had discharged it (crazy static in my apartment) but apparently not.  Ever since, this problem has been very prevalent.  

I haven't completely ruled out hardware malfunction, but I mean, my issue is perfectly described throughout this thread.  

Upgrading to 10.4 now, going to try new mouse and keyboard tonight and pick up and anti static pad

Edit: Also is it more useful to post this here or in the launchpad bug report?

==================================

Followup Edit: After updating to 10.4, there was no change in behavior.

Switched my USB Logitech MX518 mouse for a basic ps/2 HP mouse.  Linux didn't recognize it, so I plugged the HP mouse into a ps/2 to USB converter and everything worked fine.  

So it was just the mouse.  Brought the Logitech mouse into work and plugged it into my Windows XP machine, the mouse works fine.  

I've read a lot of people saying that it's NOT the mouse because the mouse works with windows. Well, I switched mice and the new one works with Ubuntu, and the old one works with Windows, so I think it's some combination of the two.

---

### Post by Moysa on 2011-02-14
Hi, i had the exact same problem as described by Jethro_uk in the first post. It happened couple of weeks ago on Ubuntu 9.04, for which updates stopped several months ago, so the problem wasn't in an update of any kind. I had a Labtec wireless keyboard and an a4Tech battery free mouse (nb-75d). Changing mouse did not help, nor did clean installing Ubuntu 10.10.

However i seem to have solved the problem by changing the keyboard. I now have a wired usb keyboard and the same a4Tech mouse. The problem hasn't appeared in a week now. Before i considered my self lucky if i managed to work for an hour. I don't know what causes this issue. Maybe some malfunction that causes the keyboard to send a signal which confuses the x-server. Couple of days before the bug started appearing wireless receiver "lost" the keyboard, so i had to reset. Maybe that's a clue. It isn't the batteries because, apart from this bug, keyboard was working fine.

Anyway hope this helps someone with the same issue. I'll report back if the problem reappears.

---

### Post by Yudley on 2011-05-13
I had the same problem today and guess what was the cause?

my wireless mouse was turned on, inside my bag, within range of my laptop ... and I wasn't aware of it

---

### Post by Hexorg on 2011-07-17
I have this issue as well, (gentoo, both gnome/kde, with a slight variation as the original), but for me it started appearing when I upgraded the whole system. I don't think there was a Xorg upgrade, but I did upgrade the kernel to 2.6.38-gentoo-r6. Could this bug be as deep as the kernel? I see a TON of forum posts online about similar symptoms on a wide range of distributions and desktop environments. 

I'm also trying to find the reason for it, but was unlucky so far. 
Next time this happens I want to see if `cat /dev/input/mice` responds with any mouse clicks, and I just installed gpm, and want to see if it'll respond when I switch to tty's.

---

### Post by Jethro_uk on 2011-08-03
Well, thanks to this bug, I had to stop using linux on my main PC. It was either that, or switch to a wired mouse, which for various reasons isn't an option. Besides, imagine if M$ replied that rather than fixing such a bug in windows, you could just use a wired mouse !!!!

FWIW I appreciate it's a real nasty. Intermittent *and* only with a small subset of possible hardware configurations.

My media server is OK, since I NX into it. Never had the problem. So there's a possible clue ... what does NX do (or not do) that X doesn't (or does) ?

---

