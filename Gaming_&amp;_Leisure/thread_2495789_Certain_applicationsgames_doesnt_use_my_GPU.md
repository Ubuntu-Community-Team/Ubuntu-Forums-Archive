---
title: "Certain applications/games doesnt use my GPU"
date: 2024-03-01
forum: Gaming &amp; Leisure
---

### Post by 48kilobytes on 2024-03-01
[SIZE=5]My specs[/SIZE][INDENT]# System Details Report
---


## Report details
- **Date generated:**                              2024-03-02 01:17:47


## Hardware Information:
- **Hardware Model:**                              BIOSTAR Group A960D+V3
- **Memory:**                                      16.0 GiB
- **Processor:**                                   AMD FX&#8482;-6300 × 6
- **Graphics:**                                    NVIDIA GeForce GTX 1050 Ti
- **Disk Capacity:**                               1.3 TB


## Software Information:
- **Firmware Version:**                            080015 
- **OS Name:**                                     Ubuntu 23.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               45.2
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.5.0-21-generic

[/INDENT]
[SIZE=5]Whats my problem: Games using my CPU as rendering instead of GPU
[/SIZE][INDENT]I just started using linux and my friend recomended ubuntu for start.

ive checked bottleneck calculator, got result with 0% bottleneck with 1080p, intense graphics card tasks ([link for calcs results]("https://pc-builds.com/bottleneck-calculator/result/0sJ0VZ/3/graphic-card-intense-tasks/1920x1080/"))
ive tried research, nothing helped.

Ive tried installing couple of games from my steam, didnt go well.[/INDENT]
[INDENT]Example of what i mean:
[IMG]https://i.imgur.com/CPeABn8.jpeg[/IMG]
(Team Fortress 2 with top-left fps counter placed, low fps, no GPU Usage in NVIDIA Settings window.)

Below is my listing of apps that doesnt offend my gpu.
- Team Fortress 2
- Terraria
- Lethal Company
- Blender
- Roblox Studio

Below is my listing of apps that does offend my gpu.
List of apps that uses my gpu:
- Brave (Browser)
- Discord

above is applications/games ive tried.

Below is my listing of benchmarks that does using gpu
-GLX-Gear (limited to refresh rate)
-GL Mark 2 (100% gpu usage, 5636 score)

above is benchmarks ive tried.
[/INDENT]
[SIZE=5]My point that its useless to play on ubuntu for me right now since my gpu useless[/SIZE][INDENT](Sorry for bad english, its isnt my first language)[/INDENT]

---

### Post by maximge on 2024-05-21
sudo add-apt-repository ppa:graphics-drivers/ppa

sudo update-pciids && sudo apt update 

sudo apt install nvidia-driver-550

---

