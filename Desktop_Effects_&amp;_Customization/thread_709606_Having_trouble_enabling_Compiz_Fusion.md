---
title: "Having trouble enabling Compiz Fusion"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by Splower on 2008-02-27
All I hear is to try Ubuntu.
Well, I have been trying since yesterday.  All I wanted was to use ubuntu with some cool compiz fusion features.

Well....  Yesterday I tried to install Ubuntu 7.1 on an old laptop.  Tried evrything to get it to work, with no luck.  Ended up installing Ubuntu 7.04.  Works fine until I tried to use compiz fusion.  Tried so many things and when I finally got it working, I realized my computer was too slow.  I was not a happy guy.

So I did the deed this morning.  I installed Ubuntu 7.1 on my office computer. (Feeling a little daring) thinking it should be easier now.

Of course it loaded great, but, still could not get Compiz Fusion to work.  

They say to just enable custom or extra visual effects:
My computer says it could not enable.

They say just go to restricted drivers Manager and choose ATi bla bla bla:
My computer says "Your hardware does not need any restricted drivers."

Now I installed serverx and I can't even log in anymore without being in a gnome safe mode...

I realize that someone that knows Ubuntu is laughing at me right now because it would take him 5 minutes to fix and be up and running, but, I have never used it before and don't know any of the commands or know anybody that can help me.

So I beg of you, Please get back to me and help me out...

Thanks,

Splower

---

### Post by yothisbalec on 2008-02-27
What video card are you using?  Just making sure your video card can actually handle compositing.

---

### Post by Afkpuz on 2008-02-27
I'm not sure how to fix your "serverx" problem as I've never heard of it, but ATI video cards usually require xserver-xgl and the restricted driver to run desktop effects.  This is due to ati's lousy support for linux.  So, get to a command line , either in safe mode, or press esc at boot up and select recovery mode.


try

```
sudo apt-get install xserver-xgl
```

---

### Post by Splower on 2008-02-27
Awesome to get a quick response guys.

I ran "sudo apt-get install xserver-xgl" and it said it was already installed. (By the way, this was the command that I meant earlier that wont allow me to log in anymore...)

I think I have an ATI radeon 7800????  How to check????

Thanks,

Splower

---

### Post by The Cog on 2008-02-27
From the command line, either **lspci** or **lshw** should tell you.

---

### Post by Splower on 2008-02-27
This is the Video card I have:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]

Thanks,

Splower

---

### Post by Splower on 2008-02-27
This is the Video card I have:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]

Thanks,

Splower

---

### Post by Splower on 2008-02-27
They moved my thread and all of a sudden no one would help me.  PLease leave on Is it worth it thread.....

---

### Post by ajeetraj on 2008-02-27
Maybe this will help with your general problem in gutsy! don't bother about xgl or anything if you are working/installed gutsy and follow my post on this page....and hopefully it will help you! At least it will not harm your computer...you can always just go back to normal :)

[Try this]("http://ubuntuforums.org/showthread.php?t=441399&page=2")

Good luck!

---

### Post by laidback on 2008-02-27
You may like to have a look here :-

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

some people have reported good results using this site.

---

