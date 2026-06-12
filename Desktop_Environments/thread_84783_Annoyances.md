---
title: "Annoyances"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Jvaldezjr on 2005-10-31
Anyone experience any of the following, and have been able to fix it let me know!

When will backports be available?  Aparently Superkaramba 0.37 RC1 is out, but the package wont install on my system due to messed up dependencies.  Also I can't get Digikam either.  Hmmm

I have a problem with KDE thinking that every medium on my PC is a hard drive. which screws up the HAL applet to thinking that I've not put a CD in when I have.

Also I do NOT like the fact that when I pop a CD into my drive, it opens up in konqueror automatically.  I want to change that.

Thats about it at the moment, I'm falling asleep as I write this.

Thanks

---

### Post by odrop on 2005-11-01
> 
 Aparently Superkaramba 0.37 RC1 is out, but the package wont install on my system due to messed up dependencies


Superkaramba, if i remember correctly has been integrated into KDE releases itself now.  If you upgrade to KDE 3.5 beta 2, its comes automagically with it.  I just checked the version info in it.  It says its 0.37.

> 
Also I do NOT like the fact that when I pop a CD into my drive, it opens up in konqueror automatically. I want to change that.


In another topic I figured out a way to turn some of this off (well, Gingermark helped point out what it was). This has to due with Ivman.

[http://www.ubuntuforums.org/showthread.php?t=84326]("http://www.ubuntuforums.org/showthread.php?t=84326")

Probably what you want to change is the xml thing in the file:

/etc/ivman/IvmConfigActions.xml

and near the end of the file, find:

```

<!-- open konqueror -->
   <ivm:Match name="hal.info.category" value="volume">
           <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" />
   </ivm:Match>

```

change to:

```

<!-- open konqueror -->
  <!-- <ivm:Match name="hal.info.category" value="volume">
           <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" /> -->
   </ivm:Match>

```

That should help out some.

Don't know how to help with the HAL stuff, never really tried messing with it.

---

### Post by Thorsten on 2005-11-02
[quote=odrop]
Probably what you want to change is the xml thing in the file:

/etc/ivman/IvmConfigActions.xml
change to:

```

<!-- open konqueror -->
  <!-- <ivm:Match name="hal.info.category" value="volume">
           <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" /> -->
   </ivm:Match>

``` 
[/quote] 
This would violate XML's "well-formedness constraint" (you be left with an end tag without a corresponfing start tag) and might cause this file not to be processed at all.

The syntactically right code would be:
```
 
<!-- open konqueror -->
<!-- 
<ivm:Match name="hal.info.category" value="volume">
  <ivm:Option name="exec" 
  value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}"
  />
</ivm:Match> 
-->

```

HTH,
Thorsten

---

