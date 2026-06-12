---
title: "LightDM/Gdm: Quick fix needed for login issue, and more general guidance :~)"
date: 2021-08-07
forum: Desktop Environments
---

### Post by heatopher2 on 2021-08-07
Hi Everyone,

I'm on Ubuntu 18.04, and trying to customise things to look nice (another post on that issue coming up somewhere else, parallel to this one).

With that in mind I wanted to make my login screen look a bit nicer than a boring purple curtain, so I tried adding a wallpaper, [following this advice]("https://www.iseelondoniseefrance.se/2019/03/11/ubuntu-18-04-lts-changing-the-login-screen-background/"). Firstly, that didn't do anything to the initial login screen, only to the screen after logging out, suspending or hibernating, and also the fonts are still tiny, and so I wanted to find a better way to do things.

Therefore, after a bit of searching, I [found this video]("https://www.youtube.com/watch?v=_dYqisDIcC0"), which turned out to be a bit out of date once I started tweaking, but anyway I thought I'd keep going for a bit. Alas I didn't get very far because after enabling LightDM and restarting,  windows were resized to some ridiculous size that couldn't fit on the screen, like three times bigger than they should be. I was able to sort out some of them but others (Telegram Desktop, Skype and maybe one other which I can't remember just now) were apparently stuck at that size. So I assumed that it must have something to do with LightDM, and reset gnome as the environment (I hope I'm using the right vocabulary, sorry, trying to understand as I go along).

Having done that, I  panicked a little on restarting when I just saw a command line login, but was thankfully able to find out that I can use this command to get the normal Gnome login:

```
sudo systemctl restart gdm3
```

Still, it's a bit annoying to have to do that every time I log on, so would like to just have the normal Ubuntu logon when I boot up. Where do I need to go to fix this?

More generally, is LightDM somehow problematic in the more recent versions of Ubuntu? It's only the greeter that I want to change, as the desktop itself is OK as is (well, I'm working on that too, but that's for another post :~)

Thanks in advance :D

---

### Post by tea for one on 2021-08-08
> **heatopher2 said:**
> 

Still, it's a bit annoying to have to do that every time I log on, so would like to just have the normal Ubuntu logon when I boot up. Where do I need to go to fix this?

Have you tried:-

```
sudo dpkg-reconfigure gdm3
```

Just a bit of info for the future.

If you install Ubuntu 20.04 LTS, you can change the gdm3 background with [https://github.com/thiggy01/change-gdm-background](https://github.com/thiggy01/change-gdm-background)

---

### Post by heatopher2 on 2021-08-08
> **tea for one said:**
> Have you tried:-

```
sudo dpkg-reconfigure gdm3
```

Yes, that's fixed that problem. Thanks very much O:)

> **tea for one said:**
> Just a bit of info for the future.

If you install Ubuntu 20.04 LTS, you can change the gdm3 background with [https://github.com/thiggy01/change-gdm-background](https://github.com/thiggy01/change-gdm-background)

Yeah, I'm a little hesitant about that upgrade, as I tried installing it before, and some of the nice aesthetic things that I like didn't work. I think it was the Variety wallpaper changer, maybe. Then again, that's currently not working quite as it should in on this 18.04 installation, so not sure actually.

---

### Post by heatopher2 on 2021-08-08
Actually, no, sorry, it wasn't Variety. It was the Cairo Dock that didn't work on 20.04, and that's another cute feature that I really like.

---

### Post by tea for one on 2021-08-08
> **heatopher2 said:**
> Yeah, I'm a little hesitant about that upgrade, as I tried installing it before, and some of the nice aesthetic things that I like didn't work.

You always have two paths for an upgrade.

Upgrade in-situ and keep all the left-over configurations etc.
Back up data, fresh install your chosen version and restore data.

I always prefer the second choice because it is easy, less stressful and reduces a certain amount of accumulated cruft.
Every two years, a couple of hours is time well-spent for LTS versions.

---

