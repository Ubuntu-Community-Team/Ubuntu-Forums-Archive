---
title: "[SOLVED] OMG PuRpLe pOnIeS 'bold' font issue"
date: 2008-08-05
forum: Forum Feedback &amp; Help
---

### Post by mips on 2008-08-05
Just some feedback on the bold font issue I was experiencing ([http://ubuntuforums.org/showthread.php?t=873787](http://ubuntuforums.org/showthread.php?t=873787)).

This occurs when setting font sizes bigger than a certain value. These values differ between Firexox3  & Konqueror4.1.

In Firefox3 setting the "Minimum font size:" bigger than 15 will result in fonts that 'look' bold.
In Konqueror4.1 setting the "Minimum font sze:" bigger than 11 will result in fonts that 'look' bold.

The font I'm using is Bitstream Vera Sans

However, this only happens in the OMG PuRpLe pOnIeS sub forum and nowhere else on the forums.

Could someone possibly veryfy this for me on their browsers please.
Is there a posibility that that there is a slight difference in the forum code realating to fonts?

This is not a big issue for me but one of those things that will keep me racking my brain as to why it happens.

---

### Post by matthew on 2008-08-05
Huh. This is really odd. I can't reproduce it at all.

---

### Post by mips on 2008-08-05
I just tried it on my laptop and I get the same results with:
Konqueror4.1 & Bitstream Vera Sans fonts
Firefox 3 & Default Serif fonts

Force font DPI is also disabled in my global font settings.

I use Arch 32&64 linux btw but I don't see how that would influence fonts unless it has a weird xorg.conf?

---

### Post by Elfy on 2008-08-05
I can see a change if I alternate between "Allow page to choose fonts" on the advanced tab - does this represent what you are seeing.

---

### Post by mips on 2008-08-05
> **forestpixie said:**
> I can see a change if I alternate between "Allow page to choose fonts" on the advanced tab - does this represent what you are seeing.

Nope. Both those look bold to me but the one just looks 'degraded'

Will post a screenshot in next 10min.

---

### Post by mips on 2008-08-05
Communtiy Council size 15 font:
[[IMG]http://img360.imageshack.us/img360/8716/cc15cw3.th.png[/IMG]]("http://img360.imageshack.us/my.php?image=cc15cw3.png")

Community Council size 16 font:
[[IMG]http://img170.imageshack.us/img170/9081/cc16mr4.th.png[/IMG]]("http://img170.imageshack.us/my.php?image=cc16mr4.png")

Purple Ponies size 15 font:
[[IMG]http://img357.imageshack.us/img357/2140/pp15mx0.th.png[/IMG]]("http://img357.imageshack.us/my.php?image=pp15mx0.png")

Purple Ponies size 16 font:
[[IMG]http://img374.imageshack.us/img374/4204/pp16wp6.th.png[/IMG]]("http://img374.imageshack.us/my.php?image=pp16wp6.png")

Sorry was going to post side by side windows with different font settings but realised that it is not possible to change the fonts on a per window basis so I just kep the second window open.

Notice how the font in the community council stays the same even though the sizes is increase, the same however does not seem to be happening in the purple ponies?

---

### Post by Elfy on 2008-08-05
Yes I can see that difference here as well. No idea why though I'm afraid.

---

### Post by matthew on 2008-08-05
This is incredibly weird.

I have one idea, but I'm having a hard time convincing myself it could be the culprit. The css definitions for text in the forums at large and in OPP are different (hence the differing colors). I can look, but maybe the preferred font lists are different as well. It's a longshot, but I suppose it could have an effect on this. Otherwise, I'm at a loss.

EDIT: I have adjusted the font face lists to be the same as the forums at large. Let me know if that makes any difference.

---

### Post by mips on 2008-08-05
> When you have eliminated all which is impossible, then whatever remains, however improbable, must be the truth. - Sherlock Holmes ;)

Matthew, thanks, you hit the nail on the head!!!

It is working 100% fine now, screenshot linked for reference.

[[IMG]http://img253.imageshack.us/img253/1431/ppfixedkm1.th.png[/IMG]](http://img253.imageshack.us/my.php?image=ppfixedkm1.png)

Thanks again, tonight I can rest peacefully :)

---

### Post by matthew on 2008-08-05
Woo hoo!

---

