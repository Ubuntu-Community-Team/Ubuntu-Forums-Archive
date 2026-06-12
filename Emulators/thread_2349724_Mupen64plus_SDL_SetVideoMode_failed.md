---
title: "Mupen64plus SDL SetVideoMode failed"
date: 2017-01-17
forum: Emulators
---

### Post by karlkimber6994 on 2017-01-17
Hi everyone, I'm really not sure what to make of this! I've used Mupen46plus on so many computers, Pi's, androids, etc & I for some reason can't make it run on my new little laptop! 
I'm running an Intel atom with 1.6ghz / 2gb RAM, 32-bit Lubuntu 14.04. I never really used 14.04 (or for that matter 32-bit) before I had this computer
Has anyone encountered this problem before? I'm stumped! 


Video: Initializing OpenGL Device Context.
Core: Setting 32-bit video mode: 640x480
Core Error: SDL_SetVideoMode failed: could not create GL context
Video Error: Failed to set 32-bit video mode: 640x480
Core Status: Rom closed.


SOLVED! As I discovered, the unstable version of Mupen64plus wasn't working with Ubuntu - I would normally always get the one PPA that holds this stuff,  PPA:Random-stuff/ppa because their stable PPA doesn't host the SNES9X emulator!
So, if you also are encountering this error, try using their stable PPA! **ppa:random-stuff/stable **but of course only after completely removing Mupen64plus & M64py with the apt-get remove mupen64plus* m64py* , if you don't use the asterisk it'll leave other plugins for the addon on your system which will prevent the stable copy from working.

---

