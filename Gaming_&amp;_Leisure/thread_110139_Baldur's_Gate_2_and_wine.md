---
title: "Baldur's Gate 2 and wine"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by tweak on 2005-12-30
I have been having the hugest headache trying to get BG2 to run with wine, and I've run out of ideas.

The best situation I've managed so far was produced by the following:

1) apt install wine from the winehq repositories (0.9.3)
2) Install BG2, Throne of Bhaal, the latest ToB patch, and a nocd on a Windows machine. Both installs were using the Full option.
3) Copy the entire install directory to ~/.wine/drive_c/ (to the exact same directory as the install was made on the Windows machine)
4) Mirror all references to Baldur's Gate and Bioware in the registry to the appropriate wine registry file.
5) Configure wine (multiple configurations without any difference) and configure BG2 (also multiple configurations without a difference). This includes editing the baldur.ini file for incorrect data paths.

This gets me to the point where I can launch the autorun menu, and get to the main menu of the game. The intro movies play correctly, and all the menu music and sound events trigger fine.

If I try to start a new game, the game crashes and debug info is spewed to the screen. The same thing happens when trying to configure the sound options in BG2.

I have attached the full console log of me trying to start a new game. The lines ending in "stub" are mouseclick events as I click past the intro movies or click buttons to start the game.

Unfortunately I'm out of ideas.
I have tried to use the loki installer, but unfortunately it seems to require too much power of my psu and intermittantly powers down the machine mid-install without warning.
Using wine directly on the disc installers produces the same result.
I have also tried to wine install DirectX, both v8.1 and v9.0c which fail.

If anyone has an idea what might be causing the problem, I would appreciate any help you could offer.

--UPDATE--

If I allow the intro movies to play without skipping them, the same crash occurs near the end of the Black Isles movie, but not with the Bioware or the Wizards movies.

---

