---
title: "Ubuntu logs out randomly while playing stepmaina"
date: 2009-09-03
forum: Gaming &amp; Leisure
---

### Post by xxterry1xx on 2009-09-03
Hey i just downloaded Stepmaina(Linux version) and got all the video game mix's and when i play a song on heavy and sometimes Ubuntu logs out randomly i don't know why. but any help?

---

### Post by hikaricore on 2009-09-03
This would be a video driver issue, a memory issue, or a problem with the game doing something bizzare.
The precompiled Linux version of Stepmania (last I checked) was quite old, you should consider downloading and compiling the svn and seeing if you still have trouble.

Alternatively you could launch the game from say tty1 like such:  DISPLAY=:0 stepmania
Then switch back over to tty7 (which is X) and play until it crashes X or as you put it "logs out".
After this occurs you could switch back to tty1 and see what error the game crashed with if any, this would rule out the game as a cause.

---

### Post by xxterry1xx on 2009-09-03
> **hikaricore said:**
> This would be a video driver issue, a memory issue, or a problem with the game doing something bizzare.
The precompiled Linux version of Stepmania (last I checked) was quite old, you should consider downloading and compiling the svn and seeing if you still have trouble.

Alternatively you could launch the game from say tty1 like such:  DISPLAY=:0 stepmania
Then switch back over to tty7 (which is X) and play until it crashes X or as you put it &quot;logs out&quot;.
After this occurs you could switch back to tty1 and see what error the game crashed with if any, this would rule out the game as a cause.

Well i have the nvidia driver 180.00 or something but if i switch to the latest thats 185.00 or whatever the last numbers are, will it not mess anything up cause my friend installed it and it messed up his ubuntu so i aint a ubuntu geek yet i mean im a windows geek(i mean like expert) but switched to linux from windows cause i wanna learn more about linux so idk how to do those commands yet.but i need help......  alright so 10 mins later i found stepmaina people say is pre compiled  [http://www.getdeb.net/app/StepMania](http://www.getdeb.net/app/StepMania) so ill give this one a try i guess see if it will work or not..... nvm it never worked

---

