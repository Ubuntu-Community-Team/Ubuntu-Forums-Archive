---
title: "Please Help!! Completely new to Linux!!"
date: 2009-06-01
forum: General Help
---

### Post by huntreilly25 on 2009-06-01
hey everyone!
I generally like to think of myself as relatively tech savvy and i decided to play with linux.  So i installed the Ubuntu Netbook Remix on my Acer Aspire One and so far i am loving it but theres obviously a lot of things i need to learn.
the first thing i'm trying to tackle is just getting the basic everyday uses that i use my computer for. Such as watch videos online or watching video files that I currently have.  

I just tried to watch videos on collegehumor and youtube and neither videos seemed to work.  the youtube ones gave me a message saying that i need to search for the right codecs but i dont know what those may be.  Maybe some sort of way to put flash on linux as well?
Also, I have a bunch of movie files that normally require a codec pack to view (such as the k-lite mega codec pack for windows) so I am wondering if there is any similar codec packs to this that will allow me to view these files.

So if anyone could help it would be greatly appreciated!!  I really like the way Ubuntu looks and I am hoping to become a full time user and not have to use windows again!

So if anyone can point me in the right direction for these topics that would be awesome! although I may need step by step procedures if need be cuz I am really new to linux.

thank you in advance!

---

### Post by ad_267 on 2009-06-01
Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

Basically you can get adobe flash, mp3 and video codecs etc by installing the ubuntu-restricted-extras package from the Synaptic Package Manager, it's explained step by step on that page.

Have a read on installing packages in Ubuntu, there's a really good link explaining package management and installing applications through other methods but I don't have it on me at the moment, I can get it later if no one else provides a good link.

---

### Post by gamblor01 on 2009-06-01
Open up a terminal (Applications -> Accessories -> Terminal) and enter the following command to install flash:

```

sudo apt-get install flashplugin-nonfree

```Now try visiting one of those web sites and see if it works.  You might also try launching synaptic, which is a GUI for managing packages:

```

sudo synaptic

```

You probably just need to install the restricted extras for everything to work properly though.

---

### Post by raymondh on 2009-06-01
> **ad_267 said:**
> 
Have a read on installing packages in Ubuntu, there's a really good link explaining package management and installing applications through other methods but I don't have it on me at the moment, I can get it later if no one else provides a good link.

Might come in handy as you read :)

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards,

---

### Post by Lunx on 2009-06-02
There's a great little guide that is an excellent intro to Ubuntu 

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

And there's some really good stuff available here as well, 20 free linux books

[http://www.linuxlinks.com/article/20...oks-Part1.html]("http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html")

Hope you enjoy the journey...:)

---

### Post by ad_267 on 2009-06-02
This is the page I was thinking of:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by huntreilly25 on 2009-06-02
wow! thanks for the help and the quick responses everyone!! I'll have time to check everything out later today but it sounds like what I will need!  Thanks again

---

