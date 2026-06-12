---
title: "DRI configuration?"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by Landser on 2006-07-12
Uhm.. Sorry, I didn't know where to post this (even though it's related to gaming a bit)

Anyway, I discovered a possible way to improve performace for DRI accelerated graphics adapters and I want to confirm it.

NOTE: This only works if your graphic card supports direct rendering
Type glxinfo in a terminal and look for the line "Direct rendering:"

According to this: [http://dri.freedesktop.org/wiki/ConfigurationInfrastructure](http://dri.freedesktop.org/wiki/ConfigurationInfrastructure)

.. It's possible to configure DRI to use various features of your graphics adapter (i.e. Anisotropic filtering etc.)

First, install driconf:
```
sudo apt-get install driconf
```

This is a configuration utility that saves you the hassle of editing the drirc file manually

Now **type driconf**, you should see something like this:
[[IMG]http://fileanchor.com/43524-t.jpg[/IMG]](http://fileanchor.com/43524.jpg)

I'm kinda shocked that my radeon 9250 has such a load of options,
this might apply for other radeons too...

Can someone test this and post the results? This looks interesting

**EDIT: This seems to work, it gave me an extra boost of 300+ FPS on glxgears :)**

[I]
PS: Did anyone beat me to this? (I mean does anyone else know about this?)[/I]

---

### Post by simplyw00x on 2006-07-12
Yeah, I've been using this for months. I may have mentioned it in my HOWTO compile radeon DRI drivers from source thread. I can't remember. I'm using a Radeon 9200 SE and it gave a signifacnt performance boost when I enabled HyperZ, but nothing else made a _great_ deal of difference.

---

### Post by Anpu on 2007-09-21
Hi, I have ati 9250.
I installed DRIconf, but when I start it, it says:
Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

And then it opens window with 2 files listed from left side. Thats it. In console it says:
Driver "r200" is not installed or does not support configuration.

I have Mesa 7.0.1 installed. 

I need to enable S3TC compression. Do u know how I can do it since I dont have options in DRIconf or how I can fix that can DRIconf works normally?

ty :)

---

### Post by Anpu on 2007-09-22
I solved problem. Thx a lot to Ubuntu Srbija and user Smoki :)

---

### Post by sperlyjinx on 2007-10-29
Anpu, how did you solve the problem?  I am having the same issue.

---

### Post by XeviMetal on 2008-08-26
> **sperlyjinx said:**
> Anpu, how did you solve the problem?  I am having the same issue.

Me too. Anpu could you please help us?

---

### Post by Apocalypse_Ant on 2012-06-19
> **XeviMetal said:**
> Me too. Anpu could you please help us?
Me too... same issue, can someone help...?
thank you

---

### Post by overdrank on 2012-06-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

