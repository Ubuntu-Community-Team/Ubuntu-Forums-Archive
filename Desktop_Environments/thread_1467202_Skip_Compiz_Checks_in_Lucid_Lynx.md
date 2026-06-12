---
title: "Skip Compiz Checks in Lucid Lynx"
date: 2010-04-30
forum: Desktop Environments
---

### Post by goober99 on 2010-04-30
Just upgraded from 9.10 to 10.04. When I tried to enable desktop effects from the Appearance Preferences, got "Desktop effects cannot be enabled."

No problem. Same thing happened on 9.10. I just ran the compiz-check script and told it to skip blacklist checks. Then everything worked fine.

I did the same thing on my freshly installed 10.04. Then tried enabling desktop effects. Still could not be enabled.

It seems the compiz-check script is unable to disable the blacklist checks in 10.04, because I typed "compiz" into a terminal and got this:

```
Blacklisted PCI ID 8086:2562 detected
```

Before you say, maybe Compiz just doesn't work with your video card: I installed fusion-icon, selected Compiz as my Window Manager, and Compiz started up fine. I just don't want the extra step of selecting Compiz from fusion-icon every time I reboot. I want Compiz to be enabled automatically when I boot up.

Does anyone know how to skip the blacklist checks in 10.04?

---

### Post by jimbudler on 2010-04-30
I had the same problem including being able to start it from fuzion-icon, and with some troubleshooting found:

/etc/xdg/compiz/compiz-manager contained:

COMPIZ_NAME="compiz.real"
which no longer existed. I changed to:

COMPIZ_NAME="compiz"

compiz started up automatically on my next login.

---

### Post by Don1500 on 2010-04-30
Since we're talking about 10.04 and Compiz...

Has some of Compiz's functionality been removed? No deformed cube, no 3-d windows, No Flaming windows. Just wondering.

Opps, Never mind. Forgot to load the extras!

---

### Post by goober99 on 2010-04-30
The file /etc/xdg/compiz/compiz-manager does not exist on my computer. I created it with the contents

```
COMPIZ_NAME="compiz"
SKIP_CHECKS="yes"
```

and I can still only launch Compiz from fusion-icon.

---

### Post by auh2o on 2010-05-01
> **jimbudler said:**
> I had the same problem including being able to start it from fuzion-icon, and with some troubleshooting found:

/etc/xdg/compiz/compiz-manager contained:

COMPIZ_NAME="compiz.real"
which no longer existed. I changed to:

COMPIZ_NAME="compiz"

compiz started up automatically on my next login.

That didn't work for me, even though I have said file. How does the rest of yours look? Mine as follows (after applying your edit):

```
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz"
```

---

### Post by konlungkao on 2010-05-01
That didn't work for me too

---

### Post by kage52124 on 2010-05-01
Same problem here, earlier edit from compiz.real to compiz didn't work, nor has SKIP CHECKS=yes.

This is strange because Compiz worked fine in 9.04 and 9.10.  I don't understand why it would be blacklisted now...

---

### Post by zpletan on 2010-05-01
```
sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz
```

Now search for the ASCII string "8086:2562" (minus quotes, of course), and change it slightly - I changed the 2 to a 3.

I have the same graphics card (8086:2562) built into... something I can't take out (don't quite remember what), but I also have a PCI NVIDIA card that I actually use, so the fact that the Intel card keeps me from using Compiz is quite annoying.

Now that I've fixed this and gotten a fatal error, I'm off to replace nouveau with NVIDIA (goodbye KMS :(), and try again.

---

### Post by zpletan on 2010-05-01
I can now confirm that my solution works (for me).  You may need to install some proprietary drivers if compiz won't work with your video card out-of-the-box.

Now I just have to decide how much I love my wobbly windows - nouveau made my system seem much snappier.

---

### Post by goober99 on 2010-05-01
Me too, zpletan. I'm actually using a NVIDIA GeForce 8400GS video card, which Compiz works find with, but Ubuntu still sees the integrated Intel video card I can't remove even though I don't use it.

---

### Post by goober99 on 2010-05-02
Your trick worked for me too, zpletan. You're amazing! Thanks!

---

### Post by oyok2112 on 2010-05-19
Exactly what I have spent a week looking for!  (Still was a bit simpler running SKIP_CHECK=yes...but I'll take it!)

---

### Post by revnobody on 2010-06-01
I was wondering if this will work if I only have the intel chipset. I am a complete NOOB, I am really excited about trying compiz, but so far I am disappointed that I can't get it to work.

---

### Post by zpletan on 2010-06-01
> **revnobody said:**
> I was wondering if this will work if I only have the intel chipset. I am a complete NOOB, I am really excited about trying compiz, but so far I am disappointed that I can't get it to work.
You can try, but last time I tried this with the Intel chipset (on Karmic), it didn't work, and I don't have much reason to think that it will now.  If you want to try, make sure to backup /usr/bin/compiz before you go in and change it, and shut down all your programs before you test in case you have to manually power-off.  (You might also want to make sure that you know how to restore the compiz binary via the command-line in recovery mode in case something gets borked real good.)

---

### Post by revnobody on 2010-06-01
Thank you. I took your advice and tried it....but it didn't work. Oh well guess I will live with it for now. Thanks for all the help.

---

### Post by andrewkk on 2010-06-26
> **zpletan said:**
> ```
sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz
```

Now search for the ASCII string "8086:2562" (minus quotes, of course), and change it slightly - I changed the 2 to a 3.

As soon as an update to Compiz comes through this hack will be overwritten. This is not a resolution to the problem.

---

### Post by zpletan on 2010-06-27
> **andrewkk said:**
> As soon as an update to Compiz comes through this hack will be overwritten. This is not a resolution to the problem.

You are exactly right - plan accordingly if you follow this workaround.  However, I don't have a patch to permanently fix this, and a workaround is better than nothing.

There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234)

---

### Post by andrewkk on 2010-06-28
Glad to see the bug report. Thanks!

---

### Post by CoreyB. on 2010-07-21
Thanks for the workaround zpletan!  I have a Nvidia GeForce 8400 GS 512MB PCI card, but my integrated intel gpu makes it so I can't enable compiz, but your workaround helped.  I hope we get a fix soon!

---

### Post by jwboyer on 2011-01-09
The hex edit worked for me.  

I have a geoforce 9500 and had not been able to use the Compiz graphics.  Noveau is Blacklisted and NVIDIA 260 .19.29 is installed with NVIDIA loader.  Strangely, the no drivers appear under Hardware Drivers.

---

### Post by glenn69 on 2011-03-03
This worked for me also.  Any word on a permanent fix to this?

---

### Post by sk4tec on 2011-05-17
having this exact issue but when trying to find the "8086:2562" string in the compiz "exe" nothing comes back so I can't change it.

On another note if the system is running slow (its only 2.4 Ghz Celeron with 1.25 GB RAM and this 'new' gfx Fx5200 card) is compiz going to slow it down further??

---

### Post by CoreyB. on 2011-07-15
The equivalent of this fix for 11.04 is as follows:

Start gedit using sudo by opening Terminal and executing "sudo gedit" and then typing your password.

Then in gedit, open "/etc/environment".

At the end of the file add "UNITY_FORCE_START=1" on its own line.

Then save the file and reboot your computer and make sure "Ubuntu" is selected in GDM as the desktop environment when you log back in.

---

