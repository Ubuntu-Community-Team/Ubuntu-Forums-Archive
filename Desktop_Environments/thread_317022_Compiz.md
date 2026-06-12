---
title: "Compiz"
date: 2006-12-11
forum: Desktop Environments
---

### Post by Zeek00 on 2006-12-11
Hey,

I want to download and install compiz. I've look around the site and others and found no truly comprehensive set of directions for it. I did find this post:

[http://www.ubuntuforums.org/showthread.php?t=263840&highlight=XGL%2Fcompiz](http://www.ubuntuforums.org/showthread.php?t=263840&highlight=XGL%2Fcompiz)

It explained how to get a version of compiz running that works but it seemed to me that it wasn't the original version install. I guess I'm asking where can I find a comprehensive guide to installing compiz on my computer.

Zeek

---

### Post by rev_b on 2006-12-11
If you have a Nvidia card using 9xxx drivers, the only thing you have to do is to get compiz with synaptic from the repositories and type compiz --replace

---

### Post by drphilngood on 2006-12-11
> **Zeek00 said:**
> ...I guess I'm asking where can I find a comprehensive guide to installing compiz on my computer.

Zeek

See here:
[ How to install Xgl/Compiz]("http://ubuntuguide.org/wiki/Dapper#Eye_Candy")

---

### Post by Zeek00 on 2006-12-11
> **drphilngood said:**
> See here:
[ How to install Xgl/Compiz]("http://ubuntuguide.org/wiki/Dapper#Eye_Candy")

Went to that site. Infact I printed out the step by step. Found it to be cryptic. But thats just me.

---

### Post by Zeek00 on 2006-12-11
> **rev_b said:**
> If you have a Nvidia card using 9xxx drivers, the only thing you have to do is to get compiz with synaptic from the repositories and type compiz --replace

Well, in the synaptic package manager what do I download. If you search Compiz you get several options. What one specifically should I download or should I just grab them all?

---

### Post by rev_b on 2006-12-11
I downloaded compiz, compiz-core, compiz-gnome and compiz-plugins.
I'm running Beryl, though. More experimental, but much faster and easier to configure.
Here's an official step by step guide to install it.

[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

Nvidia 9xxx drivers don't need XGL or AIGlX, in fact Nvidia recomends against it, because these latest drivers support GLX_EXT_texture_from_pixmap extension that compiz needs.

Here's an official guide for Nvidia cards.
[http://www.nvnews.net/vbulletin/showthread.php?t=77030](http://www.nvnews.net/vbulletin/showthread.php?t=77030)

---

### Post by Zeek00 on 2006-12-11
I've got Beryl running now, I agree easy to use and configure but Compiz is much better, smoother and overall just a better ride. Thanks I'll give your suggestions a try.

---

### Post by rev_b on 2006-12-11
> **Zeek00 said:**
> I've got Beryl running now, I agree easy to use and configure but Compiz is much better, smoother and overall just a better ride. Thanks I'll give your suggestions a try.

I have a different opinion. I switched from compiz to beryl because compiz was slower, and when cpu usage was high, mouse was very slow and jerky, making the desktop nearly unusable. bery doesn't have this problem, at least for me.

---

### Post by Zeek00 on 2006-12-11
Installed Compiz from synapt.

`compiz --replace'

and I get this:

```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0
```

---

### Post by rev_b on 2006-12-11
Either you haven't a Nvidia card or you haven't the latest drivers installed.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

You also need to edit your /etx/X11/xorg.conf as stated in NVnews linux thread.

---

### Post by Zeek00 on 2006-12-11
Ok, I added the text needed on the xorg.conf file.

Typed `compiz --replace'

`/etc/X11$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0'

In return, is it still the nvidia driver issue?

---

### Post by Zeek00 on 2006-12-11
Got it installed using one of the install manuals. The big question is how do I load other themes.

---

### Post by zgornel on 2006-12-12
Compiz supports only metacity themes. For the latest version and updates, check [http://gandalfn.wordpress.com/](http://gandalfn.wordpress.com/) .

---

