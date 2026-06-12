---
title: "Several Newbie Questions"
date: 2009-05-18
forum: General Help
---

### Post by Lyuokdea on 2009-05-18
Hi All,

This is the first serious linux system i've ever installed (i.e. meant to be useful as opposed to just playing around). Most things seem to be working, but I'm having a few problems I was hoping people could answer

1.) I have an onboard realtek ALC883, and I tried to follow the installation instructions given [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1045398](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1045398) . But, just as it wasn't working on that forum, it isn't working for me. I now have sound working, using the OSS drivers. However, the problem is that sound will only work for one program at a time. Right now AIM has no sound, because I'm playing music, but if I shutdown the music program, AIM will automatically regain sound.

2.) I used the onboard intel raid controller to set up a Raid 1 array on two of my hard drives (there are 5 HDs in all). However, when i used gparted to show the hard drives, it still shows both hard drives indepedently. I mounted one of them, and saved some files to it, but I'm not sure how to check to see if it is currently being mirrored over to the other hd or not.

I'm sure a few other things will come up, thanks for your help in advance,

~Lyuokdea

---

### Post by cariboo on 2009-05-18
I can't answer you sound problem, because mine has always worked out of the box.

> 2.) I used the onboard intel raid controller to set up a Raid 1 array on two of my hard drives (there are 5 HDs in all). However, when i used gparted to show the hard drives, it still shows both hard drives indepedently. I mounted one of them, and saved some files to it, but I'm not sure how to check to see if it is currently being mirrored over to the other hd or not.

Have a look at the [FakeRaid Howto]("http://help.ubuntu.com/community/FakeRaidHowto")

I've used it several times with great success, mind you that was with an nvidia chip set, but it should work with any onbaord raid chipset.

---

### Post by Lyuokdea on 2009-05-18
One other question I remembered:

3.) How do you turn off the system beep when you are hitting delete and there's nothing to delete, or you try to tab to an invalid option in the terminal? It's kind of annoying.

Also, on the fakeraid issue, I'm not sure if my motherboard actually has fake hardware raid, it is a server mobo and is using the ICH10R Intel Raid Controller, maybe this product still works, but I want to check.

Thanks,

~Lyuokdea

---

### Post by dhughes on 2009-05-18
> **Lyuokdea said:**
> One other question I remembered:

3.) How do you turn off the system beep when you are hitting delete and there's nothing to delete, or you try to tab to an invalid option in the terminal? It's kind of annoying.

Also, on the fakeraid issue, I'm not sure if my motherboard actually has fake hardware raid, it is a server mobo and is using the ICH10R Intel Raid Controller, maybe this product still works, but I want to check.

Thanks,

~Lyuokdea

System>Preferences>Sound>then uncheck "Play Alert Sound"

---

### Post by Lyuokdea on 2009-05-18
thanks, dhughes

~Lyuokdea

---

