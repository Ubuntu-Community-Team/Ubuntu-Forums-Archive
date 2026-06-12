---
title: "does the newest iPod Nano work on Ubuntu 7.10?"
date: 2007-11-07
forum: Desktop Environments
---

### Post by tafsen on 2007-11-07
Does the new iPod Nano (8GB and Cover flow) work with Ubuntu out of the box? It's important that cover-arts is is working as well.

---

### Post by kooldino on 2007-11-20
Well, I just picked one up today...I can connect it and mount it, but Amarok doesn't recognize it as far as I can tell.

---

### Post by ubuntios on 2007-11-20
At the moment NO.
We all have the same problem .
There are a lot of post's here in the forum that explain why .
For a nice one search for ''New ipod nano'' .
(we talking about the 3rd generation of iPod nano)
We just have to wait a little bit more.

---

### Post by kooldino on 2007-11-20
Yeah, apparently they use a different form of encryption to access the thing.

Guess I'll have to run VMware or something.

Can someone bump this thread when this issue is resolved?

Also, can Winamp run properly in WINE?

---

### Post by kooldino on 2007-11-21
I just got Winamp 5.5 running under WINE  When I get a chance, I'm going to try to see how it interfaces with the Nano.  It works under windows, but not sure how WINE will do with it.

---

### Post by Sukarn on 2007-11-21
Read [http://www.gtkpod.org/libgpod.html](http://www.gtkpod.org/libgpod.html)

The newest version of libgpod supports iPod Classic and iPod nano.

It had been in the CVS version for quite a few days and I had been using it happily.

The only problem I've been having is that artwork from videos is missing, and some songs have wrong artwork.

Oh, and the version of gtkpod-aac in the Gutsy repository is messed up, so that it does not allow people to transfer .mp4 videos. To transfer these videos, I used the testing deb [http://launchpadlibrarian.net/10273230/gtkpod-aac_0.99.10-2ubuntu1.1%7E7.10prevu1_i386.deb](http://launchpadlibrarian.net/10273230/gtkpod-aac_0.99.10-2ubuntu1.1%7E7.10prevu1_i386.deb) from the page [https://bugs.launchpad.net/ubuntu/gutsy/+source/gtkpod-aac/+bug/135178](https://bugs.launchpad.net/ubuntu/gutsy/+source/gtkpod-aac/+bug/135178)

I don't know why they've marked the bug as Invalid. Its a pretty much valid bug with lots of confirmations.

---

### Post by kooldino on 2007-11-21
I personally run KDE, so gtkpod loaded and ran, but didn't even recognize my device or anything.

---

### Post by ianare on 2007-11-21
They keep on changing them so they will not work outside of itunes. It will forever be a game of cat and mouse. Get a brand of mp3 player that supports linux if you can.

---

### Post by Sukarn on 2007-11-21
> **ianare said:**
> They keep on changing them so they will not work outside of itunes. It will forever be a game of cat and mouse. Get a brand of mp3 player that supports linux if you can.

Your post made me go "what in the world?"

Once the hardware is out, once I have it in my hands, how are you suggesting that they'll be changing the encryption technique to make it work only with iTunes?

The "cat" is out of the bag, and a well working technique to "bell the cat" has been established.

---

### Post by kooldino on 2007-11-21
> **ianare said:**
> They keep on changing them so they will not work outside of itunes. It will forever be a game of cat and mouse. Get a brand of mp3 player that supports linux if you can.

I wish I could have, but the stupid ipod has an interface with the head units in my vehicles.

---

### Post by skyjacker on 2007-11-21
> **kooldino said:**
> Yeah, apparently they use a different form of encryption to access the thing.

Guess I'll have to run VMware or something.

Can someone bump this thread when this issue is resolved?

Also, can Winamp run properly in WINE? Try xmms, a winamp clone made for Linux. Works as good as winamp, but without the Wine.

---

### Post by ubuntios on 2007-11-23
Ok guys , iPod nano 3G is now working with Linux.

I test it my self and is working fine with any player.

All the credits and many thanx to 'paradoxni'

Here is the link

[http://ubuntuforums.org/showthread.php?t=611404&page=2](http://ubuntuforums.org/showthread.php?t=611404&page=2)

Enjoy

---

### Post by kooldino on 2007-11-24
> **skyjacker said:**
> Try xmms, a winamp clone made for Linux. Works as good as winamp, but without the Wine.

Good looking out, but for some reason it refuses to play songs for me.  Allegedly my sound card isn't configured correctly, even though it is in every other program i use.

---

### Post by kooldino on 2007-11-24
> **ubuntios said:**
> Ok guys , iPod nano 3G is now working with Linux.

I test it my self and is working fine with any player.

All the credits and many thanx to 'paradoxni'

Here is the link

[http://ubuntuforums.org/showthread.php?t=611404&highlight=new+generation+ipod&page=2](http://ubuntuforums.org/showthread.php?t=611404&highlight=new+generation+ipod&page=2)

Enjoy

I'll give that a shot soon.

In other news, I was unable to get Winamp through WINE to even see my ipod nano 3g.

---

### Post by ubuntios on 2007-11-24
> **kooldino said:**
> I'll give that a shot soon.

In other news, I was unable to get Winamp through WINE to even see my ipod nano 3g.

I'm a iTunes lover and I have the same problem with wine.I'm using Rythmbox now it's kind the same with iTunes but anyway , I think something must be done in wine in order to see the pod.
I will post any news, please do the same :)

---

### Post by kooldino on 2007-11-25
ten four

---

### Post by tafsen on 2007-11-26
Almost everything works for me now.  I need to use amaroK du get cover art, but I can't get podcasts and movies to work with either amaroK or gtkpod.

---

### Post by ubuntios on 2007-11-29
> **tafsen said:**
> Almost everything works for me now.  I need to use amaroK du get cover art, but I can't get podcasts and movies to work with either amaroK or gtkpod.

Same problem here, I'm using a windows box in order to do that.
I haven't read anything about that yet, I'm happy whit the music.
I think we have to wait a bit

---

### Post by tafsen on 2007-11-30
[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

This works perfect :D No need for windows anymore ;)

---

### Post by ubuntios on 2007-12-02
> **tafsen said:**
> [http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

This works perfect :D No need for windows anymore ;)

Thats very nice , I have all ready installed it , I will try it later to see if everything works fine.
Thanks a lot

---

### Post by ubuntios on 2007-12-02
> **tafsen said:**
> [http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

This works perfect :D No need for windows anymore ;)

You are right its working fine , but still no option for photos or videos :(

---

### Post by Sukarn on 2007-12-03
What the hell is wrong with  people? I clearly posted the software to transfer videos to the new ipod classic and ipod nano on the first page of this thread, still people keep complaining that theres nothing to transfer videos yet!!!!

I quote myself -
> **Sukarn said:**
> Read [http://www.gtkpod.org/libgpod.html](http://www.gtkpod.org/libgpod.html)

The newest version of libgpod supports iPod Classic and iPod nano.

It had been in the CVS version for quite a few days and I had been using it happily.

The only problem I've been having is that artwork from videos is missing, and some songs have wrong artwork.

Oh, and the version of gtkpod-aac in the Gutsy repository is messed up, so that it does not allow people to transfer .mp4 videos. To transfer these videos, I used the testing deb [http://launchpadlibrarian.net/10273230/gtkpod-aac_0.99.10-2ubuntu1.1%7E7.10prevu1_i386.deb](http://launchpadlibrarian.net/10273230/gtkpod-aac_0.99.10-2ubuntu1.1%7E7.10prevu1_i386.deb) from the page [https://bugs.launchpad.net/ubuntu/gutsy/+source/gtkpod-aac/+bug/135178](https://bugs.launchpad.net/ubuntu/gutsy/+source/gtkpod-aac/+bug/135178)

I don't know why they've marked the bug as Invalid. Its a pretty much valid bug with lots of confirmations.

---

### Post by ubuntios on 2007-12-03
> **Sukarn said:**
> What the hell is wrong with  people? I clearly posted the software to transfer videos to the new ipod classic and ipod nano on the first page of this thread, still people keep complaining that theres nothing to transfer videos yet!!!!

I quote myself -

Probably because is not working for them , that's why.
And instead of having that kind of attitude , try to help some people here or don't post at all.

Thank you !

---

### Post by tafsen on 2007-12-04
> **ubuntios said:**
> You are right its working fine , but still no option for photos or videos :(

Just drag videos in there  as well :)
If you need an encoder, try podencoder.

---

### Post by nixgeek on 2007-12-18
> **Sukarn said:**
> What the hell is wrong with  people? I clearly posted the software to transfer videos to the new ipod classic and ipod nano on the first page of this thread, still people keep complaining that theres nothing to transfer videos yet!!!!

I quote myself -

Uh this does not work for us x64 users....

---

### Post by nixgeek on 2007-12-18
I've compiled and installed the latest gtkpod and libgpod. So i am using both of them
just fine, I can even transfer music, artwork, and movies.. 

However, movies play, but I get no sound at all.

I can play the file in mplayer and I get sound.

So something else is wrong....

I am at lost with that... 

p.s. Just use Podencoder to make the movies.... straight from DVD to IPOD movie. It will
be cool when sound is working.

---

