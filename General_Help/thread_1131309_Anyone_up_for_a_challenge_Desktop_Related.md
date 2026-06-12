---
title: "Anyone up for a challenge? Desktop Related"
date: 2009-04-20
forum: General Help
---

### Post by Hellstudios on 2009-04-20
Heres a good one.


I was making a 5GB ntfs partition last night to install windows XP for experimentation, I boot up from my partition magic live CD, fire up GParted, then shrink my main UBUNTU paritition from 73GB to 67-ish GBs make a NTFS partition (had to leave computer on all night for this) then notice a little exclamation point next to my main partition, But think nothing of it, reboot to ubuntu to check my email etc etc, but when I DO, I notice theres no taskbar and instead of the contents of my desktop it shows the contents of my home folder instead, as if it was my desktop, then an error pops up:
[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Img00014.jpg[/IMG]

So I Ask on here and someone suggests I press alt F2 to get into the terminal and do these commands:

gnome-panel&
metacity --replace
sudo dpkg --fix-broken


I did:

[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Img00012.jpg[/IMG]


Still Nada. Is this problem worth just backing up my mozilla stuff and reinstalling??? or can I just fix this?


If you can seriously help me then You deserve a god damn cookie.


P.S. I deleted that ntfs partition and restored my original Ubuntu partition to it's old settings.

---

### Post by Hellstudios on 2009-04-20
Theres more than 800 members online and only 1 person (being me) has viewed this? wow lol.

---

### Post by Ticketoride on 2009-04-20
> **Hellstudios said:**
> I was making a 5GB ntfs partition last night to install windows XP for experimentation
You need far more Space than that to install WinXP. Swap File has no breathing Room.

> **Hellstudios said:**
> shrink my main UBUNTU paritition from 73GB to 67-ish GBs make a NTFS partition
That WinXP Partition would also have to be set as a "Primary Partition", otherwise its got no Place to put the Boot Files.

> **Hellstudios said:**
> I was making a 5GB ntfs partition last night to install windows XP for experimentation, I boot up from my partition magic live CD, fire up GParted, then shrink my main UBUNTU paritition from 73GB to 67-ish GBs make a NTFS partition ... then notice a little exclamation point next to my main partition ... reboot to ubuntu to check my email etc etc, but when I DO, I notice theres no taskbar and instead of the contents of my desktop it shows the contents of my home folder instead, as if it was my desktop, then an error pops up
GParted appears not move Data first from any Partition Spaces you are truncating and have likely lost some Files.

---

### Post by cygnusx4 on 2009-04-20
have you tried reinstalling ubuntu-desktop?

---

### Post by Hellstudios on 2009-04-20
> **Ticketoride said:**
> You need far more Space than that to install WinXP. Swap File has no breathing Room.


That WinXP Partition would also have to be set as a "Primary Partition", otherwise its got no Place to put the Boot Files.


GParted appears not move Data first from any Partition Spaces you are truncating and have likely lost some Files.

Do you think testdisk would work for this? or photorec?

---

### Post by Ticketoride on 2009-04-21
> **Hellstudios said:**
> Do you think testdisk would work for this? or photorec?
I believe they are File Recovery Apps and have nothing to do with Partitioning.

I am not sure what to tell you, I merely pointed out some Possibilities. Maybe someone has already run into the same Situation you have and had found a Remedy for it.

Me ... I would get my Data off the HDD and start all over again, giving WinXP about 15 GB installed first on your C:\ Drive, then install Ubuntu.

Before I would do that, I'd have GParted make the Partitions first, since Data Loss and Partition Table Errors won't be a Factor at that Point, since the WinXP would fix any Issue before the Install anyways.

---

