---
title: "Counter Strike Source problem (Steam)"
date: 2013-05-31
forum: Gaming &amp; Leisure
---

### Post by InvasionPT on 2013-05-31
When I saw that was counter strike source compatible for linux / ubuntu I went out and bought, but once you have installed, GL_EXT_texture_sRGB_decode, had this problem if anyone knows how to solve this problem do post, I did not spend 15$ to have a game on steam, but to play it

Thx very much  :smile:

---

### Post by Perfect Storm on 2013-05-31
Which video card do you have?

---

### Post by InvasionPT on 2013-05-31
ATI Mobility Radeon HD 2400

---

### Post by Perfect Storm on 2013-05-31
The minimum requirement for CS: Source is at least  NVIDIA GeForce 8 or higher, ATI X1600 or higher, or Intel HD 3000. Did you check if there are available restricted drivers in Ubuntu?

---

### Post by InvasionPT on 2013-05-31
You mean, buy a new one?

---

### Post by Perfect Storm on 2013-05-31
See my previous post, edited it.

---

### Post by InvasionPT on 2013-05-31
I am a newbie in this kind of stuff , who can i check it?

---

### Post by Perfect Storm on 2013-05-31
> **InvasionPT said:**
> I am a newbie in this kind of stuff , who can i check it?

in Ubuntu 12.04 search dash for additional drivers.
In Ubuntu 13.04 seach dash for software, click Software & Updates. Then click additional drivers.

They keyboard key for Dash is <Windows key> or <Super key>.

---

### Post by Cheesemill on 2013-05-31
What version of Ubuntu are you using?

If it's 12.04.2 or later then you won't be able to run the game as ATI stopped supporting your video card last summer and so don't write Linux drivers for it any more.

The drivers that you need to get 3D working on your card are only available for versions of Ubuntu up to 12.04.1.

---

### Post by InvasionPT on 2013-05-31
My version is 12.04 LTS

---

### Post by InvasionPT on 2013-05-31
hmm , so i need to install a new ubuntu? like version 13.04?

---

### Post by Cheesemill on 2013-05-31
> **InvasionPT said:**
> hmm , so i need to install a new ubuntu? like version 13.04?

No. Newer versions don't have a 3D driver for your card as ATI have stopped supporting it.

Open the 'Additional Drivers' application, is there anything listed?

Also can you open a terminal and post the output of...
```
uname -r
```

---

### Post by Perfect Storm on 2013-05-31
> **InvasionPT said:**
> hmm , so i need to install a new ubuntu? like version 13.04?

Not if you want your card supported for games as ATI dropped support of your card after Ubuntu 12.04.

---

### Post by InvasionPT on 2013-05-31
nope, just one that i am using->  FGLRX ATI/AMD

---

### Post by Cheesemill on 2013-05-31
OK. So you are already running the only 3D driver available for your card.

What errors do you get when you try and run the game?

---

### Post by deri on 2013-05-31
You better post the hole steam console output here. You can ask your question steam/valve git.

---

### Post by Cheesemill on 2013-05-31
The solution can be found on the Steam website. It was the ***top*** result on Google when searching for *GL_EXT_texture_sRGB_decode*.

[http://steamcommunity.com/app/221410/discussions/1/882966057052333152/](http://steamcommunity.com/app/221410/discussions/1/882966057052333152/)

---

### Post by InvasionPT on 2013-05-31
Every time i try to  start it in steam, it shows this -->  Required OpenGL extension "[COLOR=#000000]GL_EXT_texture_sRGB_decode"  is not supported. Please update your  OpenGL driver.
Thats all, and id dont know who to update it or just make it work.[/COLOR]

---

