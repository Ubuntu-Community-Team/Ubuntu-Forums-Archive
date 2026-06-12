---
title: "Blank Screen on : Loading Gnome graphic manager"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Ali_ix on 2006-08-18
Hi all,
Since i got a free shipped ubuntu cd by my friend, i am intrested on installing and running ubunto (as a replacement to windows os)

Now while i have instaled it successfully on a Sony Vaio Laptop.
i cant boot it in my PC.

I have AMD Athlon 64 3000+ and a ATI x700 vga on a WinFast 6150 mobo.

I get a blank screen after getting message " Loading Gnome graphic manager   ...  [ok]"

Nothing happend after a while .. no cd-rom - hard disk activity ...
and i should reset PC using reset button.

what is the problem ? if there is any problem on my VGA (ATI) how can get a shell during bootup to get it fixed (with The guides provided here)

Thanks you in advance,
Ali

---

### Post by Ali_ix on 2006-08-18
any idea ?!

---

### Post by Ali_ix on 2006-10-13
Hi,

I am done,
The problem was with my ATI x700 PCIe card.
I have Switched to onboard graphic (by bios settings).
Then installed ubuntu and tried to install fglrx libs.
Then edited xorg.conf file (x server config file) and replaced VESA with "fglrx" in device section and also edited PCI address from my lspci info.

now i am running on my Ati x700 with proper resoloution adn refresh rate.

have a nice day,
Ali

---

