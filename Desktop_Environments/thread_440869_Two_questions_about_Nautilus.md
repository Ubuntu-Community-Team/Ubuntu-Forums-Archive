---
title: "Two questions about Nautilus"
date: 2007-05-12
forum: Desktop Environments
---

### Post by element42 on 2007-05-12
1) I use Thunderbird as my email program, so the option in the Nautilus context menu 'send to' won't work. How can I remove it from the menu?
2)Music files aren't previewing. I've checked the prefs menu and they certainly should be, but when I hover, I hear nothing. (I have ubuntu installed on my laptop and it works on that!). Can anyone tell me why this isn't working?

Thankyou!

---

### Post by benanzo on 2007-05-12
I can't answer the thunderbird problem, but I think you have to have mpg123 installed to preview audio in nautilus

```
sudo apt-get install mpg123
```

I don't know why it's not installed by default, or why they don't just change nautilus to use something that is installed by default for previewing.

---

### Post by jfinkels on 2007-05-12
I think ```
sudo aptitude remove nautilus-sendto
```should do the trick.

---

### Post by mcduck on 2007-05-12
> **benanzo said:**
> I can't answer the thunderbird problem, but I think you have to have mpg123 installed to preview audio in nautilus

```
sudo apt-get install mpg123
```

I don't know why it's not installed by default, or why they don't just change nautilus to use something that is installed by default for previewing.

That works for MP3, for OGG get the vorbis-tools package.

---

### Post by element42 on 2007-05-12
Thanks for the help.
I've managed to get ogg files previewing now (except if it's selected!?), but flac files still aren't working - I guess I need another package - which one though? flac will play in my applications okay...
[EDIT] ah, it seems that previewing flac, or failure to do so, is a known nautilus bug. never mind. Very strange though that it works on my laptop with feisty. Mind you i have kubuntu-desktop as well on the laptop, perhaps that makes the difference. hmm, can't see how though ...
[FURTHER EDIT]just checke my laptop. it doesn't in fact preview flac. it does do mp3 and ogg though. so there we go :-|

Also, I have removed the nautilus-sendto. I had to remove ubuntu-desktop too, which apparently could cause problems with dist-upgrade, but I can always fix that by re-installing ubuntu-desktop (or doing a fresh install I guess). Am I right in thinking that it's not going to cause any other probs?

Thanks again.

---

