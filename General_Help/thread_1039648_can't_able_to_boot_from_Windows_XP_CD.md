---
title: "can't able to boot from Windows XP CD"
date: 2009-01-14
forum: General Help
---

### Post by eAi-T0ky0 on 2009-01-14
hey all
  Don't know what's problem really , but when I trying to boot from Windows-CD it just going to my system [ubuntu] and not booting from my windows cd , but when I try to put the [ubuntu] live cd to try if my computer will boot from it or not , it still boot to Ubuntu cd and when I put my windows cd again to trying to boot from it , it can't able to boot from Windows XP CD.

When the computer boots, I can see a menu containing ubuntu (with different kernels) and windows 

my problem is that , why I can't see the blue screen of WindowsXP when it tries to boot itself from the CD?!?!?!?

any idea please will be good!~

---

### Post by taurus on 2009-01-14
Is that the original windows CD that you are trying to boot with?  Have you tried booting the same windows CD with another machine to make sure it's not the CD?

---

### Post by grantk86 on 2009-01-14
Try pressing F12 a bunch of times as your computer starts up to force it to access the boot device menu.  From there you can select the CD drive to boot from.  I think in some machines the key to press is F10, not F12... try both.

If that doesn't work, change the boot device order in your BIOS (usually accessed by pressing F2 upon startup) so that the CD drive is listed first.

If you're still stuck, it may just be a problem with the XP CD.  Try inserting it while in Ubuntu to see if the CD can even be read.  If not, download a copy of your version of Windows, burn it to CD within Ubuntu, and then try booting from it.

---

### Post by eAi-T0ky0 on 2009-01-14
> **taurus said:**
> Is that the original windows CD that you are trying to boot with?  Have you tried booting the same windows CD with another machine to make sure it's not the CD?

yes it is a original windows CD , And i Try to boot it from anther pc and it works , I think my problem in the /boot folder path , I think :( dunna wats the problem?

---

### Post by eAi-T0ky0 on 2009-01-14
> **grantk86 said:**
> Try pressing F12 a bunch of times as your computer starts up to force it to access the boot device menu.  From there you can select the CD drive to boot from.  I think in some machines the key to press is F10, not F12... try both.

If that doesn't work, change the boot device order in your BIOS (usually accessed by pressing F2 upon startup) so that the CD drive is listed first.

If you're still stuck, it may just be a problem with the XP CD.  Try inserting it while in Ubuntu to see if the CD can even be read.  If not, download a copy of your version of Windows, burn it to CD within Ubuntu, and then try booting from it.

Thanks man for the great replay , but I do all that things , and my pc BIOS boot is automatically booting from any cd I put there and i check it up and it's normal and active to boot from cd, I told u I try booting the [ubuntu] cd and it booting but my Windows cd is not :( 
:::
:::
:::
I think there was a problem in grub or booting folder in ubuntu or some partition not allowed me to be able boot the cd windows!!!!! I read some threads talking about some like this , u know!!!!!

---

### Post by aesis05401 on 2009-01-14
Inserting any bootable media to an optical drive that is included in the bios level boot sequence should commandeer the boot process before grub ever gets loaded, right?

I have never heard of anything like this happening before unless the media was faulty or the drive was dying.

---

### Post by thomasr on 2009-01-14
> **aesis05401 said:**
> Inserting any bootable media to an optical drive that is included in the bios level boot sequence should commandeer the boot process before grub ever gets loaded, right?

I have never heard of anything like this happening before unless the media was faulty or the drive was dying.

 Absolutely correct. You either have a media or hardware problem. It has nothing to do with grub or Ubuntu,

---

### Post by eAi-T0ky0 on 2009-01-15
ok if it's ,, Why ubuntu cd live can boot , while the windows cd can't boot and i try it in anther computers and it just boot and the about the media in the cd ubuntu can read it from it!!!! 

please check this LINK [https://www.answers.launchpad.net/ubuntu/+question/51850](https://www.answers.launchpad.net/ubuntu/+question/51850) << it's like my problem and it just had answered but i can't understand anything , Windows-CD will not boot after installing Ubuntu.

it may helps!!!!! :confused:

---

### Post by bumanie on 2009-01-15
Had a friend with a similar problem with xp cd, he found pushing 'e'as soon as the cd started got it working. Try it, it may work.

---

### Post by eAi-T0ky0 on 2009-01-15
sorry but what you mean pushing 'e' ? sorry guys , I think the media is working good , but the windows cd is not in the "BOOT" type , bec i try the media it's works in ubuntu and works good in windows , but when i restart the windows pc to see if the cd boot guss wat ' it's not boot , the cd windows type is "not boot" , it's not from BIOS or Media , It's from the type of windows cd , is not boot type , thanks guys for helping me and sorry for every thing.

but if u want to told me how to make cd windows able to boot? will be help

thanks

---

### Post by adamlau on 2009-01-15
Try booting the XP CD on another computer in order to verify the media.

---

### Post by todak on 2009-01-15
Browse the Windows CD using nautilus and list what files you see.

---

### Post by ajcham on 2009-01-15
> **eAi-T0ky0 said:**
> I think my problem in the /boot folder path

This is definitely not the case - neither Ubuntu nor Grub have any influence over whether a bootable CD will boot or not.

The 3 possible causes are a bad disk, bad drive or BIOS being incorrectly set.  You say you have ruled out the disk or the BIOS as being the root of the problem, so I would suggest trying another CD drive - if you have another around the place, or can borrow one temporarily try installing that and seeing if it works.

However, first, are you absolutely sure that the BIOS is set to boot from CD?  I know you say the Ubuntu CD is booting up, but it wouldn't be the first time I seen someone mistakenly believe they have booted the Live environment, when in fact they have just booted Ubuntu from the hard disk again.  If you are in fact booting the Ubuntu CD, the first thing you will be asked to do is select a language and then to 'Try without installing'. If you are not getting these options, you are not booting from the CD, so recheck the BIOS then try the Windows CD again.

---

