---
title: "sudo restart lightdm is it to be fixed?"
date: 2012-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denton Larson on 2012-10-06
Hi

I have a Dell Inspiron mini 10 sudo that used to have Windows XP on it. After pulling my hair out, I have Lubuntu 12.04 on it. The only thing that has me confused is that after it starts, it goes to a black screen.

I do a Ctrl Fn Alt F1 , login and do a sudo restart lightdm

Then I get the normal start up.

HELP

Denton Larson

---

### Post by Denton Larson on 2012-10-07
Bump

---

### Post by sidzen on 2012-10-07
I, myself, would be happy for the serendipitous malfunction of lightdm and perform the following:

[PHP]sudo apt-get update && sudo apt-get install lxde[/PHP]if still not able to login, do an apt-cache search lxde and install a few others, like lxdm lxappearance  lxde-core.

best wishes!

---

### Post by mikewhatever on 2012-10-08
I don't know what "Dell Inspiron mini 10 sudo" is, but if you have a Dell Inspiron mini 10 netbook, especially if it is a Poulsbo based GMA500 netbook, then the problem is known, and there is an easy workaround.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

To verify the netbook chipset, run **lspci** in a terminal window. A Poulsbo based netbook should show something like this:
> 
~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)


---

### Post by sidzen on 2012-10-08
In other words, download kernel 3.3.4 or later; for example,[** here**]("http://optimus-linux.blogspot.com/p/download.html")

Another [**reference**]("http://askubuntu.com/questions/6302/how-can-you-remove-unity"), FYI!

As indicated above, OP, I would just _replace_ it with lxde and lxdm!

---

### Post by mikewhatever on 2012-10-08
> **sidzen said:**
> In other words, download kernel 3.3.4 or later; for example,[** here**]("http://optimus-linux.blogspot.com/p/download.html")

Another [**reference**]("http://askubuntu.com/questions/6302/how-can-you-remove-unity"), FYI!

As indicated above, OP, I would just _replace_ it with lxde and lxdm!

What's all this nonsense? Are you sure you are in the right thread?

---

### Post by sidzen on 2012-10-08
OP asked, ". . . is it to be fixed?"

Further, see my new sig!

---

### Post by Denton Larson on 2012-10-09
> **mikewhatever said:**
> I don't know what "Dell Inspiron mini 10 sudo" is, but if you have a Dell Inspiron mini 10 netbook, especially if it is a Poulsbo based GMA500 netbook, then the problem is known, and there is an easy workaround.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

To verify the netbook chipset, run **lspci** in a terminal window. A Poulsbo based netbook should show something like this:

mikewhatever I goofed when I was entering Dell Inspiron mini 10 sorry, But it is almost working, I swallowed hard and installed new lubuntu 12.04 with all of the screen goof ups, and did a service lightdm .

It works mostly. Any way I am happy!

Denton Larson

---

