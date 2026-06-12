---
title: "https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel out of date"
date: 2023-03-25
forum: Documentation and Community Wiki Discussions
---

### Post by dungeonlords789 on 2023-03-25
As you [know]("https://ubuntuforums.org/showthread.php?t=2440297&highlight=BuildYourOwnKernel") in page
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

There is text
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-disco.git

This code is not working. This is my log:

Cloning into 'ubuntu-disco'...
fatal: remote error: no such repository: /ubuntu/ubuntu-disco.git

Please  fix this example. And check page on the whole. I afraid it contains a  lot of deprecated information... I try to build my own kernel, but I got  a lot of problems...

---

### Post by ian-weisser on 2023-03-26
The wiki page is updated by volunteers. A small group of volunteers, mostly Ubuntu Members, has permission to edit that page. A few people here have such permission.

If you really want the page updated, the best way is to offer specific suggestions. Make it simple for that volunteer to spend one hour updating instead of all day.

---

### Post by coffeecat on 2023-03-26
> **dungeonlords789 said:**
> 
There is text
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-disco.git

This code is not working. This is my log:

Cloning into 'ubuntu-disco'...
fatal: remote error: no such repository: /ubuntu/ubuntu-disco.git

Please  fix this example.

Of course you get an error. Now read that section of the wiki page again. Here it is in the quote box below:

> All of the Ubuntu Kernel source is maintained under git. **The source for each release is maintained in its own git repository on kernel.ubuntu.com.** To obtain a local copy you can **simply git clone the repository for the release you are interested in** as shown below.

[indent]git clone git://kernel.ubuntu.com/ubuntu/ubuntu-<release codename>.git[/indent]

For example to obtain the Disco Dingo tree:

[indent]git clone git://kernel.ubuntu.com/ubuntu/ubuntu-disco.git[/indent]

I've emboldened a couple of phrases you need to take particular note of. The example given, that you appear to have simply copy-pasted, is for Disco Dingo, which is long out of support. You are not using Disco, right? You simply substitute the release you are using in the line given above.

I very much doubt there is anything to fix, at least in that bit of the wiki. As ian-weisser says, if you do find real examples of problems, please provide suggestions for revising it. In a community you contribute as well as take.


**Edit:** As this is not a general help request, I've moved this thread to *Documentation and Community Wiki Discussions*.

---

