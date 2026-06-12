---
title: "UFO:AI save game error"
date: 2008-01-11
forum: Gaming &amp; Leisure
---

### Post by TCDude on 2008-01-11
I have been playing UFO:Ai for the past few days but cannot seem to save. I am running UFO version 2.1.1. When I try to save after a battle it simply says "Error saving game - Size mismatch cannot save game"  I have no clue what is wrong or how to fix it because everything  else in the game seems to work just fine. Thanks for any help that you can offer.

---

### Post by pablobm on 2008-01-13
I had the same problem and I assume its a problem of privileges when saving the files.  It works fine if you start the game from terminal as superuser 
```
sudo ufoai
```

I am sure the smart thing would be to change the privileges of the save folders for the game but I installed the game this evening so I still need to figure out where it is.

Awesome game!

---

### Post by TCDude on 2008-01-13
Awesome! thanksf or the tip. It worked and then when I updated it worked perfectly.

---

### Post by darkmane on 2008-02-01
I wouldn't advise running anything using admin privileges via sudo for anything that doesn't require them.

I had a similar problem when I installed UFO:AI yesterday. The solution is quite simple, and as pablom suggested, its a problem of file privileges.

All you need to do is:- open a terminal (Make sure you are in your home directory, you should be by default. If you are unsure just type, cd ~ ), and type the following at the prompt.

```
 sudo chown -R [username] .ufoai
```

Where [username], is your username.

You will now be able to save your game, without having to run the game with admin privileges.

> **pablobm said:**
> I had the same problem and I assume its a problem of privileges when saving the files.  It works fine if you start the game from terminal as superuser 
```
sudo ufoai
```

I am sure the smart thing would be to change the privileges of the save folders for the game but I installed the game this evening so I still need to figure out where it is.

Awesome game!

---

