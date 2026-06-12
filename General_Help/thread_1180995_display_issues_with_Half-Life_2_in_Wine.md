---
title: "display issues with Half-Life 2 in Wine"
date: 2009-06-07
forum: General Help
---

### Post by Oreo Priest on 2009-06-07
I can't get Half-Life 2 to work properly. I've tried playing with the DirectX levels at launch, and 70 seems to be the only one that even gives the main menu semi-normally. My main issue is that as anything moves, it renders fine, but as it moves away from that space, I don't see what was behind them, I just see a long streak of skybox. I was able to start a new game, but it rendered similarly horribly.

Among the error messages when I run it from the terminal:

fixme:d3d_surface:fb_copy_to_texture_direct Doing a pixel by pixel copy from the framebuffer to a texture, expect major performance issues
err:d3d_surface:fb_copy_to_texture_direct Texture filtering not supported in direct blit
fixme:d3d:get_src_and_opr Unhandled texture arg WINED3DTA_SPECULAR

Any help would be greatly appreciated.

---

### Post by BCurtisWX on 2009-06-07
Wine is only an emulator of windows.  Expect to get lots of problems with high level code (such as games and game engines like Steam).  I never got it to work, so when I want to go play HL2 I go to a winblows partition.
Steam is rumored to be making a linux version.. but thats been around for a while, so i doubt it holds any merit.

---

### Post by txcrackers on 2009-06-07
First, make sure you have a graphics card that handles accelerated graphics. Older cards will not have the basic processing power to handle even DX 7.

Secondly, turn **off** any fancy desktop rendering software (KDE4 Kwin desktop effects, compiz, etc.).

I've been able to play almost all of the Orange Box with this:

-novid -width 1440 -height 900 -dxlevel 90

except for one sequence in Episode 1 where there's just too much happening at once and have to back down to DX 7 to get through that part.

---

### Post by Oreo Priest on 2009-06-07
Thanks. I don't have any fancy effects on, or at least I don't think I do.

My graphics card is an "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)"

According to here: [http://www.google.ca/url?sa=t&source=web&ct=res&cd=7&url=http%3A%2F%2Fdownload.intel.com%2Fproducts%2Fgraphics%2Fintel_graphics_guide.pdf&ei=YB8sSsHzMNeLtgfk8MXLCA&usg=AFQjCNHH2kRhMzLrHeLywfAbXdvZjzDmww&sig2=LC7wXFSohkM44yQ82Uiw3g](http://www.google.ca/url?sa=t&source=web&ct=res&cd=7&url=http%3A%2F%2Fdownload.intel.com%2Fproducts%2Fgraphics%2Fintel_graphics_guide.pdf&ei=YB8sSsHzMNeLtgfk8MXLCA&usg=AFQjCNHH2kRhMzLrHeLywfAbXdvZjzDmww&sig2=LC7wXFSohkM44yQ82Uiw3g), it should be able to run up to DirectX 10, but I'm not sure if I have to do anything to implement that.

Otherwise, I tried your parameters, and it didn't really load. At the main menu screen, the screen was all white with some giant black and grey polygons on it (but I could tell I was at the main menu screen from the sound made when you scroll over the buttons). 

Any advice?

---

### Post by txcrackers on 2009-06-08
I don't believe that the Linux Intel drivers are capable of 3D acceleration - but that's where I'd check. If that's the case, there's plenty of relatively low-cost NVidia (my preference) and ATI cards available - and the drivers for them **are** available.

---

### Post by sandy8925 on 2009-06-08
Intel Linux drivers do have 3d acceleration. I have an integrated 915/910 card.

And by the way what wine version are you using ? The Wine AppDB site list hl2 as platinum meaning working out of the box. 

I've used the latest wine versions and hl2 and steam work amazingly well as well as in windows - and my comp is old. 

Use the latest wine versions - even though they are beta they are not really unstable and won't really crash your comp.

---

### Post by Oreo Priest on 2009-06-08
I'm using wine 1.0.1 , which seems to be the latest stable version. How can I upgrade without losing my C: drive?

---

### Post by Oreo Priest on 2009-06-11
Ok, so I updated wine, but still no luck. Any ideas?

---

