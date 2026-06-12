---
title: "What's a good opensource free program for drawing and creating electronic schematics."
date: 2006-09-07
forum: Education &amp; Science
---

### Post by jason.b.c on 2006-09-07
Like this==>
[IMG]http://www.advancedmsinc.com/images/course2.gif[/IMG]
and
[IMG]http://www.epanorama.net/circuits/lptleds.gif[/IMG]


It's just interesting stuff....:D

EDIT-->  Oh, And it has to be easy to install too.!

---

### Post by spin2cool on 2006-09-07
Dia?

---

### Post by futz on 2006-09-08
I wonder how well Eagle would run under Wine? I haven't used it in ages, but I used to love it back when I was heavily into microcontrollers and robotics.

Prices aren't too terrible for the higher versions, and if your needs are reasonably modest you can get by perfectly well with the freeware version.

[http://www.cadsoftusa.com/](http://www.cadsoftusa.com/)

---

### Post by futz on 2006-09-08
Just googled and found xcircuit
[http://opencircuitdesign.com/xcircuit/](http://opencircuitdesign.com/xcircuit/)
It's in the repos, so you can install and try it easily with Synaptic.

---

### Post by John.Michael.Kane on 2006-09-08
I use eagle it should be in the 32bit repos. i have not seen it listed in the 64bit repos. theres also spice sim's for testing your circuits.

---

### Post by futz on 2006-09-08
> **SD-Plissken said:**
> I use eagle it should be in the 32bit repos. i have not seen it listed in the 64bit repos. theres also spice sim's for testing your circuits.

Eagle is native! Awesome! One of these days I'm gonna get caught up with work and start tinkering with electronics again.

I see the repo version is 4.11. At cadsoft's site they have a 4.16 version that is supposed to update an existing install. Haven't tried it.

---

### Post by DoctorMO on 2006-09-08
> Dia?

Never Dia, it lives up to it's name, it is dia. and it's gnome 1.x to boot. old and not being activly developed for a long long time.

---

### Post by amo-ej1 on 2006-09-08
afaik eagle isn't an open source application, so i doubt a version for other architectures is available. And the readme of the src of the package (the binaries used to create the package) states:

```

  - Intel PC based Linux
  - Kernel version 2.x
  - libc6
  - X11 in at least 8bpp mode with 1024x768 min. resolution
    (800x600 with some minor restrictions)

```

and you don't really don't want to do those kind of things in dia, trust me ;)

---

### Post by jason.b.c on 2006-09-08
> **futz said:**
> Just googled and found xcircuit
[http://opencircuitdesign.com/xcircuit/](http://opencircuitdesign.com/xcircuit/)
It's in the repos, so you can install and try it easily with Synaptic.

Yea i found that one as well, But i couldn't figure out how to install it...
> 
Dia?

I tried that too, But it refuses to install cleanly...](*,) 

Anything else....????   **.deb's**..?? Perhaps..?

---

### Post by futz on 2006-09-08
> **jason.b.c said:**
> Yea i found that one as well, But i couldn't figure out how to install it...


I tried that too, But it refuses to install cleanly...](*,) 

Anything else....????   **.deb's**..?? Perhaps..?

I did a pretty thorough google search last night. There's not a whole lot of that type of software for linux out there, for free anyway.

For both drawing schematics and for designing circuit boards, Eagle is pretty tough to beat. Dan Gates' Sumo11 controller boards were designed with it ([http://www.1sorc.com/](http://www.1sorc.com/)). I've done a few projects with it and it does the job very very well. The autorouter does a decent job mostly, tho you have to help it a bit sometimes.

It takes a bit of time to get used to the way it does things, but read the docs and google for some tutorials (also check [http://cadsoftusa.com/](http://cadsoftusa.com/) for docs/tutorials) and you'll be up to speed in no time. Eagle is in the repos, so it's a snap to install with Synaptic.

If you're just doing schematics with it and not circuit boards, the freeware version is same as pay version, I think. The limitation of the freeware is in the size of circuit board it will do and the number of layers. But you can do a lot even with the free version, as long as you can pack it onto a smallish pc board.

Xcircuit just didn't grab me as a very good tool, but who knows? Maybe it's better than it looks (and worked during my couple minutes test)? It's in the repos as well, so it's a couple mouse clicks to install with Synaptic. Couldn't be easier.

---

### Post by jason.b.c on 2006-09-08
> Eagle is in the repos, so it's a snap to install with Synaptic.


I don't know man.? , I believe one of us must be mistaken..

I don't see **Eagle** in *synaptic*....:confused: ..

---

### Post by jason.b.c on 2006-09-08
I think i'll try this one...[right here.]("http://www.cadsoft.de/cgi-bin/download.pl?page=/home/cadsoft/html_public/download.htm.en&dir=eagle/program/4.1")  How do i install it..?? , Like this.?

```
sudo alien -i <package name>
```

Like that..?

---

### Post by futz on 2006-09-08
> **jason.b.c said:**
> I don't know man.? , I believe one of us must be mistaken..

I don't see **Eagle** in *synaptic*....:confused: ..

You probably don't have the right repo's enabled. Eagle is in multiverse. Enable that and there it is.

To do it in Synaptic, go Settings/Repositories. Go down the list and enable (I think this is the right one) Non-free (Multiverse). Close that dialog box and hit the Reload button in the upper left. Then search for Eagle.

---

### Post by jason.b.c on 2006-09-09
**[SIZE="3"]DAMN IT..![/SIZE]**

Why won't this thing install..??

Synaptic output==>
> eagle:
 Depends: libstdc++2.10-glibc2.2  but it is not installable
](*,) 

Terminal output==>
```
jason@Hp-Vectra-VL:~$ sudo apt-get install libstdc++2.10-glibc2.2
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

jason@Hp-Vectra-VL:~$


```](*,) 
Why is it that everytime i try this the **http//us.archive....universe**   repo is down...

How in the hell can i get it manually...???

---

### Post by futz on 2006-09-09
Sounds like you need to install build-essential. Back to Synaptic again. Build-essential really should be in the standard install, IMHO.

---

### Post by slimdog360 on 2006-09-09
wow, I just tried eagle, thats freaking awsome. At least compared to the others Ive tried in linux. I wish they had a simulation package with it. I saw that they have B2 spice which works with eagle but it costs and only has a windows and mac installer.
Something with an oscilloscope which gave accurate results would be fantastic.

---

### Post by futz on 2006-09-09
> **slimdog360 said:**
> wow, I just tried eagle, thats freaking awsome. At least compared to the others Ive tried in linux. I wish they had a simulation package with it. I saw that they have B2 spice which works with eagle but it costs and only has a windows and mac installer.
Something with an oscilloscope which gave accurate results would be fantastic.

It's a great program.

My crappy old web-site (desperately in need of a rebuild) at [http://ghmicro.com](http://ghmicro.com) has a couple of my little projects with Eagle files if you're interested. Go to Projects and look at "MAX7219 LED Display" and "PIC16F628 Board". The LED Display board page has fairly decent pictures of the whole prototyping/design/build process.

The LED display is a homemade double side board, so the layout has to be VERY carefully planned for absolute minimum number of top-side pads. All top-side components have to be mounted way high to allow soldering iron access underneath them to the top pads, and you still melt things!

---

### Post by jason.b.c on 2006-09-09
> **futz said:**
> Sounds like you need to install build-essential. Back to Synaptic again. Build-essential really should be in the standard install, IMHO.

I have that...

I'm trying to install through synaptic...But it dosen't work..

What about the windows version..?   You think it'll run under wine..?

[QUOTE=futz]All top-side components have to be mounted way high to allow soldering iron access underneath them to the top pads, **and you still melt things!**[/QUOTE]

Sounds like you need one of these [new one's that don't burn and melt things..]("http://www.coldheat.com/NR/store/index.cfm?action=cat.prodInfo&productID=81&utm_source=google&utm_medium=ppc&gclid=CN-ql86foYcCFSo5Igod9EWp5A")
[IMG]http://www.coldheat.com/pop_image.cfm?image=purch-pro-lg.jpg[/IMG]:grin:

---

### Post by futz on 2006-09-09
> **jason.b.c said:**
> I have that...
You sure? Try reinstalling it.

> What about the windows version..?   You think it'll run under wine..?
I don't know. Quite likely it will.

> Sounds like you need one of these [new one's that don't burn and melt things..]("http://www.coldheat.com/NR/store/index.cfm?action=cat.prodInfo&productID=81&utm_source=google&utm_medium=ppc&gclid=CN-ql86foYcCFSo5Igod9EWp5A"):grin:
What a joke those things are.

---

### Post by jason.b.c on 2006-09-09
> **futz said:**
> You sure? Try reinstalling it.

I'm sure.....:wink: 

> I don't know. Quite likely it will.


It don't , I tried it...:roll: 

> What a joke those things are.

[SIZE="3"]W.I.T.F..?[/SIZE]....Joke..??  What do you mean by that..???    
That thing is freakin awesome...        I want one, I'm sure they work just fine...:-\"

---

### Post by futz on 2006-09-10
> **jason.b.c said:**
> [SIZE="3"]W.I.T.F..?[/SIZE]....Joke..??  What do you mean by that..???    
That thing is freakin awesome...        I want one, I'm sure they work just fine...:-\"
Useless, except in some limited cases, like soldering a few wires. Look at the fatty tip on that thing! I solder tiny components and surface mount stuff on circuit boards. That stupid thing just isn't going to do the job. It's too big and clumsy. 

And for surface mount it won't work at all. It needs electrical contact to heat up, since it's not hot all the time. Can't get that on surface mount components.

Try soldering a few hundred joints on a pc board with it and I bet you'll fire that silly toy across the room and buy a proper anti-static temperature-controlled ***real*** soldering iron.

They're marketed to their target audience - home-handyman-do-it-yourselfers who just want to solder the odd joint.

Here's one of several reviews I looked at:
[http://www.epemag.wimborne.co.uk/cold-soldering.htm](http://www.epemag.wimborne.co.uk/cold-soldering.htm)

---

### Post by coder_ on 2006-09-10
How about tkgate?  --  [http://www.tkgate.org/](http://www.tkgate.org/)

---

### Post by jason.b.c on 2006-09-10
> And for surface mount it won't work at all. It needs electrical contact to heat up, since it's not hot all the time. Can't get that on surface mount components.

It dosen't need electrical contact to heat up , Just contact with a metalic surface...

---

### Post by futz on 2006-09-10
> **jason.b.c said:**
> It dosen't need electrical contact to heat up , Just contact with a metalic surface...
Same thing - the metallic (conductive) surface must short across the two halves of the tip for current to flow and produce heat.

Also, these things are scary with sensitive components. Read the second page of that review carefully. Get a real iron if you're even a little bit serious about doing electronics with it.

---

### Post by slimdog360 on 2006-09-10
> **coder_ said:**
> How about tkgate?  --  [http://www.tkgate.org/](http://www.tkgate.org/)

yeah but that only does logic simulation etc. Atleast as far as I can tell.
We need something like multisim or protel for linux. I likes the fancy looking stuff.

---

### Post by nousefreak on 2006-12-21
I installed eagle with wine, but i only get weard signs in stead of word like projects 

i,heard you talking about 32 respo is that something you have to change in wine (please tell me how if so)

here a sample of the crap i get wel installing eagle with wine
 [http://users.telenet.be/de_lotus/eagle_under_wine.jpg]("http://users.telenet.be/de_lotus/eagle_under_wine.jpg")

---

### Post by UbuWu on 2006-12-21
[http://gnomefiles.org/subcategory.php?sub_cat_id=107](http://gnomefiles.org/subcategory.php?sub_cat_id=107)

---

