---
title: "Flash Macromedia Troubles"
date: 2006-07-17
forum: Desktop Environments
---

### Post by El Guapo on 2006-07-17
I am having trouble getting the Flash Macromedia plugin for Firefox to work properly.  I have installed the flashplugin-nonfree package on synaptic and it hasn't changed the status of my flash player.

When I go to this mountain biking site: 

[http://www.specialized.com/bc/home.jsp?a=b&minisite=10020](http://www.specialized.com/bc/home.jsp?a=b&minisite=10020)

I get this message "Oops, looks like you need to update your flash player."  When I click on the provided link it takes me to the Adobe download site: 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

From here I have downloaded this file and installed it and still haven't had any luck.

Can anyone else see this site properly? ](*,)  Am I missing something?

---

### Post by Jagot on 2006-07-17
You could try:

```
sudo update-flashplugin
```

Failing that, it may be that the sites you are trying to visit require Flash 8 which is not available for Linux - only Flash 7.  I would check but I'm not at my Ubuntu box.

---

### Post by autocrosser on 2006-07-17
Yes-I get the same message--Means that it takes Flash 8 that has not been released to Linux yet:-?--The company I work for (brammo.com--maker of the US Ariel Atom) also uses Flash 8--I'm just hoping that Adobe/Macromedia get it in gear soon.

note: Macromedia is now owned by Adobe--no lover of Open-Source--so I don't have my hopes up:???:

---

### Post by vem0m on 2006-07-17
also of note that site might need flash player 8 which there is no linux version of and u are out of luck, i have been to several sites like that. And to top it off flash player 7 for linux is buggy and goes out of sync

*Edit* i went there with my functional Flash plugin and it said the same so i am guessign it indeed requires version 8 which as stated before there is no linux version of.

macromedia will not be releasing a flash player 8 for linux they said they will wait till 9 which is messed up seeing all the problem with the flash 7 they should at least release a fix patch or something

---

### Post by El Guapo on 2006-07-17
Well that sucks...

---

### Post by aysiu on 2006-07-17
If you need it badly, install the Windows version of Firefox using Wine. Then install Flash 8 and Shockwave from there.

---

