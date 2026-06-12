---
title: "LCD flinkers after install fglrx"
date: 2006-08-07
forum: Desktop Environments
---

### Post by shmtw on 2006-08-07
I got ubuntu 6.06 installed on my T42; everything is fine except the fglrx driver.

After I installed fglrx driver and changed the xorg.conf from "ati" driver to "fglrx". The LCD flickers and hurts my eyes. 
I have search the forum and try to change refresh rate, including modelines adjustment, but did not help. 
This may not be caused by refresh rate because sometimes the LCD does not flicker. 
I guess this is caused by driver. About two of three times I got LCD flickers when I login.

My vedio card is ATI R9600 with 64MB RAM. Any advise to resolve this issue?

---

### Post by MoToR on 2008-01-21
I'm reviving a year and a half old post describing an issue that might by this time be solved but I've failed to find any solution.

I'm having the same issue exactly and every post on this topic I found on the internet was both old and unanswered.

I have a ThinkPad T42 with SXGA+ display and Mobility Radeon 9600.

Recently I instaled ubuntu 7.10 on it and after installing fglrx using Restricted Drivers Manager (which is my only option to get full graphics card functionality AFAIK) I encountered the known brightness flicker issue.

Doesn't show on every boot, but on the majority. Sometimes I boot and there's no flicker, sometimes there is, and then it's not gone till I restart or go into stand by mode. Then it may reappear or disappear till again - reboot or stand by.

Is there a solution? Another driver? Anything except disabling fglrx?

Any info or help will be highly appreciated.

---

### Post by MoToR on 2008-05-20
**[COLOR="Red"]The flicker problem was solved for me by LCD panel replacement.[/COLOR]**

My T42 was on warranty and I went through two LCD replacements before the problem was gone - IBM guys didn't know how to solve my problem and first returned me the laptop with new LCD and invertor but the same issue - flickering was still there.

I immediately sent the laptop back to the lab and during the negotiations with different representatives I found out that the lab had panels of two manufacturers - dtech (or something) and Samsung. Of course I immediately asked for Samsung panel to be installed in my laptop and the next day I heard the good news - I've got a Samsung panel and the flicker problem was gone.

Unfortunately the panel isn't great at all - "backlight bleeding" and "lack of backlight uniformity" - these two terms were invented by people when they first looked at my LCD panel. But I must admit that the panel isn't awful either and there's no flickering. So I just forgot about it.

Just to make it clear - my negotiations with IBM technicians were based on the LCD flickering in Windows Vista, not in Ubuntu for obvious reasons.

---

