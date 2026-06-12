---
title: "I need help working some odd ends with wine and WC3 :("
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by Richmoar on 2007-07-05
I really don't know or have much to say other than I need help trouble shooting the Warcraft 3 software.

For one I cant interpret these errors or fixmes 

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b9f98) : stub, simulating 64MB for now, returning 64MB left
fixme:ntdll:NtCreateIoCompletion (0x34f7dc, 1f0003, (nil), 0)
fixme:imm:ImmGetOpenStatus (0x162d88): semi-stub
fixme:imm:ImmReleaseContext (0x60026, 0x162d88): stub
fixme:imm:ImmGetOpenStatus (0x162d88): semi-stub
fixme:imm:ImmReleaseContext (0x60026, 0x162d88): stub
fixme:imm:ImmGetOpenStatus (0x162d88): semi-stub
fixme:imm:ImmReleaseContext (0x60026, 0x162d88): stub
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

Also In-game the Sound as in unit voices tends to hang, echo and stutter, as well as slow gameplay and horribly mutilated graphics.

I just want someone to help me out since well, It work just fine on the same hardware in windows though I understand Wine is not Windows

Here are a few pics so you can see.
[http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-3.png](http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-3.png)
[http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-2.png](http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-2.png)
[http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-1.png](http://i190.photobucket.com/albums/z236/Richmoar/Screenshot-1.png)
[http://i190.photobucket.com/albums/z236/Richmoar/Screenshot.png](http://i190.photobucket.com/albums/z236/Richmoar/Screenshot.png)

---

### Post by cogadh on 2007-07-05
Ignore "fixme" messages, they are for the Wine developers to use and mean nothing to us users.

Have you used the how-to posted on Wine's AppDB? Scroll down a bit on the page, you can't miss it.
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

### Post by Mike7171 on 2007-07-05
I had the same problem with this game on Windows. My video card was messed up. Ever since I wiped my computer and switched to Ubuntu, I haven't had that problem. WC3 is just laggy on my computer, need to fix it somehow.

---

### Post by Richmoar on 2007-07-06
Yes, I used the help but it doesn't really help me out since I don't know what is causing the problem.

---

### Post by cogadh on 2007-07-06
I was more interested in whether or not you followed the WC3 installation instructions on the Wine website, or did you just install it without a guide. If you didn't follow the instructions, then that is the first place to start, since there are some very specific things you need to do with Wine and the installed files before the game will work properly at all (a registry key import, renaming the movie files, etc.).

---

### Post by Richmoar on 2007-07-06
Uh-oh :(

I guess you could say I did it on my own. :'(

I actually didn't see any of those things in the WIneHQ page. Was it the instructions at the bottom?  They didn't make sense to me. : (

---

### Post by cogadh on 2007-07-06
If the instructions didn't make sense, then you probably need to spend some time familiarizing yourself with how to use Wine before you try running a game with less than straightforward installation and running requirements. Essentially there are 5 steps required to get WC3 running:

[LIST=1]
[*]Run "winecfg" from the terminal and confirm that the default Windows version is set to Windows 2000 or higher (but not Vista). Then go to the Drives tab and confirm that there is a correct entry for your CD-ROM drive. Clcik OK to close "winecfg".
[*] Create a sybolic link to your CD-ROM drive for Wine to reference. This is probably not completely necessary, but if the how-to asks for it, then I would do it:
```
ln -s /dev/hdc ~/.wine/dosdevices/d\:\: 
```
You will need to verify the correct device entry for your CD-ROM drive before you do this (the /dev/hdc part). Depending on your system, the correct one could be something like /dev/sdc.
[*] Install the game:
```
wine /media/cdrom0/install.exe
```
Modify the command to match your actual CD-ROM path and the installation executable for the game. The installation should work just like ti does in Windows.
[*] After the install is complete, run "regedit" in the terminal. In this key: HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III, add a new DWORD entry called "Gfx OpenGL" and set its value to 1. To add the new DWORD, just navigate to the key through the file tree, then right-click in the right hand pane and select New > DWORD. Name the entry "GfxOpenGL", then hit enter to access the DWORD value and change it to 1. See the attached screenshot if that is confusing
[*] After the that is complete, you might want to browse to the WC3 install directory and rename the movies folder. The movies sometimes don't work in Wine and will crash the game. I recommend trying the game with them available and if it crashes, then rename the folder.
[/LIST]
That's it, the game should run after that.

---

### Post by Richmoar on 2007-07-06
Man you're awesome! I love you, and thanks I appreciate you helping me out and I figured out what the steps on Wine HQ ment, couldn't have done it without you. : D

---

