---
title: "Sound issue with Xubuntu + Wine + World of Warcraft"
date: 2015-08-19
forum: Gaming &amp; Leisure
---

### Post by ynot2 on 2015-08-19
I am running:

Xubuntu (Ubuntu 14.04, xfce 4.10)
wine 1.7.44
bumblebee 3.2.1-5
World of Warcraft 6.2

on an ASUS GL551J with Intel i-7, 16Gb RAM, and an nvidia GTX 860M.

The game runs as good or better than it did on Windows8. The hardware acceleration works like a champ. I just have one small issue with the sound. The sound actually works fine once I go in (in-game) to System, and select a Sound [Quality] Channel. It doesn't matter which one I select - once I change the setting, the sound turns on. This is an important point - it has nothing to do with WHICH setting, only that I change the setting - I don't even need to click save/apply. The problem is that I have to do this every time I start the game. I feel spoiled, but given that WoW is otherwise running perfectly, this small annoyance really stands out. I start the game using the script below:

optirun wine "/home/[username]/.wine/drive_c/Program Files (x86)/World of Warcraft/WoW.exe" -opengl

The game window opens (with sound working) for a brief moment, then minimizes itself right away, pauses, then re-opens a second later with enhanced graphics but no sound. I then have to go into System, and change a setting as described above. So I'm just looking for a tweak/fix so that the sound works without me having to go change a sound setting each time I start the game.

Has anyone else encountered this? Thanks in advance.

---

