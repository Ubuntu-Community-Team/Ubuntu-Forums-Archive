---
title: "Google Gadgets - how can I get it to remember my options?"
date: 2010-10-03
forum: Desktop Environments
---

### Post by BigSilly on 2010-10-03
OK, just installed Google Gadgets, which is brilliant, and added a couple of gadgets to get started. I've also added it to my startup applications so it starts on reboot. However, I'm finding that it resets to its default settings on each reboot, which basically means all the gadgets I've moved around the desktop return to the sidebar (which I'd also hidden but returns) every time.

I've had a look about the net but can't find any relevant info. Is there anyone here with experience of Google Gadgets and can help? Many thanks.

---

### Post by BigSilly on 2010-11-13
Bumping my own topic in case it helps others.

It seems a reboot or two later and it will indeed remember where you have placed the gadgets. Bit of a pain but hey-ho. However, the other problem I was having was that the Gadgets seemed to autostart before Compiz, resulting in nasty grey borders around the Gadgets instead of them being transparent. I had to delay them at startup a little to allow Compiz to start first and enable the transparency properly. So, when adding the Google Gadgets to the Startup Applications list, instead of using ggl-gtk as the command, I used this one:

```
sh -c "sleep 5 && ggl-gtk &"
```

A delay of 5 seconds is not even noticeable, but it did the trick and the Gadgets launch perfectly every time. Hope this helps someone. :)

---

### Post by eskararriba on 2011-01-10
hey there, 
didn't work for me - as startup command, I had put *ggl-gtk -ns* first, "-ns" meaning no sidebar; I then changed to *sh -c "sleep 5 && ggl-gtk -ns &"*, but things still get back to default settings every time I shut down. oh, and borders are still greyish and ugly... 
any ideas?

---

### Post by geezerone on 2011-01-23
> **BigSilly said:**
> Bumping my own topic in case it helps others.

It seems a reboot or two later and it will indeed remember where you have placed the gadgets. Bit of a pain but hey-ho. However, the other problem I was having was that the Gadgets seemed to autostart before Compiz, resulting in nasty grey borders around the Gadgets instead of them being transparent. I had to delay them at startup a little to allow Compiz to start first and enable the transparency properly. So, when adding the Google Gadgets to the Startup Applications list, instead of using ggl-gtk as the command, I used this one:

```
sh -c "sleep 5 && ggl-gtk &"
```A delay of 5 seconds is not even noticeable, but it did the trick and the Gadgets launch perfectly every time. Hope this helps someone. :)

Thanks for that - did the trick for me with solid grey bar instead of transparent sidebar! :D

---

### Post by abulooz on 2011-03-29
> **eskararriba said:**
> hey there, 
didn't work for me - as startup command, I had put *ggl-gtk -ns* first, "-ns" meaning no sidebar; I then changed to *sh -c "sleep 5 && ggl-gtk -ns &"*, but things still get back to default settings every time I shut down. oh, and borders are still greyish and ugly... 
any ideas?

BigSilly, legen....dary!!! nice one, thanks for the solution!

I had the same issue as you, so looked into the method behind it, the code you need is

sh -c "sleep 1 && ggl-gtk -ns -bg"

Basically the text between the brackets " " are the same as that of a shell, thus sleep 1 sets it to sleep for 1 second and ggl-gtk -ns -bg runs ggl-gtk with the added parameters...

Hope that helps anyone else with this problem!

---

