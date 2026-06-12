---
title: "libxine and Amarok fails again!"
date: 2006-10-05
forum: Desktop Environments
---

### Post by oleoleole on 2006-10-05
If you're using Amarok 1.4.3 with xine-engine, do not upgrade libxine today. Amarok-xine doesn't support the new libxine and will fail when trying to play music. This have happend before, and I hope they will fix it very soon. Boring to look up other files:p

Next time I hope amarok-xine and libxine will be updated at the same time, this is confusing.

But I don't think the developers is doing a bad job! ;o)=

---

### Post by mitch.c on 2006-10-05
> **oleoleole said:**
> If you're using Amarok 1.4.3 with xine-engine, do not upgrade libxine today. Amarok-xine doesn't support the new libxine and will fail when trying to play music. This have happend before, and I hope they will fix it very soon. Boring to look up other files:p

Next time I hope amarok-xine and libxine will be updated at the same time, this is confusing.

But I don't think the developers is doing a bad job! ;o)=

Hmmm. No problems here after dist-upgrade:

amarok 2:1.4.3-0ubuntu8~dapper1
libxine-main1 (1.1.1+ubuntu2-7.3)
libxine-dev (1.1.1+ubuntu2-7.3)

Maybe it's something else?

---

### Post by oleoleole on 2006-10-05
> **mitch.c said:**
> Hmmm. No problems here after dist-upgrade:

amarok 2:1.4.3-0ubuntu8~dapper1
libxine-main1 (1.1.1+ubuntu2-7.3)
libxine-dev (1.1.1+ubuntu2-7.3)

Maybe it's something else?

Weird, I have installed exactly the same versions, and reinstalling doesn't work either:/ And my sound is just fine... and it worked before I saw it upgraded libxine.. so something is broken somewhere:p maybe I have some stupid repositories:p

---

### Post by oleoleole on 2006-10-05
Hm, looks like it's only failing with FLAC-files. :/

---

### Post by dukeku on 2006-10-05
[http://ubuntuforums.org/showthread.php?t=210683](http://ubuntuforums.org/showthread.php?t=210683)

I'm patching the latest libxine to support FLAC again, I'll let you know if I get it working :)

---

### Post by happyisland on 2006-10-06
can anyone explain to me why there is this problem with FLAC in libxine? It is my preferred codec because it is high-quality and open and I just assumed it would work no problem when I switched to linux.

---

### Post by oleoleole on 2006-10-06
> **happyisland said:**
> can anyone explain to me why there is this problem with FLAC in libxine? It is my preferred codec because it is high-quality and open and I just assumed it would work no problem when I switched to linux.

I guess the problem is that they forget to compile in the correct FLAC version to the library or somethingc similar. Just wait, and I guess it will be fixed soon:p But this have happend before, and may happend later too, so just be patient:p But usually there's no problem with FLAC and GNU/Linux;o)

---

### Post by dorcssa on 2007-01-12
> **oleoleole said:**
>  Just wait, and I guess it will be fixed soon:p 

I'm still waiting... The problem started half year ago. :D The libxine-main patch will do it though, but still..the dev team just don't bother, or what? Edgy users..the latest version can play flacs, or not?

---

