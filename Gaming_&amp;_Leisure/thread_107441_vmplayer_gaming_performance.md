---
title: "vmplayer gaming performance"
date: 2005-12-23
forum: Gaming &amp; Leisure
---

### Post by link_36p on 2005-12-23
after trying to get games like hl2 to work under the latest versions of wine and having no luck, i decided to try a XP install under vmplayer. (its insatlling right now)
anyways has anyone tried playing any games? and if so what was performance like.

---

### Post by Zeroedout on 2005-12-23
[quote=link_36p]after trying to get games like hl2 to work under the latest versions of wine and having no luck, i decided to try a XP install under vmplayer. (its insatlling right now)
anyways has anyone tried playing any games? and if so what was performance like.[/quote]

If I remember correctly (though it is very possible I don't, my memory is really shitty), due to the nature of VM's, 3d gaming is not possible. I belive it had something to do with the way a virtual machine works, by emulating hardware, or something to that effect; though the details may be wrong, I don't belive gaming is possible on VMs

---

### Post by siorai on 2005-12-23
As far as I've seen, you can't install proper 3D video card drivers due to how the hardware is setup, so no gaming is possible in VMWare. So you're either going to have to dual boot, use Cedega, or only run native games. Personally, I go the last route and I'm more than happy.

---

### Post by link_36p on 2005-12-23
ya just realized that for most part its a no go :(. If you install the vmware tools svga driver you can do some stuff but not much.

---

### Post by anil_robo on 2005-12-24
I installed Windows XP in Breezy using VMware, and then ran it through VMPlayer. I installed and played Diablo in it. The game *videos* were crawling - one frame in 5 seconds! Laughable!

But when it came to actual game, the video setup utility included with Diablo had detected a 2d video card (which is not true, I have 3d). Still, I created a character and ran the game.

The game was running really fast! Much faster than windows itself! Maybe some mismatch between screen refresh rate (XP under vmware showed 85Hz, whereas Ubuntu has 60Hz only).

Edit: By the way I was running Diablo2 under 2-D mode because 3D mode wasn't available in VMware. I shall make a fresh install of XP tonight and install DirectX for 3D support. I'll post the results in this thread then. :)

My Screenies! :)

[ATTACH]4801[/ATTACH] [ATTACH]4804[/ATTACH] [ATTACH]4802[/ATTACH] [ATTACH]4803[/ATTACH]

---

### Post by Perfect Storm on 2005-12-24
What's your screen setup to in refresh rate? And how much can it handle?

---

### Post by Yagisan on 2005-12-24
If you have vmware workstation 5 or better, you could try the instructions here [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html) to set up experimental direct3d accelleration. Haven't tried it as I have no use for windows, but it may help you.

---

### Post by anil_robo on 2005-12-25
I guess this question was directed at me, so I'll answer it anyway :)[quote=Artificial Intelligence]What's your screen setup to in refresh rate? And how much can it handle?[/quote] I couldn't configure refresh rate in VMWare. Neither using VMWare tools, nor using Windows XP graphic properties. It allowed *85Hz only,* whereas Ubuntu is running on *60Hz only.*

---

### Post by Perfect Storm on 2005-12-25
But can your monitor handle 85hz? And is your ubuntu set up for the correct to getting the best refresh rate (hz)?

---

### Post by patrickfromspain on 2005-12-25
The "problem" with the 85Hz isn't a real problem. It isn't sending a 85hz to the monitor, as I believe VMware hasn't true access to the monitor. I have a LG 17" TFT monitor, with maximun refresh rate at 70Hz (if not 60). If VMware was refreshing the monitor at 85Hz I wouldn't see anything, I think it could even crash my monitor.

I think that 85Hz is the refresh rate with which vmware sends a new image to ubuntu... after that ubuntu sends a new image to the monitor, according on his settings.

---

