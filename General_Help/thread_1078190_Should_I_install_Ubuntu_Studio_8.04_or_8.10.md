---
title: "Should I install Ubuntu Studio 8.04 or 8.10?"
date: 2009-02-23
forum: General Help
---

### Post by Aat on 2009-02-23
I'm ordering a new computer, and I'm planning to install ubuntu studio on it. I'd like to try the realtime-kernel, and the ubuntustudio-website advises me to install 8.04 for that.

But is it not possible to install ubuntu studio 8.10 and add the realtime-kernel later? Will that give me problems? Does anyone have experience with this?

Thanks in advance.

---

### Post by halovivek on 2009-02-23
what is the basic needs for you to install. could you please explain little bit more.

---

### Post by Aat on 2009-02-23
I'm planning on playing around with audio, link it to my digital piano.
And for example to rip the audio-track of a DVD. All kinds of stuff.
Don't know if I really need the realtime kernel, but I would sure like to try it out.

---

### Post by Aat on 2009-02-24
Does anyone have some info on this?

---

### Post by roccivic on 2009-02-24
Do you like to often re-install your OS?

If you do, get 8.10. It will be supported for 6 month only...
If you don't get 8.04. It's LTS and will be supported for 2 more years...

---

### Post by nlz on 2009-02-24
8.10 is fancier, 8.04 is more stable.

If you need studio for production purposes: 8.04
If you need studio for messing around: 8.10

---

### Post by Aat on 2009-02-24
Well, I don't mind re-installing often as I plan on messing about...
But do you have experience installing the realtime kernel in 8.10?
Can I expect trouble, are there any known problems?

Thanks for the info

---

### Post by jerrrys on 2009-02-24
last i heard 8.10 has no SMP support, so if your getting a dual core you got to go with 8.04 (this is studio only)

---

### Post by Yellow Pasque on 2009-02-24
If you want to make life easy on yourself, install Ubuntu Studio 8.04
If you worry that Ubuntu 8.04 isn't "new" enough for your other computing needs, you could always set up another Linux environment in a different partition. If you go this route, I would recommend a common data partition to save disk storage.

---

### Post by Slim Odds on 2009-02-24
> **roccivic said:**
> Do you like to often re-install your OS?

If you do, get 8.10. It will be supported for 6 month only...
If you don't get 8.04. It's LTS and will be supported for 2 more years...

Check your facts.... 8.10 is supported until October 2010

But you main point is correct. If you don't want a something that will be unsupported sooner, use the LTS. if you want more up to date stuff, use the newer release.

---

### Post by Aat on 2009-02-24
Thank you all for sharing this information.

> **jerrrys said:**
> last i heard 8.10 has no SMP support, so if your getting a dual core you got to go with 8.04 (this is studio only)

Is it really true that a newer version will not support dual core?

> **Temüjin said:**
> If you want to make life easy on yourself, install Ubuntu Studio 8.04
If you worry that Ubuntu 8.04 isn't "new" enough for your other computing needs, you could always set up another Linux environment in a different partition. If you go this route, I would recommend a common data partition to save disk storage.

A reason for me to want to have 8.10 would be an NVidia video-card, which I think will be better supported in 8.10. Or am I very wrong at that?

---

### Post by Slim Odds on 2009-02-24
> **Aat said:**
> Is it really true that a newer version will not support dual core?
Well, Ubuntu Studio uses a special kernel (RT). So it's not the same as the standard Ubuntu kernel

> **Aat said:**
> A reason for me to want to have 8.10 would be an NVidia video-card, which I think will be better supported in 8.10. Or am I very wrong at that?

Depends on which cards it is. The FX5200 (which is a bit old) is not supported well in 8.10 but works fine in 8.04

Newer cards are probably supported better in 8.10

---

### Post by jerrrys on 2009-02-24
[http://ubuntustudio.org/8-10_release_note](http://ubuntustudio.org/8-10_release_note)

---

### Post by Aat on 2009-02-24
Thanks for all your contributions to this thread.

I´m still not sure what to chose, but I'll probably start with 8.04 and see if my graphics card is well supported.
And 9.04 will be out soon anyway.

Again thanks a lot to you all.

---

### Post by nlz on 2009-02-24
I used Studio on a lot of weird and old video cards, and it worked pretty fine. 
If you want to do some real serious audio stuff on a very light and stable realtime kernel, try 64studio. It's another Linux Distro and really nice.

But first, learn to work with Jack, Jack is the key to (realtime) linux audio.

---

### Post by Slim Odds on 2009-02-24
> **nlz said:**
> But first, learn to work with Jack, Jack is the key to (realtime) linux audio.

So do you go around telling people they don't know jack?

(that's a joke, I hope)

---

### Post by Aat on 2009-02-24
Wow, you're not making the choice any easier... :P

---

### Post by cmay on 2009-02-24
> **nlz said:**
> I used Studio on a lot of weird and old video cards, and it worked pretty fine. 
If you want to do some real serious audio stuff on a very light and stable realtime kernel, try 64studio. It's another Linux Distro and really nice.

But first, learn to work with Jack, Jack is the key to (realtime) linux audio.

thanks for making this suggestion. i was beginning to think i was the only one here that uses 64studio. :)

---

### Post by nlz on 2009-02-26
> **Slim Odds said:**
> So do you go around telling people they don't know jack?

(that's a joke, I hope)

If you start with ubuntu studio, and you don't know that Jack does all the routing for the audio applications, **** can be difficult. I was just trying to help, what are you doing?

@ cmay: 64 studio is really nice for stable production work, although i like the complete integration of all the apps in Ubuntustudio. That's why I mostly boot in studio. 
It would be heaven if there would be an option to save all Jack connections/open apps, and you could restore it with one button. Setting up everything costs so much time...

---

### Post by Slim Odds on 2009-02-26
> **nlz said:**
>  I was just trying to help, what are you doing?


Making a joke (as I tried to state right in the message).

I realize that, in these multicultural/international forums, I should avoid the use of jokes based on idiomatic expressions....... **but I just can't help myself** . . . .):P

So relax, kick back, and enjoy the ride....

---

