---
title: "Useful Info for ppl w/ intel 965 x3100"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by unoodles on 2008-01-21
Ok most of you have probably heard how to unblacklist your video card.

I have a method that is faster and (for me) more stable. It is very simple,

1. sudo apt-get install xserver-xgl .
2. Ctrl+Alt+Backspace .
3. remove SKIP_CHECKS from ~/.config/compiz/compiz-manager OR /etc/xdg/compiz/compiz-manager (only if you added it)
4. enable compiz in System->Preferences->Appearences->Visual Effects.

And thats it!

* note: video playback will have issues.

---

### Post by Jfrench on 2008-01-21
I have just ordered a new laptop with the x3100 intel chip. Thanks for the info, as I was looking if I would encounter any issues, this will be the first time I own a laptop with an Intel graphics chip.

I do believe there is a way to fix video playback after this is done, I read it earlier this evening and can not find it again. If anyone has an idea...

Thanks again.

---

### Post by Levan666 on 2008-02-12
ahh! i love you so much. thats so easy and it works. =) appreciate it alot. thanks again:):):):)

---

### Post by stlcoptony on 2008-02-12
I have found a way that I thought would allow us to enable it and play video [HERE]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61"). It involves upgrading the kernel I believe, to the hardy version, which apparently fixes the blacklisting problems (see [HERE]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/173471")). However, after updating, I tried to go to youtube and watch video but the flash player would not install. Good luck on fixing this everyone

tony

EDIT: I originally tried this with 64-bit version, I will try again with the 32-bit version soon

---

### Post by stlcoptony on 2008-02-12
Ok, I can't seem to find it now, but I have also seen other launchpad bug reports for the new Hardy 8.04 with several people saying that compiz may not even run well with hardy. I really hope everyone with this intel graphics chip isn't just out of luck for a year or so. 

As an aside, I wonder if it is possible/likely that we could install the nvidia graphics card ourselves.........

tony

---

### Post by kmb`` on 2008-05-23
nice :) thanks alot man!!

---

