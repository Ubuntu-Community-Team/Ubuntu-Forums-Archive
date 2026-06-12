---
title: "Steam Proton games not working, Ubuntu 20.04 with nvidia-390"
date: 2023-11-05
forum: Gaming &amp; Leisure
---

### Post by howeishotweb on 2023-11-05
Hello,

Short version:
None of my Steam games running through Proton are working. They don't start up and there's absolutely no clue why anywhere. Works on nouveau but not with nvidia-390

Long version:
I have an old Lenovo W540 laptop, with a Quadro K110M card. I was originally running pop_os 20.04 and all was good and all games were working, and I am pretty sure I was using the nvidia-390 driver. I then wanted to compile something that required me to upgrade to pop_os 22.04, but that upgraded the nvidia driver since 390 seems to be absolutely incompatible with Linux 6.x, and any newer driver does not use my Quadro card.

After unsuccessfully trying to get 390 installed on some different distros, I figured the safest bet would be good old Ubuntu 20.04. But no Proton games works at all. They simply don't start up, with Steam saying they are running for 1 second before then going back to nothing. There is nothing in the console output when running Steam from the terminal, other than a "chdir" command every time I try to play a game, and there is nothing in the Proton log.

I have tried older Proton versions, and different launch arguments such as using wine3d and older OpenGL versions. I've been informed that apparently nvidia-470 should work for this GPU, but it is not available in ubuntu-driver, so as far as I can tell 390 is the latest working driver.

Any ideas? As mentioned nouveau works but the performance is unusable.

pop_os 20.04 is EOL and I couldn't get nvidia-390 installed when trying the live environment anyways.

---

### Post by Tadaen_Sylvermane on 2023-11-28
Are you using the flatpak steam by chance? That is another issue. Not specifically with Proton but I've seen a handful of things around various forums about flatpak steam not working right, doing exactly what you are describing. As much as I love flatpak I had no choice but to do this.

```
dpkg --add-architecture i386 && apt update && apt install steam
```

I wasn't to thrilled with how the Snap version worked either for the record.

---

