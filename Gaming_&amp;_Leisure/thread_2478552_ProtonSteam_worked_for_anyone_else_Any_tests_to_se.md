---
title: "Proton/Steam worked for anyone else? Any tests to see if Proton is running correctly?"
date: 2022-08-29
forum: Gaming &amp; Leisure
---

### Post by rc-brooks on 2022-08-29
I haven't been able to run any games with Proton. 

Here is the log [https://github.com/farmall1125/farmall1125/blob/main/pressure-vessel.log](https://github.com/farmall1125/farmall1125/blob/main/pressure-vessel.log)

It seems to be a permissions issue. I have uninstalled steam, purged and manually removed any files I can find, I had a separate library on an ntfs folder originally and believe something is still left over somewhere. Does anyone have an idea? Everything is on an ext4 folder now.

---

### Post by Tadaen_Sylvermane on 2022-08-30
Only thing I know of is performance of a given game. I never thought to try any specific tests though. If the framerate is acceptable I just assume it's working fine.

I know it's been fixed as I no longer need it but at one point I had to add something to the launcher for Skyrim to get voices and such. Maybe similar? You need some command flag to get it to do something it doesn't automatically do?

---

### Post by rc-brooks on 2022-09-01
The issue was that the ntfs partition did not have write permission. I ended up moving everything to an ext4 partition. There is a way to get this to work with an ntfs (granting it write permission) but by the time I figured this out, I had already created a new ext4 partition. Still have issues with games that everyone else seems to say is fine, but BeamNG is working fine now. So a step in the right direciton.

---

