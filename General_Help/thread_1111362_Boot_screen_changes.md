---
title: "Boot screen changes?"
date: 2009-03-30
forum: General Help
---

### Post by letmekilluplz on 2009-03-30
Is there any way to change the boot screen where you pick your os?

I want to change it to say just Windows Vista (Unfortunately) and Ubuntu 8.10

Also after like 20 seconds my computer auto-boots into Ubuntu is there anyway to change that and make it so that it stays at the selection screen?

---

### Post by kanikilu on 2009-03-30
You can do this by editing your /boot/grub/menu.lst file, but for an easier, GUI option, search for, and install the package called StartUp-Manager. Once installed it will be under System > Administration.

---

### Post by letmekilluplz on 2009-03-30
Hmm it says I dont have the privileges to change the menu file and the startup manager wont let me change the OS names

---

### Post by CatKiller on 2009-03-30
> **letmekilluplz said:**
> Hmm it says I dont have the privileges to change the menu file

```
gksudo gedit /boot/grub/menu.lst
```

More information [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by letmekilluplz on 2009-03-30
Ok thanks but which of these can I get rid of or will I need to be able to boot into the recovery modes and stuff?

---

### Post by CatKiller on 2009-03-30
> **letmekilluplz said:**
> Ok thanks but which of these can I get rid of or will I need to be able to boot into the recovery modes and stuff?

I thought you were just changing the displayed names and removing the timeout?

If you want to remove old kernels, remove them with Synaptic/apt-get. Your menu.lst will be automatically updated. If you don't want to remove old kernels, there's no point taking them out of menu.lst.

---

### Post by letmekilluplz on 2009-03-30
What I wanted is for my boot menu to be more user friendly and less cluttered plus remove timeout. What I did was make the uncessary stuff commented so that it wouldnt show and I can always just uncomment it. So now it displays this:

Hello Sean, which operating system would you like to use?
Ubuntu 8.10
Windows Vista

---

### Post by CatKiller on 2009-03-30
> **letmekilluplz said:**
> So now it displays this:

Hello Sean, which operating system would you like to use?
Ubuntu 8.10
Windows Vista

Very nice :)

---

### Post by letmekilluplz on 2009-03-30
> **CatKiller said:**
> Very nice :)

Thanks being of high intellect like you are you probably could figure it out on your own but if you don't know how and want to send me a message

---

### Post by CatKiller on 2009-03-30
> **letmekilluplz said:**
> Thanks being of high intellect like you are you probably could figure it out on your own but if you don't know how and want to send me a message

I barely see it. I only run Ubuntu, so the boot menu doesn't display unless I explicitly ask for it because I've broken something, and there's only a 1 second window to call it up if I do want to.

It's just nice to see the many different ways that people make their computer truly their own.

---

