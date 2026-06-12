---
title: "Transparent VirtualBox using Compiz"
date: 2009-05-15
forum: General Help
---

### Post by carlosgs91 on 2009-05-15
.

---

### Post by soro2005 on 2009-05-15
You might not be using the right graphics driver. What's your graphics card?

---

### Post by Legace on 2009-05-15
[quote]I ran more tests here and if I start VirtualBox with environment variable XLIB_SKIP_ARGB_VISUALS=1 and Cairo-Dock, VirtualBox works fine:

    ```
env XLIB_SKIP_ARGB_VISUALS=1 VirtualBox
```


I put this on my launcher and it's working, but I still think that this is a workaround not a fix.

---

### Post by sinim on 2009-06-13
I have modified my launcher accordingly as well, yet no luck for mine. still transparent. Anybody else have trouble after the launcher modification? Thanks

---

### Post by joshiausdemwald on 2009-06-14
Unfortionately i am facing the same problem. The probably most interesting point is, that, when i start winXP on VBox once (on a clean, recently start up ubuntu system), everything works fine. After one shutdown of VBox and/or a restart beneath the virtual machine, i see my beloved *cough* Windows as a transparent layer above my ubuntu desktop - which makes it unusable. A X server reset then solves the problem. 

Anybody got an idea? Thanks in advance :)

//
i'm using the latest debian package of virtual box on an ubuntu intrepid-dingsda release.

---

### Post by gharweeh on 2009-06-15
[I]Same problem with me, also same as above about starting after recently starting ubuntu.

[/I][B]edit
[/B]Found this on the VirtualBox forum ([http://forums.virtualbox.org/viewtopic.php?f=7&t=17831&p=79774&hilit=transparent#p79774](http://forums.virtualbox.org/viewtopic.php?f=7&t=17831&p=79774&hilit=transparent#p79774)), also a workaround but it will do in the meanwhile. While having the "Metacity" enabled my cairodock background goes black (pretty much as when using OpenGL with my unsupported card) but atleast VirtualBox is not transparent anymore.
> [INDENT]Sasquatch wrote:[INDENT]quackking wrote:I have the same problem; Jaunty, VBox 2.2.4, Thinkpad T40 with Radeon graphics, *any* Win guest is transparent, at all times except if I raise the VBox shutdown dialog, then sometimes the Win guest becomes opaque. No Cairo apps at all, This occurs with Windows guests from Win2K to WinXP to Win7 beta (all versions.)

Help! Makes no difference if 3D effects are enabled.

No documentation on this issue that I can find.
[/INDENT]
Check my last post here [viewtopic.php?f=7&t=18207]("http://forums.virtualbox.org/viewtopic.php?f=7&t=18207")
[/INDENT]

Hi!

I have no real solution but a work around (temporary change your Windows manager to Metacity):

- If not done already, install the Compiz-Fusion icon (from synaptic);
- launch it;
- Right click on it (in the panel);
- chose the menu option "Select Window Manager";
- choose Metacity.

If your done using VirtualBox, you can choose Compiz again as your Windows manager, using the same procedure.

HTH

---

