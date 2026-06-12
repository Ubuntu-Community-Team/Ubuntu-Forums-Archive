---
title: "xserver-xgl and compizconfig-settings-manager packages not present"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by Grimbergen on 2008-03-05
Hello,

I just reinstalled Ubuntu Gutsy Gibbon. At [[COLOR="Red"]this[/COLOR]]("http://www.ubuntu1501.com/2007/11/compiz-fusion-with-xgl-in-gutsy.html") site they explain how to activate compiz fusion but when I type sudo apt-get install xserver-xgl compizconfig-settings-manager in a terminal it sais that xserver-xgl and compizconfig-settings-manager packages could not be found.
What should I do ?

Thx in advance,
Grimergen

---

### Post by {BzF}~JOKesTER on 2008-03-05
Simple

In The Toolbar Goto:

System >> Preferences >> Control Center >>Synaptic Package Manager.

Click "Reload"

Now Click "Search" Type:

xserver-xgl 

And Hit Search

Check The Box That Comes Up With It On It.

Now Click "Search" Again And Type :

compizconfig-settings-manager

And Check Its Box.

Now Press The Apply Button And Wait For Them To Download -{It May Also Ask You To Insert Your Ubuntu Installation Disc - If So Do That And Hit "Ok"}

Hope This Helps!!

---

### Post by Grimbergen on 2008-03-05
What do you mean with  System-->Preferences-->Control Center ? It's not in the list ?
Synaptic package manager is in the list of administration, but with synaptic I cannot find it.

---

### Post by {BzF}~JOKesTER on 2008-03-05
Get In Synaptic Package Manager

Now Hit "Reload"

Now Hit "Search"

Now Search For Those Filenames.

UNDER NAME AND DESCRIPTION BEFORE YOU HIT SEARCH

Try That

Hope I'm Of Some Help To You

---

### Post by {BzF}~JOKesTER on 2008-03-05
> **Grimbergen said:**
> What do you mean with  System-->Preferences-->Control Center ? It's not in the list ?
Synaptic package manager is in the list of administration, but with synaptic I cannot find it.

Synaptic Package Manager Can Be Accessed In All Ubuntu Installs Through Control Center - {Not Always Under Administration}

What I Meant By System >> Preferences >> Control Center - Was To Navigate Through Those Tabs To Get There - {I Was Trying To Make It Easier To Understand}

I Hope This Stil Helps
:-({|=

---

### Post by Grimbergen on 2008-03-05
Unfortunately still no result and I did exactly what you said.
But thx for helping anyway.

---

### Post by {BzF}~JOKesTER on 2008-03-05
Ok Sorry About That.

By The Way What Version Of Ubuntu Are You Using?

---

### Post by Grimbergen on 2008-03-05
Gutsy Gibbon 7.10(1st post)
And a dell inspiron 1501

---

### Post by boeing777 on 2008-03-05
System-->Administration-Software Sources

under Ubuntu Software tab

check all the checkboxes, except source code

under Updates tab, check all the Ubuntu Updates checkboxes

then, turn on Compiz, it should automatically downloads all the required files

---

### Post by boeing777 on 2008-03-05
let me know if it works or not.

---

### Post by Grimbergen on 2008-03-05
Yes!!! That's it! It works now :-)
Thx so much!!

---

### Post by redDEADresolve on 2008-03-06
hey man your source list must be off.

check your source lists and make sure you have the necessary repos (boxes) checked.

you dont need to ubuntu partners, source code or back ports repo enabled

when you install ubuntu without an internet connection it doesn't enable any of the software repositories.

---

