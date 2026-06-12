---
title: "speed up 8.10 on 700MHz Celeron"
date: 2009-03-02
forum: General Help
---

### Post by swimon on 2009-03-02
Hello,

I installed xubuntu 8.10 on my celeron 700Mhz (coppermine) with 247,6MB RAM. But I guess I thought it would run a little bit smoother, so what are my options to speed things up a little?

I searched the forum and found a couple of possible solutions, I'd like to have some feedback on these:

**1. use fluxbox instead of xfce**
But i'm not really sure what to expect from this, I 've read a couple of times that "the feel" is completely different than what i'm used to, but i'm not sure what that means. :)

**2. use xvesa instead of xorg**
I'm not entirely sure what this means, but how about this solution?

**3. maybe add a little bit of extra RAM?**
Is my RAM the biggest bottleneck of my system? Or is my processor slowing everything down?

**4. changing the theme**
I think xubuntu looks really great, but most of the time good looks cost a lot of resources. So maybe changing the theme to a normal one would improve my speed?

Thx, Grtz!

---

### Post by Vaphell on 2009-03-02
3. yes. You almost instantly hit swap. I recently installed xu on similar hardware with 384M of RAM and it was pretty smooth.

---

### Post by swimon on 2009-03-02
okay, i hope the ram that is in this system hasn't become to rare and thus expensive :)

thx for the reply.

---

### Post by entr3p on 2009-03-02
> **swimon said:**
> Hello,

I installed xubuntu 8.10 on my celeron 700Mhz (coppermine) with 247,6MB RAM. But I guess I thought it would run a little bit smoother, so what are my options to speed things up a little?

I searched the forum and found a couple of possible solutions, I'd like to have some feedback on these:

**1. use fluxbox instead of xfce**
But i'm not really sure what to expect from this, I 've read a couple of times that "the feel" is completely different than what i'm used to, but i'm not sure what that means. :)

**2. use xvesa instead of xorg**
I'm not entirely sure what this means, but how about this solution?

**3. maybe add a little bit of extra RAM?**
Is my RAM the biggest bottleneck of my system? Or is my processor slowing everything down?

**4. changing the theme**
I think xubuntu looks really great, but most of the time good looks cost a lot of resources. So maybe changing the theme to a normal one would improve my speed?

Thx, Grtz!

Number 3 is the best choice. Ram doesn't cost a lot these days and it makes a huge difference in performance. With the other options you will gain some performance gain but truly not even that much.

---

### Post by mrreality13 on 2009-03-02
ok heres my ideas for all 4

#1-fluxbox will help a bit but prolly not worth the small gain.to try flux you may wana d-load linux mint 5 ce its the default so you can "test" from live cd```
http://www.linuxmint.com/edition.php?id=29
```

#2-it depends on video do you use on board or a vid card?if on board yes if card prolly stick with xorg

**#3-ram **_always_** helps 

#4-shouldn't really matter imo

and a little thing i do is- i dont do alot woth openoffice so i got abiword to replace it

---

### Post by swimon on 2009-03-03
okay thanks, i'll definately look for some extra RAM.

The PC i'm working with has an onboard graphic chip. So I should change from xorg to xvesa?

Can anybody try to explain what this actually means? What consequences will this have?

Grtz & Thx for the help so far.

---

### Post by swimon on 2009-03-05
sorry to bump this, but i'd like to try a little more stuff on this PC in the weekend, 

so does anybody recommend using xvesa instead of xorg? and also, I have no idea on how to start to do this, so if anybody could direct my to a tutorial of some kind, that would be very helpful.

grtz, Thx!

---

### Post by xX-Felipao-Xx on 2009-03-05
> **swimon said:**
> sorry to bump this, but i'd like to try a little more stuff on this PC in the weekend, 

so does anybody recommend using xvesa instead of xorg? and also, I have no idea on how to start to do this, so if anybody could direct my to a tutorial of some kind, that would be very helpful.

grtz, Thx!

Hey, I use Fluxbox, and let me tell you that it can look great, and is a very light window manager.
In my case, consumes 8% of my RAM after booting (boot lasts less than 4 seconds, really) which in my case (1024MBs RAM) means 81MBs.

With emesene, firefox and a music player doesn't exceeds 22% (225 MBs)

Here you are, my screenshots of my Fluxbox config:

[http://ubuntuforums.org/attachment.php?attachmentid=105354&d=1236222628]("http://ubuntuforums.org/attachment.php?attachmentid=105354&d=1236222628")

[http://ubuntuforums.org/attachment.php?attachmentid=105355&d=1236222628]("http://ubuntuforums.org/attachment.php?attachmentid=105355&d=1236222628")

---

### Post by swimon on 2009-03-14
i'll definitly try installing fluxbox,

but first i'd like to install xvesa, but i can't find a tutorial or something anywhere, 

would someone plz show me where i can find a tutorial?

grtz

---

### Post by kerry_s on 2009-03-14
> **swimon said:**
> i'll definitly try installing fluxbox,

but first i'd like to install xvesa, but i can't find a tutorial or something anywhere, 

would someone plz show me where i can find a tutorial?

grtz

you don't need xvesa, xorg is better, just use lighter apps.
i run on 450mhz 256mb ram. i use jwm.

---

### Post by abn91c on 2009-03-14
> **swimon said:**
> okay, i hope the ram that is in this system hasn't become to rare and thus expensive :)

thx for the reply.
[http://www.geeks.com](http://www.geeks.com)
 has cheap ram for older systems, I got 512 MB PC133 stick for $22 with $8 shipping a couple of months ago

---

