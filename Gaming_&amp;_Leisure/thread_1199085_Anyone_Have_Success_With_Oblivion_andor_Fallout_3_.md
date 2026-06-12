---
title: "Anyone Have Success With Oblivion and/or Fallout 3 in Jaunty?"
date: 2009-06-28
forum: Gaming &amp; Leisure
---

### Post by jlacroix on 2009-06-28
I have a Windows XP x64 partition set up on my PC alongside my Kubuntu 64-bit main partition. The only purpose in life for the Windows XP x64 partition is to run Oblivion and Fallout 3. Without those two games, I'd have no reason to run it.

I don't really like rebooting into Windows just to play a game, and then rebooting back to Linux to check my email. (Checking email can be dangerous to a Windows installation's health). I'd really just like to consolidate everything.

I have tried several methods of getting Oblivion to work. I haven't tried Fallout 3 yet because I figure if I haven't gotten Oblivion to work then I don't see how Fallout 3 would work. I have tried Wine, Cedega, and Playonlinux. None of them will play oblivion. I have heard about Crossover Games but that costs money and I don't want to pay for something that may or may not do what I need.

Yesterday alone I spent several hours on Google searching for a solution and trying them.

If anyone has had any success getting either game to work I'd really appreciate it. I'd love to hear Oblivion AND Fallout 3 success stories.

---

### Post by Naiki Muliaina on 2009-06-28
Try the Ubuntu WINE forum :
[URL="http://ubuntuforums.org/forumdisplay.php?f=313"]
http://ubuntuforums.org/forumdisplay.php?f=313[/URL]

---

### Post by izizzle on 2009-06-28
[Fallout 3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"): Silver rating with 64-bit Jaunty, Gold with 32-bit Jaunty

[Oblivion IV]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150"): Platinum rating with original DVD install.

They both should work fine.

---

### Post by jlacroix on 2009-06-28
> **Naiki Muliaina said:**
> Try the Ubuntu WINE forum :
[URL="http://ubuntuforums.org/forumdisplay.php?f=313"]
http://ubuntuforums.org/forumdisplay.php?f=313[/URL]
My question isn't completely Wine related as I don't care what method is used to get it to work. I'll take anything, Wine or otherwise.

> **izizzle said:**
> [Fallout 3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"): Silver rating with 64-bit Jaunty, Gold with 32-bit Jaunty

[Oblivion IV]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150"): Platinum rating with original DVD install.

They both should work fine.

I have the original DVD of Oblivion, but I would rather use the GOTY Edition which I already have because it has all of the addons.

Which Wine version should I use? I have NEVER been able to get a game working in Wine ever. Should I stick with what Jaunty gives or install a newer version?

> Cannot start game (patch doesn't seem to work) or load previous one 
That doesn't sound very promising...

---

### Post by Blood//Stain//Child on 2009-06-28
To get the most out of those games requires a heavily patched & compiled WINE.

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> To get the most out of those games requires a heavily patched & compiled WINE.

Probably, especially considering that I am getting jut a blank blue screen in Wine now after going through the tutorial again. :(

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> Probably, especially considering that I am getting jut a blank blue screen in Wine now after going through the tutorial again. :(

Are you using a compiled WINE, or just the standard version?

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> Are you using a compiled WINE, or just the standard version?

The one that comes with the default repository.

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> The one that comes with the default repository.

From Add/Remove?

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> From Add/Remove?

Yeah.

I just got Oblivion to work. However, it will only go into windowed mode and I am only getting 20-30fps of the 70-80fps I get on my Windows partition. :(

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> Yeah.

I just got Oblivion to work. However, it will only go into windowed mode and I am only getting 20-30fps of the 70-80fps I get on my Windows partition. :(

Are you using 32 or 64 Bit Ubuntu?

---

### Post by jlacroix on 2009-06-28
> **blood//stain//child said:**
> are you using 32 or 64 bit ubuntu?

64

---

### Post by Blood//Stain//Child on 2009-06-28
Try this.

[http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb)

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> Try this.

[http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb)

That made it worse. Now it "encountered a serious problem and needs to close".

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> That made it worse. Now it "encountered a serious problem and needs to close".

Ok, then you have deeper issues I think. Have you installed DirectX 9.0c yet?

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> Ok, then you have deeper issues I think. Have you installed DirectX 9.0c yet?

I am not sure. I think I did because this was working for a little bit today although the framerates were poor.

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> I am not sure. I think I did because this was working for a little bit today although the framerates were poor.

Ok. Well my disc has just died, so I can't really test. But I have been able to play Oblivion with the slight side effects of no HDR and shadows as far back as Wine 1.0.1 on Hardy Heron. I have always installed the DirectX 9.0c redistributable though, so maybe you might want to consider doing that also if you haven't already.

Also, if you compile WINE with the Fallout 3 patch, you can enable HDR and shadows in Oblivion.

---

### Post by jlacroix on 2009-06-28
> **Blood//Stain//Child said:**
> Ok. Well my disc has just died, so I can't really test. But I have been able to play Oblivion with the slight side effects of no HDR and shadows as far back as Wine 1.0.1 on Hardy Heron. I have always installed the DirectX 9.0c redistributable though, so maybe you might want to consider doing that also if you haven't already.

Also, if you compile WINE with the Fallout 3 patch, you can enable HDR and shadows in Oblivion.

Were you able to get it to go full screen, and use all of the mods?

---

### Post by Blood//Stain//Child on 2009-06-28
> **jlacroix said:**
> Were you able to get it to go full screen, and use all of the mods?

Yes I was able to use fullscreen. With several patches in the compiled WINE version, I was nearly at Windows native FPS also. 

But I'm sorry, I have never used mods, so I don't know if they work now. I think I remember reading a while ago that they don't.

---

