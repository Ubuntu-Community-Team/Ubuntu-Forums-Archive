---
title: "Need to restore gnome panel"
date: 2009-07-06
forum: Desktop Environments
---

### Post by c-m on 2009-07-06
I installed 9.04 netbook remix on my girlfriends laptop. She accidentally deleted the top pannel in gnome. 

How can i restore the original panel as it is by default? 

I have tired creating a new panel but I cannot add all the default menus and applets onto it e.g the network manager, system menu etc..

Thanks

---

### Post by mhgsys on 2009-07-06
open a terminal and type:

```


gconftool-2 --recursive-unset /apps/panel

```
and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```

 
sudo /etc/init.d/gdm stop


```
```

sudo /etc/init.d/gdm start

```

---

### Post by c-m on 2009-07-06
Worked - thanks

---

### Post by mhgsys on 2009-07-06
nice, 

your welcome.

---

### Post by Pat Benson on 2009-09-28
Hello

I just tried this and I can't get the panels back :(

Switched from "Desktop Netbook mode" to "Classic mode" and panels was lost. Using a Acer Aspire one with the netbook remix, please help.

---

### Post by mhgsys on 2009-09-29
> **Pat Benson said:**
> Hello

I just tried this and I can't get the panels back :(

Switched from "Desktop Netbook mode" to "Classic mode" and panels was lost. Using a Acer Aspire one with the netbook remix, please help.


I strongly suggest you open a new thread, this one dates from july.

---

### Post by CongoJim on 2009-09-29
> **mhgsys said:**
> I strongly suggest you open a new thread, this one dates from july.

Not meaning to be rude but, there's a dog in that avatar? Where?

---

### Post by GeorgeVita on 2009-10-04
Hi **CongoJim**,
Read: [http://ubuntuforums.org/showpost.php...7&postcount=13](http://ubuntuforums.org/showpost.php...7&postcount=13)
the bug: [https://bugs.edge.launchpad.net/desk...er/+bug/349519](https://bugs.edge.launchpad.net/desk...er/+bug/349519)

Hi **mhgsys**,
although 'old' this thread, hit by my search and 'reveal' my lost top panel.  Thanks!

Regards,
George

---

### Post by mhgsys on 2009-10-07
> **CongoJim said:**
> Not meaning to be rude but, there's a dog in that avatar? Where?


@CongoJim
Lol, 

Yeah, that avatar is my dog. 

Can't you see.?

He's having his pows on his face and his mouth wide open.

@George; Good to know it worked for you, and even better you used the search function instead of opening a new thread. 
2 many people do that.

---

### Post by inearlygaveup on 2009-11-01
Just updated to Xubuntu 9.10 and my Panels have gone, any idea how to get them back

---

### Post by mhgsys on 2009-11-04
@inearlygaveup 

open a terminal and type;
```

killall xfce4-panel

```

after that;
press alt and F2 and type> ```
xfce4-panel
```

Your panels should be back,

---

### Post by inearlygaveup on 2009-11-04
thanks for your help - like your cat & dog ):P

---

### Post by mhgsys on 2009-11-06
@inearlygaveup


You're welcome.

;)

---

### Post by MartinHansell on 2009-11-27
This post will never be old - thanks for the tips!

Eeerrrrr.. is that an avatar in your dog?

Martin - great widsom!  lovely humour!!  
And remember, "remember" can sound a little condescending don't you think?  
Ruins an otherwise super saying - at least for me anyway :-(  
Glad you found your icons!

Martin (also)

---

### Post by inearlygaveup on 2009-11-27
point taken
I often forget to follow my own advice

---

### Post by mhgsys on 2010-05-15
.ignore this
I'm posting in the wrong thread now

---

### Post by mhgsys on 2010-05-15
whoops.. wrong thread again.

srry

damn;

---

### Post by brettybaby on 2010-07-26
> **c-m said:**
> Worked - thanks

worked for me too;  some one deleted the panels :(

---

