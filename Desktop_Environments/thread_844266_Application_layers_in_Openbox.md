---
title: "Application layers in Openbox"
date: 2008-06-29
forum: Desktop Environments
---

### Post by rangalo on 2008-06-29
Hi,

I am actually a Fluxbox user, after seeing some screen-shots here, I decided to give a try to Openbox. 

It looks nice.

I use adesklets and two instances of conky, I have set them up in autostart.sh file. The problem is that  one conky instance of the two and all the (a)desklets stay above my normal windows. 

I also tried setting up application properties in rc.xml like following .. without any success. 

```

    <application class="Conky*">
        <layer>below</layer>
    </application>
    <application name="adesk*">
        <layer>below</layer>
    </application>

```

How should I tell openbox to send all the instances of conky and adesklets to the layer below the normal one ?


[EDIT:] In fluxbox all the adesklets and both the instances of conky stay below normal layer by default, without any application specific settings 


thanks & regards,
Hardik

---

### Post by rangalo on 2008-06-30
- bump  -

---

### Post by Inxsible on 2008-06-30
I don't know about aDesklets..never used it.

But are you sure you have the 2nd conky setup to use ```
own_window yes
own_window_transparent yes
own_window_type desktop
```

---

### Post by rangalo on 2008-06-30
nope ... 

the second conky had

```

own_window_type override

```

Now, I changed it to desktop and it works. Thanks.

Still the adesklts are above the normal layer.

regards,
Hardik

---

### Post by ubernuber on 2008-06-30
man its funny, when silly things like that irritate the crap outta you.

I had the same problem that conky would not be on my desktop and it just didn't occur to me to check my config. I am glad I found this thread :)

---

### Post by Inxsible on 2008-06-30
> **rangalo said:**
> nope ... 

the second conky had

```

own_window_type override

```Now, I changed it to desktop and it works. Thanks.

Still the adesklts are above the normal layer.

regards,
Hardik

I am glad that works. No idea about aDesklets. Never used it. You may wanna check its config files as well.

> **ubernuber said:**
> man its funny, when silly things like that irritate the crap outta you.

I had the same problem that conky would not be on my desktop and it just didn't occur to me to check my config. I am glad I found this thread :) Happens to the best of us :)

---

### Post by rangalo on 2008-06-30
Hi,

aDesklets don't have such option in the configs, but I found that when I once kill all the desklets and then start, they will go to the layer below the normal one.

so, I added following in the autostart.sh and it works.

```

(adesklets  -k && adesklets) &

```

The first command kills all the running desklets.

This solution is weird but it works :)

Moreover, I also noticed that when I restart openbox, from the openbox menu, all the desklets with both the conky come on the layer above normal windows.


regards,
Hardik

---

