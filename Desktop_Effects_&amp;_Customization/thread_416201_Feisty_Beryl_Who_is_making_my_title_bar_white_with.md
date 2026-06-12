---
title: "Feisty? Beryl? Who is making my title bar white with no text or buttons?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by adampyre on 2007-04-20
The subject pretty much said it all. I sifted through the posts for a while and didn't run across a fix for this yet, but I upgraded to Feisty and installed beryl manager. I have all the effects going, cube, minimize maximize etc..... but when I maximize a window or increase its width to span the entire desktop, a thick white border appears around the entire window and the title bar itself is part of this and turns white, with the min, max and close buttons being lost in this white (nothing is visible on the title bar). Any suggestions? I tried turning things on and off in Beryl and it didn't change anything. I pretty sure it has something to do with Beryl as it doesn't do this when I change to Compiz or Metacity. Thanks!

---

### Post by jiminycricket on 2007-04-20
Try: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4)

> You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" />

However, it's most probable your graphics card does not enough video RAM to handle the multiple large textures anyway.

It fixed it for me on my low end 32mb card

---

### Post by adampyre on 2007-04-20
Mr. Cricket,

Are you psychic? You replied to that post almost as soon as my finger came up off of the mouse button hitting submit!!

This worked! Yeah, I have a Dell C610 with an ATI card,  16 blazing MB of ram (seriously, I had an NVidia with 32 that didn't work as good as this card does). Surprisingly, all the effects run smoothly and no slow down! Even the cube.

Thank you! I bow before thee....

---

