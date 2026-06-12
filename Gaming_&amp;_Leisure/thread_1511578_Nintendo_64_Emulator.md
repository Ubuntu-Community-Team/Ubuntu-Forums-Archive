---
title: "Nintendo 64 Emulator"
date: 2010-06-17
forum: Gaming &amp; Leisure
---

### Post by clicker4721 on 2010-06-17
I know there is countless threads on which Nintendo 64 emulator to use; that's not what I'm after. What I need is somebody to either link to or write out a step-by-step, in-depth, every-miserable-detail installation guide to any major ones, just so long as it works I don't care which. By the way, I've tried the ever-popular Mupen64 that's supposed to be painless and functional&#8212;it was definitely painless, but anything but functional. So, if you'd rather write out the ultimatum of Mupen64 troubleshooting guides, go for it. I'm just desperate. Please help.

EDIT: Oh, and I nearly forgot:  I'm running 64-bit 10.04.

---

### Post by RichardLinx on 2010-06-17
Is Mupen64 even still supported? I don't use Linux any more but I always thought Mupen64Plus was pretty straight forward and very functional. 

Here's a link to the project page: [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

I think you were probably just using an old, obsolete emulator.

---

### Post by DoktorSeven on 2010-06-17
The modern, updated version of mupen64, mupen64plus, is in the Universe repos for 10.04, just **sudo apt-get install mupen64plus** from commandline or search for it in Synaptic (assuming you have Universe enabled -- look in your repositories list to make sure Universe is enabled, you can do this from Synaptic by going to Settings->Repositories and making sure Community maintained Open Source software (Universe) is checked, and reloading from the main GUI if it was not).

As to how to use it, it's very straightforward, or at least it was for me -- configure joystick from Options->Input Settings (click the box next to Device to choose a controller device if you have one, make sure "Plugged" is active -- it should look "pressed in" and white instead of gray, and then click each of the directions and buttons to assign them to a key or gamepad function), set your desired resolution from the graphics setting, then point to an N64 rom using File->Open ROM or by pointing Options->Configure, Rom Browser to your ROM directry and choosing one from the main GUI.

Most games I tried seem to work just fine, especially the major titles.

---

### Post by clicker4721 on 2010-06-17
> **DoktorSeven said:**
> The modern, updated version of mupen64, mupen64plus, is in the Universe repos for 10.04, just **sudo apt-get install mupen64plus** from commandline or search for it in Synaptic (assuming you have Universe enabled -- look in your repositories list to make sure Universe is enabled, you can do this from Synaptic by going to Settings->Repositories and making sure Community maintained Open Source software (Universe) is checked, and reloading from the main GUI if it was not).

As to how to use it, it's very straightforward, or at least it was for me -- configure joystick from Options->Input Settings (click the box next to Device to choose a controller device if you have one, make sure "Plugged" is active -- it should look "pressed in" and white instead of gray, and then click each of the directions and buttons to assign them to a key or gamepad function), set your desired resolution from the graphics setting, then point to an N64 rom using File->Open ROM or by pointing Options->Configure, Rom Browser to your ROM directry and choosing one from the main GUI.

Most games I tried seem to work just fine, especially the major titles.

I looked at Mupen64Plus and download a rar, but decided installing it would be too much effort with the little bir of Ubuntu knowledge I have. I didn't know it was in the repositories! That's wonderful! That makes me happy!!! Thanks, I'll check it out as soon as I get home!

EDIT: Okay, I installed it easy as cake...on 64-bit, is there a specific interpreter core I should use? Namely, most games work just fine, but they all stutter when there's a lot of sound. I know my system can take the heat, I just need to know what settings to change to fix the stutter.

---

