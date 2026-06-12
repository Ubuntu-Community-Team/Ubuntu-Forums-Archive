---
title: "The K8N / nForce3 / fglrx / MESA thread: technical help needed!"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Chonnawonga on 2007-10-22
This thread is for people who have a K8N-family motherboard with the nForce3 chipset, as well as an ATI video card who are consistently getting the infamous "MESA" return to the "fglrxinfo" command.

The problem is that there is an incompatibility between the nForce3 chipset and the ATI graphics cards (or drivers... I'm not sure which).

I must stress that I am **not** a programmer or otherwise all that capable with Linux. I'm just getting handy with the forums over time.

There seem to be a few workarounds to this problem, but none of them are pretty.

1. If you have the K8N-E motherboard, you are luckier than I. You can download the _beta_ version 1012 BIOS from ASUS [here]("http://support.asus.com/download/Download.aspx?SLanguage=en-us") and you're on your way. You lucky #%$*&.

2. You can DOWNGRADE your BIOS for one of the other motherboards in the family to version 1006, also available [here]("http://support.asus.com/download/Download.aspx?SLanguage=en-us"). Be aware that this is VERY RISKY. I, and at least one other person (post #5 on [this]("http://ubuntuforums.org/showthread.php?t=235259&highlight=k8n+mesa") thread) had the result that although we now have the fglrx driver working probably, our flash chips are shot, we get an error message on startup, and we can no longer flash our BIOSes. This is bad. Others have reported complete success, but attempt this at your own risk!

3. You can boot into Windows (if you have dual boot) and then reboot into Ubuntu. I found out about this from post #6 [here]("http://ubuntuforums.org/showthread.php?t=143855&highlight=k8n+mesa"). I HAVE NO IDEA WHY THIS WORKS! I tried it before I destroyed my BIOS, though, and it worked.

4. I have no idea if this works or not, because I didn't think to try it until AFTER I blew up my flash chip. What about installing nForce3 drivers? Has anyone tried this? Does it even make sense? I have no idea.


So, that's what I have so far. Solution #3 suggests to me that there may be a better solution to this problem if someone with a much better knowledge of the technicalities than I have is brought in to address the problem. Is there somewhere we can file a bug report? I don't even understand where the problem lies.

---

### Post by alanrr_sr on 2008-01-15
> **Chonnawonga said:**
> This thread is for people who have a K8N-family motherboard with the nForce3 chipset, as well as an ATI video card who are consistently getting the infamous "MESA" return to the "fglrxinfo" command.

The problem is that there is an incompatibility between the nForce3 chipset and the ATI graphics cards (or drivers... I'm not sure which).

I must stress that I am **not** a programmer or otherwise all that capable with Linux. I'm just getting handy with the forums over time.

There seem to be a few workarounds to this problem, but none of them are pretty.

1. If you have the K8N-E motherboard, you are luckier than I. You can download the _beta_ version 1012 BIOS from ASUS [here]("http://support.asus.com/download/Download.aspx?SLanguage=en-us") and you're on your way. You lucky #%$*&.

2. You can DOWNGRADE your BIOS for one of the other motherboards in the family to version 1006, also available [here]("http://support.asus.com/download/Download.aspx?SLanguage=en-us"). Be aware that this is VERY RISKY. I, and at least one other person (post #5 on [this]("http://ubuntuforums.org/showthread.php?t=235259&highlight=k8n+mesa") thread) had the result that although we now have the fglrx driver working probably, our flash chips are shot, we get an error message on startup, and we can no longer flash our BIOSes. This is bad. Others have reported complete success, but attempt this at your own risk!

3. You can boot into Windows (if you have dual boot) and then reboot into Ubuntu. I found out about this from post #6 [here]("http://ubuntuforums.org/showthread.php?t=143855&highlight=k8n+mesa"). I HAVE NO IDEA WHY THIS WORKS! I tried it before I destroyed my BIOS, though, and it worked.

4. I have no idea if this works or not, because I didn't think to try it until AFTER I blew up my flash chip. What about installing nForce3 drivers? Has anyone tried this? Does it even make sense? I have no idea.


So, that's what I have so far. Solution #3 suggests to me that there may be a better solution to this problem if someone with a much better knowledge of the technicalities than I have is brought in to address the problem. Is there somewhere we can file a bug report? I don't even understand where the problem lies.


Hy,

I am one of the unlucky people that acquired a motherboard, asus k8n, and can not get my 9600XT working too.
This is a problem about something setting a wrong agp aperture on "cold boot", and linux (kernel) relies on this wrong value, getting nothing more than problems.....
There is already a bug report in linux kernel [http://bugzilla.kernel.org/show_bug.cgi?id=6350](http://bugzilla.kernel.org/show_bug.cgi?id=6350), but as you can see, it looks like "abandoned".

Now, We can be sorry for everyone that got this motherboard with a ati card... maybe in next hardware  upgrade, we could have more lucky.


Note: I am not saying this is linux fault....](*,)

---

