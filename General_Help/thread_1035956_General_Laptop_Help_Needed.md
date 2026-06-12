---
title: "General Laptop Help Needed"
date: 2009-01-10
forum: General Help
---

### Post by gaalaaant on 2009-01-10
Okay so I have been having A few errors that I tried to resolve myself, but the guides on the forums (that I found) and the guides in the documentation, didn't work. Here's a list of my problems (other than being totally fail):

1. Wireless connection fails every 40 mins or so, I have to restart for it to work again because reconnecting fails.

2. When I jiggle windows around or use desktop effects, my screen gets black patches on it for split seconds.

3. When I play a movie it flickers alot, which doesn't happen in windows.

4. Skype says " audio something something not found" (And I HAVE TO use Skype).
I have a Toshiba Satellite A215-S7422 (link to the specs [http://reviews.cnet.com/laptops/toshiba-satellite-a215-s7422/4507-3121_7-32689116.html?tag=mncol;psum](http://reviews.cnet.com/laptops/toshiba-satellite-a215-s7422/4507-3121_7-32689116.html?tag=mncol;psum)). I have tried both the guides on the forums and on the documentation.

---

### Post by wolfen69 on 2009-01-10
1. i'm not sure why your wireless is acting that way, but instead of restarting your computer, just do 
```
sudo /etc/init.d/networking restart
```
then reconnect to your access point.

2. ati video cards are notoriously bad with desktop effects. turning effects off will fix that. and uninstalling the ati drivers. this is up to you.

3. see above response.

4. what exactly does the audio error message say?

---

### Post by Jameshardy88 on 2009-01-10
are you using the recommended graphics and wireless drivers?

---

### Post by gaalaaant on 2009-01-10
the message says "Problem with audio playback" whenever i try to make a call.  James, I dont know, I am using the ones that came with ubuntu, plus some of the ones (i think gfx) that it said are "restricted". thanks for the terminal advice. Ill try doing it when it next drops on me.

---

### Post by gaalaaant on 2009-01-11
Also, the wireless terminal thing you gave me worked ^_^ now if anyone could just help me with those other problems.

---

