---
title: "Monitor unsupported?"
date: 2009-02-22
forum: General Help
---

### Post by xXxBlender3DxXx on 2009-02-22
I am in a huge mess.

My monitor isn't working with [COLOR="DarkOrange"]32-bit Ubuntu[/COLOR]!

I had [COLOR="DarkOrange"]64-bit Ubuntu[/COLOR], but there was [COLOR="DarkOrange"]no wireless card driver[/COLOR] compatible with [COLOR="DarkOrange"]64-bit Ubuntu[/COLOR]. So I downgraded to [COLOR="DarkOrange"]32-bit Ubuntu[/COLOR].

Now, every time I turn on my computer and boot into [COLOR="DarkOrange"]Ubuntu 8.10[/COLOR], my monitor says "[COLOR="DarkOrange"]VGA mode unsupported[/COLOR]" and goes blank. I reset the monitor, and the [COLOR="DarkOrange"]Ubuntu[/COLOR] logo and boot screen stays on the screen for like [COLOR="DarkOrange"]30 minutes[/COLOR] before my monitor turns off completely. Then to make it work again, I have to restart my computer and boot into Windows XP.

My screen resolution on [COLOR="DarkOrange"]64-bit Ubuntu[/COLOR] was [COLOR="DarkOrange"]1280 x 1024[/COLOR] and refresh rate was [COLOR="DarkOrange"]75[/COLOR].
Now, (when I was installing Ubuntu, it oddly worked for the duration of the installation) the resolution is [COLOR="DarkOrange"]600 x 800[/COLOR] and my screen is shifted to the left like [COLOR="DarkOrange"]30 pixels[/COLOR]. I can's see part of my screen when the monitor did work!

Any help?

(I know this is a lot to ask for)

Thanks in advance!
(I will provide any additional info if needed!)

---

### Post by kmac on 2009-02-22
> **xXxBlender3DxXx said:**
> I reset it, and the Ubuntu logo and boot screen stays on the screen for like...

Reset the computer or the monitor? 

At any rate, which version of Ubuntu are you running?

---

### Post by xXxBlender3DxXx on 2009-02-22
I reset the monitor (lol, I unplug it, wait 2 minutes, then plug it back in).

I am running Ubuntu (Intrepid Ibex or something like that) 32-bit 8.10. Installed today.

---

### Post by kyphi on 2009-02-22
What is important here is knowing what kind of monitor you have, LCD or CRT and also what kind of graphics card is installed.

I assume that you have a CRT monitor since LCD monitors do not have a refresh rate as such but rather a "response time".

Since your monitor displays correctly at 800x600 with a refresh rate of 75 Hz but does not display at 1280x1024, I suggest that you adjust this.  Try an adjustment to 70 Hz and then to 60 Hz.

Screen shifting to the left or right is controlled by a monitor adjustment.

---

### Post by xXxBlender3DxXx on 2009-02-22
I don't know how to distinguish my monitor type. It's flat, but that's about it. My main issue is that I cannot get my internet running. My wireless card isn't installing.

I copied the Windows drivers (.sys files, and .inf), but the computer just won't see it!

Other than that, nobody will help me... :(

EDIT: (My monitor is DEFINATELY an LCD, no Mr. Bulky for me!)

---

### Post by perlluver on 2009-02-22
Have you installed the drivers for your video card?  System>Administration>Hardware Drivers.  Make sure it is enabled first, then try to set the refresh rate on the monitor.

---

### Post by xXxBlender3DxXx on 2009-02-22
My monitor works fine, but I can't download any drivers or tools since my wireless USB card for some reason doesn't install.

Any ideas why?

---

### Post by perlluver on 2009-02-22
No sorry, not to good with wireless, it is pretty hit or miss in Linux.  Also don't really use Laptops.  I hope you can get it working though.

---

### Post by xXxBlender3DxXx on 2009-02-22
Can you give me a link for a tutorial?
It's a USB stick :P

---

### Post by kyphi on 2009-02-22
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

