---
title: "how to install gnome on wsl"
date: 2022-05-14
forum: Desktop Environments
---

### Post by chat-4432 on 2022-05-14
I search YT and found only the gwsl method 
that can run an app in GUI
but I need to install ubuntu-desktop 
how to install that ??

---

### Post by ActionParsnip on 2022-05-15
[https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/](https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/)

Why are you wanting to install a desktop environment? What are you wanting to do in the Linux desktop system in WSL?

---

### Post by chat-4432 on 2022-05-15
> **ActionParsnip said:**
> [https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/](https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/)

Why are you wanting to install a desktop environment? What are you wanting to do in the Linux desktop system in WSL?
I think it is hard to manage files I'll be welcome if you advise the CLI command.

---

### Post by ActionParsnip on 2022-05-15
> **chat-4432 said:**
> I think it is hard to manage files I'll be welcome if you advise the CLI command.

You can mount NFS or SFTP in Windows and manage files remotely. You don't need a desktop to manage files.

---

### Post by grahammechanical on 2022-05-15
I do not need Windows Subsystem for Linux. I have only read a little about it. I do not think that Microsoft developed WSL for the purpose of allowing a fully functional Linux distribution to run on Windows. A person would use a Virtual Machine for doing that. As I understand it the purpose of WSL is to make it more convenient for Windows users to develop applications for Linux server systems using Linux tools on Windows. The alternative would be for the developer to switch to using Linux completely. Which Microsoft does not want.

I also understand that it is possible to use Linux GUI apps on WSL. There is no need for the full Ubuntu desktop to do this. Microsoft explains how to do it.

[https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

Regards

---

### Post by chat-4432 on 2022-05-15
> **grahammechanical said:**
> I do not need Windows Subsystem for Linux. I have only read a little about it. I do not think that Microsoft developed WSL for the purpose of allowing a fully functional Linux distribution to run on Windows. A person would use a Virtual Machine for doing that. As I understand it the purpose of WSL is to make it more convenient for Windows users to develop applications for Linux server systems using Linux tools on Windows. The alternative would be for the developer to switch to using Linux completely. Which Microsoft does not want.

I also understand that it is possible to use Linux GUI apps on WSL. There is no need for the full Ubuntu desktop to do this. Microsoft explains how to do it.

[https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

Regards
Ok, I'll go with VM can you recommend which VM is the best in performance ??

---

### Post by DuckHook on 2022-05-16
> **chat-4432 said:**
> Ok, I'll go with VM can you recommend which VM is the best in performance ??
I can tell you which Linux VMs that I prefer, but since you are looking for VMs on Windows hosts, perhaps you would have better luck asking on a Windows forum.

Please do not interpret the comments here as trying to dissuade you from running Ubuntu. We welcome you to the Ubuntu ecosystem with warmth and hospitality. I believe that my fellow forum members are struggling with the same issue that I am: on these forums, we try to provide the best solution to the larger underlying problem; not just the immediate surface problem.

[LIST=1]
[*]If you want to install Ubuntu to educate yourself about Linux and to use all aspects of the operating system, then installing it in a VM is a great way to go.
[*]If you just want to manipulate files as stated in your post #3, then installing a full desktop environment is like building a battleship to sail you across a pond.
[*]As for CLI tools that can manipulate files, I recommend Midnight Commander which is still an awesome ncurses&#8209;based old standby that works wonderfully well. It is light, fast, intuitive and easy to learn and use.
[/LIST]
Perhaps it would help if you provide us with details and a full context. What are your larger end goals? Surely it is more than just manipulating files. There are many simple apps that will do that. Since you insist on installing a full Desktop Environment, I assume that you have much larger goals in mind. What are those?

---

### Post by mr-scott-beamer on 2022-06-06
> **chat-4432 said:**
> Ok, I'll go with VM can you recommend which VM is the best in performance ??

Are you running Windows 11 or Window 10?   If you're running Windows 10, [VirtualBox ]("https://www.virtualbox.org/")is a popular choice.

If you're running Windows 11, your best choice is Microsoft's own [Hyper-V]("https://www.makeuseof.com/windows-11-enable-hyper-v/"). [VirtualBox ]("https://www.virtualbox.org/")on Windows 11 is barely functional.

Hyper-V is technically only offered on Windows 11/10 Pro or Enterprise. If you're running Windows 11 Home, about the only option I'm aware of is VMware. It's possible to install Hyper-V on Windows 11 Home with [some hacking]("https://www.virtualbox.org/"), but it's not supported by Microsoft.

VMware [Workstation Pro]("https://www.vmware.com/products/workstation-pro.html") or [Workstation Player]("https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html") are also options (the former costs money, the latter doesn't.

 Although Workstation Player has limited functionality.

---

