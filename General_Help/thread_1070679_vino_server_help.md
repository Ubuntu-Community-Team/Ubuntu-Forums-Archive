---
title: "vino server help"
date: 2009-02-15
forum: General Help
---

### Post by opisube on 2009-02-15
Hi,

   Im new here so thanks in advance for any help!
Ive got an Ubuntu box I use as a media server and it has suddenly stopped being accesible from vnc!! The box is still alive as I can still access it by samba , ftp , http etc..

When I hook it up to a monitor it looks like the video card may be dead! Would this cause the vino server to die?

unfortunately this is the method I was using to administer the box!! I havent enabled ssh or telenet!!

Can anybody tell me how I can enable ssh remotely? I do have access to the full file system via samba so could put a script or something on there if somebidy could point me in the right direction!!  

Cheers, Op

---

### Post by fragos on 2009-02-15
Have you configured the Remote Desktop Preferences?

---

### Post by opisube on 2009-02-16
yes, Ive already had the vino server running it just seems to have stopped! And the video card has packed in so I thought this might be related?

Do you know if VNC will work without a working graphics card?

---

### Post by fragos on 2009-02-16
I'd think it would work with any graphics card but slower cards might make themselves known as would slower network connections.

---

### Post by cariboo on 2009-02-16
I don't think vnc will work without X running. You will have to physically access the media server to install openssh-server, then you can use X forwarding to run gui apps on the computer you control the media server from, start ssh like this:

```
ssh -X user@server
```

then at the prompt type the name of the graphical application you want to use.

Jim

---

### Post by bodhi.zazen on 2009-02-16
Well, to be precise, there are several VNC servers.

The default, vino, is one option.

Some vnc servers (vino, x11vnc) require X to be running and/or that you are currently logged in to be able to connect to a shared X session.

Other servers , such as vnc4server, run without X.

If you are running a headless server, learning to install, and secure ssh makes sense.

---

