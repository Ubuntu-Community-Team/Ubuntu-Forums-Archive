---
title: "Malicious commands announcement contains some inaccuracies"
date: 2008-10-28
forum: Forum Feedback &amp; Help
---

### Post by cevans on 2008-10-28
I brought this up several months ago, but upon my return to the forums, I found that nothing had been changed, and so am bringing it up again.

rm -r .* does exactly what one would naively expect it to do: it deletes everything in the directory recursively, **except . and ..**. The exclusion of . and .. is explicitly outlined in the POSIX standard, and I've never seen any rm that follows '.' or '..'. Unfortunately, the [Malicious Commands]("http://ubuntuforums.org/announcement.php?f=307") announcement describes the command as a deceptive one that will follow .. and delete everything above the working directory. In an announcement that is threatening immediate banning with no consideration for the circumstances, I would expect the examples given to be accurate enough to not create the potential for mistaken accusations. 

In general, it would be very nice if the announcement could be revised, now that the immediate situation from which it arose is far behind us. The way the examples are described could easily be mistakenly interpreted as saying, for example, that one should *never* run dd to a block device, when most of the cases when one actually needs to do so are probably going to be discussed in forums like these.

I'm posting this here because I'm not sure where it should be posted, and the announcement doesn't allow replies.

---

### Post by schauerlich on 2008-10-28
It's safer to just do
```

rm -r ./*

```

Then you don't have to find out the hard way

---

### Post by jpeddicord on 2008-10-28
> **cevans said:**
> rm -r .* does exactly what one would naively expect it to do: it deletes everything in the directory recursively, **except . and ..**. The exclusion of . and .. is explicitly outlined in the POSIX standard, and I've never seen any rm that follows '.' or '..'.

Actually, if I remember right, there was a buggy version of coreutils in an older version of Ubuntu that did in fact do that. Anyone want to back me up on this?

I'll leave this up to jdong, since he wrote it and probably has more reasoning behind it than I would care to know. :)
Also @jdong or other staff: that announcement expires on Dec 21, think it should be renewed?

As an aside, Intrepid has a modified rm that will try to safeguard against removing the root directory. **But don't go trying it out.**

---

### Post by schauerlich on 2008-10-29
> **jacobmp92 said:**
> As an aside, Intrepid has a modified rm that will try to safeguard against removing the root directory. **But don't go trying it out.**

/me actually considered it for a moment

---

### Post by Canis familiaris on 2008-10-29
> **jacobmp92 said:**
> **But don't go trying it out.**
:twisted:

---

### Post by cyberdork33 on 2008-10-29
> **EDavidBurg said:**
> /me actually considered it for a moment

I might try actually since I want to install from scratch when Intrepid final comes out.

---

### Post by -grubby on 2008-10-29
> **jacobmp92 said:**
> 
As an aside, Intrepid has a modified rm that will try to safeguard against removing the root directory. **But don't go trying it out.**


I already did, in Hardy. It went somewhat like this :

```

nathan@linda:~$ sudo [...]
[sudo] password for nathan:
rm: cannot remove root directory `/'
nathan@linda:~$

```

---

### Post by schauerlich on 2008-10-29
> **nathangrubb said:**
> I already did, in Hardy. It went somewhat like this :

```

nathan@linda:~$ sudo [...]
[sudo] password for nathan:
rm: cannot remove root directory `/'
nathan@linda:~$

```

Ptsh. But it's so fun...

---

### Post by cevans on 2008-10-29
> **EDavidBurg said:**
> It's safer to just do
```

rm -r ./*

```


That doesn't do the same thing, as it won't remove any files in the directory that start with '.'. 

> **jacobmp92 said:**
> Actually, if I remember right, there was a buggy version of coreutils in an older version of Ubuntu that did in fact do that. Anyone want to back me up on this?

Strange, though that would certainly be a bug.

> As an aside, Intrepid has a modified rm that will try to safeguard against removing the root directory. [B]But don't go trying it out.[/B

One can't mention something like that and not expect that everyone will immediately try it! That reminds me of long ago when I learned about the bash fork bomb, and proceeded to repeatedly crash my system with it while trying it out.

---

### Post by jpeddicord on 2008-10-29
> **cevans said:**
> One can't mention something like that and not expect that everyone will immediately try it! That reminds me of long ago when I learned about the bash fork bomb, and proceeded to repeatedly crash my system with it while trying it out.

Hence why I didn't mention how to do it and the above two edits. :)

---

### Post by 080812jk on 2008-10-30
&#20026;&#20102;&#20154;&#31867;,&#20026;&#20102;&#26410;&#26469;,&#20445;&#25252;&#25105;&#20204;&#30340;&#29615;&#22659;,[**&#28165;&#29702;&#21270;&#31914;&#27744;**](http://www.bjbtgdst.com.cn/qzhfc.htm)&#26159;&#19990;&#30028;&#19978;&#27599;&#20010;&#20225;&#19994;&#27599;&#20010;&#20844;&#27665;&#24212;&#26377;&#30340;&#22307;&#36131;.&#26412;&#20844;[**&#28165;&#29702;&#21270;&#31914;**&#27744;](http://www.bjbtgdst.com.cn/qzhfc.htm)&#21496;&#23545;&#22240;&#31649;&#36947;&#22581;&#22622;&#23548;&#33268;&#29615;&#22659;&#27745;&#26579;&#30340;,&#24517;&#39035;&#36827;&#34892;[**&#28165;&#29702;&#21270;&#31914;&#27744;**](http://www.bjbtgdst.com.cn/qzhfc.htm)&#24443;&#24213;&#30340;&#25972;&#27835;,&#23545;&#31649;&#36947;&#36827;&#34892;&#39640;&#31185;&#25216;&#30095;&#36890;,&#20928;&#21270;,&#28040;&#27602;&#28781;&#33740;,&#20026;&#20225;&#19994;&#21019;&#36896;&#26356;&#32654;&#22909;&#30340;&#29983;&#27963;&#29615;&#22659;.     &#30095;&#36890;&#24037;&#31243;:[**&#28165;&#29702;&#21270;&#31914;&#27744;**](http://www.bjbtgdst.com.cn/qzhfc.htm)&#19987;&#19994;&#30095;&#36890;,&#19979;&#27700;&#31649;&#36947;,&#30095;&#36890;&#22320;&#28431;,&#30095;&#36890;&#33756;&#27744;     &#30095;&#36890;&#28020;&#32568;,&#30095;&#36890;&#39532;&#26742;[**&#28165;&#29702;&#21270;&#31914;&#27744;**](http://www.bjbtgdst.com.cn/qzhfc.htm),&#30095;&#36890;&#21397;&#25152;,&#30095;&#36890;&#36466;&#22353;     &#30095;&#36890;&#25490;&#27700;&#31649;&#36947;,&#30095;&#36890;&#38452;&#27807;,&#30095;&#36890;&#22352;&#20415;&#27744;     &#30095;&#36890;&#28165;&#29702;&#21270;&#31867;&#27744;,&#30095;&#36890;&#32508;&#21512;&#25490;&#27745;&#31649;&#36947;

---

