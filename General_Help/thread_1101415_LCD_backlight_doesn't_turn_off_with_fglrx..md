---
title: "LCD backlight doesn't turn off with fglrx."
date: 2009-03-20
forum: General Help
---

### Post by wolfdale on 2009-03-20
I could never could get the proprietary ati drivers (fglrx) to turn off my LCD backlight whenever power saving mode kicks in. This was evident in Intrepid and I was hoping it would be solved in Jaunty but I still have the same problem. Does anyone else have this issue? I have a 4850HD video card and a samsung T220 widescreen.

The open-source drivers work (radeon) but I need hardware video acceleration for smooth video playback.

---

### Post by wolfdale on 2009-03-22
Ok, I have a update to my problem. Jaunty is now using the open source radeon driver (1.6.12.x) and it provides xv capability for smooth video playback. In fact, mplayer no longer tears videos which the fglrx driver always did. If I may surmise the latest radeon driver.
Pros:
  1) xv & EXA capability for R700 hardware. Videos are tear-free.
  2) Power management works, LCD backlight actually turns off.
  3) Seems much stable than fglrx, I haven't had a lockup yet.
     Probably because there is no 3-D yet.

Cons:
  1) Compiz is not working. It's something I can live without.

---

### Post by wolfdale on 2009-05-12
My latest update, in case anybody is following this.

I decided to give Nvidia a shot. I dug out my old 7600gs card, installed it and reinstalled ubuntu. Amazingly everything worked: compiz, power saver mode and no video tearing. I installed regnum and it also worked like a charm. Booting back into windows, I still could run my favorite game, Guild Wars, however I did have to tweak back some settings to get playable framerates. Inspired by these favorable results, I purchase a new 9500gt video card to give a boost to my windows game and hopefully still run Ubuntu with all it's eye candy turned on. I'm happy to report that my Guild Wars framerates are back up with max quality and most importantly, I'm running Ubuntu with compiz on. In addition, I don't see any evidence of video tearing as seen with fglrx and my power saving mode (LCD backlight turn off) is working. I don't mean to belittle the work of the oss guys who are busy developing readeon and readonhd but I clearly find the proprietary linux drivers produced by Nvidia much more superior to anything else at the moment. As for fglrx, it's a disaster (in my opinion) I could have spared months of headache if I've switch to Nvidia sooner. My HD4850 and HD3850 video cards are now on the auction block on ebay.

---

