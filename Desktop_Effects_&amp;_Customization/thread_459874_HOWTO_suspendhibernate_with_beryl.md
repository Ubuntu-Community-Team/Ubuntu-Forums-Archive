---
title: "HOWTO suspend/hibernate with beryl"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by fmaste on 2007-05-31
It work for me on my DELL inspiron 9400 (E1705) notebook

I use to have beryl on edgy but I loose suspend and hibernate (which I use a lot). I tried with the scripts to kill beryl when suspending/hibernating, but it didn't work or I had to reopen beryl manually but it was uncomfortable. Not having this feature in a transparent way is like having nothing for me, so I never installed beryl on feisty until today. I like beryl a lot, so I decided to give it another chance with what I found googling.

NOTE: I'm using feisty with beryl installed from the beryl repos, all the other setting are the default ones (I never manually edit xorg.conf or acpi-support and beryl setting were are the default ones) and suspend/hibernate was working out of the box without beryl.

- Disable "Sync To VBlank" in beryl.
It is located on general options of the veryl manager. Just unckeck it.

- Update your /etc/X11/xorg.conf and add an  "Option "NvAGP" "1"  line in the  "Section "Device":
(must look like this)
	Section "Device"
        	...
        	Option          "NvAGP"       "1"
	EndSection

- Disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :
	# Should we attempt to warm-boot the video hardware on resume?
	POST_VIDEO=false

Good luck!!

---

### Post by syko21 on 2007-06-03
the NvAGP option broke my xorg but reinstalling my driver manually fixed that, most likely because my card is pci-express. The Vblank option and POST_VIDEO options worked beautifully though and my suspend works seamlessly with beryl. I can't hibernate but then again I've never been able to with this laptop so no biggie. Thanks for the tips.

---

### Post by Ricket on 2007-07-06
Just wanted to let everyone know, this works in Compiz Fusion as well!!

I have an E1705, I have been trying things throughout the whole day today to get this to work, and finally disabling the "Sync to VBlank" worked for me too! Compiz Fusion is the recombining of Beryl features into the Compiz framework, and the CompizConfig Settings Manager has almost the exact same options as Beryl (plus some extras) so the option was named the exact same, in the General Options section.

I can now standby and resume with more than just a blank screen! I haven't tried hibernate yet, but I am just ecstatic about the standby issue! That narrows down my to-do list for fixing Ubuntu to 2 more things! (install my firefox extensions, and fix a problem where Ubuntu screws up the clock in my Vista partition) I use standby all the time so this was a major thing - THANK YOU SO VERY MUCH!!!

Oh, one more thing, I did not have to enable the NvAGP. I refuse to do that because my card is a PCI Express (well, sorta integrated PCI-E - this is a laptop with Nvidia Geforce Go 7900GS) and also I read that it slows things down and can cause problems. Just the Sync disable and the POST_VIDEO=false trick worked!

I hope this thread goes up in Google search results. It was tough for me to find this thread, and in fact if this were not an E1705 laptop I would not have found it at all, and maybe I would have gotten fed up with Ubuntu and reformatted...

~Ricket

[EDIT]
Well after a bit of experimentation I found out that I can only standby once... I am trying a combination of the procedure and I will report back here when I figure out exactly how to solve this problem. However, the first time I standby (after turning on the computer), it works fine - everything turns off and the power light pulsates, exactly as Windows does when it is in standby. Then, something that Windows doesn't do, when I open my laptop lid again (after closing it, of course), it automatically turns the computer on for me! I thought this was totally neat, and I will be looking for a way to do it in Windows. Anyway, this first time, it turns on fine, asks me for my password to unlock the computer and I'm right back where I was.

However, when I go into standby/suspend a second time, it turns off exactly the same way, just fine, and the light pulsates, and I close the lid. When I open it again, I have experienced two different things. Either 1) the power light comes back on to solid but nothing responds (num lock light stays dark, wi-fi and bluetooth lights also stay off, nothing makes a sound) or really odd, 2) the computer starts up as if it had been turned off - the bios loads, and then GRUB (the bootloader) waits a few seconds as usual, and the Ubuntu boots.

Either way is undesirable. I need it to be able to resume EVERY time. I use standby because I don't like waiting for the computer to turn off and on. It's a feature that is absolutely necessary for me, and I WILL get it working in Ubuntu, or I will go back to 100% Windows. I have taken a liking to the Compiz Fusion interface, but without standby the computer just isn't nearly as functional to me, since it is a laptop and I can't (won't) just leave it on all the time.

So yeah. I'll report back when (if) I get it working.
[/EDIT]

---

