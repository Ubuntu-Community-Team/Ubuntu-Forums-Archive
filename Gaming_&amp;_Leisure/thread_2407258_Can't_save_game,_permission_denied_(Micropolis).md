---
title: "Can't save game, permission denied (Micropolis)"
date: 2018-12-01
forum: Gaming &amp; Leisure
---

### Post by matthew883 on 2018-12-01
Hey guys, I got this old computer, it's a Fujitsu lifebook. I don't know what year. It had Windows XP installed on it but I put Lubuntu on it. It's got the latest version of Lubuntu on it, and I am trying to play Micropolis on it and it general works except that when I go to save it won't let me. It says "Permission denied". 

Here is a screenshot.

[ATTACH=CONFIG]281842[/ATTACH]

Can anyone help me?

Full discloser, I am having a lot of issues and will be needing a lot of help in the coming days.

---

### Post by Autodave on 2018-12-01
Are you playing this online or are you running it using WINE? Or ??

---

### Post by Impavidus on 2018-12-01
I don't know micropolis, but I see that the error message reads (not very clearly):```
Unable to save the city to the file named
"/usr/share/games/micropolis/cities/finnegan.cty".
Permission denied
```It's normal that you don't have permission to save anything in /usr/share/... That's how it should be, those directories are for system-wide installation of software. User files, like saved games, belong in the user's home directory. Try to find some way to set the directory where games get saved. It should be something like /home/username/whatever or ~/whatever. The latter is a shortcut for the former.

---

### Post by deadflowr on 2018-12-01
*Thread moved to **Gaming and Leisure***

---

### Post by matthew883 on 2018-12-01
> **Autodave said:**
> Are you playing this online or are you running it using WINE? Or ??

It's native to Linux, built from the source code of the original SimCity.

> **Impavidus said:**
> I don't know micropolis, but I see that the error message reads (not very clearly):```
Unable to save the city to the file named
"/usr/share/games/micropolis/cities/finnegan.cty".
Permission denied
```It's normal that you don't have permission to save anything in /usr/share/... That's how it should be, those directories are for system-wide installation of software. User files, like saved games, belong in the user's home directory. Try to find some way to set the directory where games get saved. It should be something like /home/username/whatever or ~/whatever. The latter is a shortcut for the former.

I don't know how to change the directory. It won't just let me change it from the within the game.

---

### Post by matthew883 on 2018-12-01
Please disregard this post. My computer just isn't working for me right now.

---

