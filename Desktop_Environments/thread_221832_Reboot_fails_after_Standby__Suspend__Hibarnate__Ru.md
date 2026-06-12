---
title: "Reboot fails after Standby / Suspend / Hibarnate / Ruhezustand"
date: 2006-07-24
forum: Desktop Environments
---

### Post by hannsn on 2006-07-24
I recently wanted to try out the standby (or suspend to RAM or whatever you want to call that) mode that is shipped with Dapper Drake. My screen went blank, then turned off, then on again. There was only a white underscore in the top right corner of the screen and the pc didn't turn off. I'm kind  of used to that since my pc usually has problems turning off itself (sometimes it works, sometimes not). So I turned it off manually by pressing the power button for a few seconds.
When I wanted to turn it on again the next morning my pc bootet until the USB controllers were initialized correctly and then stopped. That is short after I'm told to press "del" to enter the BIOS or press F8 for the Boot Selection Popup menu (my motherboard is an Asus P5GD2-Deluxe with an Amibios Revision 1008). When I press "del" (or "F8") it tells me that the BIOS setup (or the boot menu) is being started but nothing happens. The pc just idles, it's not frozen though.
OK, just to be a little more clear, here is a short summary of what my screens prints:


AMIBIOS(C) 2005 American Megatrends, Inc.
"Mainboard type"
"CPU type"
"CPU Speed"

Hit "del" to enter BIOS
Hit F8 to enter BBS Popup
"RAM type"
NVRAM is being checked ..
Initializing USB Controllers .. Done.


OK I hope I made my problem clear. I hadd to translate some of the screen output a little roughly from german but I think the important part is being said.

Does anyone have any idea what happened to my pc and, more importantly, how I can boot it up again?
Thanks in advance.


OK I'm sorry I posted so quickly. It turned out that that standby isn't a suspend-to-disc (what I thought it was because it said that it would need NO power) but a suspend-to-RAM and I could therefor easily reset it by unplugging the powerplug from my pc.

---

