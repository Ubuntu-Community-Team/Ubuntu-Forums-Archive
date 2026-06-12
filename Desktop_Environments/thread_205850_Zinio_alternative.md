---
title: "Zinio alternative"
date: 2006-06-29
forum: Desktop Environments
---

### Post by rejser on 2006-06-29
I suddenly came across something I need and can't find an alternative for linux, Zinio magazine reader.
There is a magazine available through the zinio that is hard to get and a bit overpricy bought in store here. 
Anybody knows if it runs through wine or if there is a linux alternative (don't feel like paying before I atleast know there is a slight chance of success.

---

### Post by saracen on 2006-08-06
I'd like to know about this too

---

### Post by pgroover on 2006-10-07
This is one of the programs that's keeping me with one foot in the windows world.  If anyone knows of an alternative, please let me know as well.  I tried wine awhile back but it didn't work, but then again it was a half-hearted effort.

---

### Post by rejser on 2006-10-12
I've e-mailed the zinio company a while back asking if they had any sugestion what one should do. It was about a month ago and still no answer.

---

### Post by pgroover on 2006-10-12
I've tried it again with internetexplorer 4 u and still no luck.  It will download magazines but simply hangs when opening the reader... :(

If I have any luck, I'll post it here.

---

### Post by David Valentine on 2006-10-20
This is my vote for getting Zinio working in Linux.  Nowhere in my subscription to the digital version of Science did it say I had to be in Windows to read it.  Grrr...:evil:

---

### Post by linuxbert on 2006-10-28
Want something even more ironic (moronic?)? They've launched an exclusively Linux magazine in Zinio. ](*,)

---

### Post by rejser on 2006-11-08
](*,)  Doh! ](*,)

---

### Post by msaied on 2006-12-18
I am currently running zinio with wine my version is 3.6.0.6119 and except for slowness and the top buttons not refreshing correctly .. it works
to get it to work I followed some instructions in the wine website , and also i had to disable all advanced visual effects from zinio also in Wine you will have to specify the windows version to be win 98 .. in my case I discovered that disabling (winecfg->select the app->graphics)"Allow the window manager to control the windows " led to a much better performance
during installation of zinio make sure your connected to the web cause i remember seeing it check for something on line during setup
 also the zinio download manager also working fine and sets right in the corner of the task bar just like in windows .

---

### Post by pgroover on 2006-12-18
> **msaied said:**
> I am currently running zinio with wine my version is 3.6.0.6119 and except for slowness and the top buttons not refreshing correctly .. it works
to get it to work I followed some instructions in the wine website , and also i had to disable all advanced visual effects from zinio also in Wine you will have to specify the windows version to be win 98 .. in my case I discovered that disabling (winecfg->select the app->graphics)"Allow the window manager to control the windows " led to a much better performance
during installation of zinio make sure your connected to the web cause i remember seeing it check for something on line during setup
 also the zinio download manager also working fine and sets right in the corner of the task bar just like in windows .

Thanks for the tip, I will definitely give this a shot later tonight! :mrgreen:

---

### Post by pgroover on 2006-12-20
> **msaied said:**
> I am currently running zinio with wine my version is 3.6.0.6119 and except for slowness and the top buttons not refreshing correctly .. it works
to get it to work I followed some instructions in the wine website , and also i had to disable all advanced visual effects from zinio also in Wine you will have to specify the windows version to be win 98 .. in my case I discovered that disabling (winecfg->select the app->graphics)"Allow the window manager to control the windows " led to a much better performance
during installation of zinio make sure your connected to the web cause i remember seeing it check for something on line during setup
 also the zinio download manager also working fine and sets right in the corner of the task bar just like in windows .

I've installed it and can run it, but I have problems viewing any magazine.  I get error #22 and have tried everything on the Zinio site, but nothing has worked thus far.  Have you run across this problem?  I'm going to check the wine site...

---

### Post by msaied on 2006-12-26
I used to get the same error before I added the dll's : msxml3.dll , msxml3a.dll , msxml4.dll copy them to your system32 of wine and then use winecfg at the console to add them and set them as native(in the Libraries tab of winecfg). and in the same dialog at the first tab make sure your default is win98.

---

### Post by pgroover on 2006-12-26
> **msaied said:**
> I used to get the same error before I added the dll's : msxml3.dll , msxml3a.dll , msxml4.dll copy them to your system32 of wine and then use winecfg at the console to add them and set them as native(in the Libraries tab of winecfg). and in the same dialog at the first tab make sure your default is win98.

Yup, I had done all that and it still had the error.  Wine just got updated so I'm going to go for it again...  Are there any other dll's that you have in your libraries tab?  It's more than possible that there are some other dependencies...

thx

---

### Post by pgroover on 2006-12-26
Never mind, all is well now.  I simply didn't remove the original downloaded magazines before attempting to read them, the licensing is fine and I can now read them.  I also had to add the delivery manager and do the same configuration for it within winecfg though, otherwise I couldn't do anything when it started up.

Thanks again for the info.

---

