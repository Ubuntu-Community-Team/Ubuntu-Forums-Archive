---
title: "Warcraft III - Choppy Sound and Video"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by prophecy on 2006-07-07
Hi all,

I've installed Warcraft III:TFT using WINE and everything was perfect...until I started the game that is...

The video and sound are so choppy as to render the game unplayable. Any thoughts on what causes this, and even better, how I can fix it? 

I'd had the game installed on Windows on this same computer before I switched to Ubuntu, so I don't see how it can be a video/sound card problem.

Thanks,
prophecy

---

### Post by polpak on 2006-07-07
You need to pass the -opengl flag to the war3.exe program

wine war3.exe -opengl

That should work significantly better assuming you have 3d hardware acceleration enabled for your card.

---

### Post by prophecy on 2006-07-07
Thank you for the reply!

However, when I use that command, I get "wine: could not load L"c:\\windows\\system32\\war3.exe": Module not found" It seems as though war3.exe was never installed to that directory, should it have been?

---

### Post by Hairy_Palms on 2006-07-07
try using the absolute path, 
```
wine /home/mike/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

```

---

### Post by prophecy on 2006-07-07
Thats much better, though there are still some lighting errors (such as flickering) and the sound's still a tad messed up. I got this when I inputed that code:

```
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f67c,0x00000000), stub!
cdukes@CDComp:~$ fixme:wave:DSD_CreateSecondaryBuffer (0x7fd54920,0x73e23144,180e0,0,0x7fd5399c,0x7fd761e4,0x7fd53978): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
fixme:imm:ImmGetOpenStatus (0x7fd41848): semi-stub
fixme:imm:ImmReleaseContext (0x10026, 0x7fd41848): stub
fixme:imm:ImmGetOpenStatus (0x7fd41848): semi-stub
fixme:imm:ImmReleaseContext (0x10026, 0x7fd41848): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8bc10,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c27c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c30c,0x00000000), stub!
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
fixme:imm:ImmGetOpenStatus (0x7fd41848): semi-stub
fixme:imm:ImmReleaseContext (0x10026, 0x7fd41848): stub
fixme:imm:ImmGetOpenStatus (0x7fd41848): semi-stub
fixme:imm:ImmReleaseContext (0x10026, 0x7fd41848): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53950
fixme:imm:ImmAssociateContextEx (0x10026, (nil), 16): stub
```

---

### Post by LordRaiden on 2006-07-07
In a shell do ```
winecfg
```

Select the Audio tab, deselect ALSA and select OSS. Wine generally works better with OSS.

If you want to use something like teamspeak or listen to music at the same time, install the alsa-oss package (sudo apt-get install alsa-oss).

After that do 'aoss wine /path/to/Warcraft III'

---

### Post by prophecy on 2006-07-07
Hmm...I can load winecfg just fine, and I have access to all the tabs. But when I click the auido tab, the program crashes.

---

