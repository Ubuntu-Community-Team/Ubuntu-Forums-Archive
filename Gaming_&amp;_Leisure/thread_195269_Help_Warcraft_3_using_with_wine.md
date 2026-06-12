---
title: "Help: Warcraft 3 using with wine"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by Andenium on 2006-06-12
ok i installed the warcraft3 under wine aplication so i go to my home folder press ctrl+h so my hidden files come up click on .wine and drive_c then program files, warcraft III and when i run it it works rly slow (am thinking its cuz i need to run it in terminal with the -opengl tag) but i dont know how to put it in terminal cuz im rly new to linux any help?

---

### Post by nephesh on 2006-06-12
first open a terminal
then do a

```
cd ~/.wine/drive_c/Program*/Warcraft*/
```

then a

```
wine war3.exe -opengl
```

make sure you have the Movies directory deleted/moved.

---

### Post by Andenium on 2006-06-12
ok i did it step by step
```
cd .wine
cd drive_c
cd Program\ Files
cd Warcraft\ III and then wine war3.exe -open gl 
```

and it gives me this but runs only problem is it runs really slow/laggy
```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f67c,0x00000000), stub!
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
```
some1 help me plz

---

### Post by Andenium on 2006-06-12
ok i changed hardware to emulation and it gives me this and still runs laggy as hell
```
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f67c,0x00000000), stub!
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd53b80
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
```
HELP ME PLZ

---

### Post by nephesh on 2006-06-12
what type of video card do you have? and have you installed the correct drivers?

also I noticed you put a space between open and gl
it should be -opengl not -open gl

also to discover whether your problem is actually audio making the game play slow (which I highly doubt) just turn off audio and see if that fixes it, if it does we can work from there.

---

### Post by at0mic on 2006-11-13
i have the exact same issue with lag / memory overflow with call of duty. im newb too :)

---

### Post by at0mic on 2006-11-14
i solved my issue weirdly enough with the command line "wine some.exe -window -opengl"

window did the trick for whatever reason ... yet it was full screen

---

