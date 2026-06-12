---
title: "Help with SCIM/Anthy"
date: 2009-05-08
forum: General Help
---

### Post by brandon88tube on 2009-05-08
I'm using Ubuntu 9.04 and I cannot get SCIM/Anthy to work for the life of me. I'm trying to get Japanese to work, but SCIM won't even show up in the panel even if I tell it to always show. None of the keyboard shortcuts work and I can't change languages. I had no problem setting this up in 8.10, but in 9.04 this doesn't seem to work at all.

---

### Post by Snydar on 2009-05-08
I am having the same problem. Although, I got it working in Jaunty 2 days ago... all was well. I just told SCIM to always show the tool bar, then the hotkeys worked fine. But eventually I installed chinese/korean input so I could see text some of my friends wrote on facebook... then my fonts for Japanese were changed from the default and it looked very ugly.

So, I reformatted and reinstalled Jaunty... and now am trying to install Japanese input again, and cannot get it to work unless I change the langauge to Japanese when I log in. (which changes everything into Japanese, which I don't want.)

I really need to install Japanese input with Anthy. I use it daily, and do not want to boot into a Japanese login to do so. I've read many posts, and people claim after a couple reboots, it magically works... but not the case for me. I've spent 5 hours trying to tweak things, rebooting between each possible thing I can think of, and to no avail.

---

### Post by brandon88tube on 2009-05-08
Yeah, its not working for me either. Have yet to get it to work in 9.04 and I don't know why.

---

### Post by Snydar on 2009-05-08
Got it fixed! Type this in terminal and log out and back in and all should be well. (Hopefully...)

```
im-switch -s scim
```

Thanks to hugstrees for the fix.

---

### Post by brandon88tube on 2009-05-09
Didn't work for me and made everything I tried to open crash on me. I decided to give up for now.

---

### Post by jezebel on 2009-10-06
> **Snydar said:**
> Got it fixed! Type this in terminal and log out and back in and all should be well. (Hopefully...)

```
im-switch -s scim
```


Snyder - thank you!! This worked for me (the glitch has been bugging me for friggin months!).

edit: Update. I am still thrilled that this is working. But, I noticed that when my Japanese anthy is activated, then Fire Fox won't launch. If the English/Other is set, then FF launches just fine. I can then switch between input languages without a problem, even in FF.

Small price to pay- I can't work in an OS without the Japanese input!

---

### Post by Snydar on 2009-10-10
Yeah, I have the same problem launching firefox with anthy set to Japanese as well. At least that is a minor nuisance.

---

### Post by guriinii on 2009-10-27
&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;Cheers

---

### Post by midwayplane on 2009-11-15
&#20170;&#26085;&#26412;&#35486;&#12434;&#26360;&#12369;&#12414;&#12377;&#65281;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;

---

### Post by vadarfone on 2010-02-11
I too am having trouble getting this to work.

I have it working on my IBM Thinkpad laptops, but I can not get it working on my Sharp Mebius...  My Sharp is actually a Japanese laptop (bought in Japan, Japanese keyboard, etc) as are my Thinkpads, but for some reason the SCIM is not working on the Sharp.

I have installed the SCIM, went through the repository and installed all the SCIM stuff there, but just can't seem to get it working.  

Any ideas?

---

