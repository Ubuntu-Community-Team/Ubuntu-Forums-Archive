---
title: "VirtualBox with XP, need to move files!"
date: 2009-04-21
forum: General Help
---

### Post by vidus on 2009-04-21
I have installed virtualbox and a very barebones copy of xp for the sole purpose of running photoshop. I need to move the photoshop files over to the "c" drive or where ever so I can install it.

I have read about mapping the network drive on my computer or whatever but networking is not available on the xp because it says my hardware isnt there. Probably because it doesnt have a driver or something but I cant get any files into xp...

I have shared my home folder in virtual box... but that does nothing.

What can I do? XP is useless if I cant share files

---

### Post by juancarlospaco on 2009-04-21
Use VBox Gust Aditions
PC <----> VBox

Use an USB Pendrive.
PC <----> VBox

Use Dropbox.
PC <----> VBox

---

### Post by bodhi.zazen on 2009-04-21
You can use any number of options. Shared flash drive, shared folders, or any network protocol (samba, ftp, http, nfs, ssh (scp) ).

I advise samba or a shared flash as both should work out of the box.

---

### Post by amingv on 2009-04-21
Asuming you set up the shared folder correctly in virtualbox:

In XP:

Start>Run>Type cmd

in the console type

```
net use X: \\vboxsvr\<nameofyourfolder>
```

Wait for the "command completed successfully" message and you should have a network drive "X:" under My Computer. It should work even if your NIC isn't set up.

---

### Post by vidus on 2009-04-21
thanks for the tips so far..

there is no internet connection, networking deosnt work, usb doesnt work, and shared folders arent showing. so i dont know what good it is to have xp

---

### Post by bodhi.zazen on 2009-04-21
What version of Virtualbox are you using ? I suggest you simply use the PUEL version you download from teh sun site directly and NOT the ose.

And if networking is probably "mis configured" , use a bridged network interface rather then NAT.

---

### Post by Slim Odds on 2009-04-21
The shared folders work just fine in OSE or PUEL

---

### Post by vidus on 2009-04-21
meh.. virtualbox didnt work.

i just downgraded from cs4 to cs2 and installed it in wine.. still buggy, but at least i can get my work done.

---

### Post by Slim Odds on 2009-04-21
> **vidus said:**
> meh.. virtualbox didnt work.Care to give any details.....?

---

### Post by cornstalk on 2009-04-24
> **vidus said:**
> I have installed virtualbox and a very barebones copy of xp for the sole purpose of running photoshop. I need to move the photoshop files over to the "c" drive or where ever so I can install it.

I have read about mapping the network drive on my computer or whatever but networking is not available on the xp because it says my hardware isnt there. Probably because it doesnt have a driver or something but I cant get any files into xp...

I have shared my home folder in virtual box... but that does nothing.

What can I do? XP is useless if I cant share files

You say your shared folder does nothing.  Does the directory actually exist on the host machine?  Have you run the "net use" command from a dos window to get windows to recognize the shared folder?

What do you mean that networking isn't available on the host machine?  Can you reach the internet from the windows guest?  Can you reach it from the host?  In general a virtualbox install will recognize the networking capabilities of the host machine and make them accessible to the guest.

Virtualbox has a website, perhaps you should look there for the answer to the question of why you can't reach the network.

---

### Post by JerichoDefeated on 2009-06-02
Thanks amingv. did what you said and it works great for me.
Oh, and by the way the newest version of virtual box, which is what i have, is the easiest to use and works the best, for me anyway.

Thanks again amingv, Josh

---

