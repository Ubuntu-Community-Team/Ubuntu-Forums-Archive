---
title: "AMD GPU Overclocking"
date: 2019-03-22
forum: Gaming &amp; Leisure
---

### Post by muddpup64 on 2019-03-22
Hello all,

I am trying to overclock my Vega 56 using this tutorial: [https://www.maketecheasier.com/overclock-amd-gpu-linux/](https://www.maketecheasier.com/overclock-amd-gpu-linux/)

However after I run this command: ```
sudo echo "5" >> /sys/class/drm/card0/device/pp_sclk_od
```

I get this error:```
bash: /sys/class/drm/card0/device/pp_sclk_od: Permission denied
```


I have even tried editing the file using *sudo vim* but the system overwrites any changes.

I found this page: [https://unix.stackexchange.com/questions/404780/cant-overclock-gpu-using-amdgpu-driver-on-archlinux](https://unix.stackexchange.com/questions/404780/cant-overclock-gpu-using-amdgpu-driver-on-archlinux)
But it does not make sense.


Here is some more information:
[ATTACH=CONFIG]282838[/ATTACH][ATTACH=CONFIG]282839[/ATTACH]


Everybody else seems to be able to write to this file. Why can't I? What am I doing wrong?

---

### Post by CatKiller on 2019-03-22
I don't think that the person that wrote that tutorial tested their instructions.

That command says to run the echo command as root and then use bash - your shell, running as your normal user - to open /sys/class/drm/card0/device/pp_sclk_od, which it doesn't have permission to do. Your privilege elevation is the wrong way round.

Instead, you want to run echo as your normal user, and write to the file as root.

Something more like this

```
echo "5" | sudo tee -a /sys/class/drm/card0/device/pp_sclk_od
```

should work better.

---

### Post by muddpup64 on 2019-03-23
> **CatKiller said:**
> I don't think that the person that wrote that tutorial tested their instructions.

That command says to run the echo command as root and then use bash - your shell, running as your normal user - to open /sys/class/drm/card0/device/pp_sclk_od, which it doesn't have permission to do. Your privilege elevation is the wrong way round.

Instead, you want to run echo as your normal user, and write to the file as root.

Something more like this

```
echo "5" | sudo tee -a /sys/class/drm/card0/device/pp_sclk_od
```

should work better.

I just tried that with no success. I don't think this problem is going to be that simple to fix.

---

### Post by CatKiller on 2019-03-23
I'm an nvidia girl, so I don't have any experience of the AMD side, but I do remember reading that tools have been released for playing with the clock speeds and voltages without having to poke at memory values.

The Arch wiki says that in order to change the settings by poking at memory values you need to have enabled that function at boot time by adding a parameter to your kernel line. You don't mention having done that.

---

### Post by muddpup64 on 2019-03-23
> **CatKiller said:**
> I'm an nvidia girl, so I don't have any experience of the AMD side, but I do remember reading that tools have been released for playing with the clock speeds and voltages without having to poke at memory values.

The Arch wiki says that in order to change the settings by poking at memory values you need to have enabled that function at boot time by adding a parameter to your kernel line. You don't mention having done that.

I will take a look at that. Thank you.

---

