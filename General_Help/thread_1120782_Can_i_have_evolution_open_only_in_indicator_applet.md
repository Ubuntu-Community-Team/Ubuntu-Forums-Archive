---
title: "Can i have evolution open only in indicator applet? 9.04 beta"
date: 2009-04-09
forum: General Help
---

### Post by edm1 on 2009-04-09
I was wondering if it's possible to have evolution open only in the indicator applet so that i dont have to have the window open but minimised to the 'window list' in order to receive emails, as is possible with pidgin. I don't see why evolution has never had a minimise to tray option, is there a reason for it.

Btw, i'm not really interested in using alltray as it's ugly and doesn't have any of the functionality of the indicator applet. Thanks!

p.s. the 9.04 beta is awesome.

---

### Post by obocho on 2009-04-10
I am wondering exactly about the same issue.

-why there is no option to minimize evolution to system tray? [too difficult? impossible?]
-why do people insist on "Alltray"? [personally I find it ugly and not useful] 

any explanation will be appreciated : )

PS: awesome +1

---

### Post by edm1 on 2009-04-25
Now that the final release is out, does anyone know more on this topic? It's annoying me quite a bit.

---

### Post by smileypaul on 2009-04-26
I too would be greatly interested in this..

---

### Post by edm1 on 2009-04-26
I've made a [brainstorm idea]("http://brainstorm.ubuntu.com/idea/19454/"). Should be accepted soon.

---

### Post by longhai on 2009-04-26
This is very annoying to me. I do want to use evolution as default mail and calendar. But this bad funtionality prevents me from leaving thunderbird. Also I found sometimes evolution doesn't change the disk file when I updates the calendar. I need this to synchronize my calendar at home computer and office computer. This also make me continue to use korgonizer. Probably evolution hasn't been updated for long.

---

### Post by TooDamFast on 2009-04-30
bump
I don't get why it does not default to this?

---

### Post by mdgrech on 2009-05-17
bump

---

### Post by KWM987 on 2009-06-01
bump

My guess is because most people ignore evolution.  

My workaround is to just leave it open in Desk 2, makes use of the second desktop for something purposeful. 

And I've been wanting this functionality for the past 2 years, and it seems to be like asking for the impossible.

---

### Post by utnubuuser on 2009-06-01
alltray

---

### Post by RommeDeSerieux on 2009-06-01
Alltray is ugly, you have two icons instead of one when new mail arrives.

---

### Post by goehle on 2009-11-11
It is something of a mystery why this is still an issue.  I mean, pidgin was able to minimize to the indicator applet, and now that we are in 9.10 empathy can do the same.  Why can't evolution?  Why can't someone write a plugin for evolution that will allow it to minimize to the indicator applet?

---

### Post by goehle on 2009-11-15
I've modified the evolution-indicator applet so that you can have evolution running in the background without a foreground window.  Disclaimers:

1.  I've done terrible things in making this work.  It will never be an accepted part of the source code.  But it (probably) works, if you want to use it. 

2.  Evolution will start up, vansih, and then start up again.  This is an artifact of the previously mentioned "terrible things".  It only does it at startup but it does look wierd. 

3.  I can't seem to get debdiff to work so I'm just going to upload the diff between the old and new evolution-indicator.c files

4.  This is the first time I've modified source code for something, so be warned.

---

### Post by themoodude on 2009-12-15
Hi,

I know I must sound like the unfortunate noob that I am here; but how exactly do I go about using your patch? I've partially migrated from Windows, and used to live with Outlook hidden from view but always there. I'm actually shocked that (with the default IM doing it perfectly) the default e-mail app (that is launched from and partially integrated into the applet) doesn't min or close to it.

But yeah; I'd love to check it out, but unfortunately have no idea where to start. Any help would be great.

Cheers!

---

### Post by JoeWheeler on 2010-02-04
How do apply this patch? Thanks

---

### Post by goehle on 2010-04-08
Gah, sorry.  I forgot about this thread.  Sorry!

Here are some instructions.  (This will only work for evolution version 0.2.4 and Jaunty). 

Download the attached file to your home directory. Then run the following: 

sudo apt-get build-dep evolution-indicator
apt-get source evolution-indicator
gunzip evolution-indicator.c.gz
mv evolution-indicator.c evolution-indicator-0.2.4/src/
cd evolution-indicator-0.2.4
./configure
make
sudo make install

Now you can remove all of the stuff thats been downloaded to your home directory and everything should work next time evolution is started.  

P.S.  Haven't actually tested this, so if you find any mistakes tell me. 
P.P.S.  This fix will get overwritten if you ever upgrade the evolution-indicator package.

---

### Post by darthpenguin on 2010-07-28
Hi. I must say that I agree. Why can't evolution run in the background. Thunderbird has the same issue. Even on windows you need a plugin to minimize to tray which is ridiculous. A mail client should run in the background an notify you when new mail arrives. Evolution (or Thunderbird) should run in the indicator-applet just like gwibber and empathy do. I use Thunderbird as it works perfect with gmail imap and use the "gnome integration" plugin to show it in the indicator applet. but it is little more than a launcher at this point. when I exit Thunderbird it should stay active in the applet, not shutdown completely.

---

### Post by choikwa on 2011-03-08
Why can't evolution run in the background like empathy does and have the mail icon turn green when mail has arrived like empathy does when a message is received?

---

