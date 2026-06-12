---
title: "cant play movies"
date: 2009-05-30
forum: General Help
---

### Post by cowboy7305 on 2009-05-30
iam using ubuntu 8.10 and i think i have downloaded all the files i need to work my movie players 
i can play avi movie files that i burned ages ago before i had trouble 
now i cant play my movies that i have bought more than likely protected ,these are store bought dvds i cant play, not pirated ones 
my player is movie player
any help please

---

### Post by Tipped OuT on 2009-05-30
```
sudo apt-get install ubuntu-restricted-extras
```

Try that, once it's done, tell me if you still can't play your movie.

---

### Post by cowboy7305 on 2009-05-30
ok

---

### Post by cowboy7305 on 2009-05-30
it plays one of my movies but not the other 
the one it cant play just sits there and does not read any thing from disk

---

### Post by c1rcu1t on 2009-05-30
what program are you trying to play them with?

---

### Post by Tipped OuT on 2009-05-30
Put these codes into terminal one by one. Should work after this, make sure to restart you computer after you install this, just in case.
```
sudo apt-get install gst-plugins-base
sudo apt-get install gst-plugins-good
sudo apt-get install gst-plugins-bad
sudo apt-get install gst-plugins-ugly
sudo apt-get install gst-ffmpeg
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------


> **c1rcu1t said:**
> what program are you trying to play them with?
He's using Movie Player.

---

### Post by cowboy7305 on 2009-05-30
Movie player

---

### Post by cowboy7305 on 2009-05-30
E: Couldn't find package gst-plugins-base
this message from trying first one

---

### Post by Tipped OuT on 2009-05-30
> **cowboy7305 said:**
> E: Couldn't find package gst-plugins-base
this message from trying first one

](*,):lolflag:

Try this.

```
 sudo apt-get install libdvdcss2 
```

If nothing still, then you might want to have a look at this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cowboy7305 on 2009-05-30
have already downloaded that 
but did try again it says i have the latest ver

---

### Post by Tipped OuT on 2009-05-30
You have all these installed?

libdvdcss
libdivx
libx264
libdca
libdvbpsi
libdvdplay
libdvbcsa

---

### Post by cowboy7305 on 2009-05-30
libdvdplay
libdvbcsa
these 2 i dont know thy dont show up on synaptic 
and iam still learning ubuntu 
i just like to plug and play lol

---

### Post by c1rcu1t on 2009-05-30
just out of curiosity, what program did you use to burn the .avi files?

---

### Post by cowboy7305 on 2009-05-30
the movie iam having trouble with is called 
NARNIA 
Prince Caspian

---

### Post by cowboy7305 on 2009-05-30
K 3b

---

