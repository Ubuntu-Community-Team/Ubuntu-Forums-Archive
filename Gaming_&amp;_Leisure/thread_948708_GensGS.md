---
title: "Gens/GS"
date: 2008-10-15
forum: Gaming &amp; Leisure
---

### Post by SonicEpsilon on 2008-10-15
I've been asked by the creator of this version of Gens to post it here, since you guys are still stuck with the official Linux port, Gens/GS is superior than the official Linux port. The main goal of Gens/GS is to clean up the source code and combine features from various forks of Gens. 

**Features of Gens/GS:**
* 7z support added
* Screenshots saved in PNG format
* Real 32-bit colour rendering
* Many more

For more information about Gens/GS along with downloads, check the article on the Sonic Retro Wiki: [http://info.sonicretro.org/Gens/GS]("http://info.sonicretro.org/Gens/GS")

The next version of Gens/GS will include packages for Ubuntu 8.04 & 8.10. For now, you'll have to build from source.

---

### Post by megamaced on 2008-10-15
Why fork Gens? Hasn't it been forked enough??

Would make much more sense if the author contacted me so he could upload his changes to cvs....

I've made a quick debian package of this anyway, because people deserve a better Gens, and theres no doubt that the changes here are good.

package here: [http://www.zshare.net/download/20609146abf66343/](http://www.zshare.net/download/20609146abf66343/)

---

### Post by GerbilSoft on 2008-10-15
Hi,

I created Gens/GS because I was sick of the current state of Gens/Linux (2.15.2 at the time). However, I didn't attempt to submit it upstream because I've done massive code overhauls, not just feature additions. For one, I'm working on converting most of the program to use C++ classes and proper abstraction instead of scattering things all over the codebase. Also, I'm converting the x86 assembly language code to C/C++, so Gens will eventually be ported to other architectures. (I have a G4 Cube that wants a decent Genesis emulator. :( )

Finally - and this is the biggest change - I'm integrating cross-platform support into a single codebase. That is, I'm adding a Win32 UI using the native Win32 APIs instead of GTK+ and SDL. With the appropriate cross-compiler setup, you can build both the Linux version and the Win32 version on the same machine from the same codebase. I also plan on writing a native Cocoa UI for MacOS X (Intel at first) later on. The Windows integration is almost done, and will be part of the next release (m5).

---

### Post by disturbedite on 2008-10-15
OMG! this is awesome!

i really liked gens32 on windows, the best genesis/md emulator there is/was imo on windows. i remember begging him to port it to linux but i don't think he ever got around to it.

it would be awesome to see some of those options in gens32 find their way to this new gens fork...
(you could consider that a feature request. ;))

---

### Post by wingnux on 2008-10-15
7zip support? YAY!!!

Thanks for the deb megamaced =)

---

### Post by GerbilSoft on 2008-10-16
Just a note in case anyone has problems opening 7z files: 7-zip support requires that you have p7zip installed. p7zip's available in the Ubuntu repositories. (I used a hackish method of calling out to the /usr/bin/7z binary to extract ROMs instead of using a library, since I couldn't find a decent 7z library.)

Gens/GS currently doesn't show an error message if the 7z binary isn't found. I will add one for m5.

disturbedite: Which features from Gens32 would you like to see in Gens/GS?

---

### Post by BigSilly on 2008-10-16
Thanks for the package megamaced, and thanks for your hard work on this GerbilSoft. I'm thrilled to bits that Gens is continuing to improve.

I've just installed the .deb above, but I'm losing my render when I select full screen. Is there a way to fix this? I use scale2X. Thanks all. :)

---

### Post by megamaced on 2008-10-16
If you installed the Gens Debian package and your Gens launcher is missing the Gens icon, just download the package again. I've fixed it.

I've noticed this Gens doesn't use 50% CPU when idle like official Gens. It actually sleeps when idle, which is good..

Another positive is that you've managed to create a consistent GUI. The OK, Save and Close buttons are all the same.

---

### Post by GerbilSoft on 2008-10-16
> **BigSilly said:**
> I've just installed the .deb above, but I'm losing my render when I select full screen. Is there a way to fix this? I use scale2X. Thanks all. :)

The original Windows Gens had separate render modes for windowed and fullscreen. I reimplemented this in the Linux version; however, since there's no right-click menu, it's not too simple to figure it out. You can press F11 and F12 to cycle through the renderers, but if you're using 32bpp, it might not let you get to Scale2x. (I plan on fixing this for m5.)

A quick workaround is to open ~/.gens/gens.cfg and copy the value for "Render Windowed" to "Render Fullscreen".

> **megamaced said:**
> Another positive is that you've managed to create a consistent GUI. The OK, Save and Close buttons are all the same.
That was one of the main reasons why I started my fork in the first place. The UI is completely rewritten using GTK+'s C API (i.e. without Glade). Also, I split each window into separate files to make maintenance a bit easier.

Also, here's an additional list of features in Gens/GS m4.2, in no particular order:

[LIST]
[*]Multi-file archive support. If you select a ZIP or 7z archive that contains multiple files, it will prompt you to select which file to open. Note that this will show up even if there's only one ROM file in the archive, and the other files are just text or images. I plan on fixing this eventually.
[*]Screenshots are saved without applying a renderer. (Fast blur does get applied though, but I will fix this later on.)
[*]Border color emulation. (Currently SDL rendering only, and the border color is not affected by the renderer.)
[*]SegaCD savestate support, ported from Gens Rerecording.
[*]Re-enabled the built-in debugger and ported several features from Gens Rerecording.
[*]Extra spaces in game names are removed when the name is placed in the title bar. This is most noticeable in Sonic games, where the internal header says something like "SONIC THE [blank spaces] HEDGEHOG".
[*]OpenGL, PNG, ZLib, physical CD-ROM, and x86 asm renderers are all conditionally selectable in the configure script. (They default to Enabled.)
[*]The video, audio, and input layers were rewritten using C++ classes.
[/LIST]

Not-so-comprehensive list of changes in the upcoming m5 release:
[LIST]
[*]Windows support. The same codebase can be used to build either a Windows version or a Linux version. Everything is exactly the same in both versions except for video/audio/input and the UI.
[*]Fixed PWM audio volume and the 8th PCM audio channel.
[/LIST]

---

### Post by disturbedite on 2008-10-16
> **GerbilSoft said:**
> ...disturbedite: Which features from Gens32 would you like to see in Gens/GS?

the audio options & video filters, if you haven't implemented them already. gens32 also has an improved game genie code manager.

---

### Post by BigSilly on 2008-10-16
> **GerbilSoft said:**
> The original Windows Gens had separate render modes for windowed and fullscreen. I reimplemented this in the Linux version; however, since there's no right-click menu, it's not too simple to figure it out. You can press F11 and F12 to cycle through the renderers, but if you're using 32bpp, it might not let you get to Scale2x. (I plan on fixing this for m5.)

A quick workaround is to open ~/.gens/gens.cfg and copy the value for "Render Windowed" to "Render Fullscreen".

Ah right. Thanks for the info, and your easy workaround fixed it. I altered the ~/.gens.cfg.

Excellent stuff!

---

### Post by megamaced on 2008-10-16
Zshare is down *again*! Alternatives please! :)

---

### Post by GerbilSoft on 2008-10-16
> **megamaced said:**
> Zshare is down *again*! Alternatives please! :)
Can you upload the m4.2 deb to the Sonic Retro wiki? [http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)

> **disturbedite said:**
> the audio options & video filters, if you haven't implemented them already. gens32 also has an improved game genie code manager.
I already improved the code manager in Gens/GS by using checkboxes for enabling/disabling codes instead of highlighting them. I'll take a look at Gens32's code system to see what's improved there.

With regards to renderers, I'm going to introduce a general plugin system in m6. At first, it will be used for renderers, but I eventually want to extend it to more than just renderers, e.g. Game Genie support will be moved to a plugin.

---

### Post by disturbedite on 2008-10-16
> **GerbilSoft said:**
> I already improved the code manager in Gens/GS by using checkboxes for enabling/disabling codes instead of highlighting them. I'll take a look at Gens32's code system to see what's improved there.

With regards to renderers, I'm going to introduce a general plugin system in m6. At first, it will be used for renderers, but I eventually want to extend it to more than just renderers, e.g. Game Genie support will be moved to a plugin.

thats really great news!

could you also look into implementing gens32's improved audio options in gens/gs?

---

### Post by GSZX1337 on 2008-10-17
> **GerbilSoft said:**
> Also, I'm converting the x86 assembly language code to C/C++, so Gens will eventually be ported to other architectures.

Can't wait for that. I've been waiting for a good 64-bit Linux Genny emulator.

---

### Post by wingnux on 2008-10-17
The "Save config as" crashes the emulator:

wingnux@wingnux-desktop ~ $ gens
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted

---

### Post by GerbilSoft on 2008-10-18
> **wingnux said:**
> The "Save config as" crashes the emulator:

wingnux@wingnux-desktop ~ $ gens
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
I missed converting a few NULLs to "" when converting some functions to use C++ strings. Apply this patch to fix the problem:
```
diff --git a/src/gens/util/file/config_file.cpp b/src/gens/util/file/config_file.cpp
index 9509c67..57ff74e 100644
--- a/src/gens/util/file/config_file.cpp
+++ b/src/gens/util/file/config_file.cpp
@@ -262,7 +262,7 @@ int Save_As_Config(void)
 {
        string filename;

-       filename = GensUI::saveFile("Save Config As", NULL, ConfigFile);
+       filename = GensUI::saveFile("Save Config As", "", ConfigFile);
        if (filename.length() == 0)
                return 0;

@@ -532,7 +532,7 @@ int Load_As_Config(void *Game_Active)
 {
        string filename;

-       filename = GensUI::openFile("Load Config", NULL, ConfigFile);
+       filename = GensUI::openFile("Load Config", "", ConfigFile);
        if (filename.length() == 0)
                return 0;

```

---

### Post by idumych on 2008-10-18
I'm glad to see you're finally getting some good feedback Gerb. Not too many people making posts like this on retro. Isn't the Ubuntu community great? :guitar:

---

### Post by megamaced on 2008-10-18
> **GerbilSoft said:**
> Can you upload the m4.2 deb to the Sonic Retro wiki? [http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)

Can't. Permissions issue

---

### Post by GerbilSoft on 2008-10-18
> **megamaced said:**
> Can't. Permissions issue
You probably need to register an account in order to upload files.

Also, if possible, can you rebuild the m4.2 package with the above patch for "Load Config" / "Save Config As"?

---

### Post by megamaced on 2008-10-18
> **GerbilSoft said:**
> You probably need to register an account in order to upload files.

I have, megamaced

[QUOTE=GerbilSoft]Also, if possible, can you rebuild the m4.2 package with the above patch for "Load Config" / "Save Config As"?[/QUOTE]

Will do :)

---

### Post by GerbilSoft on 2008-10-18
> **megamaced said:**
> I have, megamaced
Oh yeah, I forgot that Sonic Retro required admin validation before you could upload anything to the Wiki. Your account has been approved, so you should be able to upload it now.

---

### Post by wingnux on 2008-10-19
Is there any way to make Gens/GS play the audio tracks from Sega-CD games when loading from cue/bin images? When I load the cue-sheet file the game doesn't run (black screen) and when I load the bin file it runs but without the cdda tracks =/

---

### Post by GerbilSoft on 2008-10-19
> **wingnux said:**
> Is there any way to make Gens/GS play the audio tracks from Sega-CD games when loading from cue/bin images? When I load the cue-sheet file the game doesn't run (black screen) and when I load the bin file it runs but without the cdda tracks =/
BIN/CUE isn't fully supported yet; however, since Physical CD-ROM support works, you can use cdemu to create a virtual drive and mount the BIN/CUE that way. Once you have cdemu set up, change the CD drive in Gens to the virtual drive (e.g. /dev/scd1), restart Gens, and then select File, Boot CD.

---

### Post by disturbedite on 2008-10-19
@ GerbilSoft
i don't mean to be repetitive or be a pest, but i asked this before:
could you also look into implementing gens32's improved audio options in gens/gs?

---

### Post by GerbilSoft on 2008-10-19
> **disturbedite said:**
> @ GerbilSoft
i don't mean to be repetitive or be a pest, but i asked this before:
could you also look into implementing gens32's improved audio options in gens/gs?
I'll take a look at Gens32's audio options and see what's useful.

Right now, I'm finishing up the m5 release. The major new feature in m5 is integration of the Windows build into the same codebase, but there's also lots of bugfixes in the core code and the GTK+ UI.

---

### Post by megamaced on 2008-10-20
> **GerbilSoft said:**
> I missed converting a few NULLs to "" when converting some functions to use C++ strings. Apply this patch to fix the problem:
```
diff --git a/src/gens/util/file/config_file.cpp b/src/gens/util/file/config_file.cpp
index 9509c67..57ff74e 100644
--- a/src/gens/util/file/config_file.cpp
+++ b/src/gens/util/file/config_file.cpp
@@ -262,7 +262,7 @@ int Save_As_Config(void)
 {
        string filename;

-       filename = GensUI::saveFile("Save Config As", NULL, ConfigFile);
+       filename = GensUI::saveFile("Save Config As", "", ConfigFile);
        if (filename.length() == 0)
                return 0;

@@ -532,7 +532,7 @@ int Load_As_Config(void *Game_Active)
 {
        string filename;

-       filename = GensUI::openFile("Load Config", NULL, ConfigFile);
+       filename = GensUI::openFile("Load Config", "", ConfigFile);
        if (filename.length() == 0)
                return 0;

```

Didn't seem to work:

```
patching file a/src/gens/util/file/config_file.cpp
Hunk #1 FAILED at 262.
Hunk #2 FAILED at 532.
2 out of 2 hunks FAILED -- saving rejects to file a/src/gens/util/file/config_file.cpp.rej
```

---

### Post by DoktorSeven on 2008-10-20
> **megamaced said:**
> Didn't seem to work:

```
patching file a/src/gens/util/file/config_file.cpp
Hunk #1 FAILED at 262.
Hunk #2 FAILED at 532.
2 out of 2 hunks FAILED -- saving rejects to file a/src/gens/util/file/config_file.cpp.rej
```

Patch should be in the source directory and you need to run patch with -p1 since there's a leading "a" directory in the file path (patch maker used this to separate old code tree from new).

patch -p1 < gens.patch
(or whatever you called it)

Or just do what I did: open the file in a text editor, go to those lines, and change NULL to ""

---

### Post by megamaced on 2008-10-24
Doesn't work. The patch doesn't patch. I'd love to be proven wrong.

@GerbilSoft - I'll get the deb uploaded to Sonic Retro later. Been crazy busy over the last few days

---

### Post by GerbilSoft on 2008-10-26
I've released m5, but since I can't edit the first post in this topic, I'm going to start a new topic.

---

