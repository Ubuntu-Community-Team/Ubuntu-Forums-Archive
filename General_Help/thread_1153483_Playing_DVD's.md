---
title: "Playing DVD's"
date: 2009-05-08
forum: General Help
---

### Post by kelpie_canada on 2009-05-08
[Solved]
I just bought a new Brother sewing machine today and it came with a DVD instructional disc.

When I insert the disc into my laptop drive it recognizes that I have inserted a Video disc and opens it in Totem Movie Player, however after a second or two the screen looks like a sheet of blue plastic has been placed over it.

Is there something that I need to download or activate in order to play DVD's on my computer system?

Thank you for any help.

Katie

---

### Post by ikacer on 2009-05-08
[http://ubuntuforums.org/showthread.php?t=1152041]("http://ubuntuforums.org/showthread.php?t=1152041")

hope this helps!

---

### Post by dagrump on 2009-05-08
In the multimedia & video section, there is a sticky concerning most issues with audio & video. That is where you need to look, it is divided into sections for different versions & types of tasks. Read it carefully as, you don't want the wrong packages for your install. Take a look it can't hurt.
It is the "comprehensive multimedia & video howto".

---

### Post by kelpie_canada on 2009-05-08
I cheched my synaptic manager and libdvdread3 is already installed.

I am very computer illiterate. Could you please explain it to me a little more clearly than just sending me to another site that means absolutely nothing to me. Most of what I was reading might as well have been in Chinese for all the good it did me.

Katie

---

### Post by hansdown on 2009-05-08
Hi kelpie_canada.

Most electronics products come with windows disks, which ubuntu does not 

run.

You can find the same info online.

[http://www.google.ca/search?q=Brother+sewing+machine&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Brother+sewing+machine&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Primefalcon on 2009-05-08
Just add the medibuntu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then run the following command

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

---

### Post by kelpie_canada on 2009-05-08
> **Primefalcon said:**
> Just add the medibuntu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then run the following command

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

I followed your instructions and this is what I got in response:

kpringle@katie-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for kpringle: 
--2009-05-08 21:03:24--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 278 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 278         --.-K/s   in 0s      

2009-05-08 21:03:25 (34.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [278/278]

kpringle@katie-laptop:~$ sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
kpringle@katie-laptop:~$ 

I have no idea what any of this means. Did i do something wrong?

Katie

---

### Post by hansdown on 2009-05-08
You did everything right kelpie_canada.

Unfortunately, the advice you were following is incorrect. 

Please read my previous post.

---

### Post by kelpie_canada on 2009-05-08
You are sending me to a Brother web site. How does this help me to set up my system if I choose to watch a video on it or is it not capable of running videos.

Should I upgrade to the next system since I am using the Intrepid 8.10 at the moment?

Katie

---

### Post by todak on 2009-05-08
you must ```
sudo apt-get update
``` so that synaptic will load the package lists from the medibuntu repository, then you can install libdvdcss2.

---

### Post by kelpie_canada on 2009-05-08
> **todak said:**
> you must ```
sudo apt-get update
``` so that synaptic will load the package lists from the medibuntu repository, then you can install libdvdcss2.

Just to be sure that I understand what you are telling me to do. I need to go to my terminal and input the above code. Then I input the following code again :sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs.

And is this going to give me the ability to watch videos?

Katie

---

### Post by todak on 2009-05-08
> And is this going to give me the ability to watch videos?
It certainly is!

---

### Post by kelpie_canada on 2009-05-08
> **todak said:**
> you must ```
sudo apt-get update
``` so that synaptic will load the package lists from the medibuntu repository, then you can install libdvdcss2.

I followed your instructions and it ran something. Now it says "All done, no errors. All fonts downloaded and installed". Does this mean that I can now watch a video?

Katie

---

### Post by todak on 2009-05-08
When you request to download **ubuntu-restricted-extras** it is a metapackage, meaning that it will grab a group of files together rather than you having to download and install them one at a time. the fonts you refer to are the basic web fonts that many sites use. They are Microsoft fonts, subject to strict licensing for distribution and use, hence the **restricted** nomenclature. It also applies to the Adobe flash plugin and player. You should be able now to pop in a DVD and start watching.

---

### Post by kelpie_canada on 2009-05-08
> **todak said:**
> When you request to download **ubuntu-restricted-extras** it is a metapackage, meaning that it will grab a group of files together rather than you having to download and install them one at a time. the fonts you refer to are the basic web fonts that many sites use. They are Microsoft fonts, subject to strict licensing for distribution and use, hence the **restricted** nomenclature. It also applies to the Adobe flash plugin and player. You should be able now to pop in a DVD and start watching.

Thank you so much for walking me through this. I did put in a video and it is playing perfectly, however the instructional video that I got with my new sewing machine does not play. It does not go blue it just sits on the opening of the video. 

I had my boyfriend put it in his Microsoft system and the video doesn't tell me anything that 50 years of sewing hasn't taught me so that is no loss.

At least now I can watch a video anytime that I want to and since I have a good set of headphones I won't be disturbing anyone.

Thank you again for taking the time to help me. I have no doubt that I will be back again with more questions. Come to think of it should I upgrade to the new version?

Katie

---

### Post by todak on 2009-05-08
> **kelpie_canada said:**
> Come to think of it should I upgrade to the new version?

Katie

That is entirely up to you! :) If you are enjoying your system and it is stable enough for what you want it to do, then there is no need to upgrade, unless you **REALLY** want to upgrade all the time. I like to do so, but I also have a separate hard drive that has my main system on it with all my docs, pics, etc, that I use daily. The other drive is chainloaded and I am always putting something else on it to play with. My main drive I upgrade when the final releases of Ubuntu are out, no alpha, beta or RC is applied on top of my everyday drive, to avoid corrupting my files. (Yes, I have them archived on other media, but I hate having to restore everything!)

---

### Post by kelpie_canada on 2009-05-08
Do You Know Where Croton Is?

Isn't it the home of the Hartford Farm?

:guitar:

---

### Post by todak on 2009-05-08
> **kelpie_canada said:**
> Do You Know Where Croton Is?

Isn't it the home of the Hartford Farm?

:guitar:

Sure! It is only a few minutes from where I live. The Hartford Fair is advertised as the **"Biggest Little Fair in the World"**! The name of the town is Hartford, but the name of the Post Office is Croton, thus the same place with two different names.

---

### Post by kelpie_canada on 2009-05-08
jerry is my other half, his mother is from Croton. It is a small world.

---

### Post by kelpie_canada on 2009-05-08
I moved to a place that Jerry calls BFE, Ohio. It is the hamlet of Somerton, Ohio. It is smaller than Croton.

Do you know about Jamboree in the Hills? We are close to there.

---

### Post by todak on 2009-05-09
I know where it is, just south of Barnesville. Please send me PM so that we don't tie up the forum with a private discussion.

---

