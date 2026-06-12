---
title: "Can't install app from repository in university wireless network"
date: 2009-03-23
forum: General Help
---

### Post by tsynfeng on 2009-03-23
Hi guys,

When I tried to install apps in synaptic from my univeristy's wireless network, it seems that ubuntu can't download packages in that wireless network. I can download things from normal websites though.

I know that it most likely is an issue on my uni's side. But anyone had the same problem and found a way around it?

Cheer
Feng

---

### Post by 3Miro on 2009-03-23
If you start synaptic from the Terminal, do you get any error messages?

---

### Post by tsynfeng on 2009-03-24
> **3Miro said:**
> If you start synaptic from the Terminal, do you get any error messages?

No, I ddin't get any error messages from terminal. I tried both synaptic and apt-get, both can find package information and dependencies, but they just can't download, always stuck at 0%.

Strangely, I can download from [http://packages.ubuntu.com](http://packages.ubuntu.com) manually, but can't download through any package manager in the university wireless network.

Everything works fine at home.

---

### Post by mocoloco on 2009-03-24
Maybe try changing the server you're getting packages from: System -> Administration -> Software Sources.  The drop down box on the first tab.

---

### Post by dcstar on 2009-03-24
> **tsynfeng said:**
> 
........
Strangely, I can download from [http://packages.ubuntu.com](http://packages.ubuntu.com) manually, but can't download through any package manager in the university wireless network.

Everything works fine at home.

Do you use a Proxy Server at home?

---

