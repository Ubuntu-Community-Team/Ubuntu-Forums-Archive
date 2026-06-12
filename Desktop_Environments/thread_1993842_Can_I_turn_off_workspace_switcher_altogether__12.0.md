---
title: "Can I turn off workspace switcher altogether ? 12.04"
date: 2012-06-02
forum: Desktop Environments
---

### Post by userqq on 2012-06-02
Hi, Can I turn off workspace switcher altogether? Preferably with a terminal command. I dont care if I never get it back either.
TY
using precise 12.04

---

### Post by DMGrier on 2012-06-02
why? If you never click on it never turns on.

---

### Post by LiamOS on 2012-06-02
Are you using regular ubuntu with the unity interface?

---

### Post by traditionalist on 2012-06-02
> **userqq said:**
> Hi, Can I turn off workspace switcher altogether? Preferably with a terminal command. I dont care if I never get it back either.
TY
using precise 12.04

It is difficult, and there isn't much point. If you don't want to use it then don't click on it.
However, you CAN remove it if you want to;

[http://askubuntu.com/questions/38789/remove-the-workspace-switcher-launcher-from-unity-launcher](http://askubuntu.com/questions/38789/remove-the-workspace-switcher-launcher-from-unity-launcher)

ANYTHING LIKE THIS CAN BREAK YOUR SYSTEM!

---

### Post by coldjeanz on 2012-06-02
No idea why anyone would ever want to remove it, I can't function without it.

---

### Post by traditionalist on 2012-06-02
> **coldjeanz said:**
> No idea why anyone would ever want to remove it, I can't function without it.

Each to his own.   I think the greatest thing about this system is how you can customise it. Some things may seem silly or useless to some, but if you want to do something you can usually find out how with a  little research.

I do find it rather odd that people become so vehement about some things. If I want to put a bullet through my computer casing with a handgun then that's my affair. It wont affect anybody else, so why should they care?

---

### Post by traditionalist on 2012-06-02
PS.  Sometimes, shooting it seems like the only reasonable solution.............

" A modder's lament" , to the tune of, "Arthur McBride".
 
I bought a computer, my joy and my pride,
till I opened the casing and looked down inside,
when I saw what was in there, I damn nearly cried,
but the casing is pleasant and charming............
 
So off to the chip shop in haste I did stride,
and I took my nice casing along for the ride,
the nice young man there said my hard disc had died,
but the casing was pleasant and charming..........
 
So I bought a new hard disc and a fist-full of RAM,
regardless of cost now, I don't give a damn,
a new CPU then I also did cram,
in my casing so pleasant and charming.............
 
It still did not run well, my reckoning tool,
and the man at the shop said "you've been a right fool,
with all of that stuff in, it needs to stay cool",
in the casing so pleasant and charming.......
 
All of the new stuff was melted and fried,
and the casing still looked nice, but smelled bad inside,
I could not believe it, and very wide-eyed,
I stared at my casing so charming..................
 
So come all you modders and mark well my tale,
it might well save you a rant and a rail,
Beware of fine casings, for affection will pale,
though the casing is pleasant and charming.........

( Not sure this belongs here but it might give somebody in dire straits a laugh! :)  )

---

### Post by stinkeye on 2012-06-03
In unity 3d use ccsm > general options > desktop size 
and change horizontal and vertical virtual size to 1.
Log out/in and workspace switcher will be gone.

---

### Post by hyper2hottie on 2012-06-03
From command line.
```
gconftool --set /apps/compiz-1/general/screen0/options/hsize --type=int 1 gconftool --set /apps/compiz-1/general/screen0/options/vsize --type=int 1
```

If you do this the workspace switcher is still there, but you only have one workspace.

---

### Post by userqq on 2012-06-04
Thank You but these answers seem like they will not completely disable it. 
To anyone who cant understand WHY. I will tell you . I never use it anyway and it often comes on automatically (when using gimp and firefox), or im accidentally hitting a key or whatever **IDK**, I  have never clicked on it not even once, ever and it is frustrating so YES I simply want to completely disable it or completely remove if necessary  in the simpilest way there is.  
I am not interested in simply removing it from the unity launcher, I want it's functions disabled/gone/off.

Im glad that it is working for you but it is not for me,

P.S. I dont like the new 'ALT' key function either. I tend to hit that key by accident sometimes and 'wham' there it is.

Also thank you for the poem although It is not relevant in this case as I do think the dev's could have made a simple option to disable it. a simple 'off' switch. If they want something as a default,built in thing it needs to NOT come on when I dont ask it to. I have absolutely no desire to "customise" anything, Im only trying to do this because Im sick of it coming on when I dont want it to.

Anyone else who has a better way or idea please post it here.
Thanks everyone.

---

### Post by nll on 2012-06-04
In 12.10 the workspaces will be off by default and the users who want to use them will have to install it. I'm not sure that's the best decision though.

---

