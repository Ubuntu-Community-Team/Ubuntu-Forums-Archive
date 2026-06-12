---
title: "No Youtube video after Flash update"
date: 2009-02-28
forum: General Help
---

### Post by iheartubuntu on 2009-02-28
The other day there was a flash plugin update. Ive done it on all of my computers with no problems, but my dads Ubuntu system no longer shows Youtube videos. Any ideas? Flash appears to be working fine on all other websites. Thanks for any suggestions. Ive tried rebooting, reinstalling flash, etc

---

### Post by iheartubuntu on 2009-02-28
This might also be Firefox related somehow as youtube videos work fine in Opera.

Still, in Firefox I am able to go to other video sites like JustinTV and watch videos without a problem.

---

### Post by shane8002 on 2009-02-28
make sure you got java installed and turned on

---

### Post by iheartubuntu on 2009-03-01
> **shane8002 said:**
> make sure you got java installed and turned on

It is on and working fine on other websites that have video. Just youtube videos do not work.

---

### Post by kadogo05 on 2009-03-08
I'm also having the same problem with my ubuntu, i can watch some video on veoh, but i can't watch some of them. on youtube i can't watch anything at all. i have also try to remove, the reinstall the flash plugins. as stated in other threads on the websites

---

### Post by iheartubuntu on 2009-03-17
BUMP - My dad has done all his updates as usual and still no video for him in Youtube using Firefox. It does work fine for him in Opera though.

Would anyone have any recommendations? Maybe completely removing Firefox, then reinstalling it? I dont want to touch things just yet :) hoping for someone might know whats wrong. Flash videos in Firefox do work on other websites, just not Youtube videos. Is there something I can reset in Firefox related to Youtube perhaps?

---

### Post by iheartubuntu on 2009-03-18
Bump? Any tips would be much appreciated! Thanks!

---

### Post by LowSky on 2009-03-18
I would reinstall the firefox plugin, or delete the /.mozilla profile in your /home folder

---

### Post by WildeBeest on 2009-03-18
Flash works fine for me in Firefox, but not with Opera.

Not sure if it's a 64-bit issue.

---

### Post by LowSky on 2009-03-18
flash is working for me... running 9.04 though so, maybe Im not someone to trust... my system could break at anyitme...lol

---

### Post by Botbob89 on 2009-03-18
I wouldn't think it's a 64 - bit issues, in both your cases I would say it is problems with the browsers, not with flash or java...as long as both are turned on of course....

Try a reinstall of your respective browsers...

---

### Post by WildeBeest on 2009-03-18
Tried that.

Here's a thread of the things I've tried.

[http://ubuntuforums.org/showthread.php?t=1081964]("http://ubuntuforums.org/showthread.php?t=1081964")

---

### Post by iheartubuntu on 2009-03-18
In my case its a 32 bit system.

---

### Post by iheartubuntu on 2009-03-20
Would love to get my dads Youtube working in Firefox again... any ideas what I can try? I will try completely reinstalling it right now and go from there.

---

### Post by Ze MoreiRa on 2009-03-20
is there white background, or it freezes the browser? 

try this
[http://ubuntuforums.org/showthread.php?t=891458&page=3](http://ubuntuforums.org/showthread.php?t=891458&page=3)
or shorter way 
> wget [http://queleimporta.com/downloads/flash10RC_en2.sh](http://queleimporta.com/downloads/flash10RC_en2.sh) && sudo chmod +x flash10RC_en2.sh && sudo sh ./flash10RC_en2.sh

---

### Post by iheartubuntu on 2009-03-22
For me the problem is solved, but it looks like what others here are experiencing is a different problem than what i had.

So I was going to use the tips here to fix my dads computer and get his youtube working again. I decided to check his Firefox "add-ons" because he had some weird add-ons I had never seen before. Stuff to handle PDF files differently, to download files differently... I disabled those and found yet another add-on that was recently installed. I forget the name offhand but it was an adblocker. "Adblock Plus" possibly. Anyways, it was blocking youtube videos!

---

