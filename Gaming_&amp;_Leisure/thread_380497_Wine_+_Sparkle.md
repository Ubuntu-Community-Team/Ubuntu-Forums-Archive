---
title: "Wine + Sparkle"
date: 2007-03-09
forum: Gaming &amp; Leisure
---

### Post by SupremePiracy on 2007-03-09
Hey!
Today I played a new game called Sparkle on my laptop which have Windows installed. It's like frozen bubble but with a twist. Now, I couldn't find any Linux installation so I tried with Wine.

**Info:**
I used wine-0.9.32 with oss.

**What worked:**

Installation works fine.
Launching the game from the installer works fine and after that playing the game works fine except that I don't get any sound.

**What didn't work:**
But when closing the game and restart it with "wine Sparkle.exe" and after the buy-this-game-screen nothing happends. 

**What I tried:**
I tried to run the game with alsa oss, "aoss". But Sparkle won't run because nothing happends after the buy-this-game-screen.
[COLOR="DarkOrange"]
There's a demo of this game which you can get here:[/COLOR]
[http://arcade.reflexive.com/downloadgame.aspx?AID=771&CID=22028](http://arcade.reflexive.com/downloadgame.aspx?AID=771&CID=22028)

**Outputs:**

Installation and running the game output:

```
tobbe@dammburk:~/Desktop$ wine SparkleSetup.exe 
fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x34fe9c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x16c768 0x34fe1c) stub!
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185b94 0x34eeb4
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\Sparkle\\ReflexiveArcade\\unins000.exe") stub
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185be4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185bc4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185b4c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185b4c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185be4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185ba4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a54 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c74 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185ad4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c84 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185ad4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185bac 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x1859e4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c74 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c74 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185ad4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185bac 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185bac 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a4c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x185a5c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f904c 0x185c7c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f9810 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x50d570 0x184934 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185a5c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x50d570 0x185a64 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185ae4 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x50d570 0x185c4c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c84 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x50d570 0x185a5c 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x4f8e3c 0x185c84 0x34ed68
fixme:advapi:SetEntriesInAclW 1 0x50d570 0x185a54 0x34ed68
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IPersistFile_fnGetCurFile (0x1859d0)
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IPersistFile_fnGetCurFile (0x1859d0)
fixme:shell:IPersistFile_fnGetCurFile (0x1859d0)
tobbe@dammburk:~/Desktop$ err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSetPBufferAttribARB) - not found
err:wave:DSDB_MapBuffer Could not map sound device for direct access (In/ut-fel)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".

```

It's a really fun game and I would really appreciate help to get it running perfectly.
Thanks

---

### Post by SupremePiracy on 2007-03-09
It is solved! The game works!

In winecfg -> Audio tab -> Sound drivers I checked ALSA driver.

You also need to run the game from the folder. CD to the folder and then run the "wine Sparkle.exe" command.

---

### Post by Gannin on 2007-03-09
Nice game, thanks for the tip :).

---

