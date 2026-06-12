---
title: "Nomachine Help - With Using Gnome Desktop"
date: 2014-03-10
forum: Desktop Environments
---

### Post by amb1s12 on 2014-03-10
Hi, I'm creating a media server and I'm using Ubuntu 12.04 with the Gnome Desktop. I already have all of the software install on my server using gnome gui. I have no machine server install on Ubuntu and it work fine when I have a monitor plug in, but when I have the server without a monitor and I reboot the server, I can't get in. I know that since the server don't have the Monitor, the server won't use the gui. My question is how to setup nomachine that when I reboot the server without a monitor I can use no machine to login into the user that I have of the media service? Thanks in advance

---

### Post by phidia on 2014-03-10
I believe you want to have remote access to your server. That way you can manage/configure things from a laptop or desktop computer.
Check out the how to [here]("https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20(XenAPI)%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager").

---

### Post by bobbrown55518 on 2014-03-13
> **amb1s12 said:**
> My question is how to setup nomachine that when I reboot the server without a monitor I can use no machine to login into the user that I have of the media service? Thanks in advance

You need to make sure you have installed the Workstation, not the free NoMachine for Linux package. Alternatively, if you are using headless, you can use this article here to set up your Linux media server: [https://www.nomachine.com/AR10K00710](https://www.nomachine.com/AR10K00710)

---

### Post by amb1s12 on 2014-03-16
I installed free nomachine on the linux box and I follow the article and I'm able to remote using nomachine client from my mac, but the problem now is that I'm cant access my external HD. I'm getting "unable to mount HD2 not authorized". When I login using a monitor and using the same username and password that I use on the nomachine, I'm able to navigate inside the HD2 drive. How can I fix that?

---

