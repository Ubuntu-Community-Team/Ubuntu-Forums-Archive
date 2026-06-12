---
title: "KDE and Gnome 64-bit dependencies"
date: 2010-03-15
forum: Desktop Environments
---

### Post by Pauly BC on 2010-03-15
Hi all,

I had to reinstall on the weekend due to hopeless dependencies with Enlightenment. (Why oh why do I keep chasing that unicorn?!?)

I installed Mint 8 KDE as my default Linux, though I want to also have Gnome as an alternate DE. I like the speed and simplicity of Gnome, plus it offers more applications. I enjoy KDE for its usability and I have enough resources that I don't notice its demands.

Is there a procedure to install Gnome Ubuntu or Mint along side of KDE so I can select the DE during login? Is there a procedure to resolve dependencies in KDE for Gnome programs? Specifically Evolution and Creo guitar effects were not working. I know Synaptec should have resolved the dependencies, but both those programs were non-functional. Evolution would set up the email account but freeze while trying to connect to the server to download messages (network dependency?). Creo worked for me in Gnome but not in KDE (sound daemon?)

Other than that, KDE looks very nice so far!

Thanks,
Paul

---

### Post by Pauly BC on 2010-03-16
bump

---

### Post by Pauly BC on 2010-03-17
bump.

Bueller? Bueller?

---

### Post by 3Miro on 2010-03-17
Is this a Mint or Ubuntu question.

In Ubuntu, you can install 64 or 32 bit Ubuntu and then install the kubuntu-desktop:
```
sudo apt-get install kubuntu-desktop
```

then you can select which one you want on login. (I also have XFCE, install xfce4 if you want it).

Overall, under Ubuntu, right now, KDE is less stable than Gnome. They are trying to fix this for 10.04. The sound problems are the main issue. Sometimes I will have to go to KDE system settings and disable and re-enable the sound hardware to get some programs working. Sometimes I cannot open Gnome and KDE apps to play sound at the same time.

I have never used evolution and I cannot help with it, however, I should note that I have never had issues with Gnome apps using the network under KDE.

---

