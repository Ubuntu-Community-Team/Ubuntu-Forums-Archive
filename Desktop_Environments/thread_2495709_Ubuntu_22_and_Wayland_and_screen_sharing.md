---
title: "Ubuntu 22 and Wayland and screen sharing"
date: 2024-02-28
forum: Desktop Environments
---

### Post by karimarttila on 2024-02-28
I use Ubuntu 22 (Ubuntu 22.04.4 LTS, Gnome 42.9, Windowing system: Wayland). I should be able to share my screen in e.g. Teams, but at the moment I can only share one tab of the browser.
I looked in the webrtc instructions that if you put in Chrome: chrome://flags/ => WebRTC PipeWire support : Enabled, you should be able to share the entire screen. Does not work.
You can test this, for example, on the page: [https://mozilla.github.io/webrtc-landing/gum_test.html](https://mozilla.github.io/webrtc-landing/gum_test.html) => Screen sharing is only possible in "Chrome tab", but not in "Windows" or "Entire Screen". I'm interested in getting that "Entire screen" working.
Going back to Xorg is not a solution.
The machine has a version of pipewire installed:
&#955;> sudo apt list --installed *pipewire*
gstreamer1.0-pipewire/jammy-updates,now 0.3.48-1ubuntu3 amd64 [installed,automatic]
libpipewire-0.3-0/jammy-updates,now 0.3.48-1ubuntu3 amd64 [installed,automatic]
libpipewire-0.3-common/jammy-updates,jammy-updates,now 0.3.48-1ubuntu3 all [installed,automatic]
libpipewire-0.3-modules/jammy-updates,now 0.3.48-1ubuntu3 amd64 [installed,automatic]
pipewire-bin/jammy-updates,now 0.3.48-1ubuntu3 amd64 [installed,automatic]
pipewire-media-session/jammy,now 0.4.1-2ubuntu1 amd64 [installed,automatic]
pipewire/jammy-updates,now 0.3.48-1ubuntu3 amd64 [installed,automatic]

If anyone has successfully configured that "Entire screen" screen sharing to work with Ubuntu 22 and Wayland, I'd be happy to receive tips here.

---

### Post by readableauthor on 2024-02-28
Works for me both in Firefox and Chrome on Wayland Gnome 42.9. I don't think I did anything for that. Intel GPU. Browsers asked me what monitor I want to share (I chose built-in). Then a yellow screen sharing icon appeared in tray (indicating recording).

---

### Post by karimarttila on 2024-02-28
I'm deeply sorry. I assumed (never assume) that this is a Wayland issue. It turned out that I had messed my desktop at some point. The screen sharing works now (after: sudo apt install xdg-desktop-portal-gnome gnome-remote-desktop).

---

### Post by TheFu on 2024-02-29
> **karimarttila said:**
> I'm deeply sorry. I assumed (never assume) that this is a Wayland issue. It turned out that I had messed my desktop at some point. The screen sharing works now (after: sudo apt install xdg-desktop-portal-gnome gnome-remote-desktop).

Please mark the thread SOLVED using the _thread tools button_, so people don't waste time.

---

### Post by karimarttila on 2024-03-01
Ah, sorry. I missed that. I now marked this thread as solved.

---

