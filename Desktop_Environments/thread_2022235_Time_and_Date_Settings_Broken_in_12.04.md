---
title: "Time and Date Settings Broken in 12.04"
date: 2012-07-10
forum: Desktop Environments
---

### Post by WolvenSpectre on 2012-07-10
OK, about a week or so ago I noticed that the time on my Ubuntu box was well off the mark but the date was still right.

Being a fairly old machine and since I use a Smoothwall Firewall that I just had to rebuild from scratch (settings backup was damaged) I don't have any networking rules for time servers anymore.

My first instinct, BIOS battery in this OLD computer is dying. All other settings in the BIOS were still good, but I replaced the battery anyway.

The problem was still there.

I tried to manually set the time in 12.04 but no matter what I enter it keeps going to 6PM Jan 1, 1970. In the BIOS the reads 2070.

I go into the BIOS and set it there, but when I reboot, again the date is what I set it to in the BIOS, but the time is wrong.

I am using this for a SAMBA File Server on my network and it is bad enough that if it looses its mount status on the data drives or I forget to manually mount the drives every bloody time I reboot I have to remap all my network shares AND juggle files put in non existant shares because I have to do SUDO empowered versions of software to get them to work right on 12.04 ](*,):mad:](*,) but now I can't even set the time! (Sorry Rant over... deep breaths :oops:)

I am really getting to my last straw here with 12.04. As a very casual user who is mostly rooted in the windows world I have had my issues with ubuntu from time to time, but NOTHING like this.

---

### Post by Mortuis0 on 2012-10-29
Hi,

You can use the date command with su privileges :

```
sudo date --s="2012-10-29 09:21:42"
```I had the same issue just today because of the DST, and I found out this worked well for me.

Cheers

---

### Post by WolvenSpectre on 2012-10-29
Thanks for your post but the issue was an update bug that they fixed over several updates after I first posted about it in July.

In case you were intersested yest the sudo date worked, as long as you weren't in the default terminal, but the system wouldn't keep it, especially after a restart.

---

