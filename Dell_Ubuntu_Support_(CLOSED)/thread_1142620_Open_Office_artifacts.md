---
title: "Open Office artifacts"
date: 2009-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gamelord12 on 2009-04-29
A friend of mine showed me an article saying that my graphics card (GeForce 8400 laptop version) tends to overheat and fry.  The only symptom listed that I think I might have is artifacts of characters staying drawn on the screen when they're not supposed to be there.  The only time that I notice this happening though is when I use Open Office.  I can mouse over buttons and the image on them will disappear completely (most of the button graphics disappear when I use Ctrl+S to save until I mouse over them again).  Also, if I hit enter to use the next line when I'm already at the bottom of a page, sometimes the rest of the text won't move (on the screen) but it's clearly typing a new line.  Is this a problem with Open Office or with my computer?  Maybe it's just a problem with nVidia drivers (I don't recall this problem happening in the brief time using Open Office between doing a clean install of Ubuntu 9.04 and activating the restricted drivers).  If so, what are my options?  My laptop should be under warranty because they extended it for the graphics card issues, so if we can figure out that that is indeed the problem, this summer would be the most convenient time to send my computer away for repairs, before next fall semester starts.

---

### Post by Gausian on 2009-04-29
this happens to me too.  sort of like screen lag.  goes away after scrolling a little.

---

### Post by gamelord12 on 2009-04-29
That's exactly it.  So it's a bug in Open Office and not with my GPU's hardware?  That's great.  Now here's a question: why does this happen on Ubuntu and not on my Vista computer?  Why would an open source program work better on Windows than on an open source operating system?

---

### Post by mikechant on 2009-05-01
> Why would an open source program work better on Windows than on an open source operating system? 

Openoffice is a branch off of Staroffice (which still exists as a paid for version of Openoffice with non-free extras). Staroffice ran on DOS and Windows *before* it ran on Linux. So maybe this has something to do with it. (See wikipedia staroffice article).

---

### Post by gruntlips_ on 2009-05-01
I have this same problem in open office 3.0.1. These are my symptoms:

1) I scroll over the menu options and sometimes they disappear.
2) I scroll over the menu options and the ones where my mouse is on become grayed out. 
3) I tried switching from the ubuntu dusk theme to human clearlooks and that reduces the problem but it still exists.
4) When I scroll down in calc the row numbers freeze or don't update seamlessly.
5) When I scroll across in calc the column names sometimes freeze such that column K might have the name from column A.
6) These issues are transient - scrolling back and forth or toggling between sheets seems to make them go away.
7) There does not appear to be a consistent pattern, i.e. I can't reproduce the same behavior consistently.
8 ) I have tried this in blank calc workbooks as well as some pretty ones.  I get the same result.
9) I don't appear to have this problem in any other application or on my ubuntu system in general.

I switched the following open office memory settings to:
number of steps: 20
graphics cache: 128 MB
memory per object: 20 MB

I am running 9.04 on a system76 serval.  I installed it fresh 5 days ago.
My specs are: intel dual core 2.5GHz, 4 GB RAM, GeForce 8600 M GT the latest nvidia driver (version 180).

I don't think I always had this problem. I think it cropped up when I switched to office 3.0 or the newest nvidia driver but I am not 100% sure.

Thoughts? Ideas?

- gruntlips

---

### Post by gamelord12 on 2009-05-01
Did adjusting those memory settings help the problem?  You're definitely experiencing the same problem as me.  I went into Add/Remove programs and added the OpenJDK runtime, then uninstalled sun-java-bin6 in Synaptic, at the recommendation of someone else to use open java.  Assuming the steps I took were what he meant, that still didn't work for me.  This seems like a pretty big bug that someone should have identified on the dev team by now.

---

### Post by mattgif on 2009-05-01
I had this problem too, and I solved it with the fix below.

This ( [http://ubuntuforums.org/showthread.php?t=778194&highlight=openoffice+redraw](http://ubuntuforums.org/showthread.php?t=778194&highlight=openoffice+redraw) ) thread linked to this ( [http://aldeby.org/blog/index.php/fix-for-openoffice-writer-bad-screen-redraw-refresh.html](http://aldeby.org/blog/index.php/fix-for-openoffice-writer-bad-screen-redraw-refresh.html) ) site, which provided the following fix:

> The bug is actually not of OpenOffice Writer but instead concerns compiz and nvidia propietary drivers. A workaround exists, here is how to enable it:

first install compizconfig-settings-manager

sudo apt-get install compizconfig-settings-manager

then launch the applet from System -> Preferences -> CompizConfig Settings Manager navigate to Utility section and click on Workarounds plugin. Inside enable (tick) “force syncronization between X and GLX”.

---

### Post by gruntlips_ on 2009-05-01
I tried mattgif's solution and it seems to work for me.  I will play around with calc a bit more to see if I can get it to replicate some of my previous problems.  I'll post what I find.

This makes since because I think I first noticed the problem when I upgraded nvidia drivers to 180.  Also I did not have compiz installed.

Gamelord2, did this fix work for you? I didn't mess around with the java settings.

Thanks mattgif.  

- gruntlips_

---

### Post by Gausian on 2009-05-02
the fix worked for me too.  the behaviour is gone :)

---

### Post by devmage on 2009-05-10
I can confirm that this fix also worked for me.  I had been having the described behavior, using Compiz on Nvidia driver version 180.xx over an Nvidia Quadro NVS 140M chip.  Seems to have cleared up - will amend post if anything to the contrary arises.

---

### Post by BlueElk on 2009-05-14
... and it worked for me as well. *happy camper*

---

### Post by Dan_Dranath999 on 2009-05-16
I installed OpenOffice 3.1 yesterday, on Hardy. The window border disappears only on WRITER when the cursor rolls out the maximize/minimize/close buttons. (and appears on roll over)

The rest of the suite has no issues, it's just writer.

---

### Post by giovannilenzi on 2009-05-18
I tried mattgif's solution but it does not work for me.
I had this problem on Ubuntu 8.10 64bit with and old nvidia card with 256MB shared memory, Nvidia 173.
Now I still have the same problem on Ubuntu 9.04 64 bit and nvidia Geforce 8400GS 512MB integrated. Nvidia driver is 180.44.

I have the problem using Openoffice 2.4, Staroffice 9.0, Openoffice 3.01 and even with some windows programs on Wine.

Any idea?
Thanks
Giovanni

---

### Post by giovannilenzi on 2009-05-19
I solved it. See my post:
[http://ubuntuforums.org/showthread.php?p=7306949#post7306949]("http://ubuntuforums.org/showthread.php?p=7306949#post7306949")

---

