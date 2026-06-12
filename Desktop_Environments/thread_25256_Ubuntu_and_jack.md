---
title: "Ubuntu and jack"
date: 2005-04-09
forum: Desktop Environments
---

### Post by halus on 2005-04-09
Hi

Have a nice Hoary system up now, and like it a lot. Only problem for me is the not so good esd performance. What I want is to integrate the Jack Audio Connection Kit in the system. It gives nice low-latency and multible sound handling. Also many audio-applications on Linux reaquires JACK to work at all.

What I am looking for in this thread is help to get my system loading jack, not esd when booting, and have it integrated with gnome (which I belive is possible trough gstreamer. Right?). Would like a newbe friendly step by step kind of help, which could gather the information for a wiki guide.

---

### Post by socratesone on 2005-04-18
Bump.

I'd like to do the same, if it's possible. I'm not sure if gstreamer will do that, but I can hope. 

I'm using an integrated nvidia sound device (nforce2), and it doesn't allow (or, at least, I can't configure it to allow) multiple audio streams. In other words, I have to kill esd to run jack and vice-versa. I would alsa like all my esd apps to use jack and just use jack as my all-purpose audio thingamabob.

---

### Post by BrendaEM on 2005-07-17
I want JACK too!

It is high time something was done about the face of Linux audio. It is extremely fustrating that one of Linux's best chance for low-latency good audio recording is not support by most distributions!

Look how many applications support jack.
[http://jackit.sourceforge.net/apps/](http://jackit.sourceforge.net/apps/)

Please give something back to the musicians!
We want JACK!

The need to keep the kernel up to date makes compiling the kernel for Jack too impractical for the end user.

I believe, all we need are a few switches set in the kernel to allow virtual file systems. We can have a repository option to use the Jack enabled kernel or not. A great deal of the music software in the repositories is not useful without the API to run them. Perhaps even commercial packages will appear if the groundwork is there to run them. Jack also represents the oppertunity to have an open API, insead of letting everyone make proprietary ones.

I have talked to the Linux kernel people, and they have said that the next kernel version will feature lower latency, but why need we custom compile the kernel. Even if I custom compiled the kernel, how could I get it into the repository so that other people could install it?

There is more information here.
[http://jackit.sourceforge.net/](http://jackit.sourceforge.net/)

Planet CCRMA does custom kernals for audio, so why not Ubuntu? Why must musicians use a different distrubution than everyone else. It doesn't make sense.

Where is the incentive for people to spend their time writing music software if no one is able to use it?

Please! Please! Please! 
Help make this year that Linux audio editing really took off and soared!

Thank You.
Brenda

---

