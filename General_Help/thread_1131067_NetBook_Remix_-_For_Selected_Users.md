---
title: "NetBook Remix - For Selected Users ???"
date: 2009-04-20
forum: General Help
---

### Post by Tom_T on 2009-04-20
Hi

Is it possible to add Ubuntu Netbook Remix to Ubuntu 9.04, but only for selected users ??

I'd like to keep the normal desktop.. but my daughter would like the remix interface..

Is that possible ??

Thanks

---

### Post by gali98 on 2009-04-20
I would think so... Gnome-settings are user specific. My suggestion is to just try it.
Log in as her user and change it over to remix then log out and log into your username and see if it works okay.
Kory

---

### Post by redbook4574 on 2009-04-20
> **Tom_T said:**
> Hi

Is it possible to add Ubuntu Netbook Remix to Ubuntu 9.04, but only for selected users ??

I'd like to keep the normal desktop.. but my daughter would like the remix interface..

Is that possible ??

Thanks

It is actually very easy to switch between gnome and unr + 9.04 remembers your last logon. Check preferences - switch desktop in unr

---

### Post by LowSky on 2009-04-20
remix is just an application that runs ontop of gnome, so you can set it up per user... the same applies to using gnome or kde, all user specific

---

### Post by ddrichardson on 2009-04-20
Remix is UME - a different application picking interface; maximus - which automatically resizes all windows; go-home-applet - which switches to UME from the applications; and window-picker-applet - which is a very small application switcher. There are some other differences, notably in device support and booting. Oh and a different theme.

There is an applet included to switch beween UME and Gnome's desktop too.

I've been running it since the first image was released and th current 9.04 snapshot is very stable on the Acer Aspire One.

The install guide is available here:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by jaqrah on 2009-04-20
> ddrichardson **There is an applet included to switch beween UME and Gnome's desktop too.**

In 8.10, I found this applet broke my system when switching from UNR to Gnome desktop with Compiz set on highest setting. 

Despite various attempts from some great people here on the forum, I wound up having to do a fresh install due to wanting my netbook for an impending vacation.

---

### Post by ddrichardson on 2009-04-20
> **jaqrah said:**
> In 8.10, I found this applet broke my system when switching from UNR to Gnome desktop with Compiz set on highest setting. 

Despite various attempts from some great people here on the forum, I wound up having to do a fresh install due to wanting my netbook for an impending vacation.
Sorry to hear that, UNR is based around 9.04 now and the rate of development is very high. The code for that particular applet isn't mature yet though I agree.

---

### Post by Master One on 2009-04-21
> **jaqrah said:**
> In 8.10, I found this applet broke my system when switching from UNR to Gnome desktop with Compiz set on highest setting.
Yes, I just made the same mistake. I installed Ubuntu 9.04 RC from the Alternate CD, because I want to have full disk encryption, then I added the ubuntu-netbook-remix package, but forgot to disable Compiz (which was enabled in "Normal" mode by default for the main-user). I rebooted into UNR and Compiz caused a complete mess-up. Switching to normal desktop mode resulted in the usual setup, but even after switching Compiz off, and enabling UNR again did not help. At first it did not properly show the upper panel, or only with distortions, then it showed the lower panel, which should be disabled in UNR mode, and after another logout + login the upper panel was gone, switching to normal mode and back to UNR resulted in a failure message, which I do not remember what it was exactly. Adding another user, and logging in with that account resulted in a normal UNR desktop without problems. There surely would have been a way to fix this issue, but I got impatient and am just reinstalling on my Asus Eee 901GO right now...

---

### Post by LowSky on 2009-04-21
UNR is awesome for people who want really basic HTPC functions

works great on my 37" HD TV, because a normal gnome session looks horrible and fugly

---

### Post by Tom_T on 2009-04-22
Hi
I installed this on my Acer One along side Linpus and I can select which desktop my wife and daughter have :)

Only issue I have is 99% disk used !! I allowed the installer to install alongside Linpus.. 

I'll take a proper look at this tonight :confused:

---

### Post by ddrichardson on 2009-04-22
Linpus has a big(ish) swap space and around a 3 Gb install, so if you're on an A110 with an 8Gb SSD I'm amazed you got both installed.

---

### Post by Tom_T on 2009-04-22
My Acer One has a 160GB Drive !!

So I'm not to sure what I've done..  Once I get home I'll have a look at it.

---

### Post by Tom_T on 2009-04-22
Sorted out what had happend with the partitions.

For some reason letting the UNR installer take care of partition size I ended up with a hugh Linpus partition and a very small Ubuntu.

Resized the partitions and now its sorted.  

Couple of issues have a risen.

2 Users. 
1 using Ubuntu 'normal' gnome desktop, the other using UNR Desktop.

Logging in as gnome desktop user I get no bottom taskbar and no menu on the top task bar. Also this user is not automatically logged into the local WiFi network.

Logging in as the user with the UNR Desktop, everything is fine and Wifi works straight away..

Any Ideas ??

Thanks

---

### Post by ddrichardson on 2009-04-22
Do the bars remain if you add them? Is the the keyring manager coming up?

---

### Post by hyperdude111 on 2009-04-22
On jaunty use 

"sudo apt-get install ubuntu-netbook-remix"

Then go system-preferences-desktop mode and use DR

Be careful, although this works it did kill my old system.

---

### Post by Tom_T on 2009-04-26
Thanks for the replies..

Both users have now decided they like the UNR frontend so I'll leave it at that !!

:)

---

