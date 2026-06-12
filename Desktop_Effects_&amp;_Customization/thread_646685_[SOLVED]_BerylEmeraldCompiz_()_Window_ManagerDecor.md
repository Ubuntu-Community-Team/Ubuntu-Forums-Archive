---
title: "[SOLVED] Beryl/Emerald/Compiz (?) Window Manager/Decorator Issues..."
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Spirotot on 2007-12-21
Ok, here's the deal...

I installed Beryl (I don't remember how, but I DO remember that I had trouble getting it installed...), because I wasn't able to get the 3D cube effect to work with Compiz (which comes pre-loaded on 7.10, right?). So, I installed it, and the Emerald Theme Manager. But now, whenever I log into Ubuntu, none of the windows I open have any decoration (as in, titlebar, minimize/close/maximize buttons, etc.). So, I go to Applications->System Tools->Beryl Manager. The icon shows up in the taskbar, and then I get windows decorations. But, when I change the window decorator (I want to change to Emerald, because then I can use the themes that I want), the decorations immediately disappear. Same thing if I switch to the GTK Window Decorator. So, the only Decorator that works is the Heliodor decorator. I'd also like to point out that if I change the Window Manager from 'Beryl' to 'Compiz', using the icon in the system tray, the window borders (decorations) disappear, and stay gone even when I try to switch back to the Beryl Window Manager. The only way I get the borders back is by logging out and then back in, and starting the 'Beryl Manager' again.

I'm running Ubuntu 7.10 on a Toshiba Satellite A135/S4527.

If you need more info, or if my description was too confusing, let me know.

Any help is greatly appreciated, as I'm starting to get kinda ticked off with this whole thing...

Also, I posted this in the "Desktop Environments" section, but I just realized that it was probably the wrong place to post it... So I copied/pasted to here. Sorry for the double post.

---

### Post by Nano Geek on 2007-12-21
Beryl isn't supported any longer so it's best not to use it anymore.
To get the cube working in Compiz, you need to use the Compiz Settings Manager. You can install it by using this command. ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Spirotot on 2007-12-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> Beryl isn't supported any longer so it's best not to use it anymore.
To get the cube working in Compiz, you need to use the Compiz Settings Manager. You can install it by using this command. ```
sudo apt-get install compizconfig-settings-manager
```

Yeah, I pasted that into a terminal, and I already have it installed... But you didn't really answer my question. When I switch to Compiz as my Window Manager, the window borders disappear.

Thanks for the attempt, though.

---

### Post by Spirotot on 2007-12-21
Also, how can I tell if I have an old version of Compiz installed? I'm really not sure if I have 'Compiz', or 'Compiz Fusion'. If someone could just give me instructions on how to get back to an "out-of-the-box" configuration, that'd be awesome. Then I can just start from scratch. I could probably figure out how to get back to the "out-of-the-box" myself, but I'm not sure what packages I should remove from the Synaptic Package Manager...

---

### Post by Spirotot on 2007-12-21
Hm. Well, the Compiz Window Manager works, now. I noticed that in the settings there was a box called "Window Decoration", and it was unchecked... So I checked it. Now I have window decorations. But I still can't get Emerald to work as my Window Decorator... The borders just turn invisible. So, I'm still in need of help. :D

---

### Post by Nano Geek on 2007-12-21
...

---

### Post by Spirotot on 2007-12-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> ...

Heh. I don't think I even want to know what that means. ;)

---

### Post by Nano Geek on 2007-12-21
> **Spirotot said:**
> Heh. I don't think I even want to know what that means. ;)I didn't mean anything, I wrote something, but then I saw that you partly fixed your problem so I erased it.

---

### Post by AlasdairMacLeod on 2007-12-21
I know you meantiond that you didnt like compiz but...  Why not use compiz fusion!!  It is the compiz and beryl projects merged and its currently supported.  It gives access to the cube ect.  

Its a nice easy install and has brilliant support.  Im a total newb and managed to install it on my first day without any problems :D:D

[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/) 

that is a link to the home page

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

that is a link to some brilliant install instuctions

Give it a go, I think you will be plesantly suprised :D

---

### Post by Spirotot on 2007-12-21
Heh, ok.

*whew*

---

### Post by Spirotot on 2007-12-21
> **AlasdairMacLeod said:**
> I know you meantiond that you didnt like compiz but...  Why not use compiz fusion!!  It is the compiz and beryl projects merged and its currently supported.  It gives access to the cube ect.  

Its a nice easy install and has brilliant support.  Im a total newb and managed to install it on my first day without any problems :D:D

[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/) 

that is a link to the home page

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

that is a link to some brilliant install instuctions

Give it a go, I think you will be plesantly suprised :D

It's not that I don't like Compiz... It's just that it wasn't really working for me. Thanks for the links, though... I'll give it a try.

---

### Post by AlasdairMacLeod on 2007-12-21
no problem dude.

Hope it helps :D

---

### Post by Spirotot on 2007-12-24
Whoops, I kinda "thanked" the wrong post. But anyway, thanks.

---

