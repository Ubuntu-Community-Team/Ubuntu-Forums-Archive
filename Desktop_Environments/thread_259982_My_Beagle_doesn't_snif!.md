---
title: "My Beagle doesn't snif!"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Monstroxus on 2006-09-18
I installed beagle and it seems it doesn't find anything, only some major programs. But no text files or whatever. I read on the beagle website that I have to switch of the indexing function and then switch it on again... but it still doesn't work. I also added some folders to index, but still nothing.
I assume that while indexing my pc's led will blink. But no such thing happens, so I guess I doesn't find anything because he didn't index.

What to do, any help is appreciated.

Regards.

---

### Post by beko on 2006-09-18
The same here & I still can't find any solution for this ](*,)

---

### Post by _asc_ on 2006-09-18
I have the same problem. Couldn't find a solution yet :(

---

### Post by chajuram on 2006-09-18
I am having the exact same problem on one computer, on another it works great by itself and through nautilus.

I would love to have a solution.

---

### Post by chajuram on 2006-09-18
I tried this and it seemd to work. 

1. uninstall beagle
> sudo apt-get remove beagle

2. Delete the directory .beagle from your home directory

3. install beagle
> sudo apt-get install beagle

4. open beagle and start indexing.

It seems to be working for my, beagle is indexing currently. 

Chajuram.

---

### Post by beko on 2006-09-18
> **chajuram said:**
> I tried this and it seemd to work. 

1. uninstall beagle


2. Delete the directory .beagle from your home directory

3. install beagle


4. open beagle and start indexing.

It seems to be working for my, beagle is indexing currently. 

Chajuram.

Thanks I will give it a try but could u find a way to make F12 work with it?

---

### Post by aleska on 2006-09-19
I believe the problem you are all encountering is simply because beagle is currently set to only index your home directory.  
Launch beagle.  Go to search -> preferences and select the indexing tab.  
You will note that by default it has "Index my home directory" selected.  If you also want to index stuff in /bin or /etc just add those folders.

Let me know if that works for you.
-aleska

---

### Post by beko on 2006-09-19
> **aleska said:**
> I believe the problem you are all encountering is simply because beagle is currently set to only index your home directory.  
Launch beagle.  Go to search -> preferences and select the indexing tab.  
You will note that by default it has "Index my home directory" selected.  If you also want to index stuff in /bin or /etc just add those folders.

Let me know if that works for you.
-aleska
NO I already add my 2 windows partitions also beside my home folder ....now I think "chajuram" solution worked for me & it started to snif again... now & I just have 1 small problem with the F12 that still won't work!!!!

---

### Post by _asc_ on 2006-09-19
Adding some other directories to the indexing tab does not work for me either. This was one of the first things I tried when I noticed that beagle does not work properly. 

I'll try chajuram solution as soon as I get home.

---

### Post by LedStyle on 2006-10-04
Try use this command:

beagle-search --icon

So try use the "f12" key.

---

### Post by _asc_ on 2006-10-04
[quote="LedStyle"]
Try use this command:

beagle-search --icon

So try use the "f12" key.
[/quote]

Thank's, F12 key is working now.

But I still think that Beagle does not work the way it should. I uninstalled it, deleted .beagle directory and reinstalled Beagle. I added the /etc directory but Beagle doesn't find anything when I search for e.g. xorg.conf. And shouldn't Beagle find emails as well (I use Thunderbird). 

"Start search and indexing services automatically" is checked in the search preferences.

Is there any special action I have to take to start indexing.

---

### Post by beko on 2006-10-04
> **LedStyle said:**
> Try use this command:

beagle-search --icon

So try use the "f12" key.

MAN YOU ARE A LIFE SAVER :p
Worked Perfect

Many Many Many Thanks

---

