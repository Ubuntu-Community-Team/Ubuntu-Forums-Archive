---
title: "SSD help"
date: 2021-02-26
forum: Desktop Environments
---

### Post by mike010 on 2021-02-26
I just upgraded my hdd for a Crucial mx500 ssd i can run the trim command with (sudo fstrim -v /) command. This cleans up the root partition i think. Have it set as a cron job but i guess what i'm asking is there anything else i need to do to maintain it. I read somewhere about deleting blocks but can't find out how to do that or even what it does. Any help would be greatly appreciated.

---

### Post by oldfred on 2021-02-26
I used to add my own cron job.
But now it is a systemd item.

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemctl status fstrim.timer

I do change mount in fstab to use noatime.
Be sure to have good backups as once trim has run there will be no older deleted copies to recover with photorec.[/COLOR]

I have Samsung NVMe drive and downloaded new firmware from Samsung and updated it.
[/FONT]

---

### Post by andrew.46 on 2021-03-01
I built my Threadripper system in June 2019:

Building a Threadripper System for Slackware...
[https://www.andrews-corner.org/threadripper.html](https://www.andrews-corner.org/threadripper.html)

For this system I actually purchased  2 x Crucial MX500 2.5inch SSDs of 2GB each and have kept them humming along since that time. You have not given the size of your drives but the 2GB drives have a TBW (Terabytes Written) company spec of a more than adequate 700TB, the bigger drives are guaranteed for a longer life than the smaller drives.

I run the development version of Slackware on this system and thus usually upgrade the OS components every week or so and I always run the following after each upgrade:

```

fstrim -av

```

This has always been enough for me and my drives are now almost 2 years old without any drama. You and I have chosen well :).

---

