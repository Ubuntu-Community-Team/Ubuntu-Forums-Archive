---
title: "Sudden loss of sound"
date: 2005-12-17
forum: General Help
---

### Post by darne on 2005-12-17
All sound has suddenly stopped from the last boot.  Alsa has loaded, and the volume applet seems happy enough, but nothing is coming out from any application.  Card is an Audigy2 and all modules look loaded.

Tried manually stopping and restarting ALSA to no effect.  If I reboot into Windows, sound is perfectly fine, reboot again straight into Ubuntu and nothing. :confused: 

Edit: If I boot with the volume up, I actually hear the speakers 'pop' like the card has been initialised (but still nothing in ALSA after that)

Tried changing things like Amarok to use OSS, and it suddenly worked (as did XMMS in OSS) after then changing back to ALSA, they are working again....  bizarre 

Anyone any ideas for this slightly odd (to me anyway) behaviour...  it doesn't seem normal!!

---

### Post by Denis on 2005-12-17
Hi

I also use a Audigy 2. There is one thing that stops the sound for me sometimes. Maybe this happens to you too, it's just a guess. 

Sometimes the "Audigy Analog/Digital Output Jack" switch gets muted. If this happens I get no sound at all. You can fix it by checking it in alsamixer (that's the way I do it). Type alsamixer -c 0 or alsamixer -c 1 (when you have more than one soundcard) in the terminal. And check the status of the "Audigy Analog/Digital Output Jack". It should have a green button.

---

### Post by Ocxic on 2005-12-17
If you have any small pets, check yor connections too. it took me 3 days of being totally pissed cause i couldn't get my usb cam to work only to find out that my cat had chewed thru thw wire. stupid cat is no longer allowed in my room.

---

