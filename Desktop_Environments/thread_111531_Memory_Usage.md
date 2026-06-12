---
title: "Memory Usage"
date: 2006-01-02
forum: Desktop Environments
---

### Post by majkmil on 2006-01-02
I have a gig of ram in my breezy machine. Device manager shows between 50 and 60% memory usage. When I run TOP it says xorg is using about 24% usage and thats about it. I only have firefox open. Is this normal? Thanks
BTW, Happy New year

---

### Post by dcstar on 2006-01-02
[QUOTE=majkmil]I have a gig of ram in my breezy machine. Device manager shows between 50 and 60% memory usage. When I run TOP it says xorg is using about 24% usage and thats about it. I only have firefox open. Is this normal? Thanks
BTW, Happy New year[/QUOTE]
AFAIK free memory is dynamically allocated for things like disk caches etc., and is unallocated when running applications require it.

Application-System Tools-System Monitor will give you more info.

FF 1.07 apparently has a memory leak, perhaps if you do the 1.5 change that may help.

---

### Post by rado_london on 2006-01-16
Ubuntu and Linux in general uses the free RAM to cache libraries, so when you start a program it will load faster. It is annoying having your ram up all the time but there is no way to fix it. At least I dont know how.

---

### Post by Gustav on 2006-01-16
Eh.. I don't understand, how is this annoying?

---

### Post by Miguel on 2006-01-16
Mmm... 20% ram usage of Xorg seems a bit too much, especially when that means 200 megs. Here top reports 4.7% of 512 megs, which seems more reasonable. However, keep in mind that memory usage does not only depend on what you have currently running, but what you opened before. As you have lots of ram, linux will keep everything there until it needs more. This actually improves performance.

And to rado_london: free ram is wasted ram. One of the good things of linux is that it won't free memory unless you really need it. But then it will fill up a lot! you will say. Yes, sure. But if you have 300 megs to spare... why not use it to speed up possible future operations? It is actually better than having all applications using shared memory... while having free ram to spare.

---

### Post by pmj on 2006-01-16
I don't think there's any limit to how much memory xorg can eat up as long as you keep loading large images with Firefox. I've gotten it over 200MB myself.

---

### Post by mcduck on 2006-01-16
[QUOTE=rado_london]Ubuntu and Linux in general uses the free RAM to cache libraries, so when you start a program it will load faster. It is annoying having your ram up all the time but there is no way to fix it. At least I dont know how.[/QUOTE]
What's wrong with that? When usoing Windows, I think it's very annoying that I have 1GB of RAM and half of it is never used. I actually created a RAM disk and placed swap file there to get any use for my RAM in Windows..

But yes, 24% of 1GB for Xorg is much.. After 2 weeks of uptime (means opening and closing hundreds of tabs in FF) max RAM use I've seen for Xorg is around 10%.. (now it's at 3%, and FF takes 4%, uptime is 9 days and I continuously have about 10 tabs opened)

Have you got any extensions installed? You could try disabling those to see if that helps.

---

### Post by *zeus* on 2006-01-18
[QUOTE=majkmil]I have a gig of ram in my breezy machine. Device manager shows between 50 and 60% memory usage. When I run TOP it says xorg is using about 24% usage and thats about it. I only have firefox open. Is this normal? Thanks
BTW, Happy New year[/QUOTE]
I have some problem.
1.5Gb ram.
~500Mb used by xorg in kde.

---

