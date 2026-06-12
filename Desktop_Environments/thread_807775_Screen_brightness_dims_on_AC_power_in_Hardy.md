---
title: "Screen brightness dims on A/C power in Hardy"
date: 2008-05-26
forum: Desktop Environments
---

### Post by tedrogers on 2008-05-26
Hi,

Running Hardy and an IBM T42.

My problem is not when I go onto battery power, this works fine and the screen dims to 70%. The problem I have is going back onto mains power where the screen dims to about 30% and the OSD shows that I am on the lowest possible setting. 

The brigtness OSD is also unresponsive to the thinkpad buttons, i.e. slow to display the icon on the screen although the brightness does change instantly.

Never come across this before.

All my ACPI related setting in gconf-editor for gnome-power-manager are fine as far as I can tell.

I have reinstalled acpi-support as well and the problem still exists.

Hope this annoying bug will be fixed in an update. It taints the most excellent release of ubuntu yet and would be a real niggly annoyance for newbies.

---

### Post by MedellinManDem on 2008-05-26
Whenever I set my screen to "dim when idle" it does so, but a) sometimes doesn't respond to the touchpad and b) always never returns to full brightness. 

Is it the settings, or is it a bug? I had no problems with Gutsy.

---

### Post by tedrogers on 2008-05-26
This sounds like a bug to me friend.

I didn't have a problem with gutsy either.

I have also noticed that the Fn + Brightness UP button doesn't work when on full brightness, i.e. it should at least make the OSD come on the screen.

Yet, the Fn + Brightness DOWN button makes the brightness go from 100% to 30% in one big jump!!

Hopefully this extra information will help someone fix it.

---

### Post by Beatbreaker on 2008-05-26
> **tedrogers said:**
> This sounds like a bug to me friend.

I didn't have a problem with gutsy either.

I have also noticed that the Fn + Brightness UP button doesn't work when on full brightness, i.e. it should at least make the OSD come on the screen.

Yet, the Fn + Brightness DOWN button makes the brightness go from 100% to 30% in one big jump!!

Hopefully this extra information will help someone fix it.

Same here, I'm on a Dell, the Function key plus UP and DOWN go in large jumps, from full, to half way, to minimal, nothing inbetween.

---

### Post by tedrogers on 2008-05-27
Well I'm glad it's not just me then!

Now all we need is a fix.

Nothing I do seems to make it work *better* or as it should.

---

### Post by realthor on 2008-05-27
Hi,

Same issue here with some more explanations :

[http://ubuntuforums.org/showthread.php?t=805995]("http://ubuntuforums.org/showthread.php?t=805995")

---

### Post by tedrogers on 2008-05-28
The latest batch of updates on 27/05/08 didn't fix this for me...but didn't notice if there was anything related to ACPI, power manager etc.

---

### Post by tedrogers on 2008-06-03
More updates on 2nd and 3rd of June but nothing relating to ACPI, although there were some gnome-panel updates (probably not related) - problem still exists.

New info:

It seems things have changed a little.

From a fresh boot on a/c power, the Fn + Brightness DOWN button works progressively as it should - even the OSD responds properly. However, on the way back up again with Fn + Brightness UP, the brightness does change but the OSD stays on its lowest level and shows this on screen, i.e. no change to OSD although brightness does go up. This is when it totally breaks and on the way back down again it goes in one big jump from 100% to 30%, and on the way back up  the brightness does change but the OSD stays on its lowest level and shows this on screen, i.e. no change to OSD although brightness does go up. This behaviour is then repeated forever.

On a/c power, the brightness momentarily goes onto full, but then 1 second late goes to 30% and the OSD displays showing this. Fn + brightness UP is progressive, the OSD shows but does not change to reflect changes in brightness, and Fn + brightness DOWN happens in one big jump (again the OSD shows but does not change its own display to reflect the level of brightness).

Still no idea why.

Anyone?

---

### Post by tedrogers on 2008-06-04
Just installed new updates today including linux-image-2.6.24-18-generic, and it makes no difference.

Was hopeful this was a fix, but sadly no. :(

---

### Post by tedrogers on 2008-06-05
More updates...still borked!

---

### Post by srt4lifez on 2008-06-27
> **tedrogers said:**
> More updates...still borked!

any updates to this???

found a bug report for this... #222796

last comment was...

Hi,
I think I have at least found a workaround (after someone else pushed me in the right direction): if you do

sudo su
echo enable,0xffffff > /proc/acpi/ibm/hotkey

both buttons generate acpi events and show the OSD.
But now: how to make it permanent?

this works, however as said its not permanent...


another problem im having is when i unplug the powercord the brightness will drop down like normal, when i replug the power the brightness will not go all the way up. Ill unplug the power again the brightness will drop, replug it and the brightness will still not go all the way back up but rather probably another 15% lower than the previous time i plugged the powercord back in...repeat this process and it will drop ~15% everytime until it cant get any lower ... any ideas???

---

### Post by Papi-KB7VGW on 2008-06-30
I had this issue 30% brightness on AC and found that my Bios had somehow been changed.  I set it back to 100% and haven't had a problem since.  Check your Bios.

---

### Post by tedrogers on 2008-07-02
Set BIOS on battery to max. brightness....makes no difference once Ubuntu is booted.

:(

---

### Post by ed_x on 2008-07-09
That works just fine! Simply add

echo enable,0xffffff > /proc/acpi/ibm/hotkey

to /etc/rc.local (before the 'exit 0')

Thanks!

---

### Post by Amstell on 2008-10-28
> **tedrogers said:**
> Set BIOS on battery to max. brightness....makes no difference once Ubuntu is booted.

:(
Thank you.  I just went into my BIOS and adjusted it accordingly.  Hopefully this fix will happen soon.  It sucks not having a dim display when idle.

---

### Post by realthor on 2008-11-11
Hi,

It seems that the issue is present also with Intrepid Ibex. While booting, the screen brightness goes dim 100% and after user/password are provided, while gnome-panel&stuff loads, it jumps at about 85% (one step from 100%). Then I press Fn+Home to get it 100% but as this is its known max brightness it fades back to 85% when on battery power even if i have set up the power manager to not dim on battery.

I didn't try the:

"echo enable,0xffffff > /proc/acpi/ibm/hotkey

to /etc/rc.local (before the 'exit 0')"

yet on 8.10 but i'll give it a try soon.

Anyone else with this issue in Ibex?

---

