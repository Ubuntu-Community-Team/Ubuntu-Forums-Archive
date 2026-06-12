---
title: "Unity PLUS Xubuntu without losses. Possible?"
date: 2012-04-26
forum: Desktop Environments
---

### Post by WinRiddance on 2012-04-26
Hi all. I've used Ubuntu until the release of Unity which I didn't like nor could get used to. Eventually I switched to Xubuntu which basically gave me the freedom of Ubuntu 10.10 by allowing me to tweak all sorts of things and to have panels as desired. **Now** I'm ready to take another look at Ubuntu with Unity and so I was wondering ...

If I install Ubuntu 12.04 in a separate partition all by itself, followed by installing XFCE and the Xubuntu desktop as an alternative login environment, would I later (if I still didn't like Unity after a couple of months playing with it) be able to import everything from my other Xubuntu installation so it wouldn't need to be re-installed from scratch? I'm keeping my current Xubuntu setup which is already contained in its own partition on the same drive.

Sure, it wouldn't be a big deal to rebuild my old Xubuntu from scratch if I wanted it back, that's not the question. I'm trying to save on the hours that it took for custom panels, wallpapers, compiz settings, nautilus favorites (not using Thunar), and so on.That's why I'm wondering if there's some way to just import the entire old enchilada into the newly created xfce/Xubuntu environment?
Is compiz even compatible with Ubuntu 12.04 and the Unity desktop?

**Or would it make more sense** to just re-install grub with the default startup of my old Xubuntu setup since they're on the same disk anyway, followed by removing Ubuntu 12.04 and then reclaiming that space via Gparted? Just trying to figure out the fastest way to achieve the goal of keeping my old setup if I decide to stick with it later on ...

.

---

### Post by lukeiamyourfather on 2012-04-26
No need to install two operating systems just to try out two desktop environments. Any desktop interface can be installed in any Ubuntu (XFCE, Unity, GNOME, etc.). So just install the other desktop environment and try it out.

---

### Post by snowpine on 2012-04-26
I would simply upgrade to 12.04 (after THOROUGHLY testing it with a Live CD and making a backup just in case), thereby keeping all my documents and settings intact.

Some users prefer a fresh reinstall, in which case you can typically copy settings over from hidden folders (starting with a . character) in your /home, but be careful because newer versions of Xfce and so forth might have some glitches if you use older config files.

---

### Post by WinRiddance on 2012-04-26
> **lukeiamyourfather said:**
> No need to install two operating systems just to try out two desktop environments. Any desktop interface can be installed in any Ubuntu (XFCE, Unity, GNOME, etc.). So just install the other desktop environment and try it out.

**Thanks for the input everyone!**

Question though ... I thought that if you started out with Ubuntu, then you could also install the other desktop environments such as Xubuntu, Kubuntu, Lubuntu, and so on. But ever since Unity was released with Ubuntu, I thought that was no longer possible since Unity had some proprietary settings & customized stand-alone features?

Since I "only" have Xubuntu, I'm concerned that it could break my system if I install Unity on top or with Xubuntu? Hardware is not a problem, it's a quad core 64bit system with 8 GB of ram. I also thought that there were compatibility issues between Ubuntu flavors if you try to use compiz? If I'm not mistaken compiz wouldn't even work with Unity when the first version was officially released ... ??? If I do install Unity along with my existing Xubuntu 11.10 environment, will that provide me with the complete 100% Unity experience?
Any more thoughts on this? Thanks.

.

---

### Post by lukeiamyourfather on 2012-04-27
I don't know about compatibility with Compiz because I don't use it (as far as I know?). Though you can install Unity in any alternate Ubuntu (Lubuntu, Xutunbu, Kubuntu, etc.) by running the command below.

```
sudo apt-get install ubuntu-desktop
```

If you're worried about breaking your current system but have an extra drive just clone your current disk to a spare (with a tool like Clonezilla). Try the install on a clone. If it doesn't work you can just put the original disk back in.

---

### Post by WinRiddance on 2012-04-30
> **lukeiamyourfather said:**
> I don't know about compatibility with Compiz because I don't use it (as far as I know?). Though you can install Unity in any alternate Ubuntu (Lubuntu, Xutunbu, Kubuntu, etc.) by running the command below.

sudo apt-get install ubuntu-desktop

Well, if you didn't at some point intentionally install Compiz then you're not using it since it's not installed by default with 12.04 or earlier versions of Ubuntu. Okay, so earlier I mentioned Xubuntu with Compiz. Well, I really really love the bling & control that I get with Compiz _which is not stable nor endorsed for the Unity Desktop._ Consequently it would be a bad idea to run the Unity Desktop with Compiz on a dedicated working system. I'm going to mark this thread as solved, solved meaning that _the answer is "NO" it is not possible_ to safely run the full-blown 3D Unity Desktop together with full-blown Compiz 3D effects.

**Alternatively though,** it should be possible to save your existing Compiz settings, followed by removing the Compiz application after backing up your /user/.compiz folder first. Now it would be possible to run the Unity Desktop  environment without any conflicting Compiz related issues. Later, if you decide that you want to revert to your Xubuntu environment with Compiz you'd simply restart or log out followed by logging into your Xubuntu desktop again. Then you'd re-install Compiz followed by copying your backed up Compiz settings into the new /user/.compiz folder. Reboot the system and everything should be as it was when you started out, but without Unity. Thanks for all of the input.

.

---

