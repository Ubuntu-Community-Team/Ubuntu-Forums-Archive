---
title: "Broadcom WLAN HowTo fix?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by rogdef on 2006-03-09
Hello all,

I just put Breezy on my emachines laptop and the only problem I'm having is it's not recognizing my Broadcom wireless card. I did the HowTo from an earlier post with this problem, but the conversations got kinda confusing and fix did not work.

Can someone please post a link on the official and correct way to install a Broadcom wireless card in Breezy?

Thank you so much!

---

### Post by daWabbit on 2006-03-09
What chipset does that card use? I think it might be one of the pesky TI sets related to the AC series. If that's so, you can make it work, but the best thing to do is to get another card. Seeing as I've been seeing Cardbus G wireless cards fully supported in Linux for about $11 US lately, that's the easy way out. Else let us know what the chipset is and we'll take it from there.

Jack

---

### Post by rogdef on 2006-03-09
How do I check the chipset?

---

### Post by daWabbit on 2006-03-09
You can try the Broadcom site. And if you give me the full name as it was shown in the Windows device manager, I'll look too.

Jack

---

### Post by rogdef on 2006-03-09
It's the BCM4306. Is that what you needed? Thanks.

---

### Post by daWabbit on 2006-03-09
Yeah. That's it. I'll look at some HCL lists.]

Jack

---

### Post by daWabbit on 2006-03-09
Your wireless is not supported well enough to count for anything, as far as I can see. My wife's laptop is a Compaq and the Broadcom wireless in it is not supported. 
 
You can either wait for support or get a supported card to plug into the Cardbus slot. There are also USB dongles that will do it, but in my limited experience they've been a pain. 

Pick a card up for it. Remember to either take a list of supported cards and chipsets with you or check out the card before you buy. Though folks have finally written drivers for cards with the TI ACX100 and related chipsets, I urge you to avoid them. I have two such cards and while we got them working, it was hard and performance is not even up to B standards, by a long shot. Plus, they suffer random disconnects. 

Hope that helped. Sorry to be the bearer of bad tidings.

Jack

---

### Post by daWabbit on 2006-03-09
My wife just told me I was out of date and that the TI ACX 100 & 110 chipsets from TI were now supported. To prove it, she put a card using that chipset (a USR brand one) and ran the live CD. Worked just fine. She then revealed that her Breezy install on her lappie is using another card based on that chipset because she was having problems with the NetGear card I had gotten her. 

So, I stand corrected. Sorry.

Jack

---

### Post by rogdef on 2006-03-10
Thanks for all your help, Jack. But isn't the following howto supposed to solve my problem:

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

Some people have had luck with it, but not me. Perhaps I'm missing something.

---

### Post by byen on 2006-03-10
Hey rogdef, welcome to Ubuntu.
I have a Compaq Presario and have a Broadcom 43XX chipset. Pretty damn close to yours. Though your card would not work outside the box..you will however be able to use ndiswrapper to get it to work.
Here is a [how-to thread ]("http://www.ubuntuforums.org/showthread.php?t=25683") (written for hoary but works on breezy too...trust me) that has helped me when I knew squat about linux! I have suggested the same to many users and it seemed to have worked.
Note:I suggest you read the first couple of pages to get a grasp of what is goin on!

Goodluck! Hope it helps!

---

### Post by daWabbit on 2006-03-10
Using that how-to, we just got the Broadcom in two lappies working, but not in my wife's Compaq Pressario r3120us. 

Thanks,
Jack

---

### Post by rogdef on 2006-03-10
I've tried that how-to 4 times already and nothing has changed. Well, I guess it's time to buy a Linux-supported card.

---

