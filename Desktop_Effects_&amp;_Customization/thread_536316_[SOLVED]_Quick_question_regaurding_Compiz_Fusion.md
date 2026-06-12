---
title: "[SOLVED] Quick question regaurding Compiz Fusion"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by slughappy1 on 2007-08-27
Can someone clarify two thing for me please?  

I was under the impression that Beryl and Compiz merged together to make Compiz Fusion?  So what that means to me is that Compiz Fusion should be the way to go, as in more plug-ins, more compatible/stable, and the only one that would be updated anymore.

And one more question.  I installed Beryl a little while ago and just yesterday noticed a very nice how-to/100 best Linux apps, and decided to install Compiz Fusion.  Well it worked...kind of.  If I tried to boot up with out Beryl automatically loading I would get the black line that comes with AWN without Beryl.  Shouldn't Compiz Fusion just load automatically (like Beryl), so all the effects, and AWN would work properly?  

Thanks in advance

---

### Post by ThrobbingBrain66 on 2007-08-27
In theory, the Beryl/Compiz merge would equal more plugins, more stability, etc.  But reality is that merging code is difficult and time consuming and can create new and unexpected bugs.  So while most people find it stable, it still isn't for everyone yet.

If you're running Fesity, Compiz Fusion won't startup automatically unless you add the command to your Startup programs.  Something like ```
compiz --replace emerald --replace
``` should work for you.

---

### Post by slughappy1 on 2007-08-27
> **ThrobbingBrain66 said:**
> In theory, the Beryl/Compiz merge would equal more plugins, more stability, etc.  But reality is that merging code is difficult and time consuming and can create new and unexpected bugs.  So while most people find it stable, it still isn't for everyone yet.

If you're running Fesity, Compiz Fusion won't startup automatically unless you add the command to your Startup programs.  Something like ```
compiz --replace emerald --replace
``` should work for you.

Now that you point out the fact that they have to merge code it seems really obvious. Just not thinking on that one. 

So I am planning on doing a re-install on Ubuntu (because of stupid Intel video card crap) and, correct me if I am wrong.  According to you if I follow the instructions to install Compiz Fusion and then type in "compiz --replace emerald --replace" (as the last command), Compiz will start automatically when I start up, and I won't need Beryl. Right?

---

### Post by ThrobbingBrain66 on 2007-08-27
Sort of.  If you add 'compiz --replace emerald --replace' to your startup programs (System > Preferences > Sessions) then it will startup automagically.

---

