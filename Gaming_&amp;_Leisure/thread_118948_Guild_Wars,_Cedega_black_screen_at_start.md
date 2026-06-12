---
title: "Guild Wars, Cedega black screen at start?"
date: 2006-01-18
forum: Gaming &amp; Leisure
---

### Post by handy on 2006-01-18
Is there any comprehensive setup info' available on this problem?

I've been about the web to various wiki's & forums, they have no info that will help me with this apparently common problem for both ATI & nVidia GPU's.

I installed the CVS with no real problems.  Installed the Guild Wars client through cvscedega, no problems...

When I try to run GW, first I get the small GW window in the center of the screen, then it quickly flashes to a black screen & the mouse is trapped in a smaller window in the top left hand corner.  There is what is (probably) a cursor which I expect is in a name field & that's about it.

I have to do the 3 finger salute to bring up the System Monitor, so that I can kill the Wine process & get my computer back!

I have tried different screen resolutions, & had a tiny fiddle about in the .cvscedega config file.

So, if anyone has mastered this problem I (along with quite a few others I'm sure) would very much love to see a solution to the GW bsod!

Thanks in advance for any input...:KS

---

### Post by Cathbard on 2006-01-18
This should sort it out with any luck.
[Transgaming Forum: Guild Wars patch]("http://transgaming.org/forum/viewtopic.php?t=3927")

---

### Post by handy on 2006-01-18
Thanks for the reply.

I tried the fix.  

It prevents the black screen by not letting me proceed that far!!!  Which is pretty funny really. :D 

I have been wanting to just get to that log in screen, & then I would pay PlayNC for my GW client.

I guess I'll subscribe to GW & play it on the dreaded windoze untill cedega get their software patched up.

It's only a matter of time!

Thanks again :KS

---

### Post by Cathbard on 2006-01-20
I have been running GW under Ubuntu for quite some time. I just tried it again and it is working still.

Have you installed opengl and your video drivers?
I am using an FX5200 nvidia card and I'm pretty sure I installed the graphics using EasyUbuntu on this installation.

Your launch icon should say:
cedega -workdir "C:/Program Files/Guild Wars" "C:/Program Files/Guild Wars/Gw.exe"
if you installed it in the default location.

If you have already done that then here is a trick that may or may not work:
Install GW under winblows and set the video options so it matches the video settings you are using under linux. Go back into Ubuntu and copy the files from the windoze installation over the top of your linux installation of GW.
This was how I got GTA San Andreas to work. I don't know if it will help you or not in this case but it's an idea. You can always backup your files first (but it doesn't work anyway so ........)



Goodluck

---

### Post by alinuxfan on 2006-01-20
that's cool that you have the FX5200 at least that lets me know that mine should work...
Now, i don't have a windows partition so...
Handy I am going to try installing it all tomorrow (I have to leave in a bit to help a friend move)
Maybe if we are both looking at the problem we will be able to figure it out

---

### Post by Cathbard on 2006-01-20
I didn't have to install GW into winblows first to get it working myself.
I have succesfully installed GW under a few debian distros using cedega and they all worked fine.
The bit about installing it into winblows first is just a general gaming trick that sometimes works on other games.

---

