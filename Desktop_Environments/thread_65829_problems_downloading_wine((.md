---
title: "problems downloading wine:(("
date: 2005-09-15
forum: Desktop Environments
---

### Post by jervine on 2005-09-15
we are having troubles in downloading and compiling wine.. could anyone pls teach me an alternate way in retrieving wine.... we are running an internet cafe and we need windows application/games badly... pls help us and of course we are new to linux.. ](*,)  ](*,)  ](*,)

---

### Post by dave9191 on 2005-09-15
Where are you downloading it from ? There is no need to compile it yourself. You can fetch it from the repositories using the synpatic program or the following command

sudo apt-get install wine

But you need to enable the extra repositories before it will work, otherwise you will get a package not found message. You can learn how to add repositories at ubuntuguide.org. 

Dave

---

### Post by jervine on 2005-09-15
[QUOTE=dave9191]Where are you downloading it from ? There is no need to compile it yourself. You can fetch it from the repositories using the synpatic program or the following command

sudo apt-get install wine

But you need to enable the extra repositories before it will work, otherwise you will get a package not found message. You can learn how to add repositories at ubuntuguide.org. 

Dave[/QUOTE]

I already did both... but an error message is always appering or when the downloading is near 100% it always fail... i am downloading it at wine.sourceforge.net/apt/ i used synaptic and apt-get command but it is the same... and i cant download winetools... when i use wine all that come out is text or binary files... how could i make it work either... do i need a directory for windows file.. does windows installation files work on wine??  ](*,)  ](*,)  ](*,)

---

### Post by dave9191 on 2005-09-15
What is the error that you get with apt-get ?

And some windows programs work with wine and others dont. Ive only ever tried two programs. winzip for the hell of it worked and dreamweaver failed. 

Dave

---

### Post by jervine on 2005-09-15
[QUOTE=dave9191]What is the error that you get with apt-get ?

And some windows programs work with wine and others dont. Ive only ever tried two programs. winzip for the hell of it worked and dreamweaver failed. 

Dave[/QUOTE]
It says failed to get some archived files... and why i cant run ragnarok online on linux??? it cannot patch other files.. but i only copy it on a windows based comp... it is already patched by the way. but it wont start.. do you have any idea how to tweak it.. thanks a lot mister..

---

### Post by dave9191 on 2005-09-15
Try getting it again using apt-get. It might have been a temp problem. And Ragnork is a windows game, so you will have a hard time getting it to run. Although you could try cedega instead of wine. Its not free tho. But it does have ragnork listed. 

[http://transgaming.org/gamesdb/games/view.mhtml?game_id=3532](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3532)

Dave

---

