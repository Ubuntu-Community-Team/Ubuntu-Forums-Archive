---
title: "Synaptic Hanging"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Geffers on 2006-03-24
I think I read in a thread somewhere about a problem with synaptic ' hanging ' and there was a suggestion to run it in a specific manner.

I cannot find this thread anywhere, can anyone recall or any advice please.

When I use synaptic it appears to install the required program but the main window never refreshes or gives me a result and I end up having the kill synaptic.

Geffers

---

### Post by R3linquish3r on 2006-03-24
```
sudo synaptic package manager
```

---

### Post by Geffers on 2006-03-25
[QUOTE=R3linquish3r]```
sudo synaptic package manager
```[/QUOTE]

Prior to reading your post I tried sudo synaptic but did not include 'package manager'.

I got plenty of HD flashing but nothing appeared on the screen, am I to assume that the extra text of 'package manager' is important.

Geffers

---

### Post by Geffers on 2006-03-25
[QUOTE=R3linquish3r]```
sudo synaptic package manager
```[/QUOTE]

That didn't open it on my machine, disk activity but then nothing.

Geffers

---

### Post by xenmax on 2006-03-25
```
sudo synaptic
```
should be sufficient

You can also try clicking System->Administration->Synaptic Package Manager

Either should prompt you for a password. The password should be your user password, not the root password.

---

### Post by R3linquish3r on 2006-03-25
sudo synaptic doesnt do it for me I have to include thw whole thing.. Then again im using Kubuntu and it could be anal like that.

---

### Post by Matchless on 2006-03-25
Hi,
   Synaptic works perfectly for me in Kubuntu. I suggest you uninstall Synaptic completely using Adept or konsole, then install from the repositories, not the backports and see how it goes.

---

### Post by Geffers on 2006-03-25
[QUOTE=xenmax]```
sudo synaptic
```
should be sufficient

You can also try clicking System->Administration->Synaptic Package Manager

Either should prompt you for a password. The password should be your user password, not the root password.[/QUOTE]

I am the only user at the moment and was under the impression my user password was the same as Root

Geffers

---

