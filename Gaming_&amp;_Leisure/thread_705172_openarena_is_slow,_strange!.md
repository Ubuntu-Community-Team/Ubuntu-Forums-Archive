---
title: "openarena is slow, strange!"
date: 2008-02-23
forum: Gaming &amp; Leisure
---

### Post by vince-rouge on 2008-02-23
Hello,

a strange situation happen with Openarena : the game is going very slow and I have to play it with the fastest graphic configuration. I don't understand this because when I used to play openarena under Windows (before I erase it and install Unbuntu 7.10 definitly), I used to play with the normal graphic configuration and it was fast enough.

Thanks for your help, it would be gratefull !

Vince

---

### Post by ecimon on 2008-02-23
Hi,

Have you checked if direct rendering is enabled ? 

After running 'glxinfo' you should see something like this:

```

ecimon@sigonmobile:~$ glxinfo | grep direct
direct rendering: Yes
ecimon@sigonmobile:~$

```

---

### Post by vince-rouge on 2008-02-23
Hi,

thanks. it says yes...

what should i do ?

---

### Post by mivo on 2008-02-24
What video card do you have? Do you have the restricted drivers enabled?

---

### Post by vince-rouge on 2008-02-25
Hello,

I have a Intel 855GME chipset (64mo)

---

### Post by kutagh on 2008-02-25
Keep in mind that if you got Desktop Effects on Extra or Custom, that Ubuntu still does those things and slows down the game ;)

Try going System-Preferences-Appearance then go to the tab Desktop Effects and set desktop effects to none, then try running the game again.

---

