---
title: "ContertXtoDVD won't see DVD burner"
date: 2008-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joemama123 on 2008-09-15
I'm new to Linux, so I'm just learning, but I'm willing to learn and use Linux!  I'm trying to run ConvertXtoDVD using Wine emulator.  I have Ubuntu 8.04.  When I run the program, it will convert the avi file to DVD format fine.  But when it comes to burning it won't recognize my internal DVD drive.  This is on a Dell Studio 15.  My drive is there and I can burn with native Linux software.  I just can't find one that can to what ConvertX does.

---

### Post by gellijack on 2008-11-06
I am a new ubuntu user and am having exactly the same problem as you. I got so fed up trying to fix this problem that I tried reinstalling XP only to find ubuntu's partition is stopping XP from doing that. I could fix that but thought someone would know how to fix our little problem, so as I love the idea of the Linux community I have stuck with it.

I can't find an answer to our problem. I have tried running ConX from wine's virtual C: drive; from ubuntu 8.04 desktop. Both ways ConX can't find the media drive. I have just downloaded Avidemux and I am planning on using that with Brasero. You could try that but they aren't a patch on ConX. It has to be that wine - conx -ubuntu are out of sync. Next I'm going to try putting a copy in the root directory and right clicking ConX and running it with wine (again, I know ).

Keep our fingers crossed that one of these experts twig to what we are obviously missing, which will be simple no doubt.

---

### Post by TenPlus1 on 2008-11-06
Go to [www.getdeb.net](www.getdeb.net) and try a program called DeVeDe that converts your movie files to DVD Video format and provides a really good menu editor (if needed), then burn the resulting .iso using Brasero...

---

### Post by joemama123 on 2008-11-06
> **gellijack said:**
> I am a new ubuntu user and am having exactly the same problem as you. I got so fed up trying to fix this problem that I tried reinstalling XP only to find ubuntu's partition is stopping XP from doing that. I could fix that but thought someone would know how to fix our little problem, so as I love the idea of the Linux community I have stuck with it.

I can't find an answer to our problem. I have tried running ConX from wine's virtual C: drive; from ubuntu 8.04 desktop. Both ways ConX can't find the media drive. I have just downloaded Avidemux and I am planning on using that with Brasero. You could try that but they aren't a patch on ConX. It has to be that wine - conx -ubuntu are out of sync. Next I'm going to try putting a copy in the root directory and right clicking ConX and running it with wine (again, I know ).

Keep our fingers crossed that one of these experts twig to what we are obviously missing, which will be simple no doubt.

Like TenPlus1 said, use DeVeDe to convert your avi file into an .iso image file.  Then I use K3B to burn the image to a DVD.  You can get both of these programs in the repository.  I have had good luck doing this, all my DVD's have worked so far.

---

