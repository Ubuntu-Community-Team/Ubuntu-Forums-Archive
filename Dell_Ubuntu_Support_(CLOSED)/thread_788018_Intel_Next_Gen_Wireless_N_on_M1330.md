---
title: "Intel Next Gen Wireless N on M1330"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PhrygianCat on 2008-05-09
I just got myself M1330 which came with Vista, simply because Dell had a sale & I got 25% off when getting the one with Vista. I wiped out the hard drive & installed Hardy. Everything pretty much works fine as expected after doing my reading prior to the purchase, but one major issue I have is actually with the Intel wireless. This is strange since everyone else seems to say that it works out of the box.

Now, I should say that I've managed to get it to the point that I have the wifi light on and I'm able to browse what WAPs are around, but when I tried to connect it basically just sits there for a while then it asked me again to enter the passphrase/key. I even tried to connect it manually, but it behaved exactly the same way. Any help is appreciated. Thanks.

---

### Post by amendt on 2008-05-09
Just a suggestion.
I would turn off WEP or WPA2 on the router so you don't have enter a password.

---

### Post by PhrygianCat on 2008-05-09
I tried that. I removed all security on the router just to make it simpler, but it still didn't help at all. It's the same behaviour, the laptop sees the SSID, but somehow it had trouble connecting to it. I even borrowed a friend's router and it produced the same result. I'm stumped. The bad part, I cant' call Dell for support since I purchased it with Vista preloaded. So they won't support it unless it uses that config.

---

### Post by PhrygianCat on 2008-05-10
Finally got it to work,at least at home. I tried it with yet another access point, and it works. Well, not at first when the settings includes 128-bit WEP & MAC address filtering. I had to strip down everything & leave the AP insecured, then add the security one-by-one.

One observation, the previous wireless router/AP I tried uses Tomato open source firmware. So if anyone is having problem connecting to a Tomato firmware on Linksys WRT54G wireless router, you might want to try the original firmware. I was really hoping that there isn't problem with Tomato firmware since I want to go all open source. Anyway, I thought I'd share my experience.

---

