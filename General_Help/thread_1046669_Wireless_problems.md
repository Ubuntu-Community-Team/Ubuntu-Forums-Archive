---
title: "Wireless problems"
date: 2009-01-21
forum: General Help
---

### Post by rryk.ua on 2009-01-21
I am not sure where this question belongs, but since it's somehow connected to Wubi I decided to post it here. If I'm wrong - please move it to other section.

So, here is my story. I use Toshiba Satellite Pro P300-1CG with Atheros AR9281 Wireless Network Adapter. Windows Vista was pre-installed. Some time I decided to install Ubuntu and had no problems except that my wireless card didn't work. After some research I abandoned that installation, since I have no other access to Internet than via wireless and no solution seemed to work. Recently I've downloaded Windows 7 Beta distribution and Wubi installer. I decided to install both of them. Wubi was the first. I was very very smooth setup and what a good news - wireless was working out of them box. After some updates and package installations for Wubi, I went to install Windows 7 Beta. Everything was fine until I found out that for some reason my wireless is not working under Windows 7, so just decided to reboot back to Vista. However wireless didn't work in Vista either. I removed Windows 7 Beta, tried to reinstall drivers for wireless from both Atheros and Toshiba websites. Nothing helped. In Wubi everything works fine. Windows sees the card and recognizes the driver for it, however it shows yellow exclamation mark (conflict) next to it in Device Manager (see attached image, and says, that "This device cannot be started. (Code 10)").

So question is - is that possible that Ubuntu changed some settings, so I cannot use my wireless in Vista now? What can be done to enable wireless. As you can see on the image some other conflicts in Device Manager also appeared. For Marvell Yukon the conflict message is the same, and for OHCI is says "There is no free resources for this device. (Code 12). If you want to use this device you have to deactivate some other devices...".

I think this is the origin of the problem, since it looks like a bus (and I suspect it to be bus for network adapters). I tried to deactivate some other devices, but without any success.

Thank you.

P.S. I have German Vista, so messages are translated. There are original texts if needed:

Fur dieses Gerat sind nicht genugend Ressourcen verfugbar. (Code 12)
Wenn Sie dieses Gerat nutzen mochten, mussen Sie ein anderes Gerat mit Anschluss an den Computer deaktivieren.
Sie mussen den Computer neu starten, damit die am Gerat vorgenommenen Anderungen wirksam werden.
Klicken Sie auf "Problembehandlung", um Daten zu diesem Gerat an Microsoft zu senden und zu prufen, ob eine Losung verfugbar ist.
------------------------------------------------------------
Das Gerat kann nicht gestartet werden. (Code 10)
Klicken Sie auf "Problembehandlung", um Daten zu diesem Gerat an Microsoft zu senden und zu prufen, ob eine Losung verfugbar ist.
------------------------------------------------------------
Das Gerat kann nicht gestartet werden. (Code 10)
Klicken Sie auf "Problembehandlung", um Daten zu diesem Gerat an Microsoft zu senden und zu prufen, ob eine Losung verfugbar ist.

---

### Post by azmo35 on 2009-01-22
Mate your problem is with vista so you should take that problem to vista forum about wubi we not change nathing on the hardware that vista need so if you have wibi working 100% stick on it, is much beter than vista.

---

### Post by rryk.ua on 2009-01-22
I understand that, but wireless stopped to work exactly after Wubi installation (or after Windows 7 Beta - I don't know since I didn't check it in between). Since you know Wubi and Ubuntu best here - the question is if this can be origin of a problem? Can it have changed some BIOS configuration (e.g. changed IRQ's)? Is that possible that somehow Wubi installation have influenced Windows installation?

> ...so you should take that problem to vista forum ... 
I did that exactly before posted this here, but no reply yet.

> ...if you have wibi working 100% stick on it, is much beter than vista.
I do use Ubuntu now, since it's working faster and I like it, but I still need to use Visual Studio and some other stuff in Windows. Unfortunately the license for Windows I have allows me to install it only to laptop directly and not to Virtual Box or any similar program.

---

### Post by azmo35 on 2009-01-22
Hi,again have you tryed similar programs on ubuntu and if you wanted that software on ubuntu use wine.If you try rum virtual box i think you have a problem on that because wubi is kind of virtual.

---

### Post by rryk.ua on 2009-01-22
> Hi,again have you tryed similar programs on ubuntu and if you wanted that software on ubuntu use wine.If you try rum virtual box i think you have a problem on that because wubi is kind of virtual.

Visual Studio is highly integrated IDE for C#, C++, Visual Basic and ASP.NET development. Unfortunately there are no development system for C# on any Linux system since Linux is not able to run .NET programs (Mono framework for this is still not perfect). Moreover, it's always useful to have Windows installation nearby (e.g. for testing).

I want to switch Wubi to dedicated partition, so there would be no problems with virtualization. I have some problems with that, but I'd rather first look for solution online rather than bother anyone. :)

---

### Post by directhex on 2009-01-22
> **rryk.ua said:**
> Unfortunately there are no development system for C# on any Linux system since Linux is not able to run .NET programs

Flat-out fabrication.

You have 2 apps written in C# on your default Ubuntu desktop.

---

### Post by rryk.ua on 2009-01-22
> You have 2 apps written in C# on your default Ubuntu desktop.

Really? Did I missed something or Microsoft ported their .NET framework onto Linux platform?

Anyway - I still need Windows for some programs (e.g. Skype). Yes, I know there is a version for Linux, however it doesn't have all features of Windows variant. And I need Windows for testing.

---

