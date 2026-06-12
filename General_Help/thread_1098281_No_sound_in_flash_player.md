---
title: "No sound in flash player"
date: 2009-03-16
forum: General Help
---

### Post by Virtualboxbuntu on 2009-03-16
Hello,

I've heard that many people have had problems with flash player and sound. I've done research and found many solutions, but none of them worked.

Basically, flash works normally after installing flashplugin-nonfree, but there's no sound. I installed a lot of programs before trying any flash sounds, so something might have messed it up. When I get a chance I'll see if it works in the live cd.

I'm using Kubuntu 8.10. All other sounds work fine, and, strangely enough, it works on another computer, installed from the same CD.

---

### Post by spcwingo on 2009-03-16
Try installing libflashsupport.

```
sudo apt-get install libflashsupport
```

---

### Post by Virtualboxbuntu on 2009-03-16
> **spcwingo said:**
> Try installing libflashsupport.

```
sudo apt-get install libflashsupport
```

Still no sound.

---

### Post by spcwingo on 2009-03-16
The only other thing I can think to do is to remove pulseaudio and just use ALSA.

---

### Post by Virtualboxbuntu on 2009-03-17
> **spcwingo said:**
> The only other thing I can think to do is to remove pulseaudio and just use ALSA.

Hmm... After logging into another account on my computer, I discovered that sound works. So it's an issue with my account. I've renamed .mozilla, .adobe, and .macromedia but it doesn't make a difference. Do you know of any other folders I should try deleting or renaming?

---

### Post by spcwingo on 2009-03-18
> **Virtualboxbuntu said:**
> Hmm... After logging into another account on my computer, I discovered that sound works. So it's an issue with my account. I've renamed .mozilla, .adobe, and .macromedia but it doesn't make a difference. Do you know of any other folders I should try deleting or renaming?

Maybe .pulse...instead of deleting, try renaming.  That way if it doesn't work just change the name back.  ;)  If renaming that folder doesn't work hopefully someone with a little more experience in audio issues will stop by.

---

